# Day 2: OSI Model

## Core Concepts & Purpose
* **Industry Standard Language:** The Open Systems Interconnection (OSI) model provides a universal language for IT professionals to communicate network behaviors and problems across different organizations and technologies. Saying "Layer 4 problem" or "Layer 7 issue" ensures immediate, mutual understanding.
* **TCP/IP Compatibility:** While most modern networks run on the **TCP/IP** suite, the OSI model acts as a conceptual framework that maps perfectly to it.
* **Protocol Diversity:** Individual layers are protocol-agnostic; tens or hundreds of different protocols can operate simultaneously at a single layer.

## The 7 Layers of the OSI Model

### Layer 7: Application Layer
* **Definition:** The interface layer that humans interact with on-screen.
* **Function:** Directly handles network requests from software applications and displays incoming network data.
* **Key Protocols:** HTTP, HTTPS, FTP, DNS, POP3.

### Layer 6: Presentation Layer
* **Definition:** The data formatting and structuring layer.
* **Function:** Prepares data into a format readable by the application layer or human eyes just prior to display. Handles **character encoding**, as well as application-level **encryption and decryption**.
* **Key Concepts:** SSL/TLS encryption processes occur here.

### Layer 5: Session Layer
* **Definition:** The communication management layer.
* **Function:** Controls the conversation between Point A and Point B by initiating (starting), managing (tunneling/controlling), and terminating (stopping/restarting) sessions.

### Layer 4: Transport Layer
* **Definition:** The "Post Office" layer responsible for moving data reliably or efficiently between endpoints.
* **Function:** Manages data transport, segmenting large amounts of data into smaller pieces for transmission and reassembling them at the destination. It uses logical identifiers called **ports**.
* **Key Protocols:** * **TCP** (Transmission Control Protocol)
  * **UDP** (User Datagram Protocol)

### Layer 3: Network Layer
* **Definition:** The routing and logical addressing layer.
* **Function:** Determines how to forward traffic across different networks. It handles **fragmentation** (chopping frames into smaller pieces to fit through networks requiring smaller sizes, then reassembling them on the other side).
* **Key Elements:** IP addresses, subnet masks, routers, and "next hop" determinations.

### Layer 2: Data Link Layer
* **Definition:** The fundamental hardware-to-hardware communication layer between two adjacent devices.
* **Function:** Manages physical addressing and coordinates access to the physical media. Switches operate here to forward traffic based on destination hardware addresses.
* **Key Elements:** * **MAC Address** (Media Access Control / Hardware Address)
  * **DLC Address** (Data Link Control)
  * **EUI-48 / EUI-64** (Extended Unique Identifiers)
  * Ethernet frames and network switches.

### Layer 1: Physical Layer
* **Definition:** The hardware and signaling layer.
* **Function:** Moves raw binary bits/signals across a physical medium from one point to another. It contains very few protocols because it deals purely with electrical, light, or radio frequencies.
* **Key Elements:** Cables (copper), fibers, wireless signals, network adapter cards.
* **Troubleshooting Steps:** Running loopback tests, testing cables/fibers for damage, and checking for wireless interference.

---

## Quick Reference Summary Table

| Layer Number | Layer Name | Primary Function / Unit | Key Hardware / Protocols / Concepts |
| :--- | :--- | :--- | :--- |
| **7** | **Application** | User Interface & Apps | HTTP, HTTPS, FTP, DNS, POP3, UI views |
| **6** | **Presentation** | Formatting & Encryption | SSL/TLS encryption, character encoding |
| **5** | **Session** | Conversation Management | Session control protocols, tunneling |
| **4** | **Transport** | End-to-End Transport | TCP, UDP, Port numbers |
| **3** | **Network** | Routing & Logical Paths | IP Addresses, Subnet masks, Routers, Fragmentation |
| **2** | **Data Link** | Device-to-Device Switching | MAC/DLC/EUI addresses, Network Switches, Frames |
| **1** | **Physical** | Signaling & Media | Cables, Fiber optics, RF signals, Loopback tests |

---


## Real-World Application: Wireshark Protocol Decode
When analyzing a network capture in a tool like Wireshark, a single packet contains nested headers that match the OSI hierarchy from the bottom up:

1. **Physical Level Details:** Represents **Layer 1** (e.g., "Frame 88: 2005 bytes on wire").
2. **Ethernet II Header:** Represents **Layer 2**. Contains Source and Destination MAC addresses.
3. **Internet Protocol (IP) Header:** Represents **Layer 3**. Contains Source and Destination IP addresses (e.g., resolving to `googlemail.l.google.com`).
4. **Transmission Control Protocol (TCP) Header:** Represents **Layer 4**. Contains source and destination port numbers (e.g., Destination Port 443 for HTTPS).
5. **Secure Socket Layer (SSL/TLS) & Application Data:** Encapsulates **Layers 5, 6, and 7** combined. It executes the session linking, processes the decryption (Layer 6), and exposes the final application payload like Google Mail (Layer 7).
