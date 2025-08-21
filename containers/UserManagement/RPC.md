# UserManagement.Api

## Overview

## RPC Calls by Category

### 1. Authentication and Authorization

#### 1.1 Get Challenge
- **Contract**: `RemotelyInvokable<EmptyRequest, GetChallengeResponse, AuthSectionErrors>()`
- **Request Type**: `EmptyRequest` (no parameters)
- **Response Type**: `GetChallengeResponse`
  ```fsharp
  {
    Challenge: string
  }
  ```

#### 1.2 Login
- **Contract**: `RemotelyInvokable<ValidateChallengeRequest, AuthResponse, AuthSectionErrors>()`
- **Request Type**: `ValidateChallengeRequest`
  ```fsharp
  {
    Signature: string
  }
  ```
- **Response Type**: `AuthResponse`
  ```fsharp
  {
    Token: string
    User: User
  }
  ```

#### 1.3 Sign Up
- **Contract**: `RemotelyInvokable<UserRegistrationModel, AuthResponse, AuthSectionErrors>()`
- **Request Type**: `UserRegistrationModel`
  ```fsharp
  {
    EDRPOU: string
    Inn: string
    Phone: string
    Position: string
    Email: string
    Name: string
    ReturnUrl: string
  }
  ```
- **Response Type**: `AuthResponse`
  ```fsharp
  {
    Token: string
    User: User
  }
  ```

#### 1.4 Send Email Confirmation
- **Contract**: `RemotelyInvokable<VerifyEmailRequest, EmptyResponse, AuthSectionErrors>()`
- **Request Type**: `VerifyEmailRequest`
  ```fsharp
  {
    UserId: int64
    Email: string
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 1.5 Confirm Email
- **Contract**: `RemotelyInvokable<ConfirmEmailModel, AuthResponse, AuthSectionErrors>()`
- **Request Type**: `ConfirmEmailModel`
  ```fsharp
  {
    UserId: int64
    Token: string
  }
  ```
- **Response Type**: `AuthResponse`
  ```fsharp
  {
    Token: string
    User: User
  }
  ```

#### 1.6 Activate User
- **Contract**: `RemotelyInvokable<ActivationRequestModel, EmptyResponse, AuthSectionErrors>()`
- **Request Type**: `ActivationRequestModel`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

### 2. User Administration

#### 2.1 Get Activation Requests
- **Contract**: `RemotelyInvokable<GetActivationRequests, GetActivationRequestsResponse, HttpErrors>()`
- **Request Type**: `GetActivationRequests`
  ```fsharp
  {
    PageNumber: int
    PageSize: int
    SearchFilter: string option
    SortOrder: SortOrder
    SortWay: SortWay
    Roles: Role array
    Statuses: Status array
    Edrpous: string array
  }
  ```
- **Response Type**: `GetActivationRequestsResponse`
  ```fsharp
  {
    Count: int
    Items: ActivationRequest array
  }
  ```

#### 2.2 Get Users
- **Contract**: `RemotelyInvokable<GetUsersRequests, GetUsersResponse, HttpErrors>()`
- **Request Type**: `GetUsersRequests`
  ```fsharp
  {
    PageNumber: int
    PageSize: int
    SearchFilter: string option
    SortOrder: SortOrder
    SortWay: SortWay
    Roles: Role array
    Statuses: Status array
    Edrpous: string array
  }
  ```
- **Response Type**: `GetUsersResponse`
  ```fsharp
  {
    Count: int
    Items: User array
  }
  ```

#### 2.3 Get User History
- **Contract**: `RemotelyInvokable<UserHistoryRequest, UserHistoryResponse, HttpErrors>()`
- **Request Type**: `UserHistoryRequest`
  ```fsharp
  {
    UserId: int64
    PageNumber: int
    PageSize: int
  }
  ```
- **Response Type**: `UserHistoryResponse`
  ```fsharp
  {
    Count: int
    Items: HistoryItem array
  }
  ```

#### 2.4 Remove User
- **Contract**: `RemotelyInvokable<AdminActionWithReason, EmptyResponse, HttpErrors>("remove_user_endpoint")`
- **Request Type**: `AdminActionWithReason`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
    Reason: string
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 2.5 Block User
- **Contract**: `RemotelyInvokable<AdminActionWithReason, EmptyResponse, HttpErrors>("block_user_endpoint")`
- **Request Type**: `AdminActionWithReason`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
    Reason: string
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 2.6 Unblock User
- **Contract**: `RemotelyInvokable<AdminActionWithRole, EmptyResponse, HttpErrors>("unblock_user_endpoint")`
- **Request Type**: `AdminActionWithRole`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
    Role: Role
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 2.7 Approve User
- **Contract**: `RemotelyInvokable<AdminActionWithRole, EmptyResponse, HttpErrors>("approve_user_endpoint")`
- **Request Type**: `AdminActionWithRole`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
    Role: Role
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 2.8 Archive User
- **Contract**: `RemotelyInvokable<AdminActionWithReason, EmptyResponse, HttpErrors>("archive_user_endpoint")`
- **Request Type**: `AdminActionWithReason`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
    Reason: string
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 2.9 Change User Role
- **Contract**: `RemotelyInvokable<AdminActionWithRole, EmptyResponse, HttpErrors>("change_user_role_endpoint")`
- **Request Type**: `AdminActionWithRole`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
    Role: Role
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 2.10 Decline User
- **Contract**: `RemotelyInvokable<AdminActionWithReason, EmptyResponse, HttpErrors>("decline_user_endpoint")`
- **Request Type**: `AdminActionWithReason`
  ```fsharp
  {
    UserId: int64
    AdminId: int64
    Reason: string
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

### 3. User Profile Management

#### 3.1 Get Decline Info
- **Contract**: `RemotelyInvokable<ByUserIdRequest, DeclinedUserResponse, ProfileErrors>()`
- **Request Type**: `ByUserIdRequest`
  ```fsharp
  {
    UserId: int64
  }
  ```
- **Response Type**: `DeclinedUserResponse`
  ```fsharp
  {
    Reason: string
    Date: DateTime
  }
  ```

#### 3.2 Get User Image
- **Contract**: `RemotelyInvokable<ByUserIdRequest, ImageResponse, ProfileErrors>()`
- **Request Type**: `ByUserIdRequest`
  ```fsharp
  {
    UserId: int64
  }
  ```
- **Response Type**: `ImageResponse`
  ```fsharp
  {
    Image: byte array
  }
  ```

#### 3.3 Upload User Image
- **Contract**: `RemotelyInvokable<PutImageRequest, EmptyResponse, ProfileErrors>()`
- **Request Type**: `PutImageRequest`
  ```fsharp
  {
    UserId: int64
    Image: byte array
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 3.4 Delete User Image
- **Contract**: `RemotelyInvokable<ByUserIdRequest, EmptyResponse, ProfileErrors>()`
- **Request Type**: `ByUserIdRequest`
  ```fsharp
  {
    UserId: int64
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 3.5 Get User Profile
- **Contract**: `RemotelyInvokable<ByUserIdRequest, User, ProfileErrors>()`
- **Request Type**: `ByUserIdRequest`
  ```fsharp
  {
    UserId: int64
  }
  ```
- **Response Type**: `User`
  ```fsharp
  {
    Id: int64
    Inn: string
    Edrpou: string
    Email: string
    Name: string option
    Phone: string option
    Position: string option
    Role: Role
    Status: Status
    CreationDate: DateTime option
    ActivationDate: DateTime option
    Description: string option
    NewEmail: string option
    EmailConfirmationRequestDate: DateTime option
    RequestDate: DateTime option
    RequestReason: string option
    DeactivationDate: DateTime option
    DeactivationReason: string option
    OrganizationName: string option
  }
  ```

#### 3.6 Update User Profile
- **Contract**: `RemotelyInvokable<PutUserRequest, EmptyResponse, ProfileErrors>()`
- **Request Type**: `PutUserRequest`
  ```fsharp
  {
    UserId: int64
    Name: string option
    Phone: string option
    Position: string option
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 3.7 Update User Email
- **Contract**: `RemotelyInvokable<UpdateEmailModel, EmptyResponse, ProfileErrors>()`
- **Request Type**: `UpdateEmailModel`
  ```fsharp
  {
    UserId: int64
    NewEmail: string
  }
  ```
- **Response Type**: `EmptyResponse` (no data)

#### 3.8 Confirm Email Update
- **Contract**: `RemotelyInvokable<ConfirmEmailUpdateRequest, AuthResponse, ProfileErrors>()`
- **Request Type**: `ConfirmEmailUpdateRequest`
  ```fsharp
  {
    UserId: int64
    OldEmail: string
    NewEmail: string
  }
  ```
- **Response Type**: `AuthResponse`
  ```fsharp
  {
    Token: string
    User: User
  }
  ```

### 4. Notifications

#### 4.1 Get Notifications
- **Contract**: `RemotelyInvokable<GetNotificationsRequest, GetNotificationResponse, string>()`
- **Request Type**: `GetNotificationsRequest`
  ```fsharp
  {
    UserId: int64
    PageNumber: int
    PageSize: int
  }
  ```
- **Response Type**: `GetNotificationResponse`
  ```fsharp
  {
    Notifications: Notification array
    Count: int
  }
  ```

#### 4.2 Dismiss Notifications
- **Contract**: `RemotelyInvokable<DismissNotificationsRequest, EmptyResponse, string>()`
- **Request Type**: `DismissNotificationsRequest`
  ```fsharp
  {
    NotificationIds: int64 array
    UserId: int64
  }
  ```
- **Response Type**: `EmptyResponse` (no data)
