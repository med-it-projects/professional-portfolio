# Lab 03 – Organizational Units and GPO Implementation

## Objective

The objective of this lab is to organize domain objects using Organizational Units (OU) and implement Group Policy Objects (GPO) to control workstation and user behavior within the domain environment.

This lab builds upon Lab 02 (Windows Client Domain Join).

## Environment

- Windows Server (Domain Controller)
- Windows 10 Client (Domain joined)
- VirtualBox (Isolated internal network)

## Tasks Performed

1. Opened Active Directory Users and Computers
2. Created "Workstations" Organizational Unit
3. Moved Client01 into Workstations OU
4. Opened Group Policy Management Console
5. Created baseline GPO for Workstations
6. Linked GPO to Workstations OU
7. Configured GPO restrictions (Control Panel access)
8. Forced policy update (gpupdate /force)
9. Verified policy application
10. Linked GPO to OU_Users for user scope testing
11. Corrected GPO scope filtering
12. Validated successful user restriction enforcement

## Outcome

- Organizational Units properly structured
- Workstations logically separated
- Group Policy successfully linked and enforced
- User-level restrictions validated
- Demonstrated understanding of GPO scope and inheritance behavior

## Scope

This lab demonstrates structured Active Directory organization and practical implementation of centralized policy management in an enterprise-like environment.
