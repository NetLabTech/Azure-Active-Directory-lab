# 05 — Active Directory Structure (OU, Users, and Groups)

This step documents the creation of the Organizational Unit (OU) structure and
the initial user and group objects inside the new lab.local domain. This forms
the foundation for future Group Policy testing and client management.

---

## 01 — Creating the OU Structure
After promoting the server to a Domain Controller, I opened **Active Directory Users and Computers (ADUC)** and began building the OU layout for the lab.

I created the following OUs:

- **Lab Users**
- **Lab Computers**
- **Lab Groups**
- **Service Accounts**
- **Admin Accounts**
- **IT Department**
- **HR Department**
- **Sales Department**

This structure keeps users, groups, and devices organized and prepares the domain
for future GPO and security policy testing.

---

## 02 — Creating User Accounts
Inside the **Lab Users** OU, I created several test accounts to simulate real
domain users.

Examples of accounts I added:

- **John.Doe**
- **Sarah.Connor**
- **Michael.Smith**
- **Emma.Jones**

Each account was created with:

- A unique username  
- A temporary password  
- “User must change password at next logon” enabled  

These accounts will be used later for login testing and GPO validation.

---

## 03 — Creating Security Groups
Inside the **Lab Groups** OU, I created security groups to represent department
roles and access levels.

Groups created:

- **IT-Admins**
- **HR-Staff**
- **Sales-Team**
- **Lab-Users**

I added the appropriate users to each group based on their department.  
This prepares the domain for permission-based access control and future GPO
targeting.

---

## 04 — Computer Accounts (Optional)
Although no clients are joined yet, I prepared the **Lab Computers** OU for
future Windows 10/11 domain joins.

This OU will be used later when testing:

- Login policies  
- Software deployment  
- GPO enforcement  
- Device management  

---

## 05 — Verification
After creating the OUs, users, and groups, I verified the structure in ADUC:

- All OUs appeared correctly  
- User accounts were created successfully  
- Groups were visible and populated  
- Domain structure looked clean and organized  

The domain is now ready for Group Policy configuration and client device
integration.
