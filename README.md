🏗️ Minor Project – Infrastructure Deployment & Basic Logging (Azure)
📌 Project Overview

In this project, we acted as the Infrastructure Team of a simulated company and deployed a small-scale enterprise environment using Microsoft Azure (Azure for Students).

The infrastructure consists of three Linux-based virtual machines, deployed inside one mandatory Azure Resource Group.
This phase focuses only on infrastructure deployment and basic logging.

⚠️ No security hardening was performed intentionally, so the environment remains vulnerable for the Major Project (SOC & Attack Simulation).

🏢 Company / Resource Group Details

Company Name / Resource Group: Firewallis_Tech

Cloud Platform: Microsoft Azure (Azure for Students)

Region: East Asia

Tenant Naming Format: YOUR_ERP_FIRST_NAME_GROUPNO

All resources (VMs, VNet, Subnets, NICs, Disks, Public IPs) were created inside this single Resource Group only.

🌐 Network Architecture
Virtual Network (VNet)

VNet Name: Firewallis-VNet

Address Space: 10.0.0.0/16

Subnets
Subnet Name	Address Range	Description
Internal-Subnet	10.0.1.0/24	Internal services & SIEM
DMZ-Subnet	10.0.2.0/24	Public-facing Web Server
Network Flow
Internet
   |
   v
Web Server (VM-2) [DMZ Subnet]
   |
   v
SIEM Server (VM-3) [Internal Subnet]
   |
   v
Internal Server (VM-1) [Internal Subnet]


External users access the Web Server (DMZ)

Logs are generated and forwarded to SIEM

Internal services are hosted inside Internal Subnet

🖥️ Virtual Machine Inventory
VM Name	OS	Purpose	IP Type	Subnet	Size
Internal-Server	Ubuntu 22.04 LTS	Identity & File Server	Private + Public	Internal	B-series
Web-Server	Ubuntu 22.04 LTS	Apache Web Server	Public	DMZ	B-series
SIEM-Server	Ubuntu 22.04 LTS	SIEM & Analyst Workstation	Public	Internal	B-series

Exact IP addresses and sizes are visible in screenshots.

🔐 VM Roles & Configuration
🔹 VM-1: Internal Server

Roles

Identity Management (LDAP – FreeIPA simulation)

File Server (Samba)

Internal service hosting

Installed Services

slapd (LDAP)

ldap-utils

samba

Purpose
Simulates centralized user identity management and file sharing inside an organization.

🌍 VM-2: Web Server (DMZ)

Roles

Apache Web Server

Static web page hosting

Log generation

Installed Services

apache2

Purpose
Simulates an external-facing vulnerable server for future attack scenarios.

🛡️ VM-3: SIEM + Analyst Workstation

Roles

Central log collection

Security monitoring & analysis

SIEM Tool

Wazuh (All-in-One – Free Edition)

Components

Wazuh Manager

Wazuh Indexer

Wazuh Dashboard

Note
Dashboard may load slowly due to limited Azure Student VM resources, which is expected.

📜 Logging Summary
Logs Generated
VM	Logs
Internal-Server	syslog, auth.log
Web-Server	access.log, error.log, syslog
SIEM-Server	Wazuh internal logs
Logs Forwarded to SIEM

Authentication logs

System logs

Web access & error logs

📸 Screenshots Proof

All screenshots clearly show:

Azure Portal

Resource Group name

Student Azure account name

SSH login proof (whoami command)

📂 Screenshots Folder Structure
screenshots/
├── resource-group.png
├── vnet-subnets.png
├── vm1-ldap-samba.png
├── vm2-apache-page.png
├── apache-logs.png
├── vm3-wazuh-services.png

🚫 Security Hardening (Intentionally Not Done)

The following were NOT implemented as per project rules:

Firewall rules

SSH hardening

Password policies

IDS/IPS tuning

Security baselines

This is intentional so vulnerabilities can be exploited in the Major Project.

🎯 Learning Outcomes

Azure cloud infrastructure deployment

Network segmentation using VNet & subnets

Linux server administration

Web server deployment

Log generation and monitoring basics

SIEM deployment fundamentals

✅ Project Status

✔ Infrastructure deployed
✔ Logging enabled
✔ Screenshots captured
✔ Ready for submission

📌 Author

Student Name: Your Name
Course: Cyber Security
Project Type: Minor Project – Infrastructure & Logging
