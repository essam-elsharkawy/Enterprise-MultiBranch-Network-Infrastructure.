# Multi-Branch Enterprise Network Infrastructure Design & Simulation

## 📌 Project Overview
This repository contains a comprehensive, enterprise-level network infrastructure design simulation built using **Cisco Packet Tracer**. The architecture simulates a high-availability network for a corporation operating across **3 distinct geographical branches**. Each branch is engineered with a multi-layered design spanning **4 floors** to ensure maximum security, scalability, and seamless Voice over IP (VoIP) and data communication.

---

## 🏢 Network Architecture & Hierarchy

### 1. Branch Topology
The corporate network connects three main sites via an **OSPF (Open Shortest Path First)** routing domain to achieve dynamic and fast convergence:
* **Branch 1 (Main Office / HQ):** Connected via Router0.
* **Branch 2 (Regional Branch):** Connected via Router1.
* **Branch 3 (Remote Branch):** Connected via Router2.

### 2. Floor Layout & Capacity (Per Branch)
Each of the 3 branches consists of **4 floors**, structurally identical in node density but logically separated for security:
* **Departments/Floors:** 4 isolated floors managed via Virtual LANs (VLANs).
* **Office Density:** **8 offices** per floor.
* **End-User Devices:** Each office is equipped with **1 PC (Data)** and **1 IP Phone (Voice)**.
* **Shared Resources:** **1 Network Printer** per floor, accessible by all offices within that specific floor's subnet.

---

## 🛠️ Technical Implementations & Protocols

### 🔹 Switching & VLAN Segregation (Router-on-a-Stick)
To avoid broadcast storms and isolate organizational departments, **VLAN Trunking (802.1Q)** is implemented between the Core Multilayer Switches and Branch Routers using Subinterfaces:
* **VLAN 10:** Floor 1 (Data & Voice) - Subnet: `192.168.10.0/26`
* **VLAN 20:** Floor 2 (Data & Voice) - Subnet: `192.168.20.0/26`
* **VLAN 30:** Floor 3 (Data & Voice) - Subnet: `192.168.30.0/26`
* **VLAN 40:** Floor 4 (Data & Voice) - Subnet: `192.168.40.0/26`
* *Note: Subnetting utilizes **VLSM (Variable Length Subnet Masking)** to optimize IPv4 address allocation.*

### 🔹 Dynamic Routing (OSPFv2)
* **Routing Protocol:** OSPF Area 0 (Single Area Backbone).
* **Inter-Router Links:** Point-to-point networks (`10.0.0.0/8`, `11.0.0.0/8`, `12.0.0.0/8`) ensuring redundant paths and sub-second convergence times.
* **Network Advertisement:** All localized loopbacks and internal VLAN subnets are advertised dynamically across the corporate topology.

### 🔹 Voice over IP (VoIP) Configuration
* **Telephony Services:** Configured directly on Cisco Routers to automatically assign directory numbers (DN) to IP Phones via SCCP protocol.
* **Voice VLANs:** Segregated from data traffic to apply **QoS (Quality of Service)** principles, ensuring crystal-clear voice communication.

### 🔹 Infrastructure Services
* **DHCP Pools:** Routers act as DHCP servers providing automated IP, Subnet, Default Gateway, and Option 150 (TFTP Server for IP Phones) allocations for all devices.

---

## 📊 Topology Diagram

Below is the logical blueprint of the enterprise infrastructure simulation:

![Network Topology](assets/topology.png) 
*(Note: Please refer to the `assets/` directory for detailed configuration steps and device screenshots).*

---

## 🚀 How to Run the Simulation
1. Download and install **Cisco Packet Tracer** (v8.2 or higher recommended).
2. Clone this repository:
   ```bash
   (https://github.com/essam-elsharkawy/Enterprise-MultiBranch-Network-Infrastructure.)
