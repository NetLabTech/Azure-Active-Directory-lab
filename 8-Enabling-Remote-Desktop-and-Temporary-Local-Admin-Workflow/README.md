
### Step 1 — Enabling Remote Desktop for Domain Users

By default, Windows Server only allows members of the **Administrators** group to sign in via Remote Desktop.  
To allow standard domain users (such as Sarah, Mike, or the HR Team group) to log in to **PC1**, they must be added to the **Remote Desktop Users** local group.

**Steps Performed**
1. Logged into **PC1** using the domain administrator account: `lab\Administrator`
2. Opened **Settings → System → Remote Desktop**
3. Selected **Remote Desktop Users**
4. Added the required domain user/group from the `lab.local` domain
5. Confirmed the user now appears in the Remote Desktop Users list

**Screenshot**
Below is the screenshot showing Remote Desktop enabled and the dialog used to add domain users:

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/2fca6d3ec5057289f3eee0b28a99a0cd5ffcf9fe/Screenshot%202026-08-12%20at%2010.26.12.png)

### Step 2 — Create a Temporary Local Administrator Account

When a workstation is **off the corporate network**, **not connected to VPN**, or **unable to authenticate domain credentials**, MSP technicians often need a temporary local admin account to perform troubleshooting or install RMM agents. This account is only used during off‑domain access and must be deleted afterwards to remain audit‑compliant.

**Steps Performed**
1. Opened **PowerShell (Admin)** on **PC1**  
2. Created a temporary local admin account named `tempadmin`  
   ```powershell
   net user tempadmin Temppass1234! /add
**Added the new account to the Administrators local group**
```powershell
net localgroup administrators tempadmin /add
**Verified the account now appears in the local user list**
```powershell
net user
![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/1a0af429ff49b2ae668754460ca24ad97bec03d8/showing%20tempadmin%20is%20anow%20an%20adminstrattor.png)
