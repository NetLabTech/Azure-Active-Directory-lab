
# 03 — Install Active Directory Domain Services (AD DS)

This step documents the installation of the AD DS role on the Windows Server 2022
VM in Azure. After installing the role, the server will be ready for promotion to
a Domain Controller in Step 4.

---

## 01 — Open Server Manager
I began the installation by opening **Server Manager**, which is used to manage
roles and features on Windows Server.

- Start Menu → Server Manager  
- Waited for Server Manager to fully load  
- Confirmed the server was showing as **Online**

---

## 02 — Add Roles and Features
Next, I launched the Add Roles and Features wizard to install the AD DS role.

- Server Manager → **Manage** → **Add Roles and Features**  
- Selected **Role-based or feature-based installation**  
- Chose the server (**ACT-DIR-LAB**)  
- Continued to the **Roles** section

---

## 03 — Select AD DS Role
I selected the **Active Directory Domain Services** role, which is required for
domain controllers.

- Enabled **Active Directory Domain Services**  
- Accepted the required features  
- Continued through the wizard to the confirmation page

---

## 04 — Install the AD DS Role
I proceeded with the installation of the AD DS binaries.

- Clicked **Install**  
- Waited for the installation to complete  
- No reboot was required at this stage

---

## 05 — Prepare for Domain Controller Promotion
Once the role was installed, Server Manager displayed a notification indicating
that the server was ready for promotion.

- Clicked the **yellow notification flag**  
- Selected **Promote this server to a domain controller**

This begins **Step 4 — Domain Controller Promotion**.
--

