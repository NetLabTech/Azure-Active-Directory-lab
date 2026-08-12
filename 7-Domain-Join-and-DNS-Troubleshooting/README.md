
# 7 - Joining Client PC1 to the Domain (with Troubleshooting)

In this section, I joined **PC1** to the **lab.local** domain, fixed DNS issues, verified connectivity, and confirmed the computer object inside Active Directory.
This is where everything finally connects together.

---
## 1. Connecting to PC1

I connected to the PC1 VM using Remote Desktop and logged in with the local administrator account (`ActiveD`).  
PC1 is running in the same VNet as my domain controller.


## 2. Attempting the Domain Join (and the First Error)

I tried to move the PC from a WORKGROUP into the **lab.local** domain by manually typing the domain name into the system settings.


![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/1%20PC1%20name%20and%20domain%20change.png)

As soon as I attempted the join, Windows threw the domain controller error saying it couldn’t contact an AD DC. 
This confirmed something wasn’t right with the network configuration.


![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/2%20error%20for%20domain%20name%20memeber.png)

---

## 3. DNS Troubleshooting

So I checked PC1’s network settings using `ipconfig /all` and saw it was still using the default Azure DNS server. 
That explained why it couldn’t find the domain controller. 
To fix it, I went into the network settings and manually updated the IPv4 DNS to point to my domain controller’s IP address (10.0.0.4).
Once I saved the change, DNS resolution started working correctly.

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/2%20troubleshoot%20CmD%20promt%20showing%20the%20wrong%20dns%20server.png)

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/3%20trouble%20shoot%20make%20the%20prefered%20dns%20server%20teh%20ip%20fo%20the%20DC%2010.0.0.4.png)


## 4. Joining the Domain Successfully

After fixing the DNS issue, I went back and entered **lab.local** again as the domain name. 
This time Windows immediately prompted me for my domain credentials, so I entered my `ActiveD` username and password. 
The join went through without any errors, and I got the “Welcome to the lab.local domain” confirmation message.

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/4%20PC1%20name%20domain%20try%20again.%20asks%20for%20user%20and%20pass.png)

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/5%20welcome%20to%20lab.local%20domain.png)

## 5. Verifying Connectivity and Domain Registration

After restarting the PC1 VM the domain join succeeded, I tested connectivity by pinging the domain controller using its DNS name. 
The ping resolved to `10.0.0.4` and replied instantly, confirming PC1 could now reach ACT-DIR-LAB through DNS.
I then opened Active Directory Users and Computers on the domain controller and confirmed that **PC1** appeared inside the **Computers** folder, 
showing that the domain join fully registered.

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/6%20ping%20DC's%20name%20(%20act-dir-lab%20from%20pc1.png)

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/124953838eea8bbb48f99ec4f15456fa5a0366c0/7%20PC1%20shows%20up%20auto%20in%20DC%20computer%20folder.png)

---

### Step 6 — Moving PC1 into the Correct OU

After confirming that PC1 successfully joined the domain and appeared inside the default **Computers** container, I moved it into the correct organizational unit for Branch 1.

This ensures that PC1 receives the correct Group Policy Objects (GPOs) and follows the proper structure of the Active Directory hierarchy.

---

### Step 7 — Enabling Remote Desktop for Domain Users

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

![Step 7 — Remote Desktop Users](PASTE_YOUR_PERMALINK_HERE)







