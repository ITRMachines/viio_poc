# Viio Proof of Concept (POC) - Documentation Repository

This repository contains the technical architectural documentation and interaction sequences for the core user flows of the Viio application. It serves as a bridge between the client-side implementation (`viio-project-client`) and the backend microservices ecosystem.

## 🚀 Proof of Operation (Videos)
Detailed walkthroughs and video materials showing each flow in action can be found at the following link:
[**Viio Proof of Operation - Video Materials (Google Drive)**](https://drive.google.com/drive/folders/1BHgoAO1VKHe4niV59LG8ieQulRZugbue?usp=drive_link)

---

## 📂 Documented User Flows

The repository is organized by feature area, each containing a dedicated `README.md` with scope details, technical breakdowns, and Mermaid sequence diagrams.

### 1. Account & Security
*   [**Authentication & Onboarding**](./auth_onboarding/README.md): Handle phone verification, login, and session initialization.
*   [**KYC Verification**](./kyc_verification/README.md): Identity validation with 3rd-party SDK integration.
*   [**Card Management**](./card_management/README.md): Security controls (PIN reset/change) and transaction limits.

### 2. Card Services
*   [**Virtual Card Creation**](./virtual_card_creation/README.md): Instant issuance of digital Mastercards.
*   [**Physical Card Lifecycle**](./physical_card_lifecycle/README.md): Tracking, activation, and logistics synchronization.

### 3. Fiat Operations (Cash In/Out)
*   [**Deposit (PSE)**](./deposit_pse/README.md): Real-time funding via Colombian banking network.
*   [**Bank Transfer Deposit**](./bank_transfer_deposit/README.md): Manual bank deposits with proof-of-payment (Voucher) verification.
*   [**Withdrawal (Bank Transfer)**](./withdrawal/README.md): Cashing out to traditional financial institutions.

### 4. Digital Asset Operations
*   [**Internal Transfer (P2P)**](./internal_transfer/README.md): Instant transfers between Viio users (zero-fee).
*   [**External Transfer (Withdrawal)**](./external_transfer/README.md): Sending USDC/Crypto to external blockchain wallets.
*   [**Receive (Crypto Deposit)**](./receive_crypto/README.md): Wallet address generation and monitoring for incoming on-chain funds.

---

## 🛠 Tech Stack Overview
- **Frontend**: Ionic React, Capacitor, RxJS.
- **Backend Architecture**: Node.js/Python Microservices.
- **Infrastructure**: Fireblocks (Crypto), Coltepay/Paymentez (Fiat), Sumsub/Metamap (KYC).

---
© 2026 Viio. Technical architecture documented for audit and development purposes.
