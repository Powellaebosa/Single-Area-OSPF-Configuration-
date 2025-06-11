# Single-Area-OSPF-Configuration-
In this project demonstrates the configuration of OSPF (Open Shortest Path First) in a single area (Area 0) across three routers — Boise, Toledo, and Naperville — with the goal of enabling full inter-LAN communication and external Internet access via a default route. This lab is modeled on real-world enterprise routing infrastructure.

🔑 Objectives:

Configure OSPF routing between routers to enable LAN-to-LAN communication.

Ensure OSPF does not send unnecessary hello packets on LAN and external interfaces.

Create and propagate a default route to allow LAN hosts access to the internet/web server.

Verify routing tables, neighbor relationships, and end-to-end connectivity across the network.

🧰 Tools & Technologies:

Cisco Packet Tracer

Cisco IOS CLI

OSPF (Open Shortest Path First)

IPv4 Addressing

Static Routing

Passive Interface Command

Default Route Advertisement

🚀 Implementation Steps:

✅ Step 1: Boise Router Configuration
Enabled OSPF process (ospf 10) and set router ID 1.1.1.1.

Advertised all directly connected networks using wildcard masks:

bash
Copy
Edit
network 10.0.10.0 0.0.0.255 area 0
network 192.168.2.0 0.0.0.3 area 0
network 192.168.2.4 0.0.0.3 area 0
network 209.165.200.224 0.0.0.3 area 0
Disabled OSPF Hello messages on LAN and WAN interfaces using:

bash
Copy
Edit
passive-interface g0/0
passive-interface s0/0/0
Configured a default static route to the internet via ISP:

bash
Copy
Edit
ip route 0.0.0.0 0.0.0.0 209.165.200.225
Advertised default route in OSPF with:

bash
Copy
Edit
default-information originate


✅ Step 2: Toledo Router Configuration
Enabled OSPF (ospf 10) with router ID 2.2.2.2.

Advertised directly connected networks:

bash
Copy
Edit
network 192.168.100.0 0.0.0.255 area 0
network 192.168.2.0 0.0.0.3 area 0
network 192.168.2.8 0.0.0.3 area 0
Set LAN interface as passive:

bash
Copy
Edit
passive-interface g0/0



✅ Step 3: Naperville Router Configuration
Enabled OSPF (ospf 10) with router ID 3.3.3.3.

Advertised:

bash
Copy
Edit
network 172.31.10.0 0.0.0.255 area 0
network 192.168.2.4 0.0.0.3 area 0
network 192.168.2.8 0.0.0.3 area 0
Set LAN interface as passive:

bash
Copy
Edit
passive-interface g0/0
📡 Network Topology Summary:

3 Routers (Boise, Toledo, Naperville)

3 LANs: 10.0.10.0/24, 192.168.100.0/24, 172.31.10.0/24

WAN Links: /30 networks interconnecting the routers

Web Server connected via ISP to the Boise router

🧪 Validation:

Used show ip ospf neighbor to verify adjacency.

Used show ip route and show ip route ospf to confirm network propagation and default route distribution.

Verified host connectivity across all LANs via ping:

Boise → Toledo

Boise → Naperville

Naperville → Toledo

Successfully accessed the Web Server from LAN hosts via browser.

🎯 Outcome:
This project successfully demonstrated:

End-to-end OSPF implementation across a single area.

Proper default route advertisement using default-information originate.

Efficient use of passive interfaces to optimize OSPF traffic.

Realistic enterprise network scenario simulation and troubleshooting.



<b/>Video Model of Project</h> https://youtu.be/wGWqdC0Trjo
