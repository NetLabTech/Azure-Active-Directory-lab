
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


---

### Step 2 — Create a Temporary Local Administrator Account

When a workstation is off the corporate network, not connected to VPN, or unable to authenticate domain credentials, MSP technicians often need a temporary local admin account to perform troubleshooting or install RMM agents. This account is only used during off‑domain access and must be deleted afterwards to remain audit‑compliant.

**Steps Performed**
1. Opened PowerShell (Admin) on PC1  
2. Created a temporary local admin account named `tempadmin` using: net user tempadmin Temppass1234! /add  


3. Added the new account to the Administrators local group using: net localgroup administrators tempadmin /add 

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/e865d0a226ef0186d9a1930c4821f0bb23b72e2e/make%20tempadmin%20User%20account%20and%20add%20to%20adminstrator%20group.png)


4. Verified the account now appears in the local user list using: net user

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/63ca3c32b0ebe025b51ca3737c571b28f9a37f41/showing%20tempadmin%20is%20anow%20an%20adminstrattor.png)


### Step 3 — Delete the Temporary Local Administrator Account

After using the `tempadmin` account to sign in locally and complete all required troubleshooting on the workstation that cannot reach the domain controller, the final step is to remove this temporary account. We do this to stay audit‑compliant and ensure no unnecessary local admin accounts remain on the device.

**Steps Performed**
1. Logged out of the temporary admin session after troubleshooting was completed  
2. Opened PowerShell (Admin) on PC1  
3. Removed `tempadmin` from the Administrators group using the appropriate command  
4. Deleted the `tempadmin` local user account  
5. Verified the account no longer appears in the local user list  
6. Confirmed the workstation is now clean and ready to return to normal domain‑based authentication

### Step 4 — Enable Deleted Objects (Recycle Bin) for Safe Computer Removal

If a company requests that a workstation be removed from Active Directory because it is no longer needed, it is best practice to enable the Deleted Objects (Recycle Bin) feature in Active Directory Administrative Center. This allows administrators to safely delete the computer object while retaining the ability to restore it later with all of its original security permissions, group memberships, and GPO inheritance.

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/783ca83ce494794bc31641d9827bf8af4cfe8b49/screenshots2/enable%20recycling%20bin.png)

This is important because companies often change their mind weeks or months later. Without the Recycle Bin enabled, deleting a computer object permanently removes its SID, permissions, and trust relationships, requiring the workstation to be fully rejoined and reconfigured. By enabling Deleted Objects, MSP technicians can restore the PC exactly as it was, avoiding unnecessary rebuilds and ensuring audit‑compliant change control.

### Step 5 — Delete an Unneeded PC and Restore It Using Deleted Objects

If a workstation is no longer required, technicians may be asked to remove it from Active Directory. When Deleted Objects (Recycle Bin) is enabled, the computer object can be safely deleted and later restored with all of its original permissions, group memberships, and attributes intact.

**Steps Performed**
1. Opened Active Directory Users and Computers  
2. Navigated to the correct OU containing the workstation (e.g., Branch1 → Computers)  
3. Selected the PC object (e.g., PC1)  
4. Chose “Delete” and confirmed the deletion 

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/5070b5037660848f9e6ea065eb4713246c6b2162/screenshots2/are%20you%20sure%20you%20want%20to%20delete%20PC1.png)

5. Opened Active Directory Administrative Center  
6. Selected “Deleted Objects” under the domain  
7. Located the deleted PC object in the list
   
![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/1dc73ae99d3a5c3e9274d27409651523eba722b0/screenshots2/showing%20deleted%20PC%20inside%20Administrative%20center.png)
 
8. Restored the PC using either:  
   - **Restore** (returns it to its original OU), or  
   - **Restore To…** (allows choosing a different OU)  
9. Verified the PC object reappeared in Active Directory Users and Computers with its original security permissions and attributes  
10. Confirmed the workstation can now rejoin or authenticate normally without rebuilding its computer object

 ![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/23cf341ab195e9acf83270689c8ab23dad68c824/screenshots2/showing%20the%20pc%20has%20been%20restored%20from%20deleted%20objects.png)   

