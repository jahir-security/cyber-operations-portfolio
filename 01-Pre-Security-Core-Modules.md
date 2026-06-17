# TryHackMe: Core Infrastructure & Networking Mastery
**Timeline:** June 2, 2026 – June 15, 2026  
**Status:** Core Sections Complete

Comprehensive technical documentation of the foundational systems architecture, data encapsulation mechanics, routing logic, and virtualization frameworks completed during the primary phase of the Pre-Security track.

---

## 1. The OSI Model & Data Encapsulation
Deep dive into the 7-layer framework, analyzing how Protocol Data Units (PDUs) are transformed as data traverses the network stack.
*   **Application to Transport (Layers 7-4):** Analyzed payload generation and segmentation. Understood how Layer 4 (Transport) appends source/destination ports to create **Segments** (TCP) or **Datagrams** (UDP).
*   **Network Layer (Layer 3):** Explored how segments are encapsulated into **Packets** by appending logical IP addresses.
*   **Data Link Layer (Layer 2):** Studied the framing process where packets are encapsulated into **Frames** by appending physical MAC addresses and error-checking sequences (FCS).
*   **Physical Layer (Layer 1):** Mapped the conversion of frames into raw **Bits** for physical transmission over copper, fiber, or wireless mediums.

## 2. Network Infrastructure & Routing Protocol Logic
Differentiated between structural hardware components and the protocols that govern traffic flow.
*   **Hubs vs. Switches:** Contrasted legacy Hubs (Layer 1 broadcast repeaters causing collision domains) with **Layer 2 Switches**, which utilize MAC address tables to intelligently forward frames and segment collision domains.
*   **Layer 3 Switches & Routers:** Analyzed hardware capable of inter-VLAN routing. Explored how routers build **Routing Tables** and evaluate path metrics to determine the most efficient egress interface for forwarding Layer 3 packets.
*   **Address Resolution Protocol (ARP):** Mapped the ARP broadcast lifecycle used to resolve known logical Layer 3 IP addresses to unknown physical Layer 2 MAC addresses across a local subnet.
*   **DHCP Mechanics:** Detailed the DORA (Discover, Offer, Request, Acknowledge) process for automated IP leasing, default gateway assignment, and subnet mask configuration.
*   **Virtual LANs (VLANs):** Studied the logical segmentation of physical switches to isolate broadcast domains, enhance security posture, and manage traffic flow using 802.1Q tagging.

## 3. Secure Communications
Examined the mechanics of tunneling and encrypting traffic over untrusted infrastructure.
*   **Virtual Private Networks (VPN):** Investigated the architecture of site-to-site and remote-access VPNs, focusing on secure payload encapsulation.
*   **IPsec Framework:** Analyzed the IPsec suite at the Network Layer, covering the Authentication Header (AH) for data integrity and Encapsulating Security Payload (ESP) for cryptographic confidentiality.

## 4. Hardware, Virtualization & Cloud Evolution
Mastered the transition from legacy bare-metal infrastructure to modern scalable cloud environments.
*   **Computing Hardware:** Reviewed core component architecture, including CPU instruction cycles, volatile memory (RAM) operations, and system bus data transfer.
*   **Hypervisor Architecture:** 
    *   **Type 1 (Bare-Metal):** Analyzed hypervisors installed directly on physical hardware (e.g., ESXi, Proxmox) for enterprise resource allocation with minimal overhead.
    *   **Type 2 (Hosted):** Differentiated hypervisors running atop a host OS (e.g., VirtualBox, VMware Workstation), typically used for isolated testing and development.
*   **Containerization:** Explored OS-level virtualization (e.g., Docker), where applications share the host kernel but run as isolated user-space instances, providing rapid deployment compared to full VMs.
*   **Cloud Computing Models:** Traced the evolution from physical data centers to virtualized clusters. Differentiated between **IaaS** (Infrastructure), **PaaS** (Platform), and **SaaS** (Software), analyzing the Shared Responsibility Model for securing cloud assets.
