# Multi-Site-NetSec-Infrastructure
**Advanced Cisco Network Security Project - NTI Summer Intern Final Project**

## 📌 Project Overview
This project demonstrates the design and implementation of a secure, scalable enterprise network using **Cisco Packet Tracer**. [cite_start]The network architecture consists of 8 routers and 18 subnets, featuring advanced dynamic routing and multi-layered security protocols to ensure data integrity and secure remote management[cite: 1, 3].

## 🚀 Key Features & Technologies (Current Status)
- [cite_start]**Routing:** Fully implemented dynamic routing using **OSPF** (Open Shortest Path First) across all infrastructure routers to ensure connectivity[cite: 8, 9].
- **Security:**
  - [cite_start]**OSPF MD5 Authentication:** Secured routing updates between all neighbors using MD5 hashing to prevent unauthorized route injection[cite: 10].
  - [cite_start]**Secure Management (SSH):** Disabled insecure Telnet and enabled **SSH v2** on all devices with 1024-bit RSA keys for encrypted remote access.
  - [cite_start]**Zone-Based Policy Firewall (ZPF):** (Planned) Defining Inside, Outside, and DMZ zones to control traffic flow[cite: 22, 23, 24].
  - [cite_start]**Site-to-Site VPN (IPsec):** (Planned) Secure communication between private networks over the public WAN[cite: 34, 35].
  - [cite_start]**ACLs:** (Planned) Granular Access Control for ICMP, SSH, and HTTP traffic[cite: 28, 29].
  - [cite_start]**AAA:** (Planned) Authentication via RADIUS and TACACS+ with local fallback[cite: 16, 18].
- [cite_start]**Switching:** (In Progress) VLAN segmentation (Management & Data) and Layer 2 Security[cite: 37, 38, 42].
- [cite_start]**Services:** (In Progress) Centralized **Syslog** and **NTP** synchronization[cite: 12, 13, 14].

## 📊 Network Topology
![Network Topology](images/start-topology.png)

## 🔢 IP Addressing Scheme (Subnetting)
[cite_start]The network is based on the `192.168.1.0/24` range, meticulously sub-netted into 18 distinct networks to optimize address space and enhance security[cite: 1, 2]:

| Subnet # | Name | Network ID | Mask | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| 1 | ACL Network | 192.168.1.0/28 | 255.255.255.240 | [cite_start]High Security LAN (Purple Zone) [cite: 28] |
| 2 | Serial Link | 192.168.1.16/29 | 255.255.255.248 | Link between R-CORE & R-BRANCH-1 |
| 3-18 | Various | 192.168.1.x/29 | 255.255.255.248 | [cite_start]Infrastructure Links & Branch LANs [cite: 2] |

## 🛠️ Configuration Highlights (Completed Tasks)
### [cite_start]1. OSPF Authentication [cite: 10]
Secured Area 0 using Message-Digest authentication to ensure that only trusted routers can exchange routing information.
```bash
router ospf 1
 area 0 authentication message-digest
 interface [Serial_Interface]
 ip ospf message-digest-key 1 md5 [Key_Shared]

## 📂 Files Included
- `NTI_Final_Project.pkt`: The main Cisco Packet Tracer file.
- `/images`: Screenshots of connectivity tests (Pings) and configurations.
