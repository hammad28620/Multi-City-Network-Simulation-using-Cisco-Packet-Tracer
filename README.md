Computer Networks – Networking Project Report
Table of Contents
Group Information

Project Scenario Definition

Project Objective

Network Requirements

Proposed Topology Overview

Technologies and Protocols Used

Implementation Phases

VLAN Design and Switch Connectivity

Security Configuration Commands

Configuration Saving Commands

Expected Results

Tools Used

Conclusion

Contribution Matrix and Individual Responsibilities

Appendix

Screen Shots

Group Information
Group Member Name	SAP ID
Abubakar Ali	62782
Uzair Ahmed Khan	62131
Adnan Muhammad	63303
Mudansuru Auwalu Garba	66292
Hammad Ahmad	63420
Project Scenario Definition
This project focuses on creating a multi-city network simulation for an organization with branches in:

Lahore (Office One)

Faisalabad (Office Two)

Islamabad (Main Office / Head Office)

Each office contains the following departments:

HR

Finance

Admin

The Head Office (Islamabad) also includes:

CEO Office

Conference Room

The project demonstrates inter-office communication, WAN routing, departmental LAN configuration, VLAN implementation, DHCP, and basic security using Cisco Packet Tracer.

Project Objective
Design LAN and WAN networks for all three offices

Connect all branches using serial WAN links

Implement DHCP in Islamabad for dynamic addressing

Apply static routing for full inter-city communication

Configure VLANs for segmentation

Apply router and switch security

Save and document configurations

Demonstrate full end-to-end connectivity

Network Requirements
4.1 IP Addressing Scheme
Office One: Lahore

Network: 192.168.0.0 /24

Default Gateway: 192.168.0.1

DNS Server: 192.168.0.2

Switches: Admin, HR, Finance

Office Two: Faisalabad

Network: 192.168.1.0 /24

Default Gateway: 192.168.1.1

DNS Server: 192.168.1.2

Switches: Admin, HR, Finance

Office Three: Islamabad (Head Office)

Network: 192.168.2.0 /24

Default Gateway: 192.168.2.1

DNS Server: 192.168.2.2

DHCP Server located here

Switches: Admin, HR, Finance, CEO, Conference Room

4.2 WAN Addressing
Router	Interface	IP Address
Lahore (R1)	Serial 0/2/0	10.10.10.1
Lahore (R1)	Serial 0/2/1	11.11.11.1
Faisalabad (R2)	Serial 0/2/0	10.10.10.2
Faisalabad (R2)	Serial 0/2/1	12.12.12.1
Islamabad (R3)	Serial 0/2/0	11.11.11.2
Islamabad (R3)	Serial 0/2/1	12.12.12.2
4.3 Static Routing Configuration
Router 1 (Lahore)

text
ip route 192.168.1.0 255.255.255.0 10.10.10.2
ip route 192.168.2.0 255.255.255.0 11.11.11.2
Router 2 (Faisalabad)

text
ip route 192.168.0.0 255.255.255.0 10.10.10.1
ip route 192.168.2.0 255.255.255.255 12.12.12.2
Router 3 (Islamabad)

text
ip route 192.168.0.0 255.255.255.0 11.11.11.1
ip route 192.168.1.0 255.255.255.0 12.12.12.1
4.4 DHCP Requirements
A centralized DHCP server located in Islamabad dynamically assigns IP addresses to:

Lahore Network (192.168.0.0/24)

Faisalabad Network (192.168.1.0/24)

Islamabad Network (192.168.2.0/24)

Routers forward DHCP requests using IP Helper (optional based on topology).

4.5 Security Requirements
Enable password on all routers and switches

Console password protection

Encrypt all passwords

Save configurations to startup-config

Proposed Topology Overview
Three offices connected via serial WAN links

Each office contains separate departmental LANs

DHCP & DNS located in Islamabad

Static routes ensure branch-to-branch communication

VLANs separate departments logically

Basic device security is applied

(Topology diagram created in Cisco Packet Tracer)

Technologies and Protocols Used
Feature	Technology
IP Addressing	DHCP
LAN Connectivity	Layer 2 Switches
WAN Connectivity	Serial Links
Routing	Static Routing
Security	Passwords, Encryption
Simulation	Cisco Packet Tracer
Implementation Phases
Phase	Description
Planning	IP ranges, topology design
Device Configuration	Router, Switch, DHCP, DNS setup
WAN Setup	Serial link configuration
Security	Passwords, encryption
Testing	Ping tests, DHCP verification
Documentation	Report writing and screenshots
VLAN Implementation
8.1 VLAN Overview
To ensure secure and efficient network segmentation, VLANs are created for each department in every office. All switches in each office use the same VLAN structure to maintain consistency, improve traffic control, and enhance security. Each office has its own VLANs based on departmental needs.

8.2 VLAN Configuration for All Offices
A. Lahore Office VLANs

VLAN ID	Department
10	HR
20	Finance
30	IT
Commands for Every Switch in Lahore Office

text
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

VLAN ID	Department
10	HR
20	Finance
30	IT
Commands for Every Switch in Faisalabad Office

text
enable
configure terminal
vlan 10
name HR
vlan 20
name Finance
vlan 30
name IT
exit
C. Main Office – Islamabad VLANs

VLAN ID	Department
10	HR
20	Finance
30	IT
40	Conference
50	CEO
Commands for Every Switch in Islamabad Office

text
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
8.3 Trunk Configuration for Inter-Switch Links
Trunk Commands for Lahore & Faisalabad (Only VLANs 10,20,30)

text
interface gigabitEthernet 0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30
Trunk Commands for Islamabad (VLANs 10–50)

text
interface gigabitEthernet 0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30,40,50
8.4 Access Port Assignment Example Commands
text
interface gigabitEthernet 0/5
switchport mode access
switchport access vlan 10
! HR

interface gigabitEthernet 0/6
switchport mode access
switchport access vlan 20
! Finance
Security Configuration Commands
text
enable password cisco
service password-encryption
Configuration Saving Commands
text
write memory
Expected Results
Devices receive IPs via DHCP

LAN connectivity successful within each department

Inter-office routing functional

Serial links operational

Security settings applied

Configurations saved and persistent

Tools Used
Cisco Packet Tracer

Conclusion
This networking project successfully simulates a real-world multi-city enterprise network. The design implements static routing, DHCP, VLAN segmentation, WAN links, and security configurations across Lahore, Faisalabad, and Islamabad. The project demonstrates strong practical understanding of network design, device configuration, and communication testing using Cisco Packet Tracer.

Contribution Matrix and Individual Responsibilities
Group Member Roles and Assigned Tasks
Member Name	SAP ID	Assigned Role / Responsibility	Detailed Work Description
Abubakar Ali	62782	Group Leader / Network Architect	Led overall planning and design, created IP addressing scheme, designed full topology, supervised team work, and reviewed final report/configurations
Uzair Ahmed Khan	62131	Co-Designer / Router & WAN Engineer	Helped design network layout, configured routers and WAN links, implemented static routing, performed connectivity tests
Adnan Muhammad	63303	DHCP & IP Management Engineer	Configured centralized DHCP, created pools, tested device IP allocation, documented results
Mudansuru Auwalu Garba	66292	LAN & Switch Configuration Specialist	Configured Layer-2 switches, verified LAN communication, managed VLAN segmentation, documented switch testing
Hammad Ahmad	63420	Security & Documentation Engineer	Implemented router/switch security, configured passwords and encryption, compiled final report, prepared presentation
Work Division Summary by Project Phase
Phase	Description	Responsible Members
Planning & Design	Diagram creation, addressing scheme, network layout	Abubakar Ali (Lead), Uzair Ahmed Khan
Device Configuration	Router, switch, VLAN, DHCP setup	Hammad Ahmad, Mudansuru Auwalu Garba, Adnan Muhammad
Connectivity Setup	WAN links, LAN connectivity	Uzair Ahmed Khan, Mudansuru Auwalu Garba
Security Configuration	Passwords, encryption	Hammad Ahmad, Abubakar Ali
Testing & Verification	DHCP, routing, WAN/LAN connectivity	All Members
Documentation & Presentation	Screenshots, formatting, report writing	Uzair Ahmed Khan, reviewed by Abubakar Ali
Appendix
A. Routing Commands Summary
Lahore Router (R1)

text
ip route 192.168.1.0 255.255.255.0 10.10.10.2
ip route 192.168.2.0 255.255.255.0 11.11.11.2
Faisalabad Router (R2)

text
ip route 192.168.0.0 255.255.255.0 10.10.10.1
ip route 192.168.2.0 255.255.255.0 12.12.12.2
Islamabad Router (R3)

text
ip route 192.168.0.0 255.255.255.0 11.11.11.1
ip route 192.168.1.0 255.255.255.0 12.12.12.1
B. Security Commands Summary
text
enable password cisco
service password-encryption
write memory
