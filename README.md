# Voucher Purchase Screen (Flutter)

A Flutter implementation of a Voucher Purchase Screen with clean architecture, reactive state management using Riverpod, and strict separation of business logic from UI.

---

## 🚀 Features

- Dynamic voucher purchase flow
- Real-time calculation of:
  - Discount
  - Savings
  - Final payable amount
- Amount validation (min/max constraints)
- Reactive UI updates using Riverpod
- Clean separation of concerns
- Sticky Pay button with dynamic state

---

## 🏗️ Project Structure


lib/
│── core/
│ ├── theme/
│ └── constants/
│
│── data/
│ ├── models/
│ │ └── voucher_model.dart
│ └── repository/
│ └── voucher_repository.dart
│
│── state/
│ ├── voucher_state.dart
│ ├── voucher_notifier.dart
│ └── voucher_provider.dart
│
│── presentation/
│ ├── screens/
│ │ └── voucher_purchase_screen.dart
│ └── widgets/
│
│── main.dart


---

## 🔄 State Management & Flow

This project uses **Riverpod (StateNotifier)** for state management.

### Flow:

Repository → StateNotifier → UI


- **Repository**
  - Provides voucher data (mock JSON)
- **StateNotifier**
  - Handles all business logic and validations
- **UI**
  - Listens to state and rebuilds reactively

---

## 🧠 Business Logic

All business logic is centralized inside the `VoucherNotifier`.

### Calculations:
- `discountAmount = amount * percent / 100`
- `youPay = (amount - discountAmount) * quantity`
- `savings = discountAmount * quantity`

### Validation Rules:
- Amount must be between `minAmount` and `maxAmount`
- Amount must not be empty or zero

---

## 💳 Pay Button Logic

The Pay button is **disabled** when:
- `disablePurchase == true`
- Amount is invalid (below min or above max)
- Amount is empty or zero

The UI reacts to the computed `isPurchaseDisabled` state from the notifier.

---

## 🎯 UI Components

- Header with Refer & Earn + Close button
- Voucher card with dynamic discount
- Amount input field with validation
- YOU PAY & SAVINGS summary card
- Payment method selector (UPI / Card)
- Quantity stepper
- Redeem steps section
- Sticky Pay button

---

## ▶️ Getting Started

### Prerequisites
- Flutter SDK (>= 3.x)

### Run the App
```bash
flutter pub get
flutter run
📦 Dependencies
flutter_riverpod
📌 Key Design Decisions
Removed unnecessary layers (controller, service) to simplify architecture
Centralized all business logic in StateNotifier
Ensured UI is fully reactive and contains no logic
Maintained a unidirectional data flow for scalability
📸 Screenshots

(Add your UI screenshots here)

🔗 Submission
GitHub Repository: https://github.com/tsttyy/Voucher-Purchase-Screen
Live Demo:https://vocher-15711.web.app/
