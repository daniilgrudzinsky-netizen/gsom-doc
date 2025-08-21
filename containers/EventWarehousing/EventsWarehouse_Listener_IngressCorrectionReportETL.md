# EventsWarehouse.Listener.IngressCorrectionReportETL

## Listened Events

### CorrectionUploaded
- **Event Type**: `CorrectionUploaded`
- **Event Structure**:
  ```fsharp
  {
    Key: string                    // Correction report file key/identifier
    UploadFinishedAt: DateTime     
    ReportId: int64               // Unique correction report identifier
    Signature: string             // Digital signature of the correction report
    EDRPOU: string               
  }
  ```
- **Purpose**: Triggered when a correction report (file) has been successfully uploaded and it's authentity validated. This event initiates the correction ETL process. Validates the data and store it only if valid, othervise mark report as invalid. 

## Processing Flow

1. **Event Reception**: The listener receives `CorrectionUploaded` event when report file is uploaded and it's authentity confirmed.
2. **Data Validation**: Validates the correction data against registry information and existing data
3. **Correction Application**: Create a compensation events for previously processed bet events and currency operations. Then create new event records with updated information if needed.
4. **Database Updates**: Updates the EventsWarehouse database with corrected data
5. **Event Broadcasting**: Publishes `CorrectionSavedEvent` to notify other services about processing result (success/error)
