# IngressReportStatus.Api - RPC Calls Documentation

## Overview

The IngressReportStatus.Api project serves as an RPC server for report status tracking and statistics, providing endpoints for:
- Report status tracking
- Report package statistics
- Correction report status
- Correction progress monitoring

## RPC Calls by Category

### 1. Report Status Tracking

#### 1.1 Get Report Status by ID
- **Contract**: `RemotelyInvokable<ReportStatusByIdRequest, ReportStatusByIdResponse, string>()`
- **Request Type**: `ReportStatusByIdRequest`
  ```fsharp
  {
    ReportId: int64
    Edrpou: string
  }
  ```
- **Response Type**: `ReportStatusByIdResponse`
  ```fsharp
  {
    ReportId: int64
    Signature: string option
    UploadStartedAt: DateTime
    UploadFinishedAt: DateTime option
    SavedAt: DateTime option
    Status: ReportProcessingStatus
    Error: string option
  }
  ```

#### 1.2 Get Correction Report Status by ID
- **Contract**: `RemotelyInvokable<CorrectionReportStatusByIdRequest, CorrectionReportStatusByIdResponse, string>()`
- **Request Type**: `CorrectionReportStatusByIdRequest`
  ```fsharp
  {
    ReportId: int64
    Edrpou: string
  }
  ```
- **Response Type**: `CorrectionReportStatusByIdResponse`
  ```fsharp
  {
    ReportId: int64
    Signature: string option
    UploadStartedAt: DateTime
    UploadFinishedAt: DateTime option
    SavedAt: DateTime option
    ProcessedAt: DateTime option
    Status: CorrectionReportProcessingStatus
    Error: string option
  }
  ```

### 2. Report Package Statistics

#### 2.1 Get Reports Package Statistics by Days
- **Contract**: `RemotelyInvokable<ReportsPackagesStatisticByDaysRequest, ReportsPackagesStatisticResponse, string>()`
- **Request Type**: `ReportsPackagesStatisticByDaysRequest`
  ```fsharp
  {
    Edrpous: string array
    From: DateTime
    To: DateTime
    PageNumber: int
    PageSize: int
    SortWay: SortWay
    SortOrder: ReportsPackageStatisticSortOrder
  }
  ```
- **Response Type**: `ReportsPackagesStatisticResponse`
  ```fsharp
  {
    Organizers: OrganizerRow array
    Total: Period array
    TotalForAllPeriods: int
    Count: int
  }
  ```

#### 2.2 Get Reports Package Statistics by Hours
- **Contract**: `RemotelyInvokable<ReportsPackagesStatisticByHoursRequest, ReportsPackagesStatisticResponse, string>()`
- **Request Type**: `ReportsPackagesStatisticByHoursRequest`
  ```fsharp
  {
    Edrpous: string array
    Day: DateTime
    PageNumber: int
    PageSize: int
    SortWay: SortWay
    SortOrder: ReportsPackageStatisticSortOrder
  }
  ```
- **Response Type**: `ReportsPackagesStatisticResponse`
  ```fsharp
  {
    Organizers: OrganizerRow array
    Total: Period array
    TotalForAllPeriods: int
    Count: int
  }
  ```

### 3. Correction Progress Monitoring

#### 3.1 Check Any Correction in Progress
- **Contract**: `RemotelyInvokable<AnyCorrectionInProgressRequest, AnyCorrectionInProgressResponse, string>()`
- **Request Type**: `AnyCorrectionInProgressRequest`
  ```fsharp
  {
    Edrpou: string
  }
  ```
- **Response Type**: `AnyCorrectionInProgressResponse` (bool)

#### 3.2 Get Saved Correction Events
- **Contract**: `RemotelyInvokable<GetSavedCorrectionEvents, CorrectionSavedEvent array, string>()`
- **Request Type**: `GetSavedCorrectionEvents`
  ```fsharp
  {
    OrganizerIds: int array
  }
  ```
- **Response Type**: `CorrectionSavedEvent array`
  ```fsharp
  {
    Id: int64
    OrganizerId: int
    BetEventTimeRange: TimeRange option
    CurrencyOperationTimeRange: TimeRange option
  }
  ```
