
# Section 9 — Creating and Testing Group Policy Objects (GPOs)

## 🧩 Objective
In this part of the lab, I’m creating and testing Group Policy Objects (GPOs) inside my `lab.local` domain.  
This is where I start controlling domain‑joined machines from one central place.

---

## ⚙️ Lab Setup
| Component | Details |
|------------|----------|
| Domain | lab.local |
| Domain Controller | ACT-DIR-LAB |
| Client PC | PC1.lab.local |
| Admin Account | LAB\ACTIVED |

---

## 🧠 Overview
Group Policy lets me push settings to users and computers automatically.  
Here I’m creating a simple test GPO, checking how it behaves by default, linking it to an OU, and confirming it applies on a domain‑joined client.

---

## 🪜 Step‑by‑Step

### Step 1 — Open Group Policy Management
On the Domain Controller:

. Expand the tree:
   ```
   Forest: lab.local
     └── Domains
         └── lab.local
             └── Group Policy Objects
   ```

---

### Step 2 — Create a New GPO

1. Right‑click **Group Policy Objects** → **New**.
2. Name it TEST GPO

![image-alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/58c02b917e90c6eff62abd10a2e8a46960377d7d/09-Group-Policy-Examples/click%20on%20my%20test%20gpo%20%202026-08-19%20at%2023.41.40.png)

---
  ```
   ```
4. Click **OK**.  
   This creates an unlinked GPO that I can configure before applying it anywhere.
![image-alt]()---

### Step 3 — Check Default Security Filtering

![image-alt](test-gpo-screenshot-goes-here.png)

Whenever a new GPO is created, it automatically includes **Authenticated Users** under *Security Filtering*.  
This is the default behaviour in Active Directory — it means the GPO will apply to any user or computer that successfully authenticates to the domain *once the GPO is linked somewhere*.

 Select **TEST GPO**.
Go to the **Scope** tab.
 Under **Security Filtering**, you’ll see:
   ```
   Authenticated Users
   ```
   Right now, the GPO doesn’t affect anything because it isn’t linked to an OU yet.
   Next, I can remove *Authenticated Users* and replace it with specific groups if I want more control.
![image-alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/cdb40b906da79bf1116af0b1fa175a1306dab79c/09-Group-Policy-Examples/remove%20authenticatted%20users%20.png)

---

### Step 4 — Link the GPO and Apply Permissions to a User


For this test, I’m applying the GPO to a specific **user account** instead of a computer.  
I added **Mike Davidson (Mike.Davidson@lab.local)** under *Security Filtering* so the policy only applies to that user.

 ![image-alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/8038bd3094235ff4b49fbe9ead9e48846a94602a/09-Group-Policy-Examples/testing%20out%20a%20user%20on%20secruity%20filter%2020%20at%2000.16.13.png)
  
 Open the **Delegation** tab → click **Advanced** to view detailed permissions.
 Scroll down and make sure **Read** and **Apply Group Policy** are both checked as **Allow** for Mike Davidson.



This setup ensures that Mike Davidson can read and apply the GPO, but not modify or delete it.  
It’s a clean way to test user‑level GPO application without giving admin rights.

---

### ✅ Result
The **TEST GPO** is now linked to the OU and scoped to the user account.  
Mike Davidson has permission to read and apply the policy, confirming that the GPO is configured correctly for user‑based testing.






### Step 4 — Link the GPO to an OU
1. Right‑click the OU I want to test with (I used `Branch1`).
2. Choose **Link an Existing GPO**.
3. Select:
   ```
   TEST GPO
   ```
4. The GPO now shows up under that OU, meaning machines inside that OU will receive it.

---

### Step 5 — Test the GPO on a Client
On the client PC (`PC1.lab.local`):

#### Force a policy update:
```cmd
gpupdate /force
```

#### Check which GPOs applied:
```cmd
gpresult /r
```

#### Optional: Check Group Policy logs
```
Event Viewer → Applications and Services Logs → Microsoft → Windows → GroupPolicy
```

---

## ✅ Result
I’ve created a test GPO, checked its default security filtering, linked it to an OU, and confirmed it applies on a domain‑joined machine.  
This sets me up for the next part of the lab where I’ll start adding actual configurations like:

- Turning off the firewall  
- Setting a desktop wallpaper  
- Mapping a network drive  
- Configuring browser settings  

These will be added in the next part of Section 9.

---

## 📘 Next Up
- Disable Windows Firewall GPO  
- Set Desktop Wallpaper GPO  
- Map Network Drive GPO  
- Configure Edge Homepage GPO

- ### Step 6 — Adjust Security Filtering and Delegation

After creating the test GPO, I wanted to control exactly who it applies to.  
By default, every new GPO includes **Authenticated Users**, which means it would apply to all domain‑authenticated users and computers once linked.  
I removed *Authenticated Users* and added a specific user account instead.

#### Security Filtering
Security filtering is basically the first gatekeeper — it decides who’s allowed to “see” the GPO and potentially have it applied.

1. In the **Scope** tab, under **Security Filtering**, I clicked **Add**.
2. Typed in the username:
   ```
   Mike Davidson
   ```
3. Clicked **Check Names** to confirm it resolved to:
   ```
   Mike.Davidson@lab.local
   ```
4. Removed **Authenticated Users** so only Mike Davidson remains.
5. Saved the changes.

Now the GPO only applies to that user account.

