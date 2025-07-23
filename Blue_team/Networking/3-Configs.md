# Core Switch:

[Make VLANs]  
[Trunk all ports]  
[Enable VTP domain]  

---

# ISE Switch (TACACS):

[Assign ip address on VLAN and other stuff]

aaa new-model  
tacacs server PSN01  
address ipv4 192.168.149.160    
key cisco123  
exit  
aaa group server tacacs ISE-LAB  
server name PSN01  
end  
test aaa group ISE-LAB user1 Cisco123 new-code  
sh run | sec tacacs  

aaa authentication login AuthC group ISE-LAB local  
aaa authentication enable default group ISE-LAB enable  
line vty 0 4  
login authentication AuthC  

(OR)

aaa authentication login AuthC group ISE-LAB local  
line vty 0 4  
login authentication AuthC  
aaa authentication enable default group ISE-LAB enable  
exit  

aaa authorization exec AuthZ group ISE-LAB local  
line vty 0 4  
authorization exec AuthZ  
exit  
aaa authorization commands 0 AuthZ group ISE-LAB local    
aaa authorization commands 1 AuthZ group ISE-LAB local   
aaa authorization commands 15 AuthZ group ISE-LAB local  
aaa authorization config-commands  
line vty 4  
rotary 1  
authorization commands 0 AuthZ  
authorization commands 1 AuthZ  
authorization commands 15 AuthZ  

---

# Access Switch (AAA Enforcer - RADIUS):

[Do basic configurations first]

aaa new-model  
radius server CiscoISE  
address ipv4 192.168.149.160	  
key cisco321  
exit  
aaa server radius dynamic-author  
client 192.168.149.160 server-key cisco321  
exit   
aaa authentication dot1x default group radius  
aaa authorization network default group radius  
aaa accounting dot1x default start-stop group radius  
dot1x system-auth-control  
end  

int e0/1   
sw mode access  
sw access vlan 1  
no shut  
dot1x pae authenticator   
authentication port-control auto / force-authorized  
no authentication open  
mab  
authentication order mab dot1x  
authentication priority mab dot1x  
authentication host-mode single-host  
sh authentication session interface e0/1  

test aaa group radius user1 Cc123 legacy  

---

# NTP Router:

[Do basic configurations first]

show clock  
clock set HH:MM:SS DD Mon Year  
ntp master 5  
show ntp status  
show ntp associations  
show running-config | include ntp  

---

# R&D Routers:

ROUTER 1:-  
no logging console  
no service config  
int e0/0  
no ip address dhcp  
ip address 10.10.30.30 255.255.255.0  
exit  
int serial 1/0  
ip address 1.1.1.1 255.255.255.248  
no shut   
int serial 1/1  
ip address 4.4.4.2 255.255.255.248  
no shut   
end  
router eigrp 100  
network 1.1.1.0 0.0.0.7  
network 4.4.4.0 0.0.0.7  
network 10.10.30.0 0.0.0.255  
no auto-summary  
end  
conf t  
username admin secret cisco  
enable secret cisco  
line vty 0 4   
login local  
transport input telnet   
logging synchronous  
end  

ROUTER 2:-  
int serial 1/0  
ip address 1.1.1.2 255.255.255.248  
no shut  
int serial 1/1  
ip address 2.2.2.1 255.255.255.248  
no shut  
end  
router eigrp 100  
network 1.1.1.0 0.0.0.7  
network 2.2.2.0 0.0.0.7  
no auto-summary  
end  

ROUTER 3:-  
int serial 1/1  
ip address 2.2.2.2 255.255.255.248   
no shut  
int serial 1/2   
ip address 3.3.3.1 255.255.255.248  
no shut  
end  
router eigrp 100  
network 2.2.2.0 0.0.0.7  
network 3.3.3.0 0.0.0.7  
no auto-summary  
end  

ROUTER 4:-  
int serial 1/2  
ip address 3.3.3.2 255.255.255.248  
no shut  
int serial 1/1  
ip address 4.4.4.2 255.255.255.248  
no shut  
end  
router eigrp 100  
network 3.3.3.0 0.0.0.7  
network 4.4.4.0 0.0.0.7  
no auto-summary  
end  

show ip eigrp neighbors  
show ip route eigrp  

---
