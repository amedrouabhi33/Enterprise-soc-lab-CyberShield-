# Enterprise-soc-lab-CyberShield-
# Enterprise SOC & Network Security Lab

## Overview

This project demonstrates the design and implementation of a small enterprise-style Security Operations Center (SOC) lab in VMware Workstation.

The environment combines network segmentation, firewall security, centralized security monitoring, endpoint telemetry, intrusion detection, Active Directory, and controlled security investigations.

The objective is to simulate how a SOC team monitors, detects, investigates, and responds to security events across an enterprise network.

## Architecture

The lab consists of multiple security zones connected through an OPNsense firewall:

```text
                         INTERNET
                            |
                     +-------------+
                     |   OPNsense  |
                     | Firewall    |
                     | VLAN Routing|
                     | Suricata    |
                     +------+------+
                            |
                       VLAN TRUNK
                            |
        +-------------------+-------------------+
        |                   |                   |
     VLAN 10             VLAN 20             VLAN 30
        HR                   IT                  DMZ
        |                    |                   |
    HR-PC01              IT-PC01              WEB01
   Windows 11           Windows 11            Ubuntu
     Sysmon                Sysmon               Apache
     Wazuh                 Wazuh                Wazuh
        |                    |                   |
        +--------------------+-------------------+
                             |
                          VLAN 40
                         SECURITY
                             |
                         WAZUH01
                       SIEM / XDR
                             |
                          VLAN 99
                       MANAGEMENT
                             |
                           DC01
                    Windows Server / AD
```

## Network Design

| VLAN | Purpose    | Network       | Gateway    |
| ---- | ---------- | ------------- | ---------- |
| 10   | HR         | 10.10.10.0/24 | 10.10.10.1 |
| 20   | IT         | 10.10.20.0/24 | 10.10.20.1 |
| 30   | DMZ        | 10.10.30.0/24 | 10.10.30.1 |
| 40   | Security   | 10.10.40.0/24 | 10.10.40.1 |
| 99   | Management | 10.10.99.0/24 | 10.10.99.1 |

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

* OPNsense
* Suricata
* Wazuh
* Sysmon
* Active Directory
* Apache
* Windows Event Logging
* Linux Logging
* Kali Linux
* VMware Workstation

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

The project will contain documented investigations based on controlled activity inside the lab.

### INC-001 — Network Reconnaissance

Simulated port scanning activity is detected by network security monitoring and investigated through centralized logging.

**MITRE ATT&CK:** T1046 — Network Service Scanning

### INC-002 — Authentication Activity

Controlled authentication failures are generated and investigated using Windows security logs and Wazuh.

### INC-003 — Suspicious PowerShell Activity

Controlled PowerShell activity is monitored using Sysmon and analyzed through Wazuh.

### INC-004 — Web Attack Attempt

Controlled web attack traffic is generated against the isolated DMZ web server and correlated with Apache, Suricata, and Wazuh telemetry.

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

This project is designed to demonstrate practical experience with enterprise networking, security monitoring, SIEM operations, endpoint telemetry, intrusion detection, and SOC investigation workflows.

All security testing is performed within an isolated and authorized laboratory environment.
