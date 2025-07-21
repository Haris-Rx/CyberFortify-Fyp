# Cisco ISE

Cisco ISE (Integrated Services Engine) is placed in a seperate module with its supporting components in VLAN 100.

---

## Purpose
- Authenticate endpoints through RADIUS
- Provide security to NADs through TACACS+
- Automatic VLAN assignment of endpoints

---

## Implementation

### RADIUS (Remote Authentication Dial-In User Service)
- IP address is assigned on SVI (Switched Virtual Interface) of VLAN 100 of Access Switch 1
- NAD (Network Access Device) is integrated into Cisco ISE with radius shared secret
- AAA related RADIUS commands are configured in NAD/Switch
- MAC address of endpoint is configured as trusted mac in ISE
- RADIUS policies are configured in ISE

![vlan_svi](/assets/screenshots/cisco_ise/rad3.png)
![nad](/assets/screenshots/cisco_ise/rad0.png)
![nadcommands1](/assets/screenshots/cisco_ise/rad1.png)
![nadcommands2](/assets/screenshots/cisco_ise/rad2.png)

### Automatic VLAN Assignment
- A profile is made for VLAN 100 automatic assignment
- Profile is configured into RADIUS policy
- Cisco ISE will push the policy and switch will enforce it on endpoint to make it a part of VLAN 100 and authenticate using RADIUS
- Operations -> Radius Live Logs

![vlan_assign](/assets/screenshots/cisco_ise/rad_vlan_assign.png)
![authlogs](/assets/screenshots/cisco_ise/rad4.png)
![logs2](/assets/screenshots/cisco_ise/rad5.png)
![logs3](/assets/screenshots/cisco_ise/rad6.png)

### TACACS+ (Terminal Access Controller Access-Control System)
- Similarly to RADIUS, IP address is assigned on VLAN 100
- NAD is integrated into Cisco ISE with tacacs shared secret
- AAA related TACACS commands are configured in NAD/Switch
- Policies are made regarding which protocol is selected, login or enable shell on switch and what privilege level to be assigned
- Authorization is configured as which commands are authorized to run and which are not
- A username/password combination is made on Cisco ISE that NAD/Switch will use
- Operations -> Tacacs Live Logs

![vlan_svi](/assets/screenshots/cisco_ise/tt1.png)
![vlan_svi](/assets/screenshots/cisco_ise/tt2.png)
![vlan_svi](/assets/screenshots/cisco_ise/tt3.png)
![vlan_svi](/assets/screenshots/cisco_ise/tac2.png)
![vlan_svi](/assets/screenshots/cisco_ise/tac3.png)
![vlan_svi](/assets/screenshots/cisco_ise/tac4.png)

---
