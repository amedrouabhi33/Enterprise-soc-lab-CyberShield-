# IP Addressing & Network Segmentation

## Network Overview

The lab uses a segmented enterprise network with separate VLANs for HR, IT, DMZ, Security, and Management.

All inter-VLAN communication is controlled by the OPNsense firewall.

## VLAN Plan

| VLAN | Name       | Network       | Gateway    | Purpose                   |
| ---: | ---------- | ------------- | ---------- | ------------------------- |
|   10 | HR         | 10.10.10.0/24 | 10.10.10.1 | HR workstations           |
|   20 | IT         | 10.10.20.0/24 | 10.10.20.1 | IT workstations           |
|   30 | DMZ        | 10.10.30.0/24 | 10.10.30.1 | Public-facing services    |
|   40 | SECURITY   | 10.10.40.0/24 | 10.10.40.1 | Security monitoring       |
|   99 | MANAGEMENT | 10.10.99.0/24 | 10.10.99.1 | Infrastructure management |

## Static Systems

| Hostname | IP Address  | VLAN | Role                   |
| -------- | ----------- | ---: | ---------------------- |
| DC01     | 10.10.99.10 |   99 | Active Directory / DNS |
| WAZUH01  | 10.10.40.10 |   40 | SIEM / XDR             |
| WEB01    | 10.10.30.10 |   30 | Ubuntu / Apache        |

## Endpoints

| Hostname | IP Assignment | VLAN | Role           |
| -------- | ------------- | ---: | -------------- |
| HR-PC01  | DHCP          |   10 | HR workstation |
| IT-PC01  | DHCP          |   20 | IT workstation |

## Security Zones

### HR

HR workstations are isolated from the IT network and management network.

Expected access:

* Internet: Allowed
* Active Directory/DNS: Allowed
* Wazuh: Allowed
* IT VLAN: Blocked
* Management VLAN: Blocked

### IT

IT workstations have access to required infrastructure services while remaining isolated from HR endpoints.

Expected access:

* Internet: Allowed
* Active Directory/DNS: Allowed
* Wazuh: Allowed
* HR VLAN: Blocked
* Management VLAN: Restricted

### DMZ

The DMZ contains systems that may provide services to external networks.

The web server is isolated from internal user networks.

Expected access:

* Internet → WEB01: HTTP/HTTPS only
* DMZ → HR: Blocked
* DMZ → IT: Blocked
* DMZ → Management: Blocked
* DMZ → Wazuh: Required monitoring traffic only

### SECURITY

The Security VLAN contains centralized security monitoring infrastructure.

Primary system:

* WAZUH01

Endpoints and network security devices send relevant telemetry to the security infrastructure.

### MANAGEMENT

The Management VLAN contains critical infrastructure such as the domain controller.

Access to this network is restricted to authorized administrative systems.

## Design Goals

The network segmentation is designed around:

* Least privilege
* Network isolation
* Defense in depth
* Centralized monitoring
* Controlled inter-VLAN communication
* Separation of user, server, security, and management networks

This design allows security events to be generated and investigated while maintaining separation between enterprise network zones.

