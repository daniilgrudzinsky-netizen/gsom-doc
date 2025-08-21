# EventsWarehouse.Api.Monitoring
## Overview

## RPC Calls by Category

### 1. Monitoring Operations

#### 1.1 Currency Operation Monitoring
- **Contract**: `RemotelyInvokable<CurrencyOperationInfoRequest, CurrencyOperationInfoResponse, string>()`
- **Request Type**: `CurrencyOperationInfoRequest`
  ```fsharp
  {
    TimeRange: TimeRange
    GamblingOrganizerId: int
    AmountRange: AmountRange
    EstablishmentId: int option
    Kind: TransactionKind option
    PlayerId: int64 option
    PageNumber: int
    PageSize: int
  }
  ```
- **Response Type**: `CurrencyOperationInfoResponse`
  ```fsharp
  {
    Count: int
    Items: CurrencyOperationReportModel array
  }
  ```

#### 1.2 Bet Event Monitoring
- **Contract**: `RemotelyInvokable<BetEventInfoRequest, BetEventInfoResponse, string>()`
- **Request Type**: `BetEventInfoRequest`
  ```fsharp
  {
    TimeRange: TimeRange
    GamblingOrganizerId: int
    AmountRange: AmountRange
    EstablishmentId: int option
    Equipment: string option
    EquipmentTypeId: int16 option
    PlayerId: int64
    PageNumber: int
    PageSize: int
  }
  ```
- **Response Type**: `BetEventInfoResponse`
  ```fsharp
  {
    Count: int
    Items: BetEventReportModel array
    Establishments: BetEventEstablishmentInfo array
  }
  ```

### 2. Registry Validation

#### 2.1 Check Gambling Organizer in Reports
- **Contract**: `RemotelyInvokable<IdRequest, IsExistResponse, string>("gambling-organizer")`
- **Request Type**: `IdRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `IsExistResponse`
  ```fsharp
  {
    IsExist: bool
  }
  ```

#### 2.2 Check Establishment in Reports
- **Contract**: `RemotelyInvokable<IdRequest, IsExistResponse, string>("establishment")`
- **Request Type**: `IdRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `IsExistResponse`
  ```fsharp
  {
    IsExist: bool
  }
  ```

#### 2.3 Check Gambling License in Reports
- **Contract**: `RemotelyInvokable<IdRequest, IsExistResponse, string>("gambling-licence")`
- **Request Type**: `IdRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `IsExistResponse`
  ```fsharp
  {
    IsExist: bool
  }
  ```

#### 2.4 Check Equipment License in Reports
- **Contract**: `RemotelyInvokable<IdRequest, IsExistResponse, string>("equipment-licence")`
- **Request Type**: `IdRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `IsExistResponse`
  ```fsharp
  {
    IsExist: bool
  }
  ```
