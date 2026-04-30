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

Alright — let’s build you a **clean, printable, multi-page final exam study guide** based on your course (Ch. 7–12 focus + key earlier concepts that keep showing up).

I’m structuring this like something you can paste into Word / print double-sided.

---

# 📘 ITNT 1500 FINAL EXAM STUDY GUIDE

**Chapters 7–12 + Core Concepts Review**

---

# 🧠 PAGE 1 — NETWORK ARCHITECTURE (CH. 7)

## Core Concepts

* **LAN vs WAN**

  * LAN = local (building/campus)
  * WAN = large scale (ISP, Internet)

* **Client-Server vs Peer-to-Peer**

  * Client-server = centralized control
  * Peer-to-peer = decentralized

* **High Availability**

  * Redundancy (multiple systems)
  * Load balancing distributes traffic
  * Failover = backup takes over

## Key Technologies

* **Load Balancing (NLB)**
* **Virtualization**

  * Hypervisors (Type 1 vs Type 2)
* **Disaster Recovery**

  * RTO (Recovery Time Objective)
  * RPO (Recovery Point Objective)

---

# 🌐 PAGE 2 — NETWORK SEGMENTATION (CH. 8)

## VLANs

* Operate at **Layer 2**
* Separate broadcast domains
* Use **802.1Q tagging**

## Switch Concepts

* **Access Port** = single VLAN
* **Trunk Port** = multiple VLANs

## Subnetting (CRITICAL)

* Splits networks into smaller networks
* Uses **CIDR notation**

### Key Formulas

* Hosts per subnet = 2ⁿ - 2
* Subnets = 2ⁿ (borrowed bits)

## Broadcast vs Collision Domains

* Switch = reduces collisions
* VLAN = reduces broadcasts

---

# 🌍 PAGE 3 — WAN TECHNOLOGIES (CH. 9)

## Common WAN Types

* MPLS
* Broadband (Cable, DSL, Fiber)
* Cellular (4G/5G)

## Routing Basics

* **Static Routing**
* **Dynamic Routing (OSPF, BGP)**

## Key Commands

* `show ip route` → routing table
* `tracert / traceroute` → path

## NAT

* Private → Public IP translation
* Types:

  * Static
  * Dynamic
  * PAT (most common)

---

# 🔐 PAGE 4 — RISK MANAGEMENT (CH. 10)

## Security Concepts

* **CIA Triad**

  * Confidentiality
  * Integrity
  * Availability

## Common Attacks

* DoS / DDoS
* MAC Spoofing
* VLAN hopping

## Network Hardening

* Disable unused ports
* Patch systems
* Use firewalls

## Tools

* **nmap** → scanning
* **Wireshark** → packet capture
* **tcpdump**

---

# 🔑 PAGE 5 — ACCESS CONTROL (CH. 11)

## AAA Model

* Authentication (who are you)
* Authorization (what can you do)
* Accounting (tracking)

## Protocols

* **RADIUS**
* **TACACS+**
* **LDAP**

## ACLs (VERY IMPORTANT)

* Processed top-down
* First match wins
* **Implicit rule = DENY ALL**

👉 Common mistake:
If traffic is allowed when it shouldn’t be →
**a rule above is overriding it**

## Trust Zones

* Trusted
* Untrusted
* **Screened subnet = DMZ**

---

# 📊 PAGE 6 — PERFORMANCE & MONITORING (CH. 12)

## Monitoring Tools

* **SNMP**

  * Uses **community string**
* **NetFlow / IPFIX**

  * Tracks traffic flows (metadata)

## Performance Metrics

* Latency
* Jitter
* Packet loss
* Throughput

👉 Baseline = **normal performance reference**
Used to detect anomalies

## Tools

* **iPerf**

  * Measures throughput
  * Must run on BOTH ends
* **PRTG**

  * Network monitoring

---

# 🧪 PAGE 7 — TROUBLESHOOTING + TOOLS

## Packet Analysis

* File type: **.pcap**
* Tool: Wireshark

## Filters Example

```
ip.addr == 192.168.1.1 && tcp.port == 80
```

👉 `&&` = Boolean AND

## Key Commands

* `ping` → connectivity
* `tracert` → path
* `nslookup` → DNS

## Nmap

* `-sn` → ping scan
* `-A` → aggressive
* `-oN` → save output

---

# 🌐 PAGE 8 — PROTOCOLS TO MEMORIZE

## Plaintext vs Secure

* HTTP (plaintext ❌)
* HTTPS (secure ✅)
* SSH (secure ✅)
* IMAP vs IMAPS

## Ports

* 80 → HTTP
* 443 → HTTPS
* 22 → SSH
* 445 → SMB

---

# 🧠 PAGE 9 — COMMON EXAM TRAPS

## Trick Questions You WILL See

* Default ACL rule → **DENY ALL**
* VLAN layer → **Layer 2**
* SNMP requires → **community string**
* iPerf limitation → **needs both endpoints**
* Packet capture tool → **Wireshark**
* Flow monitoring → **IPFIX / NetFlow**
* Printer sharing → **SMB (port 445)**

---

# ⚡ PAGE 10 — QUICK REVIEW CHEAT SHEET

## If you see:

* Slow network at specific time → check **WAN throughput / congestion**
* VoIP issues → check **packet loss + QoS**
* ACL not working → check **rule order**
* Can’t reach host → check:

  * ARP
  * Routing table
  * Gateway

---

# 📌 FINAL EXAM STRATEGY

From your exam rules (very important):

* 40 questions
* 25 minutes
* No calculator
* No notes

👉 That means:

* ~35–40 seconds per question
* You must **recognize answers instantly**

## Strategy

1. Skip anything slow
2. Answer easy first
3. Eliminate 2 wrong answers fast
4. Watch wording like:

   * “FIRST step”
   * “PRIMARY purpose”

---

# 📎 COURSE CONTEXT (FROM YOUR MODULES)

Your final pulls heavily from:

* Chapters 7–12 quizzes + scenarios 
* Labs:

  * ACLs
  * RADIUS
  * Monitoring (PRTG, iPerf)
  * Routing and VLANs 

👉 Translation:
**Expect applied questions, not definitions**

---

# 🚀 If you want next level prep

I can:

* Turn this into a **downloadable Word/PDF**
* Create a **1-page cram sheet**
* Build a **timed practice test (40 questions, real format)**

# ITNT 1500 Final Exam Condensed Book

## Principles of Networking Final Review

### Built from Chapters 7 through 12, earlier core concepts, subnetting practice, Packet Tracer work, Wireshark, Nmap, pfSense, ACLs, RADIUS, PRTG, iPerf, cloud networking, virtualization, routing, VLANs, security, monitoring, and troubleshooting examples from your course conversations.

---

# How to Use This Book

This condensed book is designed to help you prepare for the ITNT 1500 final exams. It is written as a practical study guide, not as a replacement for learning the material. The goal is to help you recognize concepts quickly, understand why answers are correct, and connect the ideas to the labs and scenarios you have practiced.

Your course final exam material focuses heavily on Chapters 7 through 12, but many questions also depend on earlier networking fundamentals such as OSI layers, IP addressing, subnetting, ports, protocols, Wireshark, Nmap, Packet Tracer, routing, VLANs, and troubleshooting.

The final exam style is fast. You need to recognize the topic, eliminate wrong answers, and choose the best answer. Many questions use wording like primary purpose, first thing to investigate, most likely explanation, or best fit. Those phrases matter.

---

# Table of Contents

1. Final Exam Strategy
2. Networking Foundations You Still Need
3. OSI Model and Encapsulation
4. IP Addressing and Subnetting
5. Ports and Protocols
6. Wireshark, Packet Capture, and Traffic Analysis
7. Nmap, Zenmap, and Network Discovery
8. Chapter 7: Network Architecture
9. Chapter 8: Network Segmentation
10. Chapter 9: Wide Area Networking
11. Chapter 10: Risk Management
12. Chapter 11: Access Control
13. Chapter 12: Performance and Recovery
14. Packet Tracer Skills Review
15. pfSense, ACLs, Firewall Rules, and Routing
16. RADIUS, AAA, Identity, and Access Management
17. Cloud Networking and Virtualization
18. Wireless Networking Review
19. Troubleshooting Methodology
20. Common Exam Traps
21. Practice Scenarios With Explanations
22. Final Cram Sheet

---

# 1. Final Exam Strategy

Your final exam is not just about memorizing definitions. It is about recognizing networking situations quickly and choosing the best answer. The questions often describe a real-world problem and ask what tool, protocol, command, or concept applies.

## The Big Strategy

When reading a question, ask yourself:

1. What is the problem?
2. What layer of the OSI model is involved?
3. Is this about addressing, routing, switching, security, access control, monitoring, or performance?
4. Is the question asking for the first step, best tool, most likely cause, or primary purpose?
5. Are there two answers that sound close, but only one fits the wording?

## Words That Matter

### Primary purpose

This usually asks for the main reason something exists.

Example:

Question: After you set up a network monitoring solution, what is the primary purpose of measuring baseline metrics?

Best idea: Baseline metrics define normal network performance so you can detect anomalies later.

Why: A baseline is not mainly about cost, maximum capacity, or configuration drift. It is about knowing what normal looks like.

### First thing to investigate

This asks what you should check before jumping to more complex causes.

Example:

Question: Every day around 2 PM the network becomes significantly slower. Cloud apps, VoIP calls, and file transfers are impacted. What should you investigate first?

Best idea: WAN throughput or congestion.

Why: If cloud apps, VoIP, and file transfers all slow down at the same time every day, the shared WAN connection is a likely bottleneck.

### Most likely explanation

This asks you to infer the cause.

Example:

Question: You added a new ACL rule to block RDP traffic, but some RDP traffic still gets through. What is the most likely explanation?

Best idea: Another rule earlier in the list is allowing it.

Why: ACLs are processed top-down. First match wins.

---

# 2. Networking Foundations You Still Need

Even though the final focuses on Chapters 7 through 12, you still need the basics from earlier modules.

## What a Network Does

A computer network allows devices to share data, applications, resources, printers, files, Internet access, and services.

Networks are built from:

* Hosts
* Switches
* Routers
* Firewalls
* Access points
* Servers
* Cabling
* Wireless links
* IP addresses
* MAC addresses
* Protocols

## LAN, WAN, and Internet

### LAN

A local area network is a network in a small area such as a home, office, school, or building.

### WAN

A wide area network connects networks over long distances. The Internet is the largest WAN.

### Internet

The global network of networks.

## Client and Server

A client requests a service. A server provides a service.

Examples:

* Web browser is the client.
* Web server provides web pages.
* Email client requests messages.
* Mail server stores and sends mail.

## Peer-to-Peer

In peer-to-peer networking, devices can share directly without a central server. This can be simpler but harder to control.

---

# 3. OSI Model and Encapsulation

The OSI model is one of the most important networking frameworks. It helps you organize where a problem lives.

## The Seven Layers

1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

## Layer 1: Physical

This is the electrical, radio, fiber, and physical cabling layer.

Examples:

* Cables
* Connectors
* Fiber
* Signal strength
* Wireless radio signal
* Hubs

Common problems:

* Bad cable
* Loose connector
* Failed NIC
* Damaged fiber
* Weak wireless signal

## Layer 2: Data Link

This layer uses MAC addresses and switching.

Examples:

* Ethernet frames
* MAC addresses
* Switches
* VLANs
* 802.1Q tagging
* ARP

Important final exam point:

VLANs operate at Layer 2.

## Layer 3: Network

This layer uses IP addresses and routing.

Examples:

* IPv4
* IPv6
* Routers
* Routing tables
* ICMP
* Subnets

Important final exam point:

Routers forward traffic between networks.

## Layer 4: Transport

This layer uses TCP and UDP.

Examples:

* TCP ports
* UDP ports
* Reliable delivery
* Flow control
* Segmentation

TCP is connection-oriented. UDP is connectionless.

## Layer 5: Session

This layer manages sessions between applications.

## Layer 6: Presentation

This layer handles data formatting, encryption, and compression.

## Layer 7: Application

This layer includes user-facing network services.

Examples:

* HTTP
* HTTPS
* DNS
* DHCP
* SMTP
* IMAP
* SSH
* SMB

## Encapsulation

When data moves down the OSI model, each layer adds its own information.

Application data becomes:

* Data
* Segment
* Packet
* Frame
* Bits

When the receiving device gets the data, it removes each layer of information in reverse.

---

# 4. IP Addressing and Subnetting

Subnetting is one of the most important final exam areas. You have worked through subnetting examples involving borrowing bits, masks, usable hosts, and CIDR notation.

## IPv4 Address Basics

An IPv4 address has four octets.

Example:

198.198.98.0

Each octet is 8 bits.

A full IPv4 address is 32 bits.

## Subnet Mask Basics

A subnet mask tells which part of an IP address is the network portion and which part is the host portion.

Example:

255.255.255.0 = /24

That means the first 24 bits are network bits.

## CIDR Notation

CIDR notation is the slash format.

Examples:

* 255.255.255.0 = /24
* 255.255.255.128 = /25
* 255.255.255.192 = /26
* 255.255.255.224 = /27
* 255.255.255.240 = /28
* 255.255.255.248 = /29
* 255.255.255.252 = /30

## Binary Value of One Octet

Each bit position in an octet has a value:

128 64 32 16 8 4 2 1

If the bit is on, count it. If it is off, ignore it.

Example:

11111000

That equals:

128 + 64 + 32 + 16 + 8 = 248

So:

11111111.11111111.11111111.11111000 = 255.255.255.248

That is /29 because there are 29 network bits.

## Borrowing Bits

Borrowing bits means taking bits from the host portion and using them to create more networks.

Original /24 mask:

11111111.11111111.11111111.00000000

If you borrow 1 bit:

11111111.11111111.11111111.10000000 = /25

If you borrow 2 bits:

11111111.11111111.11111111.11000000 = /26

If you borrow 3 bits:

11111111.11111111.11111111.11100000 = /27

If you borrow 4 bits:

11111111.11111111.11111111.11110000 = /28

## Subnet Formulas

Number of subnets created:

2 to the power of borrowed bits

Number of total addresses per subnet:

2 to the power of host bits

Number of usable host addresses:

2 to the power of host bits minus 2

You subtract 2 because one address is the network address and one is the broadcast address.

## Example From Your Practice

Network Address: 198.198.98.0
Number of Subnets Needed: 10
Number of Usable Hosts Needed: 11

Start with a /24 network.

You need at least 10 subnets.

Try borrowing bits:

* Borrow 1 bit = 2 subnets
* Borrow 2 bits = 4 subnets
* Borrow 3 bits = 8 subnets
* Borrow 4 bits = 16 subnets

You need 10, so borrow 4 bits.

A /24 plus 4 borrowed bits = /28.

Now count host bits:

32 total bits minus 28 network bits = 4 host bits.

Total addresses per subnet:

2 to the 4th power = 16

Usable addresses:

16 minus 2 = 14

That satisfies the need for 11 usable hosts.

Final answers:

* Total Number of Subnets Created: 16
* Number of Bits Borrowed: 4
* Number of Total/Possible Addresses Per Subnet: 16
* Number of Usable/Assignable Addresses Per Subnet: 14
* Custom Subnet Mask: 255.255.255.240
* Prefix/Slash Notation: /28

## Subnet Increments

The subnet increment is also called the block size.

Formula:

256 minus interesting octet mask value

Example:

/28 = 255.255.255.240

256 - 240 = 16

So the subnet ranges increase by 16:

* 198.198.98.0
* 198.198.98.16
* 198.198.98.32
* 198.198.98.48
* 198.198.98.64
* 198.198.98.80
* 198.198.98.96
* 198.198.98.112
* 198.198.98.128
* 198.198.98.144
* 198.198.98.160
* 198.198.98.176
* 198.198.98.192
* 198.198.98.208
* 198.198.98.224
* 198.198.98.240

For the first subnet:

* Network address: 198.198.98.0
* First usable: 198.198.98.1
* Last usable: 198.198.98.14
* Broadcast: 198.198.98.15

## APIPA

APIPA is used when a host is configured for DHCP but cannot reach a DHCP server.

APIPA range:

169.254.0.0 through 169.254.255.255

Example APIPA address:

169.254.255.254

## Loopback

The loopback address tests the local TCP/IP stack.

Common loopback address:

127.0.0.1

This does not send traffic out of the NIC.

---

# 5. Ports and Protocols

Ports and protocols appear constantly in networking exams.

## Plaintext vs Secure Protocols

### Plaintext

HTTP sends data in plaintext.

This means someone capturing traffic could read it if no other encryption is used.

### Secure

HTTPS encrypts web traffic.
SSH encrypts remote administration.
IMAPS secures IMAP email retrieval.
SFTP and SCP use SSH.

## Common Ports

* FTP: 20 and 21
* SSH: 22
* Telnet: 23
* SMTP: 25
* DNS: 53
* DHCP: 67 and 68
* HTTP: 80
* POP3: 110
* NTP: 123
* IMAP: 143
* SNMP: 161 and 162
* LDAP: 389
* HTTPS: 443
* SMB: 445
* RDP: 3389

## SMB

SMB is used for Windows file and printer sharing.

Port:

445

Example:

Question: What protocol does Windows network sharing use?

Answer: SMB

## SSH

SSH is used for secure remote command-line access.

Port:

22

SFTP and SCP both use SSH.

Example:

Question: Which protocol do SFTP and SCP use?

Answer: SSH

## SFTP Commands

To download a file from a connected SFTP server:

get

To upload a file:

put

To list files:

ls

To remove a file:

rm

## HTTP and HTTPS

HTTP uses port 80 and sends data in plaintext.

HTTPS uses port 443 and encrypts traffic.

## DNS

DNS translates names to IP addresses.

A record:

Maps a hostname to an IPv4 address.

DNSSEC:

Adds validation and protection to DNS records.

Example:

If you register a website URL with a new A record and need validation so visitors can find the site safely, DNSSEC is the best fit among security-related DNS choices.

---

# 6. Wireshark, Packet Capture, and Traffic Analysis

A packet analyzer allows you to inspect individual packets.

## Packet Capture Tool

Tool used to examine individual packets:

Packet capture tool

Common software:

Wireshark

## PCAP Files

Packet captures are commonly saved as .pcap files.

Example:

Question: What file extension identifies a file that can be opened by a packet analyzer such as Wireshark?

Answer: .pcap

## Wireshark Display Filters

Example filter:

ip.addr == 192.168.1.1 && tcp.port == 80

The && means Boolean AND.

This filter shows packets where the IP address is 192.168.1.1 and the TCP port is 80.

## Common Wireshark Concepts

### Follow TCP Stream

This lets you follow a conversation between two endpoints.

### Export Objects

This lets you extract files from a series of packets.

Example:

Question: What Wireshark feature enables the extraction of files from a series of packets?

Answer: Export Objects

## What Packet Capture Helps With

Packet capture can help you analyze:

* DNS lookups
* HTTP requests
* TCP handshakes
* Failed connections
* Plaintext protocols
* Suspicious traffic
* ICMP traffic
* ARP traffic

---

# 7. Nmap, Zenmap, and Network Discovery

Nmap is used for network scanning and discovery.

Zenmap is a graphical front end for Nmap.

## Common Nmap Uses

* Discover hosts
* Scan ports
* Identify services
* Identify operating systems
* Find open services
* Save output to files

## Common Nmap Switches

### Ping Scan

-sn

This discovers hosts without doing a full port scan.

### Aggressive Scan

-A

This enables OS detection, version detection, script scanning, and traceroute.

### Save Normal Output

-oN

Example:

Question: Which nmap switch is used to save output to a file?

Answer: -oN

## Nmap and Netstat

You practiced comparing Nmap results with netstat.

Nmap shows what another system can see from the network.

Netstat shows what the local machine is listening on.

Command example:

netstat -a -p tcp

## Network Discovery Purpose

Network discovery helps identify:

* Live hosts
* Open ports
* Services
* Operating systems
* Network layout

---

# 8. Chapter 7: Network Architecture

Chapter 7 focuses on how networks are designed and how systems stay available.

## Network Architecture

Network architecture is the design of a network. It includes topology, redundancy, security, scalability, and performance.

## Topologies

### Star Topology

Most common modern LAN design.

Devices connect to a central switch.

### Mesh Topology

Devices have multiple paths.

Useful for redundancy.

### Hybrid Topology

Combination of multiple designs.

## High Availability

High availability means systems are designed to stay online even when components fail.

Common HA methods:

* Redundant links
* Redundant power
* Backup routers
* Server clustering
* Load balancing
* Failover

## Load Balancing

Load balancing distributes traffic across multiple servers or paths.

Example from your lab context:

You worked with IIS and Network Load Balancing using a virtual IP address. The point was to allow two servers to share traffic so users could still reach the service if one path or server was not handling all requests.

## Disaster Recovery

Disaster recovery is the plan for restoring systems after a failure.

Important terms:

### RTO

Recovery Time Objective.

How long can the system be down?

### RPO

Recovery Point Objective.

How much data can the organization afford to lose?

## Backups

Backup types:

* Full backup
* Incremental backup
* Differential backup
* Snapshot

## Fault Tolerance

Fault tolerance means a system continues operating after a failure.

Examples:

* RAID
* Multiple power supplies
* Redundant network paths
* Clustering

---

# 9. Chapter 8: Network Segmentation

Network segmentation divides a network into smaller logical or physical sections.

## Why Segment a Network?

Segmentation improves:

* Security
* Performance
* Troubleshooting
* Broadcast control
* Access control
* Organization

## VLANs

A VLAN is a virtual LAN.

A VLAN separates devices logically even if they are connected to the same physical switch.

Important point:

VLANs operate at Layer 2.

## 802.1Q

802.1Q is the VLAN tagging standard.

Example:

Question: Which protocol enables VLAN tagging?

Answer: 802.1Q

## Access Ports

An access port belongs to one VLAN.

Used for end devices like:

* PCs
* Printers
* Phones

## Trunk Ports

A trunk port carries traffic for multiple VLANs.

Used between:

* Switch to switch
* Switch to router
* Switch to firewall
* Switch to hypervisor host

## Default VLAN

On Cisco switches, VLAN 1 is commonly the default VLAN.

Best practice is to avoid using VLAN 1 for user traffic when possible.

## Broadcast Domains

A broadcast domain is the group of devices that receive each other's broadcasts.

VLANs create separate broadcast domains.

## Collision Domains

A collision domain is where packet collisions can occur.

Switches reduce collisions because each switch port is its own collision domain.

## Inter-VLAN Routing

Devices in different VLANs need routing to communicate.

This can be done by:

* Router-on-a-stick
* Layer 3 switch
* Firewall routing

## Troubleshooting VLANs

If devices in the same VLAN cannot communicate, check:

* IP address
* Subnet mask
* VLAN assignment
* Switch port mode
* Cable or NIC

If devices in different VLANs cannot communicate, check:

* Default gateway
* Router or Layer 3 switch
* Trunk configuration
* ACL or firewall rules
* Routing table

Example from your conversations:

If throughput is much lower between VLANs than within the same VLAN, the first thing to investigate is the routing path between VLANs. Inter-VLAN traffic must pass through a router, Layer 3 switch, or firewall, while same-VLAN traffic can stay switched at Layer 2.

---

# 10. Chapter 9: Wide Area Networking

WANs connect networks over large distances.

## WAN Technologies

Common WAN technologies include:

* Fiber
* Cable broadband
* DSL
* Cellular
* MPLS
* Satellite
* Leased lines
* VPN tunnels

## Routing

Routing moves traffic between networks.

Routers make decisions using routing tables.

## Static Routes

A static route is manually configured.

Example:

You add a route so Accounting can reach an HR printer subnet using a specific path.

That is a static route.

## Dynamic Routes

Dynamic routing protocols automatically share route information.

Examples:

* OSPF
* EIGRP
* BGP
* RIP

## Default Route

A default route is used when no more specific route exists.

Often written as:

0.0.0.0/0

## Route Specificity

More specific routes win.

Example:

A route to 192.168.1.0/24 is more specific than 0.0.0.0/0.

## Routing Table Commands

### Windows

route print

### Cisco

show ip route

Example:

Question: You need to determine whether the router has a route to the server's subnet. What command should you use?

Answer: show ip route

## ARP

ARP maps IPv4 addresses to MAC addresses on a local network.

Cisco command:

show arp

Example:

If you want to know whether a router knows of a server's presence on the local subnet, show arp can reveal whether the router has learned the server's MAC address.

## Traceroute and Tracert

Traceroute shows the path traffic takes across routers.

Windows:

tracert

Linux/macOS:

traceroute

Default TTL in many traceroute tools is commonly 30 hops.

## MTU and Fragmentation

MTU is the maximum transmission unit.

If packets are too large and cannot be fragmented, they can be dropped.

This can create a path MTU black hole.

## NAT

NAT translates private IP addresses to public IP addresses.

### Static NAT

One private address maps to one public address.

### Dynamic NAT

Private addresses map to a pool of public addresses.

### PAT

Port Address Translation allows many internal devices to share one public IP address.

PAT is common in home and small business routers.

---

# 11. Chapter 10: Risk Management

Risk management is about identifying, reducing, and responding to risk.

## Risk

Risk is the possibility that a threat will exploit a vulnerability and cause harm.

## Threat

A threat is anything that could cause harm.

Examples:

* Malware
* Attacker
* Natural disaster
* Insider threat
* Hardware failure

## Vulnerability

A weakness that can be exploited.

Examples:

* Unpatched software
* Weak password
* Open port
* Misconfigured firewall
* Default credentials

## Exploit

A method used to take advantage of a vulnerability.

## CIA Triad

### Confidentiality

Only authorized people can access data.

### Integrity

Data is accurate and not improperly changed.

### Availability

Systems and data are accessible when needed.

## Common Attacks

### MAC Spoofing

MAC spoofing means impersonating the physical address of a network device.

Example:

Question: What technique involves impersonating the physical address of a network device?

Answer: MAC spoofing

### Evil Twin

A fake wireless access point that imitates a legitimate one.

### DoS and DDoS

Denial-of-service attacks attempt to make a system unavailable.

Distributed denial-of-service uses many attacking systems.

### VLAN Hopping

An attacker tries to access traffic from another VLAN.

### ARP Poisoning

An attacker sends false ARP messages to redirect traffic.

You saw Bettercap used for ARP poisoning-style attack demonstrations in lab context.

## Bettercap

Bettercap is a security testing tool often used for network attacks and assessments.

In your lab context, it was deployed in Docker.

Docker makes tools easier to deploy because dependencies and runtime environment are packaged.

## Network Hardening

Hardening means reducing attack surface.

Examples:

* Disable unused ports
* Change default passwords
* Use strong authentication
* Patch systems
* Use VLANs
* Apply ACLs
* Use firewall rules
* Enable DHCP snooping
* Disable unused services

## DHCP Snooping

DHCP snooping helps prevent rogue DHCP servers by allowing DHCP responses only from trusted ports.

## Account Management

Reasons to disable an account include:

* Employee departure
* Suspicious activity
* Compromised credentials

Onboarding is not a reason to disable an account.

## Documents and Policies

### AUP

Acceptable Use Policy.

Defines acceptable use of company systems.

### NDA

Non-Disclosure Agreement.

Used when people must agree not to share confidential project information.

Example:

If employees must sign a document saying they will not discuss project information outside the team, use an NDA.

---

# 12. Chapter 11: Access Control

Access control determines who can access what.

## AAA

AAA stands for:

* Authentication
* Authorization
* Accounting

### Authentication

Proves who the user is.

Example:

Username and password.

### Authorization

Determines what the user can access.

Example:

A help-desk technician can reset passwords but cannot delete users.

### Accounting

Tracks what users do.

Example:

Logs of login times and admin changes.

## Principle of Least Privilege

Users should only receive the permissions needed to do their job.

Example:

A help-desk technician who only needs to reset passwords should be given password reset permission, not permission to delete users.

## RADIUS

RADIUS provides centralized authentication, authorization, and accounting.

Commonly used for:

* VPN authentication
* Wireless authentication
* Network device login

## TACACS+

TACACS+ is often used for network device administration.

It separates authentication, authorization, and accounting more strongly than RADIUS.

## LDAP

LDAP is used to access directory services.

Example:

Microsoft Active Directory uses LDAP-style directory access.

## SAML

SAML is used for single sign-on and identity federation.

## ACLs

ACL means Access Control List.

ACLs allow or deny traffic based on rules.

Common criteria:

* Source IP
* Destination IP
* Protocol
* Source port
* Destination port

## ACL Rule Order

ACLs are processed from top to bottom.

First match wins.

If a rule allows traffic before a later deny rule, the traffic may still pass.

Example:

Question: You added a rule to block RDP traffic, but some still gets through. What is the most likely explanation?

Answer: Another rule earlier in the list is conflicting with the rule you made.

## Implicit Deny

Most ACLs have an implied deny rule at the end.

That means traffic not explicitly allowed is denied.

Example:

Question: On a typical ACL, what is the implied rule?

Answer: Deny all traffic not covered by an explicit rule.

## Firewalls

A firewall controls incoming and outgoing traffic.

Example:

Question: Which network appliance acts as a gatekeeper to control incoming and outgoing traffic through a device?

Answer: Firewall

## Stateful vs Stateless Firewall

### Stateless Firewall

Looks at individual packets without remembering connections.

### Stateful Firewall

Tracks the state of active communication sessions.

Example:

Question: What is the primary difference between a stateful and stateless firewall?

Answer: Whether it tracks the status of existing communication sessions.

## Network Trust Zones

### Trusted Zone

Internal network.

### Untrusted Zone

External network, often the Internet.

### Screened Subnet or DMZ

Intermediate-trust zone.

Used for public-facing servers.

Example:

Question: In terms of network trust zones, what is a screened subnet?

Answer: Intermediate-trust.

## ZTNA

Zero Trust Network Access verifies access every time based on identity, device posture, and policy.

Example:

If a smartphone app must require a specific OS version every time a user signs in, ZTNA is the best fit among options like FWaaS, SWG, CASB, and ZTNA.

## CA and PKI

A Certificate Authority helps create a trusted infrastructure for issuing and managing digital identities.

Example:

Question: What creates a trusted infrastructure for issuing and managing digital identities?

Answer: CA

## VPN

A VPN creates an encrypted tunnel across an untrusted network.

A remote machine that connects to a VPN server is called a VPN client.

---

# 13. Chapter 12: Performance and Recovery

Chapter 12 focuses on network performance, monitoring, baselines, and recovery.

## Performance Metrics

### Bandwidth

The maximum theoretical capacity of a link.

### Throughput

The actual amount of data transferred successfully.

### Latency

Delay.

How long it takes data to travel from source to destination.

### Jitter

Variation in latency.

Important for VoIP and video.

### Packet Loss

Packets that fail to arrive.

Very important for voice and video.

## VoIP Troubleshooting

VoIP is sensitive to:

* Latency
* Jitter
* Packet loss
* QoS configuration
* Congestion

Example:

Question: A VoIP network intermittently experiences high packet loss, though latency and jitter are usually low. What troubleshooting step is most likely to identify the problem?

Best idea: Analyze network paths for VoIP traffic to identify congestion points or faulty equipment.

Why: Intermittent packet loss usually means something in the path is dropping traffic.

## QoS

Quality of Service prioritizes important traffic.

Commonly used for:

* VoIP
* Video conferencing
* Real-time applications

## Baseline Metrics

A baseline is a known normal performance level.

Example:

Question: What is the primary purpose of measuring baseline metrics?

Answer: To provide a standard for normal network performance and identify anomalies.

## SNMP

SNMP is used to monitor and manage network devices.

Important terms:

* Manager
* Agent
* MIB
* OID
* Community string
* Trap

## Community String

The community string must be shared by all components on the same SNMP network.

Example:

Question: What must be shared by all components on the same SNMP network?

Answer: Community string

## SNMP Trap

An SNMP trap is an alert sent by an SNMP agent to the manager.

## OID

An Object Identifier identifies a specific managed object.

## SNMP Get and Get Next

SNMP Get retrieves a value.

SNMP Get Next retrieves the next object in the MIB tree.

## NetFlow and IPFIX

NetFlow collects traffic flow metadata.

IPFIX is an IETF standard based on NetFlow concepts.

Example:

Question: You want to collect traffic metadata without complete packet capture so that you can track flows based on source and destination IP addresses and ports. What standard IETF protocol could you use instead of NetFlow?

Answer: IPFIX

## sFlow

sFlow samples packets and interface counters.

## PCAP

PCAP is full packet capture format, not just flow metadata.

## iPerf

iPerf measures network throughput.

Important limitation:

iPerf must be installed and run on both ends of the path being tested.

Example:

Question: What is the primary limitation of using iPerf to measure network performance?

Answer: You must install it on both ends of the path you are testing.

## PRTG

PRTG Network Monitor is used to monitor devices, sensors, bandwidth, and network health.

Your lab used PRTG through a web browser.

## Daily Slowdown Scenario

Example:

Every day around 2 PM, cloud apps, VoIP, and file transfers become slow.

First thing to investigate:

WAN throughput or congestion.

Why:

All those services depend heavily on the WAN or Internet connection.

---

# 14. Packet Tracer Skills Review

Packet Tracer is used to simulate networks.

You used or reviewed Packet Tracer for:

* Building basic networks
* Switch MAC address tables
* VLANs
* Subnet boundaries
* ACLs
* RADIUS
* DHCP snooping
* Wireless SOHO routers
* Secure switch ports

## Basic Packet Tracer Workflow

1. Add devices.
2. Connect devices with proper cables.
3. Assign IP addresses.
4. Configure subnet masks.
5. Set default gateways.
6. Configure switches or routers.
7. Test with ping.
8. Troubleshoot layer by layer.

## Switch Port Security

Switch port security helps prevent unauthorized devices.

It can restrict which MAC addresses are allowed on a port.

Common violation actions:

* Protect
* Restrict
* Shutdown

## VLAN Configuration Steps

Typical steps:

1. Create VLANs.
2. Name VLANs.
3. Assign access ports to VLANs.
4. Configure trunk ports.
5. Configure inter-VLAN routing if needed.
6. Test connectivity.

## Packet Tracer Troubleshooting

If ping fails:

Check:

* Is the device powered on?
* Is the cable connected?
* Is the IP correct?
* Is the mask correct?
* Is the default gateway correct?
* Are devices in the same VLAN?
* Is trunking configured?
* Is routing configured?
* Is an ACL blocking traffic?

---

# 15. pfSense, ACLs, Firewall Rules, and Routing

pfSense is a firewall/router platform.

Your lab examples included pfSense management and ACL/firewall concepts.

## Firewall Interface Direction

In pfSense, firewall rules are usually applied to the interface where traffic enters pfSense.

Example:

To control traffic coming from the LAN into the firewall, apply rules on the LAN interface.

## SSH Rule

SSH uses TCP port 22.

Example:

Question: The ACL on the pfSense firewall enabled communication via port 22. Which service does this represent?

Answer: SSH

## Firewall Types

### Packet Filtering Firewall

Filters based on packet headers.

### Stateful Firewall

Tracks sessions.

### Application Layer Firewall

Can inspect application content.

Example:

If a school wants to block problematic website content or gaming communications, an application layer firewall gives the greatest ability to filter by content or application behavior.

## ACL Rule Order

Always remember:

Top-down processing.

First match wins.

Implicit deny at the end.

---

# 16. RADIUS, AAA, Identity, and Access Management

## RADIUS Use Case

RADIUS is commonly used to centralize authentication for:

* Wi-Fi
* VPN
* Network devices

## AAA Again

Authentication: Who are you?

Authorization: What are you allowed to do?

Accounting: What did you do?

## Least Privilege Example

A help-desk technician needs to reset passwords.

They should receive only the permission to reset or create passwords as needed by the system, not permissions to delete users or perform unrelated admin tasks.

## MDM

Mobile Device Management manages mobile devices.

It can enforce policies such as device encryption, lock screen, remote wipe, and app controls.

## ZTNA vs MDM

MDM manages the device.

ZTNA controls access based on trust evaluation each time.

If the question emphasizes checking device OS version every time a user signs into an app, ZTNA is often the better access-control concept among choices.

---

# 17. Cloud Networking and Virtualization

Cloud networking appeared in your Chapter 8 and virtualization review.

## Virtual Switches in Hyper-V

### External Switch

Allows VMs to communicate with external networks.

### Internal Switch

Allows communication between VMs and the host, but not external networks.

### Private Switch

Allows communication only between VMs on the same host.

Example:

Question: In Hyper-V, which type of switch allows communication between VMs on the same host while not allowing communication with an external network?

Answer: Private

## ISO Files

An .iso file may include a disk image and can be used as a virtual CD or DVD to boot an operating system installer.

## Cloud Networking Terms

### VPC

Virtual Private Cloud.

A logically isolated network in the cloud.

### Subnet

A smaller network inside a VPC.

### Internet Gateway

Allows a cloud VPC to connect to the Internet.

### Security Group

Instance-level firewall-like control.

### Network ACL

Subnet-level firewall-like control.

### NFV

Network Function Virtualization.

Runs network functions like firewalls and routers as software.

---

# 18. Wireless Networking Review

Wireless was earlier than the final chapters, but it supports many scenarios.

## Wireless Standards

Common Wi-Fi standards:

* 802.11a
* 802.11b
* 802.11g
* 802.11n
* 802.11ac
* 802.11ax

## Wireless Security

### WPA2

Strong older standard.

### WPA3

Newer and stronger.

## Evil Twin

A malicious wireless access point pretending to be legitimate.

## SOHO Router

Small Office/Home Office router.

Often combines:

* Router
* Switch
* Firewall
* Wireless access point
* DHCP server
* NAT

---

# 19. Troubleshooting Methodology

Troubleshooting questions often ask what to check first.

## General Process

1. Identify the problem.
2. Establish a theory.
3. Test the theory.
4. Establish a plan.
5. Implement the solution.
6. Verify functionality.
7. Document findings.

## Layered Troubleshooting

Start with simple layers first.

### Physical

* Cable plugged in?
* Link lights?
* Wireless signal?
* Correct port?

### Data Link

* VLAN correct?
* MAC address learned?
* Port security?
* Switchport mode?

### Network

* IP address correct?
* Subnet mask correct?
* Gateway correct?
* Route exists?

### Transport

* Port open?
* TCP or UDP blocked?
* Firewall rule?

### Application

* Service running?
* DNS name correct?
* App configured properly?

## Useful Commands

### ping

Tests reachability.

### tracert or traceroute

Shows path.

### ipconfig

Shows Windows IP configuration.

### ifconfig or ip addr

Shows Linux IP configuration.

### nslookup

Tests DNS resolution.

### netstat

Shows connections and listening ports.

### route print

Shows Windows routing table.

### show ip route

Shows Cisco routing table.

### show arp

Shows ARP table.

---

# 20. Common Exam Traps

## Trap 1: VLANs Are Layer 2

Do not choose Layer 3 just because VLANs are often routed.

The VLAN itself is Layer 2.

## Trap 2: ACLs Are Top-Down

If a deny rule does not work, check for an allow rule above it.

## Trap 3: Implicit Deny

Most ACLs deny everything not explicitly allowed.

## Trap 4: HTTP Is Plaintext

HTTPS is encrypted.

HTTP is plaintext.

## Trap 5: SMB Is Windows File Sharing

SMB uses TCP port 445.

## Trap 6: SFTP and SCP Use SSH

They are not plain FTP.

## Trap 7: iPerf Needs Both Ends

You cannot properly test throughput with iPerf unless both endpoints participate.

## Trap 8: Baselines Define Normal

A baseline is not mainly a max capacity test. It defines normal behavior.

## Trap 9: Packet Capture Uses PCAP

Wireshark opens .pcap files.

## Trap 10: IPFIX Is Flow Metadata

IPFIX is not full packet capture.

---

# 21. Practice Scenarios With Explanations

## Scenario 1: Packet Analysis

You need to examine individual network packets.

Best tool type:

Packet capture.

Best software example:

Wireshark.

Why:

Packet capture tools show individual frames and packets.

## Scenario 2: Plaintext Protocol

Which protocol sends data in plaintext?

HTTP.

Why:

HTTPS, SSH, and IMAPS are encrypted. HTTP is not encrypted by itself.

## Scenario 3: Packet Analyzer File

Which file extension can be opened by Wireshark?

.pcap

Why:

PCAP stands for packet capture.

## Scenario 4: Boolean AND

Filter:

ip.addr == 192.168.1.1 && tcp.port == 80

The && means AND.

Why:

Both conditions must match.

## Scenario 5: Nmap Save Output

Which Nmap switch saves normal output to a file?

-oN

Why:

-oN means output normal.

## Scenario 6: Windows Network Share

Which protocol does Windows network sharing use?

SMB.

Why:

SMB is used for Windows file and printer sharing.

## Scenario 7: Extracting Files From Packets

Which Wireshark feature enables extraction of files from packets?

Export Objects.

Why:

Follow TCP Stream follows a conversation, while Export Objects extracts transferred objects.

## Scenario 8: SFTP Download

Which SFTP command downloads files?

get.

Why:

get pulls a file from the server to the client.

## Scenario 9: Linux Superuser Group

Which group often provides Linux administrative privileges?

sudoers or wheel depending on distribution.

In many Red Hat-style systems, wheel is commonly used. In Debian/Ubuntu-style systems, sudo is commonly used.

## Scenario 10: Stateful Firewall

What is the primary difference between stateful and stateless firewalls?

Stateful firewalls track communication sessions.

Why:

Stateless firewalls inspect packets individually.

## Scenario 11: ACL Blocking RDP Fails

You block RDP, but some still gets through.

Most likely explanation:

An earlier rule allows it.

Why:

First match wins.

## Scenario 12: Screened Subnet

A screened subnet is an intermediate-trust zone.

It is also commonly called a DMZ.

## Scenario 13: SNMP Community String

What must be shared by all components on the same SNMP network?

Community string.

Why:

It functions like a shared SNMP access value.

## Scenario 14: Flow Metadata Without Full Packet Capture

Use IPFIX.

Why:

IPFIX is a standard for flow information.

## Scenario 15: Baseline Purpose

The purpose of a baseline is to define normal network performance.

Why:

You cannot identify abnormal performance if you do not know what normal looks like.

## Scenario 16: Daily 2 PM Slowdown

Cloud apps, VoIP, and file transfers slow every day around 2 PM.

Investigate WAN throughput first.

Why:

A daily pattern affecting many Internet/cloud services suggests congestion or bandwidth saturation.

## Scenario 17: Inter-VLAN Throughput Problem

Throughput is much lower between VLANs than within a VLAN.

Investigate inter-VLAN routing path first.

Why:

Same-VLAN traffic stays switched. Inter-VLAN traffic must be routed.

## Scenario 18: VoIP Packet Loss

VoIP has intermittent packet loss.

Analyze network paths for congestion or faulty equipment.

Why:

Packet loss is often caused by congestion, bad links, faulty equipment, or poor QoS handling.

## Scenario 19: Traceroute Default TTL

Many traceroute implementations use a maximum hop count around 30.

The key idea:

Traceroute manipulates TTL values to discover each router along the path.

## Scenario 20: iPerf Limitation

The main limitation is that iPerf must run on both ends of the path.

Why:

One side acts as server and the other as client.

## Scenario 21: DNS A Record Validation

DNSSEC validates DNS information.

Why:

DNSSEC helps protect against spoofed DNS responses.

## Scenario 22: Device OS Version Checked Every Login

ZTNA is the best fit.

Why:

Zero Trust evaluates access continuously or at each access attempt using identity and device posture.

## Scenario 23: NDA

A company wants employees to sign a document saying project information should not be discussed outside the team.

Use an NDA.

Why:

An NDA protects confidential information.

## Scenario 24: Disable Account

Valid reasons:

* Employee departure
* Suspicious activity
* Compromised credentials

Not a valid reason:

Onboarding.

## Scenario 25: Firewall Gatekeeper

The appliance controlling incoming and outgoing traffic is a firewall.

Why:

Firewalls enforce traffic rules.

---

# 22. Final Cram Sheet

## Must-Know Answers

VLAN layer:

Layer 2

VLAN tagging:

802.1Q

Windows file sharing:

SMB

SMB port:

445

SSH port:

22

HTTP port:

80

HTTPS port:

443

HTTP security:

Plaintext

Packet capture file:

.pcap

Packet analyzer:

Wireshark

Wireshark file extraction:

Export Objects

Wireshark conversation view:

Follow TCP Stream

Nmap save normal output:

-oN

Nmap ping scan:

-sn

SNMP shared value:

Community string

Flow metadata standard:

IPFIX

iPerf limitation:

Must run on both ends

Baseline purpose:

Define normal performance and detect anomalies

ACL processing:

Top-down, first match wins

Implicit ACL rule:

Deny all not explicitly allowed

Screened subnet:

Intermediate-trust or DMZ

Stateful firewall:

Tracks sessions

Static route:

Manually configured route

Default route:

Used when no specific route matches

APIPA range:

169.254.0.0/16

Loopback:

127.0.0.1

SFTP download:

get

SFTP upload:

put

SFTP and SCP use:

SSH

DNS A record:

Hostname to IPv4 address

DNSSEC:

Validates DNS responses

RADIUS:

Centralized AAA

AAA:

Authentication, Authorization, Accounting

CA:

Issues and manages digital identities

VPN remote endpoint:

VPN client

## Subnetting Quick Table

/24 = 255.255.255.0 = 256 total addresses = 254 usable

/25 = 255.255.255.128 = 128 total addresses = 126 usable

/26 = 255.255.255.192 = 64 total addresses = 62 usable

/27 = 255.255.255.224 = 32 total addresses = 30 usable

/28 = 255.255.255.240 = 16 total addresses = 14 usable

/29 = 255.255.255.248 = 8 total addresses = 6 usable

/30 = 255.255.255.252 = 4 total addresses = 2 usable

## Subnetting Steps

1. Identify the starting network.
2. Identify how many subnets are needed.
3. Borrow enough bits to create that many subnets.
4. Add borrowed bits to the original prefix.
5. Count remaining host bits.
6. Calculate total addresses.
7. Subtract 2 for usable hosts.
8. Convert the mask to dotted decimal.
9. Find the block size.
10. List network ranges if needed.

## Best Mental Model

Switching happens inside a local network.

Routing happens between networks.

VLANs split Layer 2 networks.

Routers, Layer 3 switches, and firewalls connect different networks.

ACLs and firewalls control traffic.

Monitoring tools tell you what is happening.

Baselines tell you what normal looks like.

Troubleshooting finds where the normal path breaks.

---

# Final Study Advice

Do not study only definitions. Study situations.

Ask:

What is the device doing?

What layer is involved?

What protocol fits?

What command would prove it?

What is the first reasonable thing to check?

The final exam questions are often designed to test whether you can connect the tool to the problem. If you can quickly identify whether the problem is about VLANs, routing, ACLs, authentication, packet capture, monitoring, or performance, you will move faster and avoid traps.

Focus hardest on:

* Subnetting
* VLANs
* Routing
* ACLs
* Firewalls
* RADIUS and AAA
* SNMP
* iPerf
* PRTG
* Wireshark
* Nmap
* Ports and protocols
* Troubleshooting scenarios


