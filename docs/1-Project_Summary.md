# CyberFortify – Project Summary

CyberFortify is a virtual Security Operations Center (SOC) lab designed to simulate real-world red team attacks and evaluate blue team defenses using enterprise-grade tools. The project provides hands-on experience with detection, response, and identity-based access control in a fully segmented and monitored network environment.

---

## Objective

To build and test a complete cybersecurity defense environment that can:

- Simulate red team attacks (e.g., brute force, tunneling, DDoS, malware)
- Detect and log threats in real-time using SIEMs and IDS
- Apply role-based access policies using Cisco ISE and AAA
- Demonstrate blue team defense through logs, alerts, and firewall rules

---

## Key Components

- **Firewall:** Fortinet – network segmentation and policy enforcement
- **IDS/IPS:** Suricata – detects and logs attack traffic in real time
- **SIEM:** Wazuh and Splunk – event correlation, alerting, and forensic search
- **Access Control:** Cisco ISE – AAA enforcement using RADIUS/TACACS+, VLAN assignment
- **Red Team:** Kali Linux – attack simulations using tools like Hydra, Netcat, hping3

---

## Technologies Used

- Fortinet Firewall
- Suricata IDS
- Wazuh SIEM
- Splunk SIEM
- Cisco ISE (AAA)
- Kali Linux (attack VMs)
- Windows Server (internal endpoints)
- EVE-NG (virtual lab)

---

## What We Demonstrated

- Detection of brute-force, tunneling, malware, and DoS attacks
- Real-time alert generation and dashboarding in SIEMs
- Role-based network segmentation enforced by AAA via Cisco ISE
- Full attack-to-detection lifecycle for each simulated threat

---

## Documentation

- `CyberFortify_Report.pdf`: Complete project report with screenshots, logs, and theory
- `architecture_overview.md`: Visual breakdown of the project architecture
- `simulations/`: Attack procedures and terminal screenshots
- `blue_team/`: Defense logs, screenshots, and configuration summaries

---

## Outcomes

This project demonstrates how a complete SOC can be set up using open-source and enterprise-grade tools to:
- Detect advanced persistent threats
- Respond to network intrusions
- Apply identity-based access control
- Log, alert, and analyze security events across layers

CyberFortify reflects a real-world, defensive cybersecurity environment aimed at building both offensive insight and defensive strategy.

