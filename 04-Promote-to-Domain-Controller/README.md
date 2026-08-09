# 04 — Promote Server to Domain Controller

This step documents the promotion of the Windows Server 2022 VM to a Domain
Controller, creating the new forest and domain (lab.local).

---

## 01 — Begin Promotion Wizard
After installing AD DS, Server Manager displayed a yellow notification flag.

- I opened Server Manager
- Clicked the yellow flag
- Selected “Promote this server to a domain controller”

---

## 02 — Choose Deployment Type
I created a brand-new forest and domain:

- Deployment: Add a new forest
- Domain name: lab.local

---

## 03 — Domain Controller Options
I configured the DC options:

- Forest functional level: Windows Server 2022
- Domain functional level: Windows Server 2022
- DNS Server: Enabled
- Global Catalog: Enabled
- RODC: Not selected
- Set the DSRM password

---

## 04 — DNS Options
A delegation warning appeared, which is normal in a new forest.

- I continued past the warning

---

## 05 — Additional Options
The wizard generated the NetBIOS name automatically:

- NetBIOS name: LAB

---

## 06 — Paths
I kept the default paths:

- Database: C:\Windows\NTDS
- Logs: C:\Windows\NTDS
- SYSVOL: C:\Windows\SYSVOL

---

## 07 — Review & Install
I reviewed the configuration and started the installation.

- The server rebooted automatically after promotion

---

## 08 — Verification After Reboot
After rebooting, I verified the promotion:

- AD DS and DNS roles were present
- Active Directory Users and Computers opened successfully
- The domain lab.local was created

---

## Promotion Checkpoint
- Domain created: lab.local
- DNS installed and running
- SYSVOL healthy
- Server promoted successfully
- Ready for OU structure and user creation

