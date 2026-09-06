# Enterprise SOC & Network Security Lab

## Overview

This project demonstrates the design and implementation of a small enterprise-style Security Operations Center (SOC) lab in VMware Workstation.

The environment combines network segmentation, firewall security, centralized security monitoring, endpoint telemetry, intrusion detection, Active Directory, and controlled security investigations.

The objective is to simulate how a SOC team monitors, detects, investigates, and responds to security events across an enterprise network.

## Architecture

The lab consists of multiple security zones connected through an OPNsense firewall:

<img width="1312" height="1199" alt="ChatGPT Image Sep 5, 2026, 11_03_03 PM" src="https://github.com/user-attachments/assets/c2fefd25-2ec9-427b-ab4a-1bb006f9995b" />
## Network Design

<img width="1774" height="887" alt="ChatGPT Image Sep 5, 2026, 11_08_46 PM" src="https://github.com/user-attachments/assets/3e350ee8-391d-43fb-b534-b7f7d5322375" />


## Virtual Machines

| System      | Operating System | Purpose                           |
| ----------- | ---------------- | --------------------------------- |
| OPNsense-FW | OPNsense         | Firewall, routing, VLANs, IDS/IPS |
| DC01        | Windows Server   | Active Directory and DNS          |
| WAZUH01     | Linux            | SIEM/XDR                          |
| HR-PC01     | Windows 11       | Employee endpoint                 |
| IT-PC01     | Windows 11       | IT endpoint                       |
| WEB01       | Ubuntu Server    | DMZ web server                    |
| Kali        | Kali Linux       | Authorized security testing       |

## Security Technologies

<img width="1536" height="1024" alt="ChatGPT Image Sep 5, 2026, 11_14_28 PM" src="https://github.com/user-attachments/assets/beccf224-eec4-4aee-8dda-d87fc4ad6da3" />


## Security Objectives

This lab demonstrates:

* Network segmentation using VLANs
* Inter-VLAN firewall controls
* Least-privilege network access
* Centralized security logging
* Windows endpoint monitoring
* Sysmon telemetry
* Network intrusion detection
* Authentication monitoring
* PowerShell activity monitoring
* Web attack detection
* Security incident investigation
* MITRE ATT&CK mapping

## Security Investigations

<img width="1536" height="1024" alt="ChatGPT Image Sep 5, 2026, 11_17_53 PM" src="https://github.com/user-attachments/assets/16619769-de8f-42db-a36a-a7ff0b986de8" />


## Project Workflow

The environment will be built in phases:

1. VMware network infrastructure
2. OPNsense firewall
3. VLAN segmentation
4. Active Directory
5. Wazuh SIEM
6. Windows endpoints
7. Sysmon
8. Ubuntu web server
9. Suricata IDS/IPS
10. Security detections
11. Controlled attack simulations
12. SOC investigations
13. MITRE ATT&CK mapping

## Portfolio Objective

<img width="1536" height="1024" alt="ChatGPT Image Sep 5, 2026, 11_20_28 PM" src="https://github.com/user-attachments/assets/337b7a88-2a4c-49d9-8a33-8c97924855c8" />

