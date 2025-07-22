# Wazuh SIEM

Wazuh SIEM is made on server placed in Security Operations Center (SOC), its an Ubuntu VM pulled into EVE-NG.

---

## Purpose
- Agent health and stats monitoring
- Logs monitoring
- Threat Hunting
- Vulnerability Detection
- Threat Intelligence

---

## Implementation

### Stats monitoring
- Install new wazuh agent in endpoint
- Agent details would show in Wazuh server
- Complaince, SCA checks, config files and other options are in control

![stats](/assets/screenshots/wazuh/w1.png)

### Logs monitoring and Threat Hunting
- Threat Hunting -> [endpoint_name] -> Events
- Events would show real time logs of endpoint
- Detailed reports are generated from logs
- Example: Wrong password input on CentOS 7 server which is wazuh agent, logs appear

![stats](/assets/screenshots/wazuh/w2.png)
![stats](/assets/screenshots/wazuh/w5.png)
![stats](/assets/screenshots/wazuh/w4.png)

### Vulnerability Detection
- Graphical views of everything related to found vulnerabilities
- Integrated CVEs and system to patch vulnerabilities
- Vulnerability Detection -> [endpoint_name] -> Inventory
- Logs related to vulnerabilities, details reports are also generated

![stats](/assets/screenshots/wazuh/w6.png)
![stats](/assets/screenshots/wazuh/w7.png)

### Threat Intelligence
- MITRE ATT&CK framework integrated
- Provides tactics, techniques about security breaches
- Provides information about hacking groups around the world

![stats](/assets/screenshots/wazuh/w8.png)

---
