# Apex University Multi-Campus Network (CSE405)

A full-fledged enterprise-style network design for **Apex University** connecting eight campuses with multiple subnets, centralized services, and dynamic routing. [file:1]

## Overview
This project designs a unified wired + wireless network across **8 campuses**, intended to support academic, administrative, and research connectivity. [file:1]  
The design uses centralized services (DHCP, DNS, and a Web Server) and aims for scalability, manageability, and campus-to-campus connectivity. [file:1]

## Architecture
- **Topology:** Routers R1–R8 are assigned one per campus, and each campus has its own LAN subnet with both wired and wireless hosts. [file:1]  
- **Server room placement:** The server room is connected to **Campus 5** and hosts the DHCP server, DNS server, and the Web server. [file:1]  
- **Core services:** DNS resolves `apex.edu.bd`, and there is a single Web Server serving the website for that domain. [file:1]

Routing and addressing (high level):
- **Dynamic routing:** OSPF is used so campus routers can exchange routes dynamically (configured in area 1 using network statements with wildcard masks). [file:1]  
- **Central DHCP relay:** Campus LAN interfaces use `ip helper-address 128.254.20.1` to relay DHCP requests to the centralized DHCP server. [file:1]  
- **Scale in the report:** The design includes **8 networks** and **27 hosts** (including **7 wireless** hosts). [file:1]

## How to run (Packet Tracer / Cisco IOS simulator)
1. Build the physical topology with **8 routers (R1–R8)**, campus switches, and wired + wireless end devices per campus. [file:1]  
2. Connect the server room to **Campus 5** and add DHCP, DNS, and Web Server devices in that segment. [file:1]  
3. Apply the router CLI configurations (interfaces + OSPF) and ensure each campus LAN interface has the DHCP relay (`ip helper-address 128.254.20.1`). [file:1]

Example snippets from the report (reference):
- R1 includes LAN `fa0/0 128.10.20.254/16`, serial links (e.g., `128.20.0.1/16`, `128.30.0.1/16`), OSPF networks, and `ip helper-address 128.254.20.1`. [file:1]  
- R5 (Campus 5) includes LAN `fa0/0 128.254.20.254/16`, multiple serial links (e.g., `128.38.0.1/16`, `128.32.0.2/16`, `128.34.0.2/16`), and OSPF for the campus and backbone networks. [file:1]

## Testing
- **IP assignment:** Verify hosts in different campuses receive IP addresses via the centralized DHCP server. [file:1]  
- **Connectivity:** Use ICMP ping tests between hosts across campuses (the report demonstrates ping testing with Simple PDU). [file:1]  
- **DNS + Web:** Confirm DNS resolves `apex.edu.bd` and clients from different networks can reach the Web Server for the university URL. [file:1]

## Notes (issues & limitations)
The report highlights design risks such as lack of redundancy for critical devices (e.g., a failure in Router 8 can disrupt inter-campus connectivity). [file:1]  
It also notes missing segmentation/security controls (e.g., no firewalls/segmentation between subnets), plus complexity and scaling/management challenges as the network grows. [file:1]

### Author / Course
- **Submitted by:** Hasnay Hasin, East West University, CSE405 (Computer Network), Section 01. [file:1]
- **Submitted to:** Dr. Anisur Rahman, Associate Professor, Dept. of CSE. [file:1]
