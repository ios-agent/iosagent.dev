# Integration Patterns

Practical patterns for integrating ProximityReader into production apps.

## Table of Contents

1. [SwiftUI + MVVM Architecture](#swiftui--mvvm-architecture)
2. [PSP Integration Patterns](#psp-integration-patterns)
3. [Combined Payment + Loyalty Flow](#combined-payment--loyalty-flow)
4. [Store and Forward Offline Pattern](#store-and-forward-offline-pattern)
5. [Session Lifecycle Management](#session-lifecycle-management)

---

## SwiftUI + MVVM Architecture

### Payment View Model

```swift
import ProximityReader
import Observation

@Observable
@MainActor
class PaymentViewModel {
    // MARK: - State
    var amount: Decimal = 0
    var isReady = false
    var isProcessing = false
    var readProgress: Int = 0
    var errorMessage: String?
    var transactionComplete = false
    
    // MARK: - Private
    private let reader = PaymentCardReader()
    private var session: PaymentCardReaderSession?
    private var eventTask: Task<Void, Never>?
    
    // MARK: - Setup
    
    func setup(pspToken: String) async {
        guard PaymentCardReader.isSupported else {
            errorMessage = "Tap to Pay is not supported on this device."
            return
        }
        
        do {
            let token = PaymentCardReader.Token(rawValue: pspToken)
            
            // Link account if needed (first-time setup)
            if try await !reader.isAccountLinked(using: token) {
                try await reader.linkAccount(using: token)
            }
            
            // Create and prepare session
            session = try await PaymentCardReaderSession(reader: reader, token: token)
            try await session?.prepare()
            
            // Observe events
            observeEvents()
            
            isReady = true
        } catch {
            errorMessage = "Setup failed: \(error.localizedDescription)"
        }
    }
    
    // MARK: - Read Payment
    
    func readPayment() async {
        guard let session, amount > 0 else { return }
        
        isProcessing = true
        errorMessage = nil
        
        do {
            let request = PaymentCardTransactionRequest(
                amount: amount,
                currencyCode: "USD",
                type: .purchase
            )
            
            let result = try await session.readPaymentCard(request)
            
            // Send to PSP for processing
            try await processWithPSP(result.paymentCardData)
            
            transactionComplete = true
            
            // Re-prepare for next transaction
            try await session.prepare()
            
        } catch let error as PaymentCardReaderSession.ReadError {
            handleReadError(error)
        } catch let error as PaymentCardReaderError {
            handleReaderError(error)
        } catch {
            errorMessage = "Payment failed: \(error.localizedDescription)"
        }
        
        isProcessing = false
    }
    
    // MARK: - Events
    
    private func observeEvents() {
        eventTask?.cancel()
        eventTask = Task {
            guard let session else { return }
            for await event in session.events {
                switch event {
                case .updateProgress(let progress):
                    readProgress = progress
                case .ready:
                    isReady = true
                case .notReady:
                    isReady = false
                case .readCompleted:
                    readProgress = 100
                case .readCancelled:
                    isProcessing = false
                default:
                    break
                }
            }
        }
    }
    
    // MARK: - Error Handling
    
    private func handleReadError(_ error: PaymentCardReaderSession.ReadError) {
        switch error {
        case .cancelled:
            errorMessage = nil // User cancelled, no error to show
        case .invalidAmount:
            errorMessage = "Invalid payment amount."
        case .notReady:
            errorMessage = "Reader not ready. Please wait."
        default:
            errorMessage = "Read error: \(error)"
        }
    }
    
    private func handleReaderError(_ error: PaymentCardReaderError) {
        switch error {
        case .backgrounded:
            errorMessage = "App was backgrounded. Please try again."
            Task { try? await session?.prepare() }
        case .networkError:
            errorMessage = "Network error. Check your connection."
        case .invalidReaderToken:
            errorMessage = "Session expired. Please restart."
        default:
            errorMessage = "Reader error: \(error)"
        }
    }
    
    private func processWithPSP(_ cardData: String?) async throws {
        // Send cardData to your PSP's backend for processing
        // Implementation depends on your PSP (Stripe, Adyen, Square, etc.)
    }
    
    deinit {
        eventTask?.cancel()
    }
}
```

### SwiftUI Payment View

```swift
import SwiftUI

struct PaymentView: View {
    @State private var viewModel = PaymentViewModel()
    @State private var amountText = ""
    
    let pspToken: String
    
    var body: some View {
        VStack(spacing: 24) {
            // Amount Input
            TextField("Amount", text: $amountText)
                .keyboardType(.decimalPad)
                .font(.largeTitle)
                .multilineTextAlignment(.center)
                .onChange(of: amountText) { _, newValue in
                    viewModel.amount = Decimal(string: newValue) ?? 0
                }
            
            // Status
            if viewModel.isProcessing {
                ProgressView("Reading card...")
                    .progressViewStyle(.circular)
                
                if viewModel.readProgress > 0 {
                    ProgressView(value: Double(viewModel.readProgress), total: 100)
                }
            }
            
            // Error
            if let error = viewModel.errorMessage {
                Text(error)
                    .foregroundStyle(.red)
                    .font(.callout)
            }
            
            // Charge Button
            Button("Charge") {
                Task { await viewModel.readPayment() }
            }
            .buttonStyle(.borderedProminent)
            .controlSize(.large)
            .disabled(!viewModel.isReady || viewModel.isProcessing || viewModel.amount <= 0)
            
            // Success
            if viewModel.transactionComplete {
                Label("Payment Complete", systemImage: "checkmark.circle.fill")
                    .foregroundStyle(.green)
                    .font(.title2)
            }
        }
        .padding()
        .task {
            await viewModel.setup(pspToken: pspToken)
        }
    }
}
```

---

## PSP Integration Patterns

### Stripe

Stripe wraps ProximityReader in their Terminal SDK. You can either use Stripe's SDK (simpler) or use ProximityReader directly with Stripe as the token provider.

```swift
// Using Stripe Terminal SDK (recommended for Stripe users)
import StripeTerminal

// Stripe handles ProximityReader internally
let config = try LocalMobileDiscoveryConfiguration(simulated: false)
let cancelable = Terminal.shared.discoverReaders(config, delegate: self) { readers, error in
    guard let reader = readers?.first else { return }
    Terminal.shared.connectLocalMobileReader(reader, delegate: self) { reader, error in
        // Reader connected, ready for payments
    }
}
```

```swift
// Using ProximityReader directly with Stripe token
// 1. Get token from your backend (which calls Stripe's API)
let stripeToken = try await fetchStripeReaderToken()
let token = PaymentCardReader.Token(rawValue: stripeToken)

// 2. Standard ProximityReader flow
let session = try await PaymentCardReaderSession(reader: reader, token: token)
// ... continue with normal flow
```

### Adyen

```swift
// Adyen provides their own iOS Mobile SDK
// But the token can also be used directly with ProximityReader
let adyenToken = try await fetchAdyenReaderToken()
let token = PaymentCardReader.Token(rawValue: adyenToken)
```

### Generic PSP Pattern

```swift
protocol PaymentServiceProvider {
    func fetchReaderToken() async throws -> String
    func processPayment(cardData: String, amount: Decimal, currency: String) async throws -> PaymentResult
    func processRefund(cardData: String, amount: Decimal, currency: String) async throws -> RefundResult
}

class TapToPayService {
    private let psp: PaymentServiceProvider
    private let reader = PaymentCardReader()
    private var session: PaymentCardReaderSession?
    
    init(psp: PaymentServiceProvider) {
        self.psp = psp
    }
    
    func initialize() async throws {
        let jwt = try await psp.fetchReaderToken()
        let token = PaymentCardReader.Token(rawValue: jwt)
        
        if try await !reader.isAccountLinked(using: token) {
            try await reader.linkAccount(using: token)
        }
        
        session = try await PaymentCardReaderSession(reader: reader, token: token)
        try await session?.prepare()
    }
    
    func charge(amount: Decimal, currency: String) async throws -> PaymentResult {
        guard let session else { throw TapToPayError.notInitialized }
        
        let request = PaymentCardTransactionRequest(
            amount: amount,
            currencyCode: currency,
            type: .purchase
        )
        
        let readResult = try await session.readPaymentCard(request)
        
        guard let cardData = readResult.paymentCardData else {
            throw TapToPayError.noCardData
        }
        
        let paymentResult = try await psp.processPayment(
            cardData: cardData,
            amount: amount,
            currency: currency
        )
        
        // Re-prepare for next transaction
        try await session.prepare()
        
        return paymentResult
    }
}
```

---

## Combined Payment + Loyalty Flow

```swift
func chargeWithLoyalty(
    amount: Decimal,
    currency: String,
    loyaltyPassIdentifier: String
) async throws -> (PaymentCardReadResult, VASReadResult?) {
    guard let session else { throw TapToPayError.notInitialized }
    
    let paymentRequest = PaymentCardTransactionRequest(
        amount: amount,
        currencyCode: currency,
        type: .purchase
    )
    
    let vasRequest = VASRequest(
        merchantIdentifier: loyaltyPassIdentifier,
        localizedDescription: "Scan your loyalty card"
    )
    
    // Single tap reads both payment AND loyalty card
    let result = try await session.readPaymentCard(
        paymentRequest,
        vasRequest: vasRequest
    )
    
    // Process payment
    if let cardData = result.paymentCardData {
        try await psp.processPayment(cardData: cardData, amount: amount, currency: currency)
    }
    
    // Process loyalty (may be nil if customer has no matching pass)
    if let vasResult = result.vasReadResult {
        for entry in vasResult.entries where entry.status == .success {
            try await loyaltyService.recordVisit(identifier: entry.identifier)
        }
    }
    
    try await session?.prepare()
    
    return (result, result.vasReadResult)
}
```

---

## Store and Forward Offline Pattern

```swift
@Observable
@MainActor
class OfflinePaymentManager {
    var pendingBatchCount = 0
    var pendingTransactionCount = 0
    
    private let reader = PaymentCardReader()
    private var sfSession: StoreAndForwardPaymentCardReaderSession?
    private let store = PaymentCardReaderStore()
    
    func initialize(token: PaymentCardReader.Token) async throws {
        sfSession = try await StoreAndForwardPaymentCardReaderSession(
            reader: reader,
            token: token
        )
        try await sfSession?.prepare()
        await refreshStatus()
    }
    
    /// Accept payment offline — stored securely on device
    func acceptPayment(amount: Decimal, currency: String) async throws {
        guard let sfSession else { throw TapToPayError.notInitialized }
        
        let request = PaymentCardTransactionRequest(
            amount: amount,
            currencyCode: currency,
            type: .purchase
        )
        
        _ = try await sfSession.readPaymentCard(request)
        try await sfSession.prepare()
        await refreshStatus()
    }
    
    /// Upload all stored batches when connectivity is restored
    func syncPendingTransactions() async throws {
        let batches = try await store.allBatches()
        
        for batch in batches {
            do {
                // Send to PSP
                try await psp.submitBatch(batch.data)
                // Delete on success
                try await store.delete(using: batch.deletionToken)
            } catch {
                // Skip this batch, try next
                continue
            }
        }
        
        await refreshStatus()
    }
    
    private func refreshStatus() async {
        if let status = try? await store.status {
            pendingBatchCount = status.batchCount
            pendingTransactionCount = status.totalTransactionCount
        }
    }
}
```

---

## Session Lifecycle Management

Critical pattern: handle app backgrounding and foregrounding properly.

```swift
@Observable
@MainActor
class ReaderSessionManager {
    private var session: PaymentCardReaderSession?
    private var scenePhaseTask: Task<Void, Never>?
    
    /// Call from SwiftUI's .onChange(of: scenePhase)
    func handleScenePhase(_ phase: ScenePhase) {
        switch phase {
        case .active:
            // CRITICAL: Re-prepare when returning to foreground
            Task {
                do {
                    try await session?.prepare()
                } catch {
                    // Handle re-preparation failure
                }
            }
        case .background:
            // Session is automatically invalidated by the system
            // No action needed, but prepare() is required on return
            break
        default:
            break
        }
    }
}

// In your SwiftUI App or root view:
struct ContentView: View {
    @Environment(\.scenePhase) var scenePhase
    @State private var sessionManager = ReaderSessionManager()
    
    var body: some View {
        PaymentView()
            .onChange(of: scenePhase) { _, newPhase in
                sessionManager.handleScenePhase(newPhase)
            }
    }
}
```
