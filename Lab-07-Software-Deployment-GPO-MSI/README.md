# Lab 07 - Centralized Software Deployment using Group Policy (MSI Deployment)

## Objective

The objective of this lab is to deploy software automatically on domain-joined workstations using **Group Policy Software Installation**.

In this scenario, the software **7-Zip** is deployed centrally from a **software repository located on the Domain Controller**. Once the policy is applied, the application is installed automatically during computer startup.

This lab demonstrates how administrators can centrally manage software distribution in an **Active Directory environment** without manually installing applications on each workstation.

---

## Environment

- Windows Server (Domain Controller)
- Active Directory Domain Services (AD DS)
- Group Policy Management Console (GPMC)
- Domain: `lab.local`
- Windows 10 Client (Domain Joined)
- Software Repository: `\\LAB-DC01\Software`
- Software Package: `7z2600-x64.msi`

---

## Implementation Steps

### 1️⃣ Create Software Repository on Domain Controller

A centralized **software repository** was created on the Domain Controller.

Folder created: `C:\Software`

This repository stores software packages that will be deployed using Group Policy.

Using a dedicated repository is a common practice in enterprise environments because it centralizes application management and simplifies future deployments.

---

### 2️⃣ Share Software Repository for GPO Deployment

The repository folder was shared so domain computers can access the installation packages.

Shared path: `\\LAB-DC01\Software`

This allows domain computers to retrieve installation files during Group Policy processing.

---

### 3️⃣ Create 7-Zip Package Folder in Repository

Inside the repository, a dedicated folder was created for the application package:

`C:\Software\7zip`

Separating software packages into individual folders improves repository organization and maintainability.

---

### 4️⃣ Copy 7-Zip MSI to Server Repository

The **7-Zip MSI installer** was copied into the repository folder.

Final path: `\\LAB-DC01\Software\7zip\7z2600-x64.msi`

Group Policy Software Installation requires the package to be referenced using a **network path (UNC path)** instead of a local disk path.

---

### 5️⃣ Create a Dedicated Software Deployment GPO

A new Group Policy Object was created:

`GPO_Deploy_7Zip`

Creating dedicated GPOs for specific configurations improves policy management and troubleshooting in enterprise environments.

---

### 6️⃣ Open the Software Installation Policy

The newly created GPO was opened in **Group Policy Management Editor**.

Navigation path:

`Computer Configuration → Policies → Software Settings → Software Installation`

This section is used to deploy software packages to domain computers.

---

### 7️⃣ Add the 7-Zip MSI Package from Network Share

The MSI package was added using the network path:

`\\LAB-DC01\Software\7zip\7z2600-x64.msi`

Deployment type selected:

`Assigned`

Assigned deployment ensures that the software is automatically installed on the workstation during system startup.

---

### 8️⃣ Link the Deployment GPO to Workstations OU

The GPO was linked to the Organizational Unit containing domain computers:

`OU: Workstations`

Linking the policy to the correct OU ensures that all computers within that OU receive the software deployment policy.

---

### 9️⃣ Force Group Policy Update on Client Machine

On the domain-joined workstation, Group Policy was refreshed manually using:

`gpupdate /force`

Because software installation policies apply during **computer startup**, the system prompted for a reboot.

---

### 🔟 Verify GPO Deployment using gpresult

Policy application was verified using:

`gpresult /r`

This command allows administrators to confirm which Group Policy Objects are applied to the system.

---

### 1️⃣1️⃣ Confirm Software Installation on Client

After rebooting the client workstation, the software was automatically installed.

The application **7-Zip** appeared in the Start Menu, confirming that the deployment was successful.

This demonstrates how administrators can deploy applications centrally across multiple workstations without manual installation.

---

## Key Concepts Demonstrated

This lab demonstrates several enterprise-level administration practices:

- Creating a centralized **software repository**
- Deploying applications using **Group Policy Software Installation**
- Using **UNC network paths** for software packages
- Linking policies to **Organizational Units**
- Understanding **Computer Configuration policies**
- Verifying policy application using:
  - `gpupdate`
  - `gpresult`

---

## Conclusion

This lab demonstrates how to centrally deploy software in an Active Directory environment using **Group Policy Software Installation**.

By storing installation packages in a centralized repository and linking deployment policies to workstation organizational units, administrators can automate software installation across multiple domain computers.

The deployment of **7-Zip** was successfully validated from a domain-joined client workstation.

---

## Screenshots

All execution proof screenshots are available in the `images` directory.
