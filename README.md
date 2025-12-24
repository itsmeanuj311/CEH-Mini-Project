# Minor Project – Infrastructure Deployment & Logging (Azure)

## 1. Project Overview

This project demonstrates the deployment of a basic enterprise-style infrastructure on **Microsoft Azure**.  
The objective is to design a small network, deploy virtual machines, and enable basic logging for monitoring.

All resources are created inside **one Azure Resource Group**.  
Security hardening is intentionally **not applied**, as this environment will be used for future attack and SOC simulations.

---

## 2. Cloud & Resource Details

- **Cloud Platform:** Microsoft Azure (Azure for Students)
- **Resource Group Name:** Firewallis_Tech
- **Region:** East Asia

---

## 3. Network Architecture

### Virtual Network (VNet)

- **VNet Name:** Firewallis-VNet
- **Address Space:** 10.0.0.0/16

### Subnets

| Subnet Name | Address Range | Purpose |
|------------|--------------|--------|
| Internal-Subnet | 10.0.1.0/24 | Internal services & SIEM |
| DMZ-Subnet | 10.0.2.0/24 | Public-facing web server |

### Network Flow

Internet → Web Server (DMZ) → SIEM Server → Internal Server

---

## 4. Virtual Machine Inventory

| VM Name | OS | Purpose | Subnet | IP Type | Size |
|------|----|--------|--------|--------|------|
| VM-1 Internal Server | Ubuntu 22.04 LTS | Identity & File Server | Internal | Private + Public | D-Series |
| VM-2 Web Server | Ubuntu 22.04 LTS | Apache Web Server | DMZ | Public | D-Series |
| VM-3 SIEM Server | Ubuntu 22.04 LTS | Log Monitoring | Internal | Public | B-Series |

---

## 5. VM Roles & Configuration

### VM 1 – Internal Server
**Roles:**
- Identity Management (LDAP / FreeIPA concept)
- File Server (Samba)
- Internal service hosting

**Installed Services:**
- LDAP
- Samba
- System logging services

**Purpose:**  
Simulates internal corporate identity and file management.

---

### VM 2 – Web Server (DMZ)
**Roles:**
- Apache Web Server
- Hosts a simple web page
- Generates access and error logs

**Installed Services:**
- Apache2

**Purpose:**  
Simulates an external-facing vulnerable web server.

---

### VM 3 – SIEM + Analyst Workstation
**Roles:**
- Central log collection
- Security monitoring

**Installed Tool:**
- Wazuh (Free SIEM)

**Purpose:**  
Collects and analyzes logs from internal and web servers.

---

## 6. Logging Summary

### Logs Generated

| VM | Logs |
|----|-----|
| Internal Server | auth.log, syslog |
| Web Server | access.log, error.log, syslog |
| SIEM Server | Wazuh service logs |

### Logs Forwarded to SIEM
- Authentication logs
- System logs
- Web access and error logs

---

## 7. Screenshot Proof

Screenshots included in this repository show:
- Azure Resource Group
- Virtual Network & Subnets
- All Virtual Machines
- SSH login (`whoami` command)
- Apache web page
- Wazuh dashboard/services

All screenshots clearly display the **student Azure account name**.

---

## 8. Security Note

No security hardening was applied:
- No firewall tuning
- No IDS/IPS rules
- No password policies

This is intentional for future attack simulation and SOC analysis.

---

## 9. Conclusion

The project successfully demonstrates:
- Cloud infrastructure deployment
- Network segmentation (Internal + DMZ)
- Linux server configuration
- Web server hosting
- Centralized logging using SIEM

This infrastructure is ready for the next phase of security testing and monitoring.

---

## Author

**Name:** ANUJ PRIYADARSHI
**ERP:** 6604606
**Branch:** B.Tech-Computer Science Engineering(Artificial Intelligence & Machine Learning)
**Course:** Ethical Hacking
**Project Type:** Minor Project – Infrastructure & Logging
