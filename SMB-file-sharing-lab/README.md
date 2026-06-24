# Windows SMB File Sharing, Authentication & Access Control Lab

## Project Summary

Designed and implemented a secure SMB file-sharing environment on Windows 11 with access validation from Linux and Android clients.

This lab focused on SMB configuration, authentication, authorization, NTFS permissions, Share permissions, and least-privilege access control.

---

## Scenario

A small organization requires centralized file sharing while ensuring users can access only the resources they are authorized to use.

The objective of this lab was to deploy a Windows-based SMB file-sharing solution that supports user-specific access controls, shared resources, and cross-platform connectivity while maintaining proper security practices.

---

## Objectives

- Configure SMB file shares on Windows 11
- Create user-specific access controls
- Configure Share Permissions
- Configure NTFS Permissions
- Validate authentication and authorization
- Implement read-only and read/write access
- Access shares from Linux and Android clients
- Troubleshoot SMB connectivity and permission issues
- Apply least-privilege security principles

---

## Environment

### Server

Windows 11

### Clients

Linux Mint Virtual Machine

Honor 200 Pro (Android)

OnePlus 8T (Android)

### Technologies Used

- SMB/CIFS
- Windows File Sharing
- NTFS Permissions
- Local User Accounts
- PowerShell
- Command Prompt
- Linux smbclient
- CX File Explorer

---

```text
Windows 11 Host (192.168.59.187)
        |
        |--- Honor 200 Pro Android
        |--- OnePlus 8T Android
        |--- Linux Mint VM

---

## User Accounts

| Username    | Purpose    | Privilege Level |
| ----------- | ---------- | --------------- |
| Honor200Pro | SMB Access | Standard User   |
| OnePlus     | SMB Access | Standard User   |

---

## Share Structure

LabShare/
├── Honor Data
├── OnePlus Data
└── SharedReadOnly

---

## Access Control Matrix

| User        | Resource       | Permission |
| ----------- | -------------- | ---------- |
| Honor200Pro | Honor Data     | Read/Write |
| OnePlus     | OnePlus Data   | Read/Write |
| Honor200Pro | SharedReadOnly | Read Only  |
| OnePlus     | SharedReadOnly | Read Only  |


---

## Verification Tests

| Test                                 | Expected Result | Outcome |
| ------------------------------------ | --------------- | ------- |
| Honor200Pro access to Honor Data     | Read/Write      | Pass    |
| OnePlus access to OnePlus Data       | Read/Write      | Pass    |
| Honor200Pro access to SharedReadOnly | Read Only       | Pass    |
| OnePlus access to SharedReadOnly     | Read Only       | Pass    |
| Invalid credentials                  | Access Denied   | Pass    |
| Share enumeration from Linux         | Shares Visible  | Pass    |
| Android SMB connection               | Successful      | Pass    |


---

## SMB Client Commands

### Enumerate Available Shares

```bash
smbclient -L //192.168.59.187 -U Honor200Pro
```

### Connect to a Share

```bash
smbclient "//192.168.59.187/Honor Data" -U Honor200Pro
```

### Common SMB Operations

```bash
ls
pwd
cd
mkdir
put
get
del
help
exit
```

---

## Technical Skills Demonstrated

### Windows Administration

- Local User Management
- SMB Share Configuration
- Share Permission Management
- NTFS Permission Configuration

### Networking

- SMB Protocol Operation
- Client/Server Communication
- Authentication Testing
- Connectivity Validation

### Linux Administration

- smbclient Usage
- Remote File Operations
- SMB Troubleshooting

### Security

- Authentication
- Authorization
- Least Privilege Access
- Access Control Validation
- Permission Inheritance Analysis

---

## Security Observations

- SMB access remains functional even when Network Discovery is disabled.
- SMB services remain available until the underlying service is stopped.
- Administrative shares such as C$ and ADMIN$ may be visible during share enumeration.
- Share Permissions and NTFS Permissions work together to determine effective access.
- The most restrictive permission always applies.
- SMB authentication requires valid user credentials.
- Proper access control design prevents unauthorized access while maintaining usability.

---

## Troubleshooting

### Issue

Authentication failures due to incorrect credentials.

### Investigation

- Verified account credentials
- Reviewed NTFS permission entries
- Checked Share Permissions
- Tested connectivity using smbclient

### Root Cause

Incorrect user credentials.

### Resolution

Corrected credentials and validated successful authentication.

---

### Issue

Users unable to access intended resources.

### Investigation

- Reviewed NTFS permissions
- Reviewed Share permissions
- Tested effective permissions

### Root Cause

Incorrect permission assignments.

### Resolution

Adjusted NTFS and Share permissions and re-tested access.

---

### Issue

Confusion caused by permission inheritance.

### Investigation

- Examined inherited permissions
- Compared effective access results

### Root Cause

Inherited permissions affecting expected behavior.

### Resolution

Reviewed inheritance settings and validated effective permissions.

---

### Issue

Linux smbclient path and syntax errors.

### Investigation

- Tested alternate command syntax
- Verified share names

### Root Cause

Incorrect smbclient command formatting.

### Resolution

Corrected command syntax and validated connectivity.

---

## Screenshots

### 1. Windows Host IP Configuration

images/01-ipconfig.jpg

### 2. Honor200Pro Share Permission

images/02-share-permission-honor.jpg

### 3. OnePlus Share Permission

images/03-share-permission-oneplus.jpg

### 4. SharedReadOnly Share Configuration

images/04-share-readonly.jpg

### 5. SharedReadOnly Access Validation

images/05-share-readonly-validation.jpg

### 6. Android SMB Share Enumeration

images/06-android-share-enumeration.jpg

### 7. Android SMB Share Access

images/07-android-share-access.jpg

### 8. Shared Files Verification

images/08-shared-files.jpg

### 9. CX File Explorer SMB Setup

images/09-cxfileexplorer-smb-setup.jpg

### 10. SMB Login Configuration

images/10-smb-login-configuration.jpg

### 11. NTFS Permission Configuration

images/11-ntfs-permission.jpeg

### 12. Administrator Permission Review

images/12-admin-permission-review.jpg

### 13. SMB Client Connection

images/13-smbclient-connect.jpg

### 14. SMB Directory Listing

images/14-smbclient-list-files.jpg

### 15. SMB Navigation

images/15-smbclient-navigation.jpg

### 16. SMB File Operations

images/16-smbclient-file-operations.jpg

### 17. SMB Access Validation

images/17-smbclient-access-validation.jpg

---

## Lessons Learned

- SMB authentication and authorization are separate processes.
- Share Permissions and NTFS Permissions must both be considered when designing access controls.
- The most restrictive permission determines effective access.
- Android devices can access SMB resources using third-party file management tools.
- Linux SMB utilities provide detailed visibility into remote file shares.
- Proper permission design allows secure resource separation between users.
- Cross-platform testing is valuable for validating real-world deployments.

---

## Result

Successfully deployed and validated a Windows-based SMB file-sharing solution using user-specific access controls and secure permission management.

The environment was tested from Windows, Linux, and Android clients to verify authentication, authorization, and effective permission enforcement.

This lab demonstrates practical experience with:

- SMB Administration
- Windows User Management
- NTFS Permissions
- Share Permissions
- Access Control Design
- Linux SMB Client Operations
- Android SMB Connectivity
- Authentication & Authorization
- Infrastructure Troubleshooting
- Cross-Platform File Sharing