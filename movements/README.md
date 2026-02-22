# Transaction Movements & History

## Scope
This flow allows users to audit their financial history, providing detailed information for every credit and debit operation performed within the Viio ecosystem.

## Flow Details
1.  **History Retrieval**:
    *   The `transactionsManager` queries the `viio-project-transactions` service to fetch a paginated list of all previous operations.
2.  **Detail Audit**:
    *   Users can click on any movement to see metadata such as Transaction ID, Timestamp, Status (Completed/Pending/Rejected), and applied fees.
3.  **Data Persistence**:
    *   The app leverages local storage via `sqliteManager` to cache recent history for offline viewing and improved performance.

## User Experience Showcase
[**Movements Video Proof**](https://drive.google.com/drive/folders/1FJ4VdIVyd_0rQ_cyZNWlQH5WFp7bJVwc?usp=drive_link)
