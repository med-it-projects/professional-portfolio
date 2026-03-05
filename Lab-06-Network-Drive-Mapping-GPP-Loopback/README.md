# Lab 06 - Network Drive Mapping via Group Policy (GPP) and Loopback Processing

## Objective

The objective of this lab is to automatically map a network drive (`IT_Share`) on domain-joined workstations using **Group Policy Preferences (GPP)**.

This lab also demonstrates a practical troubleshooting scenario:

- The drive mapping policy was correctly created but did not initially appear for the user.
- The issue was resolved by enabling **Loopback Processing**, allowing user settings to be applied based on the workstation OU.
- A drive letter conflict was identified and resolved by modifying the mapped drive letter.

---

## Environment

- Windows Server (Domain Controller)
- Active Directory Domain Services (AD DS)
- Group Policy Management (GPMC)
- Domain: `lab.local`
- Windows 10 Client (Domain Joined)
- Shared Folder: `\\LAB-DC01\IT_Share` (created in Lab 05)

---

## Implementation Steps

### 1️⃣ Validate Existing GPO Configuration in Workstations OU

Before creating the new policy, the existing Group Policy configuration inside the **Workstations OU** was verified.

This step ensures visibility of already linked policies and helps confirm the initial configuration state before implementing the drive mapping policy.

---

### 2️⃣ Create and Link a Dedicated Drive Mapping GPO

A new Group Policy Object was created and linked to the **Workstations OU**:

`GPO_MapDrive_ITShare`

Using a dedicated GPO for specific configurations is considered best practice in enterprise environments because it improves organization, troubleshooting, and long-term maintainability.

---

### 3️⃣ Open the GPO in Group Policy Management Editor

The newly created GPO was opened in the **Group Policy Management Editor** to configure the drive mapping settings.

---

### 4️⃣ Configure Drive Mapping using Group Policy Preferences

Drive mapping was configured under:

User Configuration  
→ Preferences  
→ Windows Settings  
→ Drive Maps

Drive configuration:

- Action: Create  
- Location: `\\LAB-DC01\IT_Share`  
- Label: `IT Share`  
- Drive Letter: `Z:`  

Group Policy Preferences allows administrators to deploy mapped drives centrally without using login scripts.

---

### 5️⃣ Force Group Policy Update on Client Machine

On the domain-joined client workstation, Group Policy was refreshed manually using:

`gpupdate /force`

This forces the system to retrieve and apply the latest policies immediately instead of waiting for the normal background refresh cycle.

---

### 6️⃣ Verify Applied Policies using gpresult

Policy application was verified using:

`gpresult /r`

This command allows administrators to confirm which Group Policy Objects are applied to the user and the computer.

---

### 7️⃣ Enable Loopback Processing

The drive mapping policy was configured under **User Configuration**, but the GPO was linked to the **Workstations OU** (computer location).

To ensure the policy applies correctly when users log onto those workstations, **Loopback Processing** was enabled:

Computer Configuration  
→ Policies  
→ Administrative Templates  
→ System  
→ Group Policy  
→ Configure user Group Policy loopback processing mode

Mode used:

Replace

This ensures that user settings applied during login are determined by the workstation's OU instead of the user's OU.

---

### 8️⃣ Verify Drive Mapping GPO Application

After enabling loopback processing, policy application was verified again using:

`gpresult /r`

The output confirms that `GPO_MapDrive_ITShare` is now applied successfully.

---

### 9️⃣ Resolve Drive Letter Conflict

A drive letter conflict was identified.

The letter `Z:` was already used by another mapped drive (`\\VBoxSrv`).

To resolve this conflict, the drive letter in the GPO configuration was modified:

`Z:` → `I:`

Changing the drive letter ensures the mapping can be applied successfully without conflicts.

---

### 🔟 Confirm Network Drive Mapping

Final validation was performed on the client workstation.

The mapped drive appears in **This PC** as:

`IT Share (I:)`

The network drive is automatically mapped through Group Policy and points to the correct shared folder.

---

## Key Concepts Demonstrated

This lab demonstrates several enterprise-level administration practices:

- Deploying network drives using **Group Policy Preferences**
- Understanding **User vs Computer policy scope**
- Implementing **Loopback Processing**
- Using troubleshooting tools such as:
  - `gpupdate`
  - `gpresult`
- Diagnosing and resolving **drive letter conflicts**

---

## Conclusion

This lab demonstrates how to centrally deploy a mapped network drive using Group Policy Preferences in an Active Directory domain environment.

A real-world configuration issue involving policy scope and drive letter conflict was identified and resolved using loopback processing and GPO modification. The final configuration was successfully validated from a domain-joined client workstation.

---

## Screenshots

All execution proof screenshots are available in the `images` directory.
