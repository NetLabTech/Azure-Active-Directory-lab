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

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/087e57a41ca8bc04d66031280563b793d80c875d/05-Active-Directory-Structure/Add%20user%20Sarah%20O.53.28.png)

Examples of accounts I added:

- **John.Doe**
- **Sarah.Connor**
- **Michael.Smith**
- **Emma.Jones**

Each account was created with:

- A unique username  
- A temporary password  
- “User must change password at next logon” enabled

  ![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/694bb7af90042b945f9b66974fc9059a52709264/05-Active-Directory-Structure/Create%20new%20user%20and%20assign%20password.png)

These accounts will be used later for login testing and GPO validation.

---
## 03 — Creating a Security Group

Inside the **Lab Groups** OU, I created a **Security Group** to represent the HR department’s access level.

Group created:

- **HR‑Staff**

I then added **Sarah O’Connor** to the HR‑Staff group.  
This ensures she receives the correct permissions and prepares the domain for future GPO targeting and access control.

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/f2e8b1762b1757e12876bf8b89b692b50461f956/05-Active-Directory-Structure/assign%20sarah%20%20to%20group.png)

## 04 – Copying an Existing User to Create a New One

To speed up user creation and ensure consistent permissions, I used the **Copy Object** feature in Active Directory. This allows a new user account to inherit the original user’s:

- OU location  
- Group memberships  
- Account properties  
- Password policies  

In this case, I copied **Sarah O’Connor’s** account to create a new HR user:

- **New user:** Mike Davidson  
- **Logon name:** Mike.Davidson@lab.local  
- **Inherited group:** HR‑Staff  
- **Password:** Set manually  
- **User must change password at next logon:** Enabled  

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/b72efb791ee366629e2ad560615e5c3b80d9304e/05-Active-Directory-Structure/Copy%20user%20in%20group%20to%20another%20user%2018.01.41.png)

This method is ideal for onboarding users who require identical access permissions within the same department. It ensures consistency and reduces manual configuration time.


## 05 — Verification
After creating the OUs, users, and groups, I verified the structure in ADUC:

- All OUs appeared correctly  
- User accounts were created successfully  
- Groups were visible and populated  
- Domain structure looked clean and organized  


The domain is now ready for Group Policy configuration and client device
integration.
