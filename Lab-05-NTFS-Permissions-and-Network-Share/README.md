# Lab 05 - NTFS Permissions and Network Share Implementation

## Objective

The objective of this lab is to implement and validate NTFS and Share permissions in a Windows Server domain environment using the previously designed AGDLP security group structure.

This lab focuses on secure access control to a shared folder using Domain Local groups for permission assignment and testing access from a domain-joined client machine.

---

## Environment

- Windows Server (Domain Controller)
- Active Directory Domain Services (AD DS)
- Domain: lab.local
- Windows 10 Client (Domain Joined)
- Security Group Model: AGDLP (from Lab 04)

---

## Implementation Steps

### 1️⃣ Create Shared Folder

A folder named `IT_Share` was created on the Domain Controller.

This folder will be used to demonstrate permission delegation via Domain Local groups.

---

### 2️⃣ Configure Share Permissions

The folder was shared on the network.

Share configuration:

- Default permissions were removed.
- `DL_IT_Share_RW` → Full Control
- `DL_IT_Share_RO` → Read

This ensures that access is controlled strictly through Domain Local groups.

---

### 3️⃣ Configure NTFS Permissions

NTFS permissions were configured as follows:

- Inherited permissions were removed.
- `DL_IT_Share_RW` → Modify
- `DL_IT_Share_RO` → Read & Execute
- Administrators → Full Control

This enforces proper security layering at the file system level.

---

### 4️⃣ Validate AGDLP Model Integration

The AGDLP structure applied:

Accounts → Global Groups → Domain Local Groups → Permissions

- `GG_IT_Users` → nested into → `DL_IT_Share_RW`
- `GG_Standard_Users` → nested into → `DL_IT_Share_RO`

This ensures scalable and enterprise-ready access control.

---

### 5️⃣ Access Validation from Client Machine

Testing was performed from a domain-joined Windows 10 client.

Two user scenarios were validated:

#### 🔹 Read-Only User Test

- User successfully accessed the shared folder.
- Attempt to create a file resulted in "Access Denied".
- Read permissions confirmed.

#### 🔹 Read/Write User Test

- User successfully accessed the shared folder.
- File creation succeeded.
- File deletion succeeded.
- Modify permissions confirmed.

This validates correct permission implementation at both Share and NTFS levels.

---

## Security Model Applied

This lab demonstrates:

- Separation of Global and Domain Local groups
- Secure delegation of folder access
- Implementation of enterprise best practice permission design
- Practical validation from client environment

---

## Conclusion

This lab demonstrates the complete implementation of NTFS and Share permissions in a domain environment using the AGDLP model.

Access control was successfully tested and validated from a client machine, confirming correct permission delegation and security configuration.

---

## Screenshots

All execution proof screenshots are available in the `images` directory.
