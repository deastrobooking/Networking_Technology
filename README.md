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

* Make flashcards
* Generate practice quiz questions
* Or create a Layer-by-Layer OSI cheat sheet

Just tell me what format you want.
