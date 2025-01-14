🏥 Hospital Network Project
A robust and scalable network designed for hospital infrastructure, featuring high availability, gateway redundancy, and automatic failover. This project leverages advanced networking protocols and automation to ensure uninterrupted connectivity for critical healthcare operations.

📋 Project Overview
🌟 Features:
HSRP Protocol (Hot Standby Router Protocol): Ensures seamless gateway redundancy and failover.
Dual ISP Setup: Provides internet redundancy via two ISPs.
Dynamic IP Allocation: Configured DHCP server for automatic IP address assignment.
DNS Server: Resolves domain names like google.com and facebook.com into IP addresses.
Default Routing: Simplifies routing to external networks.
LAN Infrastructure: Supports multiple devices with reliable connectivity.
🖥 Network Topology:
The topology includes:

2 Routers (R1 and R2) connected to ISPs.
A LAN switch connecting PCs and a DHCP server.
HSRP Virtual IP Address: 192.168.100.254 for gateway redundancy.
🔧 Technical Specifications


1. HSRP Configuration
Router 1 (R1):
interface f0/0  
ip address 192.168.100.10 255.255.255.0  
standby 10 ip 192.168.100.254  
standby 10 priority 150

Router 2 (R2):
interface f0/0  
ip address 192.168.100.20 255.255.255.0  
standby 10 ip 192.168.100.254  

2. DHCP Server Configuration
ip dhcp pool LAN1  
   network 192.168.100.0 255.255.255.0  
   default-router 192.168.100.254  
   dns-server 192.168.100.100  
ip dhcp excluded-address 192.168.100.1 192.168.100.9

4. Default Routing
Router 1 (R1):
ip route 0.0.0.0 0.0.0.0 10.100.101.1  
Router 2 (R2):
Copy code
ip route 0.0.0.0 0.0.0.0 10.100.102.1

📂 Repository Contents
GNS3 Topology File: Import this file into GNS3 to replicate the network setup.
Configuration Files: Pre-written configurations for routers, DHCP server, and DNS.
Project Documentation: Detailed explanation of the setup process and testing results.


✅ Testing and Validation
Test Scenarios:
Failover Test: Simulate a router failure to verify seamless traffic redirection using HSRP.
Connectivity Check: Ping external domains like google.com and facebook.com to ensure DNS resolution and internet access.
DHCP Functionality: Verify automatic IP allocation to LAN devices.

Sample Commands:
On PCs:
ip dhcp  
show ip  
ping www.google.com  
ping www.facebook.com  
ping 192.168.100.254  

On Routers:
show standby  
show ip route  

📊 Results and Learnings
Redundancy Achieved: Gateway failover was successfully tested using HSRP.
Seamless Internet Access: Dual ISPs ensured uninterrupted connectivity.
Scalability Enabled: DHCP server simplified IP address allocation.
This project demonstrates the importance of designing resilient and scalable networks for critical environments like hospitals.

Contributions are welcome! Feel free to fork this repository, suggest improvements, or open a pull request.


