# 01 — Planning Phase

## Overview
This section outlines the planning and design considerations for building an
Active Directory lab environment hosted in Microsoft Azure. The goal is to
create a clean, realistic, enterprise-style AD setup using Windows Server 2022
and Azure infrastructure.

## Objectives
- Build a functional Active Directory domain
- Deploy a Windows Server 2022 Domain Controller in Azure
- Create a structured OU hierarchy
- Add users and test password policies
- Connect via RDP from multiple devices
- Prepare the environment for future GPO and client-join testing

## Lab Architecture
- **Azure VM:** Windows Server 2022 Datacenter  
- **Role:** Domain Controller (AD DS + DNS)  
- **Domain:** lab.local  
- **Network:** Single Azure VNet with static private IP  
- **Access:**Via Bastion and with RDP from macOS and Windows  

## Tools Used
- Azure Portal  
- Windows Server 2022  
- Active Directory Domain Services  
- DNS Server  
- Windows App (macOS) for RDP  

## Why This Lab Exists
This lab provides hands-on experience with identity infrastructure, domain
administration, and Azure-hosted Windows Server environments. It serves as a
foundation for deeper AD learning such as GPOs, client joins, DHCP, and
multi-site topology.
