# CentOS 7 Server

To simulate a data center server CentOS 7 is used which is placed in a Demilitarized Zone (DMZ) in its own VLAN 50.

---

## Purpose
- To simulate a crucial server

---

## Implementation

### Critical server
- VLAN 50 is made on DMZ-MP switch
- Port 3 on firewall is configured as DMZ
- Policy is configured on firewall that would allow only specified VLANs to access this server
- Wazuh agent is configured on this server so SIEM can surveil it using its EDR solutions
- Suricata IDS is also configured so its network traffic can be monitored

![centosping](/assets/screenshots/servers/dc3.png)
![dmzpolicy](/assets/screenshots/servers/dc2.png)
![agent](/assets/screenshots/servers/wazuh_agent_centos.png)
![centosping2](/assets/screenshots/servers/dc4.png)

---
---

# Windows 2016 Server

A windows server is placed in VLAN 100 which is same module as ISE and NTP router.

---

## Purpose
- Support nameserver and domain requirements for Cisco ISE
- Active directory server

---  

## Implementation

### ISE support and AD server
- Configured windows server as an Active Directory server to host backup TACACS credentials for switch
- An OU (Organizational Unit) is specifically made along with user for credentials
- Configured **test.local** domain
- Synced with NTP router to avoid errors like *lw_error_clock_skew* while integrating with ISE
- Wazuh agent is configured for EDR support
- Suricata IDS is configured for network monitoring

![winsrv](/assets/screenshots/servers/win1.png)

---
