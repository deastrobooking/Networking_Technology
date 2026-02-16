# Networking_Technology


# 🌐 Networking Study Guide – Core Concepts (10 Key Areas)

---

## 1️⃣ OSI Layer 4 – Transport Layer (TCP vs UDP)

### 🔹 What Layer 4 Devices Read

Layer 4 devices (firewalls, load balancers) inspect:

* **TCP header**
* **UDP header**
* Source/destination ports
* Sequence numbers
* Flags

### 🔹 TCP (Transmission Control Protocol)

* Connection-oriented
* Reliable
* Sequencing
* Flow control
* Acknowledgments
* Checksum

### 🔹 UDP (User Datagram Protocol)

* Connectionless
* Fast
* No sequencing
* No flow control
* Minimal overhead

✔ UDP emphasizes **speed over accuracy**

---

## 2️⃣ TCP Data Integrity

### 🔹 TCP Checksum

Ensures:

* Data was not corrupted
* Header and payload match what was sent

If checksum fails:

* Segment is discarded
* Retransmission occurs (TCP reliability)

---

## 3️⃣ Internet MTU (Maximum Transmission Unit)

### 🔹 Standard Internet MTU:

> **1500 bytes**

Used in standard Ethernet networks.

### 🔹 Why It Matters:

* Larger packets → fewer transmissions
* Too large → fragmentation
* Fragmentation reduces performance

Other values:

* 1522 bytes → VLAN tagging
* 9000+ bytes → Jumbo frames
* 65535 bytes → Max IP packet size (theoretical)

---

## 4️⃣ IPv4 Neighbor Discovery

### 🔹 ARP (Address Resolution Protocol)

* Resolves IPv4 address → MAC address
* Operates on local network

### 🔹 ICMP

* Network diagnostics
* Reachability (ping)
* Error reporting

✔ IPv4 uses **ARP + ICMP**

---

## 5️⃣ GRE and IPsec

### 🔹 GRE (Generic Routing Encapsulation)

* Encapsulates packets
* No encryption
* Used in site-to-site tunnels

### 🔹 IPsec

* Encryption
* Authentication
* Integrity
* Key exchange

✔ GRE is secured by pairing it with **IPsec**

---

## 6️⃣ The CIA Triad (Security Fundamentals)

### 🔹 Confidentiality

* Data is secret
* Encryption protects it

### 🔹 Integrity

* Data is not altered
* Hashing / digital signatures ensure this

### 🔹 Availability

* Systems are accessible when needed

✔ Integrity ensures data isn’t modified in transit.

---

## 7️⃣ Secure File Transfer Protocols

### 🔹 SFTP

* Runs over SSH
* Encrypted file transfers
* Secure remote file access

### 🔹 Differences:

| Protocol | Security Method |
| -------- | --------------- |
| SFTP     | SSH             |
| FTPS     | SSL/TLS         |
| TFTP     | No security     |
| HTTPS    | Web encryption  |

✔ SFTP is an extension of SSH.

---

## 8️⃣ VPNs and Firewall Traversal

### 🔹 IPsec

* Uses ESP (protocol 50)
* Uses UDP 500 / 4500
* Often blocked by strict firewalls

### 🔹 OpenVPN

* Uses SSL/TLS
* Can run over TCP 443 (HTTPS)
* Harder to block

✔ OpenVPN can cross firewalls where IPsec fails.

---

## 9️⃣ Network Interface Statistics

### 🔹 Command:

```
netstat -e
```

Displays:

* Bytes sent/received
* Errors
* Discards
* Interface statistics

Other commands:

* `tcpdump -D` → Lists interfaces
* `arp -d` → Deletes ARP entries
* `traceroute -I` → Uses ICMP for path discovery

---

## 🔟 Quick Comparison Chart

| Topic                   | Key Answer          |
| ----------------------- | ------------------- |
| Layer 4 header          | TCP                 |
| TCP integrity field     | Checksum            |
| Standard MTU            | 1500 bytes          |
| IPv4 neighbor discovery | ARP + ICMP          |
| GRE security            | IPsec               |
| Data not modified       | Integrity           |
| SSH file transfer       | SFTP                |
| UDP characteristic      | Speed over accuracy |
| Firewall-friendly VPN   | OpenVPN             |
| Interface error stats   | netstat -e          |

---

# 🧠 Memory Anchors for Exams

* **Layer 4 = Ports**
* **TCP = Reliable**
* **UDP = Fast**
* **1500 = Standard MTU**
* **ARP = Who has this IP?**
* **IPsec = Encrypts tunnels**
* **Integrity = Hashing**
* **SFTP = SSH Files**
* **OpenVPN = Port 443 trick**
* **netstat = Interface stats**

---

## Introduction to Transmission Media & Circuit Fundamentals

*A Foundation Guide for Networking Technicians*

As a networking technician, your job doesn’t stop at configuring switches and assigning IP addresses. The physical layer — cables, signal behavior, and electrical integrity — is what makes everything else possible. Understanding how signals travel, how cables are built, and how failures occur will make you faster at troubleshooting and more confident in the field.

---

# 1️⃣ Transmission Characteristics

Every network link has physical limits. These define how well data can travel from one device to another.

### Key Terms

* **Bandwidth** – The theoretical maximum capacity of a link.
* **Bit Rate** – How many bits per second can be transmitted.
* **Throughput** – The *actual* data transferred after overhead, collisions, and interference.
* **Latency** – The delay between sending and receiving data.

🔎 **Important Reality:**
Throughput is *never* equal to bandwidth. Overhead (TCP/IP headers, retransmissions, encryption, switching delays) always reduces real-world performance.

---

# 2️⃣ Twisted-Pair Cabling (Copper Networks)

Twisted-pair cabling is the most common physical medium in enterprise environments.

## Why Wires Are Twisted

Twisting reduces electromagnetic interference (EMI) and crosstalk between wire pairs.

### Crosstalk Types

* **NEXT (Near-End Crosstalk)**
  Occurs near the transmitting end. Often caused by poor termination or damaged insulation near the source.

* **FEXT (Far-End Crosstalk)**
  Occurs near the receiving end.

* **Alien Crosstalk**
  Interference between separate adjacent cables.

---

## Twisted-Pair Categories & Speeds

| Category | Max Speed | 10G Support (100m?) |
| -------- | --------- | ------------------- |
| Cat 5e   | 1 Gbps    | ❌                   |
| Cat 6    | 1–10 Gbps | Limited (~55m)      |
| Cat 6a   | 10 Gbps   | ✅                   |
| Cat 7    | 10 Gbps+  | ✅                   |

🔧 **For 10GBASE-T at 100 meters:**
Minimum required standard = **Cat 6a**

---

## Patch Cable Standards

Two wiring standards exist:

* **T568A** (Common in government installations)
* **T568B** (Common in commercial environments)

For T568A:

* **Pin 1 = White/Green**

Knowing this matters when making patch cables or testing wiring faults.

---

# 3️⃣ Twinaxial & High-Speed Rack Connections

Inside data center racks, short-distance high-speed connections often use:

### Passive Twinaxial Cable

* Used for 10G, 25G, 40G connections
* Very low latency
* Extremely efficient for short rack-to-rack links

This is common between:

* Router ↔ Switch
* Switch ↔ Switch
* Server ↔ Top-of-Rack switch

---

# 4️⃣ Fiber Optic Fundamentals

Fiber uses light instead of electrical signals.

## Multimode Fiber (MMF)

* Core size: 50 or 62.5 microns
* Uses LED light sources
* More modal dispersion
* Shorter distances

## Single-Mode Fiber (SMF)

* Core size: ~8–10 microns
* Uses laser light
* Minimal modal dispersion
* Long-distance transmission (kilometers)

### Why SMF Is Better for Long Distances

Because it has a **narrower core**, light travels in a single path. This reduces signal spreading (dispersion) and preserves signal integrity over long distances.

---

## Fiber Problems

### Fiber Type Mismatch

Pairing:

* 50-micron ↔ 62.5-micron cores

This causes signal loss and performance issues.

---

## What Limits Fiber Distance?

### Optical Loss (Attenuation)

As light travels:

* It weakens due to absorption and scattering.
* Connectors and splices add loss.
* Eventually, the signal drops below detectable levels.

This is why link budgets matter in fiber design.

---

# 5️⃣ Circuit Fundamentals for Network Techs

Understanding electrical faults is critical when diagnosing cable issues.

## Open Circuit

* Missing connection
* Current cannot flow
* Example: Broken conductor in a cable

## Short Circuit

* Unintended connection
* Current flows where it should not
* Example: Two wires touching due to damaged insulation

---

# 6️⃣ Practical Technician Mindset

When troubleshooting:

1. Start physical.
2. Check link lights.
3. Test continuity.
4. Verify pinout standard.
5. Confirm cable category rating.
6. Test for interference or attenuation.

Layer 1 issues often masquerade as Layer 3 problems.

---

# Final Takeaway

A strong networking technician understands:

* Signal limitations
* Cable standards
* Fiber differences
* Crosstalk behavior
* Electrical faults
* Real-world throughput vs theoretical speeds

Master the physical layer, and everything above it becomes easier.

---


