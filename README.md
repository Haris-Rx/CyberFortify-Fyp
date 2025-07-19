# CyberFortify – Final Year Cybersecurity Project.

## 👤 Team Members

| Haris Dawood | Ali Naeem |
|--------------|-----------|
| <a href="mailto:harisdawoodofficial@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a> <br> <a href="https://www.linkedin.com/in/haris-dawood-b69195282"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a> | <a href="mailto:ali00xac@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a> <br> <a href="https://www.linkedin.com/in/ali-naeem-908545372/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a> |

---

## Project Goals
- Build a virtual defense architecture lab from scratch
- Emulate realistic red team attacks (DDoS, reverse shell, brute force, tunneling)
- Detect and respond using real-time tools (SIEM, IDS, firewall, logging)
- Enforce network access policies and role-based control using AAA

---

## Tools & Technologies

<p align="left">
  <img src="https://img.shields.io/badge/Fortinet-FC1F1F?style=for-the-badge&logo=fortinet&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wazuh-0077C8?style=for-the-badge&logo=wazuh&logoColor=white"/>
  <img src="https://img.shields.io/badge/Suricata-F5821F?style=for-the-badge&logoColor=white"/>
  <img src="https://img.shields.io/badge/EVE--NG-000000?style=for-the-badge&logo=gnubash&logoColor=white"/>
  <img src="https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Windows_Server-00ADEF?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Cisco_ISE-1D9BD1?style=for-the-badge&logo=cisco&logoColor=white"/>
</p>

---

## Simulated Attacks

| Attack Type          | Tool/Technique         | Detection Layer        |
|----------------------|------------------------|------------------------|
| Ping of Death        | hping3                 | Firewall / Wazuh       |
| Brute Force (SSH)    | Hydra                  | Suricata               |
| Reverse Shell        | Netcat / Bash          | Wazuh / Suricata       |
| DDoS (Layer 4/7)     | Slowloris, hping3      | Fortinet / Suricata    |
| HTTP Tunneling       | Custom Python Scripts  | Fortinet / Suricata    |
| Malware Simulation   | Custom Python Scripts  | EDR / Wazuh SIEM       |
| Port Scanning        | Nmap                   | Suricata               |

---

## Multi Layered Security Architecture

> ![Topology Preview](docs/5-network_topology.jpg)

### Defense Structure
- **Fortinet** Firewall as perimeter guard
- **Suricata** IDS for real-time alerts
- **Wazuh** SIEM for correlation, dashboards and EDR
- **Cisco ISE (RADIUS/TACACS)** for identity and access management (IAM)
- Servers used for data center DMZ simulation
- Role-based VLAN segmentation and subnetting

### Attack Emulation
- **Kali Linux** for outside attacker and internal threat
- Multiple linux bots for DDoS
- **Python** for HTTP tunneling, reverse shell and keylogger scripts

---

## Repository Structure

```
CyberFortify/
├── README.md
├── docs/                    # Report, diagrams, architecture
│   ├── CyberFortify_Report.pdf
│   ├── network_topology.png
│   └── architecture.drawio
├── simulations/             # Attack payloads & steps
│   ├── brute_force.md
│   ├── icmp_tunneling.md
│   └── reverse_shell.md
├── blue_team/               # Defense logs & configs
│   ├── cisco_ise/
│   │   ├── access_policy.png
│   │   ├── radius_auth_logs.png
│   │   └── ise_notes.md
│   ├── fortinet/
│   │   ├── firewall_rules.png
│   │   ├── ddos_detection.png
│   │   └── fortinet_logs.md
│   ├── wazuh/
│   │   ├── alerts_dashboard.png
│   │   ├── ssh_brute_log.png
│   │   └── wazuh_config.yaml
│   └── suricata/
│       ├── suricata_alerts.png
│       ├── portscan_detection.png
│       └── suricata.yaml
├── red_team/                # Attacker terminal screenshots
│   ├── brute_force.png
│   ├── icmp_tunnel_demo.png
│   └── reverse_shell_trigger.png
```

---

## Key Learnings
- How real-world SIEMs detect threat behavior
- How firewalls filter Layer 3-7 attack traffic
- How to build a monitorable SOC from scratch
- How AAA protocols control internal access dynamically
- Importance of log correlation, anomaly detection, and IDS
- Importance of putting crucial servers behind DMZ
