# EventsWarehouse.Listener.IngressRegularReportETL


## Listened Events


### 1. ReportUploaded
- **Event Type**: `ReportUploaded`
- **Contract**: Broadcast event from IngressReportUpload.Gateway
- **Event Structure**:
  ```fsharp
  {
    Key: string                    // Report file key/identifier
    UploadFinishedAt: DateTime    
    ReportId: int64               // Unique report identifier
    Signature: string             // Digital signature of the report
    EDRPOU: string              
  }
  ```
- **Purpose**: Triggered when a file with operations has been successfully uploaded and it's authentity validated. This event initiates the ETL process to extract data from the uploaded report and load it into the EventsWarehouse database.

## Processing Flow

1. **Event Reception**: The listener receives `ReportUploaded` events from the IngressReportUpload.Gateway
2. **Data Extraction**: Download report from the binary storage, extracts bet events and currency operations from the report file
3. **Data Validation**: Validates the extracted data against registry information (gambling organizers, establishments, licenses)
4. **Database Storage**: Stores the processed data in the EventsWarehouse database if all events are valid.
5. **Event Broadcasting**: Publishes `ReportSavedEvent` to notify other services about the report processing status

