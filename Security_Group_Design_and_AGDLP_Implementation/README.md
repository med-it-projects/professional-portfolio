# Lab 04 – Security Group Design and AGDLP Implementation

## Objective

The objective of this lab is to design and implement a structured security group architecture in Active Directory using the **AGDLP model** (Accounts → Global → Domain Local → Permissions).

This lab focuses on proper group nesting and scalable access control design within the domain environment.

---

## Environment

- Windows Server (Domain Controller)
- Active Directory Domain Services (AD DS)
- Domain: `lab.local`

---

## Implementation Steps

### 1️⃣ Create Organizational Unit for Groups

An Organizational Unit named `OU_Groups` was created under the `LAB` container to logically separate security groups.

---

### 2️⃣ Create Global Security Groups

Two Global Security Groups were created inside `OU_Groups`:

- `GG_Standard_Users`
- `GG_IT_Users`

Configuration:
- **Group scope:** Global  
- **Group type:** Security  

---

### 3️⃣ Verify Global Groups Creation

The Active Directory structure was verified to confirm that the Global Security Groups were successfully created inside `OU_Groups`.

---

### 4️⃣ Add User to Global Group

The domain user `MedUser` was added to:

- `GG_Standard_Users`

This represents the **Accounts → Global** part of the AGDLP model.

---

### 5️⃣ Create Domain Local Groups

Two Domain Local Security Groups were created inside `OU_Groups`:

- `DL_IT_Share_RW`
- `DL_IT_Share_RO`

Configuration:
- **Group scope:** Domain Local  
- **Group type:** Security  

---

### 6️⃣ Implement AGDLP Nesting

Group nesting was implemented as follows:

- `GG_IT_Users` → added to → `DL_IT_Share_RW`
- `GG_Standard_Users` → added to → `DL_IT_Share_RO`

This establishes the AGDLP structure:

Accounts → Global Groups → Domain Local Groups

---

### 7️⃣ Validate Final Group Structure

The final structure inside `OU_Groups` confirms:

- Proper separation of Global and Domain Local groups  
- Correct group membership  
- A scalable and enterprise-ready security model  

---

## Conclusion

This lab demonstrates the implementation of the **AGDLP model** in Active Directory to ensure structured, scalable, and maintainable access control design.

No folder permissions were configured at this stage.  
This lab focuses strictly on security group architecture and nesting logic.
