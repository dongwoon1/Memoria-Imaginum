# Requirements

## 1. Overview
This document defines the functional and non-functional requirements for Memoria Imaginum.

Memoria Imaginum is a cloud-based photo management service designed to help users securely preserve, organize, and manage their photos and associated metadata. The service also allows users to selectively share their photos with trusted people while keeping their personal photo collection private by default.

## 2. User Requirements
- UR-001 — Account Management
Users should be able to create an account and securely log in to the service.

- UR-002 — Photo Backup
Users should be able to upload their photos and store them securely in the cloud.

- UR-003 — Photo Management
Users should be able to organize, browse, and manage their photos.

- UR-004 — Photo Information
Users should be able to view detailed information associated with their photos, including available metadata.

- UR-005 — Photo Search
Users should be able to search and filter their photos based on relevant information.

- UR-006 — Selective Sharing
Users should be able to share selected photos or albums with specific people.

- UR-007 — Storage Management
Users should be able to view and manage their cloud storage usage.

## 3. Functional Requirements

### 3.1 User Authentication
- FR-001 — User Registration
The system shall allow users to create an account.

- FR-002 — User Login
The system shall allow registered users to securely log in and log out.

- FR-003 — Authentication
The system shall restrict access to private user data to authenticated users.

### 3.2 Photo Upload and Storage
- FR-010 — Photo Upload
The system shall allow authenticated users to upload photos.

- FR-011 — Cloud Storage
The system shall store uploaded photo files in cloud storage.

- FR-012 — Upload Status
The system shall provide users with the status of photo uploads.

- FR-013 — Upload Failure
The system shall notify users when a photo upload fails.

- FR-014 — Photo Ownership
Each uploaded photo shall be associated with the user who uploaded it.

### 3.3 Photo Metadata
- FR-020 — Metadata Extraction
The system shall extract available metadata from uploaded photos.

- FR-021 — Capture Information
The system shall preserve available information such as capture date and time.

- FR-022 — Camera Information
The system shall preserve available camera and lens information.

- FR-023 — Shooting Information
The system shall preserve available shooting information such as ISO, aperture, shutter speed, and focal length.

- FR-024 — Location Information
The system shall preserve GPS information when it is available.

- FR-025 — Missing Metadata
The system shall allow photos with missing or incomplete metadata to be uploaded and managed normally.

### 3.4 Album Management
- FR-030 — Album Creation
Users shall be able to create albums.

- FR-031 — Add Photos to Album
Users shall be able to add photos to an album.

- FR-032 — Remove Photos from Album
Users shall be able to remove photos from an album without deleting the original photo.

- FR-033 — Album Management
Users shall be able to rename and delete their albums.

### 3.5 Photo Search and Filtering
- FR-040 — Photo Search
Users shall be able to search their photos.

- FR-041 — Filtering
Users shall be able to filter photos based on available information such as capture date, location, or album.

- FR-042 — Private Search Scope
Search results shall only include photos that the user is authorized to access.

### 3.6 Photo Sharing
- FR-050 — Selective Sharing
The system shall allow users to share selected photos or albums with specific people.

- FR-051 — Private by Default
Photos shall remain private unless the owner explicitly shares them.

- FR-052 — Shared Content Access
Recipients shall only be able to access photos or albums explicitly shared with them.

- FR-053 — Access Revocation
Users shall be able to revoke access to previously shared photos or albums.

- FR-054 — Shared Photo Information
Recipients shall be able to view the information associated with shared photos according to the owner's sharing settings.

- FR-055 — No Public Feed
The system shall not provide a public feed or public user profile that exposes a user's entire photo collection.

### 3.7 Storage Usage Management
- FR-060 — Storage Usage
The system shall display the user's current storage usage.

- FR-061 — Storage Limit
The system shall prevent users from uploading additional photos when their available storage limit has been exceeded.

- FR-062 — Storage Calculation
The system shall calculate storage usage based on the size of stored photo files and other applicable data.

## 4. Non-Functional Requirements
- NFR-001 — Security
Private photos and user information shall only be accessible to authorized users.

- NFR-002 — Data Protection
The system shall protect stored photos and metadata from unauthorized access or modification.

- NFR-003 — Reliability
The system should minimize the risk of photo loss or corruption during upload and storage.

- NFR-004 — Performance
The system should provide responsive photo browsing and metadata viewing under normal operating conditions.

- NFR-005 — Scalability
The system should be designed to accommodate an increasing number of users and stored photos.

## 5. Data Requirements
The system should manage the following information for each photo where available:
- Photo ID
- Owner ID
- File name
- File format
- File size
- Storage location
- Upload date
- Capture date and time
- GPS location
- Camera manufacturer and model
- Lens information
- ISO
- Aperture
- Shutter speed
- Focal length

For shared photos, the system should also manage:
- Photo or album ID
- Owner
- Recipient
- Sharing status
- Access permissions
- Sharing date
- Access expiration, if applicable

## 6. Out of Scope
The following features are not included in the current scope:
- Photo editing
- Photo printing
- Likes, comments, and follower systems
- Third-party cloud storage integration