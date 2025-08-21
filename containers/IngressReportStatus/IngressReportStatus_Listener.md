# IngressReportStatus.Listener

## Listened Events

### 1. Regular Report Events

#### 1.1 ReportUploadInitiatedEvent
- **Event Type**: `ReportUploadInitiatedEvent`
- **Event Structure**:
  ```fsharp
  {
    ReportId: int64               // Unique report identifier
    FileName: string              // Name of the uploaded file
    EDRPOU: string              
    UploadStartedAt: DateTime    
  }
  ```
- **Purpose**: Triggered when a regular report upload has been initiated (file is not yet persisted in the binray data storage). Updates the report status to "Uploading".

#### 1.2 ReportUploadFinishedEvent
- **Event Type**: `ReportUploadFinishedEvent`
- **Event Structure**:
  ```fsharp
  {
    ReportId: int64               // Unique report identifier
    FileName: string              // Name of the uploaded file
    Signature: string option      // Digital signature (if successful)
    EDRPOU: string              
    UploadFinishedAt: DateTime    
    Error: ReportUploadError option // Error details (if failed)
  }
  ```
- **Purpose**: Triggered when a regular report upload has completed (successfully or with error). Updates the report status to "Uploaded" with or without an error

#### 1.3 ReportSavedEvent
- **Event Type**: `ReportSavedEvent`
- **Event Structure**:
  ```fsharp
  {
    ReportId: int64               // Unique report identifier
    FileName: string              // Name of the processed file
    Signature: string             // Digital signature
    EDRPOU: string              
    Establishments: EstablishmentPair array option // Processing results
    SavedAt: DateTime           
    Error: ReportProcessingError option // Processing error (if any)
  }
  ```
- **Purpose**: Triggered when a report has been processed and ETL is done. Updates the report status to "Saved" with or without the processing error.

### 2. Correction Report Events

#### 2.1 CorrectionUploadingEvent
- **Event Type**: `CorrectionUploadingEvent`
- **Event Structure**:
  ```fsharp
  {
    ReportId: int64               // Unique correction report identifier
    FileName: string              // Name of the uploaded correction file
    EDRPOU: string              
    UploadStartedAt: DateTime    
  }
  ```
- **Purpose**: Same as for regular report

#### 2.2 CorrectionUploadedEvent
- **Event Type**: `CorrectionUploadedEvent`
- **Event Structure**:
  ```fsharp
  {
    ReportId: int64               // Unique correction report identifier
    FileName: string              // Name of the uploaded correction file
    Signature: string option      // Digital signature (if successful)
    EDRPOU: string             
    UploadStartedAt: DateTime    
    Error: ReportUploadError option // Error details (if failed)
  }
  ```
- **Purpose**: Same as for regular report

#### 2.3 CorrectionSavedEvent
- **Event Type**: `CorrectionSavedEvent`
- **Event Structure**:
  ```fsharp
  {
    ReportId: int64               // Unique correction report identifier
    FileName: string              // Name of the processed correction file
    Signature: string             // Digital signature
    EDRPOU: string             
    BetEventTimeRange: TimeRange option // Time range of corrected bet events
    CurrencyOperationTimeRange: TimeRange option // Time range of corrected currency operations
    SavingFinishedAt: DateTime    // When processing completed
    Error: CorrectionReportProcessingError option // Processing error (if any)
  }
  ```
- **Purpose**: Same as for regular report, then triggers report data re-aggregation for the affected period (days) as scheduled rollups are not performed for past dates.

#### 2.4 CorrectionReAggregatedEvent
- **Event Type**: `CorrectionReAggregatedEvent`
- **Event Structure**:
  ```fsharp
  {
    Corrections: int64 array      // Array of correction report IDs
    ProcessFinishedAt: DateTime  
    Error: CorrectionProcessedError option // Processing error (if any)
  }
  ```
- **Purpose**: Triggered when correction reports have been re-aggregated and updated data is already present in read models.
