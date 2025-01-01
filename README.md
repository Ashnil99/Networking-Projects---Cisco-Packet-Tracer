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

# DHCP
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
