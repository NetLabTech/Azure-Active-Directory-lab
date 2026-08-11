
06 — Deploy PC1 and Prepare for Domain Join

This step documents the deployment of the second virtual machine (PC1) and prepares it for joining the lab.local Active Directory domain.

01 — Create the PC1 Virtual Machine

PC1 is deployed in the same resource group, virtual network, and subnet as ADSERVER to ensure proper DNS resolution and network connectivity.

Configuration:

- Resource group: ACT-D-LAB
- Virtual machine name: PC1
- Region: East US
- Availability zone: Zone 3
- Image: Windows Server 2022 Datacenter (Gen2)
- Size: Standard DC1ds v3

![image alt](https://github.com/NetLabTech/Azure-Active-Directory-lab/blob/45c8ed717408ab5fa7f2d99a66e77254d79e02c3/Create%20a%20PC1%20VM.png)
(Insert screenshot)

---

02 — Networking Configuration

PC1 must be placed in the same VNet as ADSERVER.

- Virtual network: ACT-DIR-LAB-vnet
- Subnet: default (10.0.0.0/24)
- Private IP: 10.0.0.5 (Dynamic)
- Public IP: Enabled

(Insert screenshot)

---

03 — Configure DNS to Use ADSERVER

To allow PC1 to locate the domain controller, update its NIC DNS settings:

- Open PC1 → Networking
- Select the network interface
- Open DNS servers
- Choose Custom
- Enter: 10.0.0.4

(Insert screenshot)

---

04 — Verify IP Configuration

PC1 should now show:

- Private IP: 10.0.0.5
- Subnet: default
- Virtual network: ACT-DIR-LAB-vnet
- DNS: 10.0.0.4 (custom)

(Insert screenshot)
