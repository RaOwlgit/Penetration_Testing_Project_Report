# 🌐 Minor Project: Infrastructure Deployment & Logging (Azure)

![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E94333?style=for-the-badge&logo=ubuntu&logoColor=white)
![Apache](https://img.shields.io/badge/Apache-D22128?style=for-the-badge&logo=Apache&logoColor=white)
![Logging](https://img.shields.io/badge/Logging-Enabled-brightgreen?style=for-the-badge)

## 📌 Project Overview
This project demonstrates the deployment of a functional **enterprise-style infrastructure** on Microsoft Azure. The primary objective was to design a segmented network, deploy Linux-based virtual machines, and establish a centralized logging pipeline for future security monitoring.

---

## ☁️ Cloud & Resource Details
* **Platform:** Microsoft Azure (Azure for Students)
* **Resource Group:** `Firewallis_Tech`
* **Region:** East Asia
* **Status:** Deployment Complete / Hardening Pending (Intentional)

---

## 🏗️ Network Architecture
The environment uses a **Virtual Network (VNet)** approach to simulate real-world segmentation between public-facing and internal assets.

* **VNet Name:** `Firewallis-VNet`
* **Address Space:** `10.0.0.0/16`

### Subnet Segmentation
| Subnet Name | Address Range | Purpose |
|:--- |:--- |:--- |
| **Internal-Subnet** | `10.0.1.0/24` | Identity Services, File Storage & SIEM |
| **DMZ-Subnet** | `10.0.2.0/24` | Public-facing Web Server |

---

## 🖥️ Virtual Machine Inventory
Three Ubuntu instances were deployed to serve specific enterprise roles:

| VM Name | OS | Role | Subnet | IP Type |
|:--- |:--- |:--- |:--- |:--- |
| **VM-1 (Internal)** | Ubuntu 22.04 | Identity & File Server | Internal | Private + Public |
| **VM-2 (Web Server)** | Ubuntu 22.04 | Apache Web Server | DMZ | Public |
| **VM-3 (SIEM)** | Ubuntu 22.04 | Log Monitoring (Wazuh) | Internal | Public |

---

## 🛠️ Service Configuration

### 🔹 VM 1: Internal Server
* **Identity Management:** Simulates LDAP/FreeIPA concepts for corporate identity.
* **File Services:** Configured with **Samba** for internal file sharing.
* **Logging:** Captures authentication and system-level events.

### 🔹 VM 2: Web Server (DMZ)
* **Web Engine:** **Apache2** hosting a baseline landing page.
* **Log Generation:** Tracks HTTP access and error logs to identify potential web-based attacks.

### 🔹 VM 3: SIEM + Analyst Workstation
* **Core Tool:** **Wazuh** (XDR/SIEM).
* **Function:** Serves as the central "brain" for collecting and visualizing logs from VM-1 and VM-2.

---

## 📊 Logging & Monitoring
A centralized logging pipeline was established to ensure full visibility of the infrastructure.

| Source VM | Logs Captured | Forwarded To |
|:--- |:--- |:--- |
| **Internal Server** | `auth.log`, `syslog` | Wazuh SIEM |
| **Web Server** | `access.log`, `error.log`, `syslog` | Wazuh SIEM |
| **SIEM Server** | Wazuh internal service logs | Local Dashboard |

---

## ⚠️ Security Note
> [!WARNING]
> Security hardening (Firewall rules, password policies, IDS/IPS) has been **intentionally omitted**. This environment is a "baseline" build designed for future attack simulations, vulnerability scanning, and SOC analysis labs.

---

## 📸 Deployment Validation
*The repository contains screenshots documenting the following:*
* **Azure Resource Group:** Visual proof of all assets in `Firewallis_Tech`.
* **Networking:** VNet and Subnet configuration maps.
* **Services:** Active Apache web page and Wazuh dashboard connectivity.
* **Identity:** `whoami` and system status via SSH (Student name visible).

---

## 🎓 Conclusion
This minor project successfully establishes the foundation for a professional security lab. It demonstrates proficiency in:
* Cloud resource management and networking.
* Linux server administration (Ubuntu).
* Deployment of critical enterprise services (Web, File, SIEM).
* Establishing a baseline logging architecture.

---

## 👤 Author
**Rahul Chandrakar** *Course: Ethical Hacking* *Project Type: Minor Project – Infrastructure & Logging*
