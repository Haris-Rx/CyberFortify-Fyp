
# Attack Simulation – DDoS

This part demonstrates different types of DDoS (Distributed Denial of Service) attacks.

---

## Objective
- Conduct multiple DDoS attacks on topology
- Monitor the generated logs of those attacks
- Monitor the effects caused by the DDoS attacks

---

## Technique Summary

| Attack           | Detail                                                                        |
|------------------|-------------------------------------------------------------------------------|
| TCP SYN Flood    | Floods the target with **tcp syn** messsages but attacker's ip is revealed    |
| UDP Flood        | Floods the target with **udp** messages while revealing ip                    |
| ICMP Flood       | Floods the target with **icmp** messages while revealing ip                   |
| LAND attack      | Uses target against itself by attacking the target with its own ip address    |
| Random Source    | Attacks the target with random ip addresses and floods it                     |

---

## Implementation and Effects

1. Anti DDoS policy was set to drop the DDoS attacks but log them
2. C2 center machines were used to launch distributed attack on firewall
3. If Anti DDoS policy is disabled or set to only log the attacks, high usage is detected on firewall
4. Firewall GUI also crashes if attack goes for prolonged time

![ddos](/assets/screenshots/ddos/Ddos_attack.png)
![effect1](/assets/screenshots/ddos/highusage.png)
![effect2](/assets/screenshots/ddos/reloadsc.png)

---

## Detection

- Firewall logs all the incoming attacks coming from the simulated internet

![ddos logs1](/assets/screenshots/ddos/ddoslog1.png)
![ddos logs2](/assets/screenshots/ddos/ddoslog2.png)
![ddos logs3](/assets/screenshots/ddos/ddoslog3.png)
![ddos logs4](/assets/screenshots/ddos/land.png)
![ddos logs5](/assets/screenshots/ddos/randsour.png)

---
