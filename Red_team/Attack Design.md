# Attack Design 1

Both the attacker and internal threat operate collaboratively to bypass firewall and communicate for malicious purposes.

---

## Attacker
- Is outside the company LAN in open internet
- **Kali Linux** is used as OS
- Hosts most of the server codes

## Internal Threat
- Is inside the company LAN operating an endpoint of VLAN 40
- **Kali Linux** is used as OS
- Connects to attacker's server to communicate

---
---

# Attack Design 2

A command and control (C2) center is made with multiple machines causing the attack.

---

## Implementation
- The ethernet node seen in topology is mapped to ethernet NIC of two different real machines (laptops/PCs)
- One machine sends the DDoS attack from first laptop which goes through ethernet cable and enter second laptop
- This design distributes the load of the topology is two parts and the attacker topology can be increased as much as someone wants

![red](/assets/screenshots/designs/red_topology.png)

---
