# 02 — Azure VM Deployment

This section documents the deployment of the Windows Server 2022 Datacenter VM
in Azure. This VM will later be promoted to a Domain Controller.

---

## Resource Group
I created a dedicated resource group for the lab:

- Resource Group: ACT-D-LAB
- Region: East US (Zone 3)

---

## Virtual Machine Configuration
I deployed the Windows Server 2022 VM with the following settings:

- VM Name: ACT-DIR-LAB
- Image: Windows Server 2022 Datacenter
- Size: Standard DC1ds v3 (1 vCPU, 8GB RAM)
- Admin Username: ActiveD


![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/b86045a9abf29bc8a58e3fad2b5657f073c60747/overview%20of%20VM%20in%20Azure%20interface.png)

---

## Networking
I configured the VM networking as follows:

- Virtual Network: ACT-DIR-LAB-vnet
- Subnet: default
- Public IP: Automatically assigned
- Network Security Group: Basic
- Inbound Rule: RDP (TCP 3389)

---

## Static Private IP Configuration
To ensure stable AD DS and DNS functionality, I changed the private IP from
Dynamic to Static.

### Steps Performed
- Opened the VM in Azure Portal
- Navigated to Networking → Network Interface
- Selected IP Configuration
- Switched Private IP from Dynamic → Static
- Saved changes

### Reason
Domain Controllers require a consistent private IP to avoid issues with:
- DNS records
- Domain join operations
- AD DS replication

---

## RDP Access VS Bastion
I choose RDP because connecting via Bastion is a lot more costly for this demonstration LAB. 
SO I connected to the VM using the Remote Desktop on PC and the Windows App on macOS:

- Public IP: 20.115.45.35
- Username: ActiveD

---

## Deployment Checkpoint
- VM running successfully
- Public IP reachable
- Private IP set to static
- Ready for AD DS installation
