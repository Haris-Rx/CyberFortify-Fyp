# EVE-NG Network Topology Overview

This section explains the actual EVE-NG topology built to emulate the enterprise environment for CyberFortify.

---

## 🔹 Virtual Devices Used

- **Fortinet FortiGate** – Placed at the perimeter as first line of defense, DHCP server per VLAN
- **Cisco ISE** – Placed seperately in VLAN 100, enforces RADIUS auth, TACACS+ on NAD and VLAN assignment
- **Wazuh SIEM** – Connected via management VLAN, collects logs, performs EDR through agents
- **Suricata IDS** – Integrated inside Wazuh, logs network traffic via custom ruleset
- **Data Center Server** – Based on CentOS 7 for simulating a crucial server, in seperate VLAN 50
- **Windows Server** – Active Directory server for supporting Cisco ISE domain
- **NTP Router** – Configured as only NTP master for supporting Cisco ISE
- **Core Switch (Cisco IOSv)** – Trunked with other switches, Hosts VLANs
- **ISE module Switch** – Connected to Cisco ISE, TACACS+ enabled security
- **Access Switches (Cisco IOSv and IOL)** – Connected to endpoints of departments, Access switch 1 is RADIUS enforcer
- **Kali Linux** – Launches attacks into internal zones with help of Internal Threat

---

## 🔹 VLANs / Departments

| VLAN ID | Purpose            | Devices                             |
|---------|--------------------|-------------------------------------|
| 10      | Endpoints          | Windows/Ubuntu Desktops             |
| 20      | Endpoints          | Windows/Ubuntu Desktops             |
| 30      | Endpoints / R&D    | Desktops, Network Devices           |
| 40      | Endpoints          | Windows/Linux Desktops              |
| 50      | DMZ                | CentOS 7 SRV                        |
| 99      | Segmentation (SOC) | Siem/Ids SRV                        |
| 100     | Management (ISE)   | Cisco ISE, Windows SRV, NTP router  |

- VLAN 10 is department 1 which is supervised by Cisco ISE and its supporting components, these endpoints have access to data center/dmz server
- VLAN 20 is department 2 which is monitored by SOC (SIEM and IDS), these endpoints also have access to data center/dmz server
- VLAN 30 is department 3 which is only allowed access to NetSec R&D section in topology which is just to simulate segmentation
- VLAN 40 is department 4 which is only allowed access to internet

---

## Topology Diagram

![EVE-NG Network Topology](/assets/screenshots/designs/network_topology.jpg)

---

## Summary

This EVE-NG emulation is an enterprise-grade, multi-layered security architecture using some licenced (EVAL) and open-source technologies.

