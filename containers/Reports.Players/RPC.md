# Reports.Players.Api

## Overview
## RPC Calls by Category

### 1. Receiveal and storage of the data, aggregated within the Reports service group

#### 1.1 Players Statistics Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<PlayersStatistic>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<PlayersStatistic>`
  ```fsharp
  {
    GamblingOrganizerId: int
    PlayerId: int64
    AmountPlaced: int64
    AmountPaid: int64
    WinningAmount: int64
    Day: DateOnly
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

### 2. Player Statistics Reports

#### 2.1 Players Statistics by Day
- **Contract**: `RemotelyInvokable<ByDayRequest, Response, string>()`
- **Request Type**: `ByDayRequest`
  ```fsharp
  {
    Edrpous: string array
    From: DateTime
    To: DateTime
    PageNumber: int
    PageSize: int
    SortOrder: SortOrder
    SortWay: SortWay
  }
  ```
- **Response Type**: `Response`
  ```fsharp
  {
    Items: ResponseItem array
  }
  ```
  Where `ResponseItem` is:
  ```fsharp
  {
    GamblingOrganizerId: int
    Edrpou: string
    GamblingOrganizerName: string
    PlayerId: int64
    AmountPlaced: int64
    AmountPaid: int64
    WinningAmount: int64
  }
  ```

#### 2.2 Players Statistics by Month
- **Contract**: `RemotelyInvokable<ByMonthRequest, Response, string>()`
- **Request Type**: `ByMonthRequest`
  ```fsharp
  {
    Edrpous: string array
    From: DateTime
    To: DateTime
    PageNumber: int
    PageSize: int
    SortOrder: SortOrder
    SortWay: SortWay
  }
  ```
- **Response Type**: `Response`
  ```fsharp
  {
    Items: ResponseItem array
  }
  ```

#### 2.3 Players Statistics by Quarter
- **Contract**: `RemotelyInvokable<ByQuarterRequest, Response, string>()`
- **Request Type**: `ByQuarterRequest`
  ```fsharp
  {
    Edrpous: string array
    From: DateTime
    To: DateTime
    PageNumber: int
    PageSize: int
    SortOrder: SortOrder
    SortWay: SortWay
  }
  ```
- **Response Type**: `Response`
  ```fsharp
  {
    Items: ResponseItem array
  }
  ```

#### 2.4 Players Statistics by Semester
- **Contract**: `RemotelyInvokable<BySemesterRequest, Response, string>()`
- **Request Type**: `BySemesterRequest`
  ```fsharp
  {
    Edrpous: string array
    From: DateTime
    To: DateTime
    PageNumber: int
    PageSize: int
    SortOrder: SortOrder
    SortWay: SortWay
  }
  ```
- **Response Type**: `Response`
  ```fsharp
  {
    Items: ResponseItem array
  }
  ```

#### 2.5 Players Statistics by Year
- **Contract**: `RemotelyInvokable<ByYearRequest, Response, string>()`
- **Request Type**: `ByYearRequest`
  ```fsharp
  {
    Edrpous: string array
    From: DateTime
    To: DateTime
    PageNumber: int
    PageSize: int
    SortOrder: SortOrder
    SortWay: SortWay
  }
  ```
- **Response Type**: `Response`
  ```fsharp
  {
    Items: ResponseItem array
  }
  ```
