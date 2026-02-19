# Lab 01 – Active Directory and DNS Setup

## Objective
The objective of this lab is to install and configure Active Directory Domain Services (AD DS) and DNS on Windows Server, and to establish the initial foundation of an enterprise Active Directory environment.

## Environment
- Windows Server (Virtualized)
- VirtualBox
- Isolated lab network

## Implementation Overview
- Installation of Active Directory Domain Services using the Add Roles and Features Wizard
- Configuration of a new Active Directory forest
- Promotion of the server to a Domain Controller
- DNS role installation and integration with Active Directory
- Configuration of domain controller options (DNS server, Global Catalog, DSRM password)
- Definition of directory paths and initial domain settings

## Active Directory Structure
- Creation of a dedicated Organizational Unit (OU) named **LAB**
- Sub-OUs created:
  - **OU_Users**
  - **OU_Computers**
  - **OU_Servers**
  - **OU_IT**
- Creation of user accounts:
  - Standard user account in **OU_Users**
  - Administrative account in **OU_IT**

## Validation and Readiness
Before proceeding to client integration and further domain configurations, the following validation and stabilization steps were performed:
- Configuration of a **static IPv4 address** on the Domain Controller to ensure network stability and reliable name resolution
- Verification of DNS Forward Lookup Zones to confirm proper Active Directory–integrated DNS functionality

## Scope
This lab represents the foundation of the Active Directory environment. All subsequent labs build upon this initial domain configuration and validated infrastructure.

## Outcome
- Active Directory Domain Services successfully installed
- DNS role installed and fully integrated
- New Active Directory domain created and validated
- Initial OU structure implemented
- User and administrative accounts created
- Domain Controller configured with a static IP and ready for client integration

---

## Screenshots

All execution proof screenshots are available in the `images` directory.

