# Signature RPC Server

## RPC Operations

### 1. Validate Challenge Signature
- **Contract**: `RemotelyInvokable<SignValidationRequest, SignValidationResponse, string>()`
- **Request Type**: `SignValidationRequest`
  ```fsharp
  {
    Data: byte[]                    // Challenge data to validate
    Sign: byte[]                    // Digital signature to verify
  }
  ```
- **Response Type**: `SignValidationResponse`
  ```fsharp
  {
    SignerEdrpou: string            // EDRPOU of the signature owner
    SignerInn: string               // INN of the signature owner
    SignerCommonName: string        // Common name of the signature owner
  }
  ```
- **Purpose**: Validates digital signatures of the authorization challenge. Used during login processes to verify user's ownership of the digital signature key. Response properties are present only if key, used for report signature, is valid (not expired and not revoked).

### 2. Validate Report File Signature
- **Contract**: `RemotelyInvokable<ReportValidationRequest, ReportValidationResponse, string>()`
- **Request Type**: `ReportValidationRequest`
  ```fsharp
  {
    UploadLink: string              // link to download the full file being verified
    Sign: string                    // Digital signature of the report
    Key: string                     // Report file key/identifier
    ReportId: int64                 // Unique report identifier
  }
  ```
- **Response Type**: `ReportValidationResponse`
  ```fsharp
  {
    SignerEdrpou: string            // EDRPOU of the report signer
    SignerInn: string               // INN of the report signer
    SignerCommonName: string        // Common name of the report signer
    Key: string                     // Report file key/identifier
    ReportId: int64                 // Unique report identifier
    Signature: string               // Validated signature
    ConfirmationSignature: string   // Confirmation signature for the response
  }
  ```
- **Purpose**: Validates digital signatures of uploaded report files. Ensures data integrity and authenticity of submitted file before further processing. Returned confirmation signature is signed with the digital key, owned by application. It is meant to be stored by organizator to ensure report delivery to system and may be used as a legal proof of report delivery.

