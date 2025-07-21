# FortiGate Firewall

The firewall is placed in security perimeter layer, acts as the first line of defense.

---

## Purpose
- Seperating WAN and LAN
- Creating VLANs with DHCP server
- Internet access to LANs
- Inter-VLAN routing
- Creating a DMZ
- Policies and Security profiles
- Anti DDoS policy
- WAN 2 for attack emulation

---

## Implementation

### Base configuration
- SecureCRT software is used to open CLI of node
- Default username is admin and fortinet will force to make a new password
- Enter ip address in browser to open GUI
- Network -> Interface
- Port 1 is internet facing and is configured as WAN
- Port 2 is configured as LAN

![Fortinet CLI](/assets/screenshots/fortigate/1.png)
![Fortinet GUI](/assets/screenshots/fortigate/2.png)

### VLANs with DHCP
- Network -> Interfaces -> Create New -> Interface
- 6 VLANs are made with IDs (10, 20, 30, 40, 100, 99)
- All VLANs are configured to land on LAN port
- All VLANs are configured with a DHCP server
- These VLANs will serve as default gateway for department endpoints

![Fortinet GUI 3](/assets/screenshots/fortigate/3.png)
![PC ping](/assets/screenshots/fortigate/4.png)

### Internet
- Network -> Static Routes -> Create New
- A static route is configured to default gateway of EVE-NG which brings in Internet
- Network -> DNS -> Specify
- Manual DNS is configured
- Now Internet can reach firewall but not LANs yet

### Inter-VLAN
- Network -> Interfaces -> Create New -> Zone
- A Zone or Group is made of VLANs that require Internet
- Disable block intra zone traffic option to enable inter vlan communication
- Actual communication is still not enabled

![Fortinet GUI 4](/assets/screenshots/fortigate/6.png)

### Policies
- Policy and Objects -> Firewall policy -> Create New
- A new policy is made with the VLANs group as source and WAN as destination
- Rest of configurations are made alongside enabling NAT (Network Address Translation)
- Now Inter-VLAN communication and Internet will be enabled
- Policy and Objects -> IPv4 DoS policy -> Create New
- A policy is configured to protect from DDoS attacks and log them

![Fortinet GUI 5](/assets/screenshots/fortigate/5.png)
![Inter vlan ping](/assets/screenshots/fortigate/7.png)

### DMZ
- Network -> Interfaces
- Port 3 is configured as DMZ
- There is no NAT option as DMZs are not meant to have them

### Security Profiles
- Security profiles -> Anti Virus -> Create New
- Security profiles -> Web Filter -> Create New
- Security profiles -> DNS Filter -> Create New
- SSL/SSH certificate inspection is enabled which is pre configured
- These 4 security profiles are configured, Intrusion Prevention was also configured but there is a bug that does not let it run

![security profile](/assets/screenshots/fortigate/8.png)

### WAN 2 (Attack Emulation)
- Port 4 is configured as another WAN
- This WAN's ip address is mapped with the ip address of physical ethernet adapter on machine
- Ethernet adapter was pulled into EVE-NG as a network using VMware Workstation
- Another machine would be used to send malicious traffic from a physical ethernet cable
- This was done solely with the purpose to reduce hardware load on single machine, it is not necessary

---
