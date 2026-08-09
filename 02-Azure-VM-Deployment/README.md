
## Overview
This section documents the creation of the Windows Server 2022 Datacenter VM
that will become the Domain Controller for the Active Directory lab.

## Resource Group
- Resource Group: ACT-D-LAB
- Region: East US (Zone 3)

## Virtual Machine Configuration
- VM Name: ACT-DIR-LAB
- Image: Windows Server 2022 Datacenter
- Size: Standard DC1ds v3 (1 vCPU, 8GB RAM)
- Admin Username: ActiveD

## Networking
- Virtual Network: ACT-DIR-LAB-vnet
- Subnet: default
- Public IP: Automatically assigned
- Network Security Group: Basic
- Inbound Rule: RDP (TCP 3389)

## RDP Access
Connected using Windows App (macOS):
- Public IP: 20.115.45.35
- Username: ActiveD

## Static Private IP
Changed private IP from Dynamic → Static to prevent DNS and AD DS issues.

## Deployment Checkpoint
- VM running successfully
- Public IP reachable
- Private IP set to static
- Ready for AD DS installation
