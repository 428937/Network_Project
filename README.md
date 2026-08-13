### Network_Project

## Router Studios: Enterprise Network Infrastructure for Game Development

A high-performance, secure, and scalable enterprise network design for Router Studios, a multi-departmental game development house. Designed and simulated using Cisco Packet Tracer.

## Project Overview
Router Studios requires a robust network capable of handling massive asset transfers, real-time collaboration, and secure data management. This project implements a hierarchical **Core-Access** architecture to ensure low latency for developers and high security for management and server resources.

## Network Architecture & Topology
The infrastructure is built on a **Cisco 3560 Multilayer Switch** (Core) and **Cisco 2911 Router** (WAN Gate), utilizing **VLAN segmentation** to isolate departmental traffic.

### Departmental Segmentation (VLANs)
| VLAN ID | Department | Primary Function |
| :--- | :--- | :--- |
| **VLAN 10** | Management | Admin & Financial Operations |
| **VLAN 20** | Coding | Unity/C++ Development & Engine Coding |
| **VLAN 30** | Audio / Music | Sound Engineering & OST Production |
| **VLAN 40** | Lore / Story | Creative Writing & Documentation |
| **VLAN 50** | Visual Design | 3D Modeling, Texturing & Level Design |
| **VLAN 60** | QA / Test | Bug Reporting & Performance Testing |
| **VLAN 70** | Data Center | Web, DNS, and Project Management Servers |
| **VLAN 80** | Security | IP Surveillance & Infrastructure Monitoring |
| **VLAN 90** | HR | Recruitment & Personnel Management |


## Technical Configuration
### 1. Inter-VLAN Routing (Layer 3 Switching)
Inter-departmental communication is managed via **Switch Virtual Interfaces (SVI)** on the 3650 Multilayer Switch. This ensures that internal traffic (e.g., Coding to Servers) stays within the high-speed core.

### 2. Security & ACLs (Access Control Lists)
* **Restricted Access:** The **QA/Test (VLAN 60)** department can access the **Data Center (VLAN 70)** for reporting but is strictly blocked from the **Management (VLAN 10)** and **HR (VLAN 90)** networks.
* **Surveillance:** **Security (VLAN 80)** monitoring is restricted to authorized admin terminals only.

### 3. Edge Connectivity (NAT/PAT)
The **Cisco 2911 Router** performs **NAT Overload (PAT)**, allowing all studio workstations to access the external Internet/ISP Server via a single Public IP, while masking internal topology from external threats.

## Verification Tests
* **Connectivity:** 100% success rate for `ICMP Ping` across authorized VLANs.
* **Web Access:** Successful HTTP retrieval of the internal `routerstudios.local` portal from all departments.
* **Security Validation:** Confirmed "Request Timed Out" for unauthorized inter-VLAN attempts (ACL Verification).
