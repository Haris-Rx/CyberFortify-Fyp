# Suricata IDS

Suricata IDS (Intrusion Detection System) is configured on same server as Wazuh SIEM and is a part of SOC.

---

## Purpose
- Integration into Wazuh for better visibility
- Custom rules for modifiability of traffic
- Network traffic monitoring on endpoints

---

## Implementation

### Wazuh integration
- On wazuh server the location is **/var/ossec/etc/ossec.conf**
- In ossec.conf file enter **localfile** entry in **ossec_config** tab
- The entry is of **eve.json** log file of suricata for both linux and windows so both linux and windows endpoints can send logs

![integration](/assets/screenshots/wazuh/w3.png)

### Custom rules
- Create a *.rules* file in **/etc/suricata/rules/**
- That *.rules* file would be inserted into suricata configuration file at **/etc/suricata/suricata.yaml**
- This would enable suricata IDS on wazuh server
- For endpoints, suricata IDS would be installed and similar configurations is done inside wazuh-agents installed on endpoints

![idsrules1](/assets/screenshots/suricata/s1.png)
![idsrules2](/assets/screenshots/suricata/s2.png)

### Network traffic monitoring
- On wazuh server: Threat Hunting -> [endpoint_name] -> Events
- Suricata logs would also appear here
- Clicking a single log would generate detailed reports
- Any new file created inside or tampered with in suricata directories would be logged too

![idslogs1](/assets/screenshots/suricata/s3.png)
![idslogs2](/assets/screenshots/suricata/d1.png)
![idslogs3](/assets/screenshots/suricata/d2.png)
![idslogs4](/assets/screenshots/suricata/d3.png)
![idslogs5](/assets/screenshots/suricata/d5.png)

---

