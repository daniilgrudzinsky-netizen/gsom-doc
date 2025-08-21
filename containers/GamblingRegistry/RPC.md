# GamblingRegistry.Api

## Overview
## RPC Calls by Category

### 1. Gambling Organizer Management

#### 1.1 Create Gambling Organizer
- **Contract**: `RemotelyInvokable<CreateRequest, Response, string>()`
- **Request Type**: `ManageGamblingOrganizers.CreateRequest`
  ```fsharp
  {
    Edrpou: string
    Name: string
    Address: string
  }
  ```
- **Response Type**: `ManageGamblingOrganizers.Response`
  ```fsharp
  {
    Id: int
    Edrpou: string
    Name: string
    Address: string
  }
  ```

#### 1.2 Get Gambling Organizers
- **Contract**: `RemotelyInvokable<EmptyRequest, ResponseArray, string>()`
- **Request Type**: `EmptyRequest` (no parameters)
- **Response Type**: `ManageGamblingOrganizers.ResponseArray`
  ```fsharp
  {
    Array: Response array
  }
  ```

#### 1.3 Delete Gambling Organizer
- **Contract**: `RemotelyInvokable<DeleteRequest, EmptyResponse, string>("delete-organizer")`
- **Request Type**: `DeleteRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

### 2. Establishment Management

#### 2.1 Create Establishment
- **Contract**: `RemotelyInvokable<CreateRequest, Response, string>()`
- **Request Type**: `ManageEstablishments.CreateRequest`
  ```fsharp
  {
    Edrpou: string
    IsOnline: bool
    Address: string
    PermissionNumber: string option
    PermissionDate: DateTime option
    PermissionStatus: PermissionStatus option
    Description: string option
    CancellationDate: DateTime option
  }
  ```
- **Response Type**: `ManageEstablishments.Response`
  ```fsharp
  {
    Id: int
    Edrpou: string
    PublicId: int64
    IsOnline: bool
    Address: string
    PermissionNumber: string option
    PermissionDate: DateTime option
    PermissionStatus: PermissionStatus option
    CancellationDate: DateTime option
    Description: string option
  }
  ```

#### 2.2 Get Establishments
- **Contract**: `RemotelyInvokable<EmptyRequest, ResponseArray, string>()`
- **Request Type**: `EmptyRequest` (no parameters)
- **Response Type**: `ManageEstablishments.ResponseArray`
  ```fsharp
  {
    Array: Response array
  }
  ```

#### 2.3 Cancel Establishment
- **Contract**: `RemotelyInvokable<CancelRequest, EmptyResponse, string>("cancel-establishment")`
- **Request Type**: `CancelRequest`
  ```fsharp
  {
    Id: int
    CancellationDate: DateTime
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 2.4 Delete Establishment
- **Contract**: `RemotelyInvokable<DeleteRequest, EmptyResponse, string>("delete-establishment")`
- **Request Type**: `DeleteRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

### 3. Gambling License Management

#### 3.1 Create Gambling License
- **Contract**: `RemotelyInvokable<CreateRequest, Response, string>()`
- **Request Type**: `ManageGamblingLicences.CreateRequest`
  ```fsharp
  {
    Edrpou: string
    GamblingType: string
    Brand: string
    Number: string
    Description: string option
    LicenceStatus: LicenceStatus
    IssueDate: DateTime
    ExpirationDate: DateTime
    CancellationDate: DateTime option
    Establishments: int array
  }
  ```
- **Response Type**: `ManageGamblingLicences.Response`
  ```fsharp
  {
    Id: int
    Edrpou: string
    GamblingType: string
    GamblingTypeId: int16
    Brand: string
    Number: string
    Description: string option
    LicenceStatus: LicenceStatus
    IssueDate: DateTime
    ExpirationDate: DateTime
    CancellationDate: DateTime option
    Establishments: int array
  }
  ```

#### 3.2 Get Gambling Licenses
- **Contract**: `RemotelyInvokable<EmptyRequest, ResponseArray, string>()`
- **Request Type**: `EmptyRequest` (no parameters)
- **Response Type**: `ManageGamblingLicences.ResponseArray`
  ```fsharp
  {
    Array: Response array
  }
  ```

#### 3.3 Cancel Gambling License
- **Contract**: `RemotelyInvokable<CancelRequest, EmptyResponse, string>("cancel-gambling-licence")`
- **Request Type**: `CancelRequest`
  ```fsharp
  {
    Id: int
    CancellationDate: DateTime
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 3.4 Delete Gambling License
- **Contract**: `RemotelyInvokable<DeleteRequest, EmptyResponse, string>("delete-gambling-licence")`
- **Request Type**: `DeleteRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

### 4. Equipment License Management

#### 4.1 Create Equipment License
- **Contract**: `RemotelyInvokable<CreateRequest, Response, string>()`
- **Request Type**: `ManageEquipmentLicences.CreateRequest`
  ```fsharp
  {
    EstablishmentId: int
    LicenceNumber: string
    EquipmentType: string
    Number: string
    Description: string option
    LicenceStatus: LicenceStatus
    IssueDate: DateTime
    ExpirationDate: DateTime
    CancellationDate: DateTime option
    InstanceNumbers: string array
  }
  ```
- **Response Type**: `ManageEquipmentLicences.Response`
  ```fsharp
  {
    Id: int
    EstablishmentId: int
    LicenceNumber: string
    EquipmentType: string
    EquipmentTypeId: int16
    Number: string
    Description: string option
    LicenceStatus: LicenceStatus
    IssueDate: DateTime
    ExpirationDate: DateTime
    CancellationDate: DateTime option
    InstanceNumbers: string array
  }
  ```

#### 4.2 Get Equipment Licenses
- **Contract**: `RemotelyInvokable<EmptyRequest, ResponseArray, string>()`
- **Request Type**: `EmptyRequest` (no parameters)
- **Response Type**: `ManageEquipmentLicences.ResponseArray`
  ```fsharp
  {
    Array: Response array
  }
  ```

#### 4.3 Cancel Equipment License
- **Contract**: `RemotelyInvokable<CancelRequest, EmptyResponse, string>("cancel-equipment-licence")`
- **Request Type**: `CancelRequest`
  ```fsharp
  {
    Id: int
    CancellationDate: DateTime
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 4.4 Delete Equipment License
- **Contract**: `RemotelyInvokable<DeleteRequest, EmptyResponse, string>("delete-equipment-licence")`
- **Request Type**: `DeleteRequest`
  ```fsharp
  {
    Id: int
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

### 5. Registry Data Retrieval

#### 5.1 Get Gambling Organizers Registry
- **Contract**: `RemotelyInvokable<GamblingOrganizerRegistryRequest, WebServerArrayResponse<GamblingOrganizer>, string>()`
- **Request Type**: `GamblingOrganizerRegistryRequest` (unit type)
- **Response Type**: `WebServerArrayResponse<GamblingOrganizer>`
  ```fsharp
  {
    Items: GamblingOrganizer array
  }
  ```
  Where `GamblingOrganizer` is:
  ```fsharp
  {
    GamblingOrganizerId: int
    Name: string
    EDRPOU: string
  }
  ```

#### 5.2 Get Gambling Organizer Details
- **Contract**: `RemotelyInvokable<GamblingOrganizerDetailsRequest, GamblingOrganizerDetailsResponse, string>()`
- **Request Type**: `GamblingOrganizerDetailsRequest`
  ```fsharp
  {
    Edrpou: string
    EstablishmentId: int
    LicenceNumber: string
  }
  ```
- **Response Type**: `GamblingOrganizerDetailsResponse`
  ```fsharp
  {
    Edrpou: string
    Name: string
    Address: string
    Status: LicenceStatus
    Decision: string
    IssueDate: DateTime
    GamblingTypeId: int16
    EstablishmentIsOnline: bool
    EstablishmentPermission: string
    EstablishmentPermissionStatus: PermissionStatus option
    OpenDate: DateTime option
    CloseDate: DateTime option
    AddressAndArea: string
    EquipmentBlocks: EquipmentBlock array
  }
  ```

#### 5.3 Get Gambling Organizers Report
- **Contract**: `RemotelyInvokable<GamblingOrganizersReportRequest, GamblingOrganizersReportResponse, string>()`
- **Request Type**: `GamblingOrganizersReportRequest`
  ```fsharp
  {
    Edrpous: string array
    GamblingTypeIds: int16 array
    LicenceStatuses: LicenceStatus array
    PageSize: int
    PageNumber: int
    SortOrder: SortOrder
    SortWay: SortWay
  }
  ```
- **Response Type**: `GamblingOrganizersReportResponse` (contains paginated report items)

#### 5.4 Get Establishments Registry
- **Contract**: `RemotelyInvokable<EstablishmentsRegistryRequest, WebServerArrayResponse<Establishment>, string>()`
- **Request Type**: `EstablishmentsRegistryRequest` (unit type)
- **Response Type**: `WebServerArrayResponse<Establishment>`
  ```fsharp
  {
    Items: Establishment array
  }
  ```
  Where `Establishment` is:
  ```fsharp
  {
    Id: int32
    PublicId: int64
    GamblingOrganizerId: int32
    Address: string
    LicenceId: int32
    DateOpening: DateTime
    IsOnline: bool
    PermissionNumber: string option
    PermissionIssueDate: DateTime option
    PermissionCancellationDate: DateTime option
    PermissionStatus: PermissionStatus option
    DateClosing: DateTime option
  }
  ```

#### 5.5 Get Gambling Types
- **Contract**: `RemotelyInvokable<GamblingTypesRegistryRequest, WebServerArrayResponse<GamblingType>, string>()`
- **Request Type**: `GamblingTypesRegistryRequest` (unit type)
- **Response Type**: `WebServerArrayResponse<GamblingType>`
  ```fsharp
  {
    Items: GamblingType array
  }
  ```
  Where `GamblingType` is:
  ```fsharp
  {
    Id: int16
    Name: string
  }
  ```

#### 5.6 Get Equipment Types
- **Contract**: `RemotelyInvokable<EquipmentTypesRegistryRequest, WebServerArrayResponse<EquipmentType>, string>()`
- **Request Type**: `EquipmentTypesRegistryRequest` (unit type)
- **Response Type**: `WebServerArrayResponse<EquipmentType>`
  ```fsharp
  {
    Items: EquipmentType array
  }
  ```
  Where `EquipmentType` is:
  ```fsharp
  {
    Id: int16
    Name: string
  }
  ```

#### 5.7 Get Equipments Registry
- **Contract**: `RemotelyInvokable<EquipmentsRegistryRequest, Equipment array, string>()`
- **Request Type**: `EquipmentsRegistryRequest` (unit type)
- **Response Type**: `Equipment array`
  ```fsharp
  Equipment array
  ```
  Where `Equipment` is:
  ```fsharp
  {
    Id: int32
    EquipmentLicenceId: int32
    Number: string
  }
  ```

#### 5.8 Get Equipment Licenses Registry
- **Contract**: `RemotelyInvokable<EquipmentLicencesRegistryRequest, EquipmentLicence array, string>()`
- **Request Type**: `EquipmentLicencesRegistryRequest` (unit type)
- **Response Type**: `EquipmentLicence array`
  ```fsharp
  EquipmentLicence array
  ```
  Where `EquipmentLicence` is:
  ```fsharp
  {
    Id: int32
    EstablishmentId: int32
    GamblingLicenceId: int32
    EquipmentTypeId: int16
    Number: string
    Description: string
    Status: LicenceStatus
    IssueDate: DateTime
    ExpirationDate: DateTime
    CancellationDate: DateTime option
  }
  ```

#### 5.9 Get Gambling Licenses Registry
- **Contract**: `RemotelyInvokable<GamblingLicencesRegistryRequest, GamblingLicence array, string>()`
- **Request Type**: `GamblingLicencesRegistryRequest` (unit type)
- **Response Type**: `GamblingLicence array`
  ```fsharp
  GamblingLicence array
  ```
  Where `GamblingLicence` is:
  ```fsharp
  {
    Id: int32
    GamblingOrganizerId: int32
    GamblingTypeId: int16
    Brand: string
    Description: string option
    Number: string
    LicenceStatus: LicenceStatus
    IssueDate: DateTime
    ExpirationDate: DateTime
    CancellationDate: DateTime option
  }
  ```


