# Windows SMB File Sharing & Access Control Lab

## Project Summary

Designed and implemented a secure SMB file sharing environment on Windows 11 with access validation from Linux and Android clients.

The lab focused on SMB configuration, NTFS permissions, Share permissions, authentication, authorization, and least-privilege access control.

---

## Objectives

- Configure SMB shares
- Create user-specific access controls
- Configure Share Permissions
- Configure NTFS Permissions
- Test authentication and authorization
- Validate read-only and read/write access
- Access shares from Linux and Android
- Practice troubleshooting SMB connectivity issues

---

## Environment

### Server

- Windows 11

### Clients

- Linux Mint VM
- Honor 200 Pro
- OnePlus 8T

### Tools

- SMB
- Windows File Sharing
- NTFS Permissions
- Local Users and Groups
- smbclient
- CX File Explorer
- PowerShell
- Command Prompt

---

## Lab Topology

```text
Windows 11 Host (192.168.59.187)
        │
 ┌──────┼─────────────┐
 │      │             │
Honor   OnePlus    Linux Mint
```

---

## User Accounts

| Username | Purpose | Privilege |
|-----------|-----------|-----------|
| Honor200Pro | SMB Access | Standard User |
| OnePlus | SMB Access | Standard User |

---

## Share Structure

```text
LabShare/
├── Honor Data
├── OnePlus Data
└── SharedReadOnly
```

---

## Access Verification

| User | Share | Permission |
|--------|--------|------------|
| Honor200Pro | Honor Data | Read/Write |
| OnePlus | OnePlus Data | Read/Write |
| Honor200Pro | SharedReadOnly | Read Only |
| OnePlus | SharedReadOnly | Read Only |

---

## Commands Used

### Enumerate Shares

```bash
smbclient -L //192.168.59.187 -U Honor200Pro
```

### Connect to SMB Share

```bash
smbclient "//192.168.59.187/Honor Data" -U Honor200Pro
```

### Common SMB Commands

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

## Skills Demonstrated

### Windows Administration

- Local User Management
- Share Configuration
- NTFS Permission Management

### Networking

- SMB Protocol
- Client/Server Connectivity
- Authentication Testing

### Linux Administration

- smbclient Usage
- Remote File Operations
- SMB Troubleshooting

### Security

- Least Privilege
- Authentication vs Authorization
- Access Control Validation

---

## Security Observations

- Network Discovery can be disabled while SMB access remains available.
- SMB services remain accessible until the service is stopped.
- Administrative shares such as C$ and ADMIN$ can be discovered during enumeration.
- Share permissions and NTFS permissions work together.
- The most restrictive permission always applies.
- SMB authentication requires valid user credentials.

---

## Troubleshooting

### Issues Encountered

- Authentication failures
- Incorrect permission assignments
- Permission inheritance confusion
- SMB access behavior after disabling Network Discovery
- Linux file path mistakes

### Resolution

- Verified credentials
- Reviewed NTFS permissions
- Validated Share permissions
- Tested access using smbclient
- Compared GUI behavior with command-line testing

---

## Screenshots

### 1. Windows Host IP Configuration

![Windows Host IP Configuration](images/01-ipconfig.jpg)

### 2. Honor200Pro Share Permission

![Honor200Pro Share Permission](images/02-share-permission-honor.jpg)

### 3. OnePlus Share Permission

![OnePlus Share Permission](images/03-share-permission-oneplus.jpg)

### 4. SharedReadOnly Share Configuration

![SharedReadOnly Configuration](images/04-share-readonly.jpg)

### 5. SharedReadOnly Access Validation

![SharedReadOnly Validation](images/05-share-readonly-validation.jpg)

### 6. Android SMB Share Enumeration

![Android Share Enumeration](images/06-android-share-enumeration.jpg)

### 7. Android SMB Share Access

![Android SMB Share Access](images/07-android-share-access.jpg)

### 8. Shared Files Verification

![Shared Files Verification](images/08-shared-files.jpg)

### 9. CX File Explorer SMB Setup

![CX File Explorer SMB Setup](images/09-cxfileexplorer-smb-setup.jpg)

### 10. SMB Login Configuration

![SMB Login Configuration](images/10-smb-login-configuration.jpg)

### 11. NTFS Permission Configuration

![NTFS Permission Configuration](images/11-ntfs-permission.jpeg)

### 12. Administrator Permission Review

![Administrator Permission Review](images/12-admin-permission-review.jpg)

### 13. SMB Client Connection

![SMB Client Connection](images/13-smbclient-connect.jpg)

### 14. SMB Directory Listing

![SMB Directory Listing](images/14-smbclient-list-files.jpg)

### 15. SMB Navigation

![SMB Navigation](images/15-smbclient-navigation.jpg)

### 16. SMB File Operations

![SMB File Operations](images/16-smbclient-file-operations.jpg)

### 17. SMB Access Validation

![SMB Access Validation](images/17-smbclient-access-validation.jpg)

---

## Lessons Learned

- Share permissions and NTFS permissions work together.
- The most restrictive permission always applies.
- SMB authentication requires valid Windows credentials.
- Android devices can access SMB shares using third-party file managers.
- Linux SMB tools provide excellent visibility into remote shares.
- Proper access control design allows secure separation of user permissions.

---

## Result

Successfully implemented a secure SMB file sharing environment with:

- User-specific access controls
- NTFS permission enforcement
- Share permission management
- Linux and Android client connectivity
- Authentication and authorization validation
- Practical SMB troubleshooting experience
