Computer Networks – NetworkingProjectReport
Table of Contents
1. Group Information
2. Project Scenario Definition
3. Project Objective
4. Network Requirements
4.1 IP Addressing Scheme
4.2 WAN Addressing
4.3 Static Routing Configuration
4.4 DHCP Requirements
4.5 Security Requirements
5. Proposed Topology Overview
6. Technologies and Protocols Used
7. Implementation Phases
8. VLAN Design and Switch Connectivity
8.1 VLAN Structure
8.2 Switch Setup per Office
8.3 Inter-VLAN Routing
8.4 Summary of VLAN Implementation
9. Security Configuration Commands
10. Configuration Saving Commands
11. Expected Results
12. Tools Used
13. Conclusion
14. Contribution Matrix and Individual Responsibilities
15. Appendix
• Router Routing Commands
• Security Commands Summary
16. Screen Shots
1. Group Information
Group Member Name SAP ID
Abubakar Ali 62782
Uzair Ahmed Khan 62131
Adnan Muhammad 63303
Mudansuru Auwalu Garba 66292
Hammad Ahmad 63420
Computer Networks
Networking Project
2. Project Scenario DefinitionThis project focuses on creating a multi-city network simulation for an organization withbranches in:  Lahore (Office One)
Faisalabad (Office Two)  Islamabad (Main Office / Head Office)
Each office contains the following departments:  HR
 Finance  Admin
The Head Office (Islamabad) also includes:  CEO Office  Conference Room
The project demonstrates inter-office communication, WAN routing, departmental LANconfiguration, VLAN implementation, DHCP, and basic security using Cisco Packet Tracer. 3. Project Objective
Design LAN and WAN networks for all three offices  Connect all branches using serial WAN links  Implement DHCP in Islamabad for dynamic addressing
 Apply static routing for full inter-city communication
 Configure VLANs for segmentation
 Apply router and switch security
 Save and document configurations  Demonstrate full end-to-end connectivity
4. Network Requirements
4.1 IP Addressing Scheme
Office One: Lahore
 Network: 192.168.0.0 /24
 Default Gateway: 192.168.0.1
 DNS Server: 192.168.0.2
 Switches: Admin, HR, Finance
Computer Networks
Networking Project
Office Two: Faisalabad
 Network: 192.168.1.0 /24
 Default Gateway: 192.168.1.1
 DNS Server: 192.168.1.2
 Switches: Admin, HR, Finance
Office Three: Islamabad (Head Office)  Network: 192.168.2.0 /24
 Default Gateway: 192.168.2.1
 DNS Server: 192.168.2.2
 DHCP Server located here  Switches: Admin, HR, Finance, CEO, Conference Room
4.2 WAN Addressing Scheme
Router Interface IP Address
Lahore (R1) Serial 0/2/0 10.10.10.1
Serial 0/2/1 11.11.11.1
Faisalabad (R2) Serial 0/2/0 10.10.10.2
Serial 0/2/1 12.12.12.1
Islamabad (R3) Serial 0/2/0 11.11.11.2
Serial 0/2/1 12.12.12.2
4.3 Static Routing Configuration
 Router 1 (Lahore)
ip route 192.168.1.0 255.255.255.0 10.10.10.2
ip route 192.168.2.0 255.255.255.0 11.11.11.2
 Router 2 (Faisalabad)
ip route 192.168.0.0 255.255.255.0 10.10.10.1
ip route 192.168.2.0 255.255.255.255 12.12.12.2
 Router 3 (Islamabad)
ip route 192.168.0.0 255.255.255.0 11.11.11.1
ip route 192.168.1.0 255.255.255.0 12.12.12.1
4.4 DHCP Requirements
A centralized DHCP server located in Islamabad dynamically assigns IP addresses to:  Lahore Network (192.168.0.0/24)  Faisalabad Network (192.168.1.0/24)  Islamabad Network (192.168.2.0/24)
Computer Networks
Networking Project
Routers forward DHCP requests using IP Helper (optional based on topology). 4.5 Security Requirements
Enable password on all routers and switches  Console password protection
 Encrypt all passwords  Save configurations to startup-config
5. Proposed Topology Overview Three offices connected via serial WAN links  Each office contains separate departmental LANs  DHCP & DNS located in Islamabad
 Static routes ensure branch-to-branch communication
 VLANs separate departments logically
 Basic device security is applied
(Topology diagram created in Cisco Packet Tracer.)
6. Technologies and Protocols UsedFeature Technology
IP Addressing DHCP
LAN Connectivity Layer 2 Switches
WAN Connectivity Serial Links
Routing Static Routing
Security Passwords, Encryption
Simulation Cisco Packet Tracer
7. Implementation Phases
Phase Description
Planning IP ranges, topology design
Device Configuration Router, Switch, DHCP, DNS setup
WAN Setup Serial link configuration
Security Passwords, encryption
Testing Ping tests, DHCP verification
Documentation Report writing and screenshots
Computer Networks
Networking Project
8. VLAN Implementation
8.1 VLAN Overview
To ensure secure and efficient network segmentation, VLANs are created for each
department in every office. All switches in each office use the same VLANstructure tomaintain consistency, improve traffic control, and enhance security. Each office has its own VLANs based on departmental needs. 8.2 VLAN Configuration for All OfficesA. Lahore Office VLANs
VLAN List (Lahore)
VLAN ID Department
10 HR
20 Finance
30 IT
Commands for Every Switch in Lahore Office
enable
configure terminal
vlan 10
name HR
vlan 20
name Finance
vlan 30
name IT
exit
B. Faisalabad Office VLANs
VLAN List (Faisalabad)
VLAN ID Department
10 HR
20 Finance
30 IT
Computer Networks
Networking Project
Commands for Every Switch in Faisalabad Office
enable
configure terminal
vlan 10
name HR
vlan 20
name Finance
vlan 30
name IT
exit
C. Main Office – IslamabadVLANsVLAN List (Islamabad)
VLAN ID Department
10 HR
20 Finance
30 IT
40 Conference
50 CEO
Commands for Every Switch in Islamabad Office
enable
configure terminal
vlan 10
name HR
vlan 20
name Finance
vlan 30
name IT
vlan 40
name Conference
vlan 50
name CEO
exit
8.3 Trunk Configuration for Inter-SwitchLinks
Trunk Commands for Lahore & Faisalabad (Only VLANs 10,20,30)
Computer Networks
Networking Project
interface gigabitEthernet 0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30
Trunk Commands for Islamabad (VLANs 10–50)
interface gigabitEthernet 0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30,40,50
8.4 Access Port Assignment
Example Commands
interface gigabitEthernet 0/5
switchport mode access
switchport access vlan 10 ! HR
interface gigabitEthernet 0/6
switchport mode access
switchport access vlan 20 ! Finance
9. Security Configuration Commandsenable password cisco
service password-encryption 10. Configuration Saving Commandswrite memory
11. Expected Results
 Devices receive IPs via DHCP
 LAN connectivity successful within each department  Inter-office routing functional  Serial links operational  Security settings applied
 Configurations saved and persistent
12. Tools Used
 Cisco Packet Tracer
Computer Networks
Networking Project
13. Conclusion
This networking project successfully simulates a real-world multi-city enterprise network. The design implements static routing, DHCP, VLAN segmentation, WAN links, and securityconfigurations across Lahore, Faisalabad, and Islamabad. The project demonstrates strongpractical understanding of network design, device configuration, and communication testingusing Cisco Packet Tracer. 14. Contribution Matrix andIndividualResponsibilities
Group Member Roles and Assigned Tasks
Member Name
SAP
ID
Assigned Role /
Responsibility
Detailed Work DescriptionAbubakar Ali 62782 Group Leader /
Network Architect
Led overall planning and design, createdIPaddressing scheme, designed full topology, supervised team work, and reviewed final
report/configurations. Uzair Ahmed
Khan
62131
Co-Designer /
Router & WAN
Engineer
Helped design network layout, configuredrouters and WAN links, implemented staticrouting, performed connectivity tests. Adnan
Muhammad
63303
DHCP & IP
Management
Engineer
Configured centralized DHCP, created pools, tested device IP allocation, documentedresults. Mudansuru
Auwalu Garba
66292
LAN & Switch
Configuration
Specialist
Configured Layer-2 switches, verified LANcommunication, managed VLANsegmentation, doc umented switch testing. Hammad
Ahmad
63420
Security &
Documentation
Engineer
Implemented router/switch security, configuredpasswords and encryption, compiled final
report, prepared presentation. 14.1 Work Division Summary by Project Phase
Phase Description Responsible Members
1. Planning & Design
Diagram creation, addressing
scheme, network layout
Abubakar Ali (Lead), Uzair AhmedKhan
2. Device
Configuration
Router, switch, VLAN, DHCP
setup
Hammad Ahmad, MudansuruAuwalu Garba, Adnan Muhammad3. Connectivity Setup WAN links, LAN connectivity
Uzair Ahmed Khan, MudansuruAuwalu Garba
Computer Networks
Networking Project
Phase Description Responsible Members
4. Security
Configuration
Passwords, encryption Hammad Ahmad, Abubakar Ali
5. Testing &
Verification
DHCP, routing, WAN/LAN
connectivity
All Members
6. Documentation &
Presentation
Screenshots, formatting, report
writing
Uzair Ahmed Khan, reviewedbyAbubakar Ali
15. Appendix
A. Routing Commands Summary
Lahore Router (R1)
ip route 192.168.1.0 255.255.255.0 10.10.10.2
ip route 192.168.2.0 255.255.255.0 11.11.11.2
Faisalabad Router (R2)
ip route 192.168.0.0 255.255.255.0 10.10.10.1
ip route 192.168.2.0 255.255.255.0 12.12.12.2
Islamabad Router (R3)
ip route 192.168.0.0 255.255.255.0 11.11.11.1
ip route 192.168.1.0 255.255.255.0 12.12.12.1
B. Security Commands Summary
enable password cisco
service password-encryption
write memory
