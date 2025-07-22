# IP Plan

A simple FLSM (Fixed Length Subnet Masking) is done to keep everything in CIDR of /24, the IP plan is kept super simple to focus on security concepts.

![ip plan](/assets/screenshots/networking/ip_plan.png)

---
---

# Core Switch

A central switch placed in Core Network layer, all communications pass through this switch.

---

## Purpose
- Hosting VLANs
- Propagating VLANs

---

## Implementation

### VLANs
- 6 VLANs with IDs (10, 20, 30, 40, 100, 99) are made on core switch

![core1](/assets/screenshots/networking/cs1.png)

### Propagating VLANs via VTP
- All switchports are configured to be trunk as they have to carry VLANs
- VTP (Vlan Trunking Protocol) is used so all switches can synchronize their vlan databases

![core2](/assets/screenshots/networking/cs2.png)
![core3](/assets/screenshots/networking/cs3.png)

---
---

# NTP Router

A router placed in same module as Cisco ISE.

---

## Purpose
- Support NTP (Network Time Protocol) requirements for Cisco ISE

---

## Implementation

### NTP setup
- Clock is set to custom time
- NTP master with stratum level 5 is configured

![ntp](/assets/screenshots/networking/ntp.png)

---
---

# R&D Routers

A group of routers placed in seperate section of architecture.

---

## Purpose
- Giving a sense of segmentation to VLAN 30 endpoints
- Hosting EIGRP area

---

## Implementation

### Simulating segmentation and EIGRP
- IP addresses with CIDR of /29 is configured
- EIGRP is configured on all 4 routers
- Only endpoints of VLAN 30 are allowed to access in order to give a sense of segmentation to VLAN 30 members

![routers](/assets/screenshots/networking/eig1a2.png)

---
---

# Other Switches

- **Access switches:** these connected to endpoints and represent the access layer, access switch 1 has a special purpose of being a AAA enforcer for Cisco ISE.
- **DMZ-MP switch:** This switch is connected to Cisco ISE and supports VLAN 100 nodes, this switch is secured with IAM and AAA protocols from ISE.
- **DMZ-HP switch:** This switch is connected to the data center server and it hosts a single VLAN 50
- Other switches are connected to their respective endpoints or are only for data transfer

*Note: Switches connected to Cisco ISE are discussed in Cisco ISE's directory*

---
