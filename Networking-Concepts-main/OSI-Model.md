#  OSI Model – Practical Analysis from a Single-Host Lab

The OSI (Open Systems Interconnection) Model is a 7-layer framework that explains how data moves across a network. In cybersecurity, it is not used for memorization — it is used to understand how packets behave, where vulnerabilities exist, and how attacks move through a system.

All demonstrations in this documentation were performed directly on my main operating system:

##  Lab Environment

- **Host OS:** CachyOS (Arch-based Linux)
- **Tools Used:**
  - Wireshark
  - ip command
  - netstat / ss
  - curl

All traffic analysis and testing were performed locally and against controlled targets for educational purposes.

---

##  OSI Model Overview

The OSI model consists of seven layers:

7. Application  
6. Presentation  
5. Session  
4. Transport  
3. Network  
2. Data Link  
1. Physical  

Data travels from Layer 7 down to Layer 1 before transmission (encapsulation), then back up from Layer 1 to Layer 7 when received (decapsulation).

Each layer represents a potential attack surface.

---

##  Layer 7 – Application Layer

The Application layer is where user-facing protocols operate. This includes HTTP, FTP, DNS, and SSH. When using curl, interacting with web services, or running Metasploit modules targeting services, activity occurs at this layer.

This is the most commonly exploited layer because it processes user input and server responses.

<img width="751" height="586" alt="Screenshot_20260303_174130" src="https://github.com/user-attachments/assets/6211aa96-ddd2-45ac-a252-4e2371c889c2" />


The screenshot above should show:
- HTTP protocol in the Protocol column
- GET request
- Host header
- Source and destination IP addresses

Common attack surface:
- SQL Injection
- XSS
- Authentication bypass
- Misconfigured services

---

##  Layer 6 – Presentation Layer

The Presentation layer handles encryption and data formatting. HTTPS traffic is encrypted using TLS at this layer.

When visiting an HTTPS site, the traffic appears encrypted in Wireshark.

<img width="753" height="581" alt="Screenshot_20260303_174552" src="https://github.com/user-attachments/assets/e876330e-c805-4f82-81fa-6e40658154d2" />


The screenshot above should show:
- Client Hello
- Server Hello
- Encrypted Application Data
- No readable HTTP content

Security relevance:
- Weak TLS configurations
- Downgrade attacks
- Certificate validation issues

---

##  Layer 5 – Session Layer

The Session layer manages active communication sessions between systems. Persistent connections such as SSH or long-lived TCP streams operate at this level.

When running Metasploit sessions (e.g., Meterpreter), session management becomes critical.

<img width="1161" height="567" alt="Screenshot_20260303_174750" src="https://github.com/user-attachments/assets/fccd65d7-4c81-4ad5-8400-a10bac8ce31f" />


The screenshot above should show:
- Established TCP connections
- Local and remote ports
- Process names

Session hijacking attacks target this layer when authentication tokens or session IDs are exposed.

---

##  Layer 4 – Transport Layer

The Transport layer ensures reliable or fast data delivery using TCP or UDP.

TCP uses the three-way handshake:

SYN → SYN-ACK → ACK

This handshake can be directly captured.

<img width="752" height="580" alt="Screenshot_20260303_174954" src="https://github.com/user-attachments/assets/3e773153-1079-482f-b91d-2fc4fc5a474e" />


The screenshot above must show:
- SYN packet
- SYN-ACK response
- ACK confirmation
- Matching source/destination IPs

Security relevance:
- Port scanning
- SYN flood attacks
- Service enumeration
- UDP-based amplification attacks

Metasploit modules rely heavily on understanding open ports at this layer.

---

##  Layer 3 – Network Layer

The Network layer handles logical addressing using IP addresses and routing.
To inspect this layer, run:

<img width="998" height="673" alt="Screenshot_20260303_175126" src="https://github.com/user-attachments/assets/e24da6d0-d3d6-49f9-b18f-5a750499fd38" />

Must show:
- Interface name
- IP address
- MAC address
- Interface state

Must show:
- Default gateway
- Network range
- Interface used

Security relevance:
- IP spoofing
- ICMP abuse
- Network enumeration
- Identifying reachable targets

---

## 🔗 Layer 2 – Data Link Layer

The Data Link layer manages MAC addressing and local network communication. ARP operates here.

To observe ARP traffic:

<img width="756" height="579" alt="Screenshot_20260303_175423" src="https://github.com/user-attachments/assets/2f3164a0-f370-460d-8a89-3df09f6d1a8b" />

The screenshot should show:
- “Who has X.X.X.X?”
- MAC address response
- Source and destination MAC addresses

Security relevance:
- ARP spoofing
- Man-in-the-Middle attacks
- Local network interception

---

##  Layer 1 – Physical Layer

The Physical layer represents hardware transmission — cables, signals, and network interfaces.

Although not directly visible in Wireshark, this layer represents physical access to a device or network infrastructure.

In real-world security, physical access can override logical security controls.

---

##  Why the OSI Model Matters in Offensive Security

Understanding the OSI model helps:

- Identify where a vulnerability exists
- Determine which tool to use
- Analyze traffic at packet level
- Understand how exploits travel through a network
- Troubleshoot failed exploitation attempts

Metasploit exploitation depends on:
- Open ports (Layer 4)
- Reachable IPs (Layer 3)
- Service behavior (Layer 7)

Without understanding OSI layers, exploitation becomes guesswork.

---

##  Key Takeaways

- Every OSI layer is a potential attack surface.
- Wireshark allows visualization of multiple layers in a single packet.
- Enumeration begins at Layer 3 and progresses upward.
- Most application vulnerabilities exist at Layer 7.
- Transport behavior determines exploit reliability.

The OSI model is not theoretical knowledge.
It is a structured way to understand how attacks move across systems.
