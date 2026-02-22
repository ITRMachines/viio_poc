# User Profile & Settings

## Scope
This flow manages the user's identity data, security preferences, and account configurations. It ensures that personal information is kept up to date and that the user has control over their session security.

## Flow Details
1.  **Identity Management**:
    *   Users can view their registered data (Email, Phone, Name) managed by the `UserService`.
2.  **Security Prefs**:
    *   Configuration of Biometric login (FaceID/Fingerprint) and session timeout settings.
3.  **Support & Legal**:
    *   Direct access to help center and terms of service.

## Interaction Sequence Diagram
```mermaid
sequenceDiagram
    participant User
    participant Client as viio-project-client
    participant UserSvc as viio-project-usercredentials
    participant SessionMgr as AccountSessionManager
    participant DB as sqliteManager

    Client->>DB: Get Cached User Data (GET /stored-data)
    DB-->>Client: Stored Profile Information
    
    User->>Client: Edit Profile / Change Settings
    Client->>UserSvc: Update Metadata (PATCH /user-metadata)
    UserSvc-->>Client: Success + Updated Token
    
    Client->>SessionMgr: Update Local Session
    SessionMgr->>DB: Persist Updated Data
    
    User->>Client: Enable Biometrics
    Client->>Client: Capacitor Biometric Prompt
    Client->>DB: Store Biometric Preference
    DB-->>Client: Confirmed
```

## User Experience Showcase
[**User Profile Video Proof**](https://drive.google.com/drive/folders/1jnqZZV_ztyHFmv81iz2EzOFjoznwqDh8?usp=drive_link)
[**Onboarding Video Proof**](https://drive.google.com/drive/folders/1lQ2fNsq6vCTNHcvBGtSB4VLd3-HthPUW?usp=drive_link)