# 04 — Promote Server to Domain Controller

This step covers promoting the Windows Server 2022 VM to a Domain Controller
after installing the AD DS role. This creates the new forest and domain
(lab.local) for the Active Directory lab.

---

## 01 — Begin Promotion Wizard
After AD DS installation, Server Manager shows a yellow notification flag.

- Open **Server Manager**
- Click the **yellow flag** in the top-right corner
- Select **Promote this server to a domain controller**

This launches the Active Directory Domain Services Configuration Wizard.

---

## 02 — Choose Deployment Type
You are creating a brand-new domain and forest.

- Select **Add a new forest**
- Enter your domain name: **lab.local**

Click **Next**.

---

## 03 — Domain Controller Options
These settings define how your DC will operate.

- Forest functional level: **Windows Server 2022**
- Domain functional level: **Windows Server 2022**
- Tick **Domain Name System (DNS) Server**
- Tick **Global Catalog (GC)** (enabled by default)
- Leave **Read-only domain controller (RODC)** unchecked

Set the **DSRM password** (Directory Services Restore Mode).

Click **Next**.

---

## 04 — DNS Options
You may see a warning about delegation — this is normal.

- Ignore the delegation warning
- Click **Next**

---

## 05 — Additional Options
The wizard automatically generates the NetBIOS name.

- Confirm NetBIOS name: **LAB**

Click **Next**.

---

## 06 — Paths
Default paths are fine for a lab environment.

- Leave:
  - **Database**: C:\\Windows\\NTDS
  - **Log files**: C:\\Windows\\NTDS
  - **SYSVOL**: C:\\Windows\\SYSVOL

Click **Next**.

---

## 07 — Review & Install
The wizard performs a prerequisites check.

- Review summary
- Click **Install**

The server will automatically reboot when promotion completes.

---

## 08 — Verification After Reboot
After reboot, confirm the promotion succeeded.

- Log in using your local admin account
- Open **Server Manager**
- Check **AD DS** and **DNS** roles are present
- Open **Active Directory Users and Computers**
- Confirm the domain **lab.local** exists

Your server is now a fully functional **Domain Controller**.

---

## Promotion Checkpoint
- Domain created: **lab.local**
- DNS installed and running
- SYSVOL replicated and healthy
- Server promoted successfully
- Ready for OU structure and user creation
