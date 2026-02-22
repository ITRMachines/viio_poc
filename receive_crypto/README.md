# Receive (Crypto Deposit) Flow

## Scope
This flow allows users to receive USDC or other crypto assets from external wallets. It provides the user with their unique blockchain address and QR code, and monitors the network for incoming transfers.

## Flow Details
1.  **Wallet Allocation**:
    *   The client fetches the user's unique deposit address for a specific network (e.g., Polygon, Ethereum) using `userService.getUserWalletAddressFromAsset`.
    *   Addresses are typically managed via Fireblocks.
2.  **Display & Sharing**:
    *   The `ReciverTransfer` component displays the full wallet address and a corresponding QR code.
    *   Users can copy the address to the clipboard or share it via native system dialogs.
3.  **Network Monitoring**:
    *   The user performs the transfer from an external wallet.
    *   Backend listeners (`viio-project-database-listener` or direct Fireblocks webhooks) monitor the blockchain for incoming transactions to the user's address.
4.  **Asynchronous Settlement**:
    *   When an incoming transfer is detected and reaches the required number of confirmations, the `viio-project-realtime-db-sync` and `balance-synchronization` services update the user's balance in real-time. The user is typically notified via push notification.

## User Experience Showcase
[Video Link Placeholder]

## Interaction Sequence Diagram
```mermaid
sequenceDiagram
    participant ExtWallet as External Wallet
    participant User
    participant Client as viio-project-client
    participant UserSvc as viio-project-usercredentials
    participant Fireblocks as viio-project-fireblocks
    participant SyncSvc as viio-project-realtime-db-sync

    Client->>UserSvc: Get Deposit Address (GET /wallet-address)
    UserSvc->>Fireblocks: Fetch/Assign Vault Address
    Fireblocks-->>UserSvc: Address String
    UserSvc-->>Client: Address & Chain Info
    
    Client->>User: Display Address & QR Code
    User->>ExtWallet: Send Crypto to Address
    
    ExtWallet->>Fireblocks: Incoming Blockchain Transaction
    Fireblocks->>SyncSvc: Webhook: Incoming Funds
    SyncSvc->>SyncSvc: Update User Balance
    SyncSvc-->>Client: Push Notif: "Funds Received"
```
