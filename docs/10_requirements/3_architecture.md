# Architecture

## 1. Overview
Memoria Imaginum follows a client-server architecture consisting of an Angular frontend, a Spring Boot backend, and AWS-based infrastructure.

The frontend communicates with the backend through REST APIs. The backend handles business logic, authentication, metadata management, and access control. Photo files are stored in Amazon S3, while application data and photo metadata are stored in Amazon RDS.

## 2. System Architecture
┌──────────────────────┐
│       Client         │
│       Angular        │
└──────────┬───────────┘
           │
           │ REST API
           ▼
┌──────────────────────┐
│       Backend        │
│     Spring Boot      │
│                      │
│  - Authentication    │
│  - Photo Management  │
│  - Album Management  │
│  - Sharing           │
│  - Metadata          │
└───────┬────────┬─────┘
        │        │
        │        │
        ▼        ▼
┌────────────┐  ┌────────────┐
│ AWS RDS    │  │  AWS S3    │
│            │  │            │
│ User data  │  │ Photo files│
│ Metadata   │  │            │
│ Albums     │  │            │
│ Sharing    │  │            │
└────────────┘  └────────────┘

## 3. Components

### 3.1 Frontend
Technology: Angular, TypeScript, SCSS

The frontend provides the user interface for:
- User registration and login
- Photo upload
- Photo browsing
- Album management
- Photo search and filtering
- Photo metadata viewing
- Photo sharing
- Storage usage management

The frontend communicates with the backend through REST APIs.

### 3.2 Backend
Technology: Spring Boot, Java

The backend is responsible for:
- User authentication and authorization
- Photo and album management
- Photo metadata management
- Photo sharing and access control
- Storage usage management
- Communication with AWS services

The backend exposes REST APIs for the frontend.

### 3.3 Database
Technology: AWS RDS

AWS RDS stores structured application data, including:
- User information
- Photo metadata
- Album information
- Photo-album relationships
- Sharing information
- Storage usage information

Photo files themselves are not stored in the database.

### 3.4 Object Storage
Technology: AWS S3

AWS S3 is used to store the actual photo files.
The database stores references to the files rather than the photo binary data itself.

## 4. Data Flow

### 4.1 Photo Upload
User
  │
  │ Upload photo
  ▼
Angular
  │
  │ REST API
  ▼
Spring Boot
  │
  ├──────► AWS S3
  │         │
  │         └── Photo file
  │
  └──────► AWS RDS
            │
            └── Photo metadata


When a user uploads a photo:
- The frontend sends the photo to the backend.
- The backend processes the uploaded photo.
- Available metadata is extracted from the photo.
- The photo file is stored in AWS S3.
- Photo metadata and the S3 file reference are stored in AWS RDS.

### 4.2 Photo Retrieval
User
  │
  ▼
Angular
  │
  │ REST API
  ▼
Spring Boot
  │
  ├──────► AWS RDS
  │         │
  │         └── Photo metadata
  │
  └──────► AWS S3
            │
            └── Photo file

The backend verifies the user's access permissions before returning photo information or allowing access to the stored photo.

## 5. Access Control
Photos are private by default.

The backend is responsible for verifying whether a user has permission to access a photo or album.

Request
   │
   ▼
Authentication
   │
   ▼
Authorization
   │
   ├── Authorized ──► Allow access
   │
   └── Unauthorized ─► Deny access

For shared photos, access is granted only to users explicitly specified by the photo owner.

## 6. Architecture Principles
The frontend is responsible for presentation and user interaction.
The backend is responsible for business logic and access control.
AWS S3 is responsible for photo file storage.
AWS RDS is responsible for structured application data and metadata.
Private photo access is controlled by the backend.
Photo files and application data are stored separately.

## 7. Future Considerations
The architecture may be extended as the project grows.

Potential future considerations include:
- Direct client-to-S3 uploads using pre-signed URLs
- Image thumbnail generation
- CDN integration
- Background processing for metadata extraction
- Caching
- Automated backup and disaster recovery