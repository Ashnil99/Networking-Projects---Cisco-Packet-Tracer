# 01. Single Area OSPF
![OSPF - SINGLE AREA](https://github.com/user-attachments/assets/d15f19ef-ec6b-4b04-884d-ac1d72bb8c03)
- CLI Commands For Setting up Single Area OSPF
R1:
enable
configure terminal
log-adjacency-changes
router-id 1.1.1.1
network 1.1.1.1 0.0.0.0 area 0
network 192.168.0.0 0.0.0.255 area 0
network 12.1.1.0 0.0.0.255 area 0

Other Routers are set up according to their IP Networks
