# Install Active Directory Domain Services (AD DS)

This step covers installing the AD DS role on your Windows Server 2022 VM in Azure. 
You will install the role first, then promote the server to a Domain Controller in Step 4.

---

## 01 — Open Server Manager
Server Manager is where Windows Server roles and features are installed.

- Start Menu → Server Manager  
- Wait for Server Manager to fully load  
- Ensure the server shows as **Online**

---

## 02 — Add Roles and Features
This wizard installs the AD DS role required for domain controllers.

- Server Manager → **Manage** → **Add Roles and Features**  
- Choose **Role-based or feature-based installation**  
- Select your server (**ACT-DIR-LAB**)  
- Continue to the **Roles** section

---

## 03 — Select AD DS Role
**Critical Step**  
Active Directory Domain Services is the core identity role.

- Tick **Active Directory Domain Services**  
- Accept required features when prompted  
- Click **Next** until the confirmation page

---

## 04 — Install the AD DS Role
This installs the binaries needed before promotion.

- Click **Install**  
- Wait for installation to complete  
- Do **not** reboot unless prompted

---

## 05 — Prepare for Domain Controller Promotion
After installation, Server Manager shows a notification to promote the server.

- Look for the **yellow flag** in Server Manager  
- Click **Promote this server to a domain controller**  

This begins **Step 4 — Domain Controller Promotion**.
