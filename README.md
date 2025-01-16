# 01. Single Area OSPF
![OSPF - SINGLE AREA](https://github.com/user-attachments/assets/d15f19ef-ec6b-4b04-884d-ac1d72bb8c03)
- CLI Commands For Setting up Single Area OSPF<br>
R1:<br>
enable<br>
configure terminal<br>
router ospf 10<br>
log-adjacency-changes<br>
router-id 1.1.1.1 <br>
network 1.1.1.1 0.0.0.0 area 0<br>
network 192.168.0.0 0.0.0.255 area 0<br>
network 12.1.1.0 0.0.0.255 area 0<br>
wr<br>
<br>
Other Routers are set up according to their IP Networks<br>

# 02. DHCP
![image](https://github.com/user-attachments/assets/c63e33bf-9265-4681-8dcd-7579e3adfa44)


- CLI Commands for DHCP Configuration <br>
R1: <br>
enable <br>
configure terminal <br>
ip dhcp pool BURAK-POOL <br>
network 192.168.1.0 255.255.255.0 <br>
default-router 192.168.1.1 <br>
dns-server 192.168.1.254 <br>
wr <br>

# 03. VLANs

![image](https://github.com/user-attachments/assets/7d6b62da-891b-42df-9595-544e13028d52)

- CLI Commands for Configuring Two VLANs <br>
R1: <br>
enable <br>
configure terminal <br>
interface range fastethernet 0/1-2<br>
switchport access vlan 2 <br>
interface range fastethernet 0/3-4 <br>
switchport access vlan 3 <br>
wr <br>

# 04. TRUNK 

![TRUNK](https://github.com/user-attachments/assets/972c1c07-b078-4cfe-b683-377472cb4cee)

- CLI Configuration for Trunk link <br>

SW1: <br>
switchport mode trunk <br>

SW2: <br>
switchport trunk encapsulation dot1q <br>  
switchport mode trunk <br>

# 05. BGP

![image](https://github.com/user-attachments/assets/dac56a9f-d96e-49dc-9442-ec5782856cc9)

R1 <br>
int loopback0<br>
ip address 10.0.0.5 255.0.0.0<br>
no shut<br>
exit<br>
int g0/0<br>
ip address 192.168.0.5 255.255.255.0<br>
no shut<br>
exit<br>
router bgp 1234<br>
neighbor 192.168.0.6 remote-as 5678<br>
network 10.0.0.0<br>
end<br>

R2 <br>
int loopback0<br>
ip address 172.16.0.5 255.255.0.0<br>
no shut<br>
int g0/0<br>
ip address 192.168.0.6 255.255.255.0<br>
no shut<br>
exit<br>
router bgp 5678<br>
neighbor 192.168.0.5 remote-as 1234<br>
network 172.168.0.5<br>
end<br>

# 06. IPS (Intrusion Prevention System)
![image](https://github.com/user-attachments/assets/8bffde4e-bd51-42e9-bb91-f30b129b6e3e)

R1: <br>
license boot module c1900 technology-package securityk9<br>
yes<br>
end<br>
wr<br>
reload<br>
mkdir ipsdir<br>
conf t<br>
ip ips config location ipsdir<br>
ip ips name iosips<br>
ip ips signature-category<br>
caregory all<br>
retired true<br>
exit<br>
category ios_ips basic<br>
retired false<br>
exit<br>
exit<br>

int g0/1<br>
ip ips iosips out<br>
exit<br>
logging host 192.168.1.50<br>
service timestamps log datetime msec<br>
ip ips signature-definition<br>
signature 2004 0<br>
status<br>
retired false<br>
enabled true<br>
exit<br>
engine<br>
event-action produce-alert<br>
event-action deny-packet-inline<br>
<br>
do sh ip ips all<br>

