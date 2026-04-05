#  Networking Concepts for Ethical Hackers

Understanding networking from a real-world cybersecurity perspective — not textbook memorization.

>  All demonstrations in this repository are performed inside a controlled lab environment for educational purposes only.

---

##  About This Project

Most networking guides explain definitions.

This repository explains:
- How networks actually function
- Where vulnerabilities exist
- How attackers abuse protocols
- How defenders detect suspicious traffic

This is networking explained through **hands-on labs, packet analysis, and attack surface breakdowns**.

The goal is simple:
Understand the network deeply enough to both exploit and secure it.

---

##  Objectives

- Build strong networking fundamentals for penetration testing
- Analyze traffic at packet level
- Understand protocol behavior in real environments
- Identify common attack surfaces in network communication
- Map networking concepts to real-world cybersecurity techniques

---

##  Topics Covered

###  Core Concepts
- What is Networking?
- OSI Model (Practical breakdown)
- TCP/IP Model
- Packet Encapsulation
- 3-Way Handshake Analysis

###  Protocol Deep Dive
- HTTP / HTTPS
- DNS
- ARP
- ICMP
- DHCP
- FTP
- SSH

Each protocol section includes:
- What it does
- Default port
- How it works
- Common attack vectors
- Detection insights

###  Subnetting & Addressing
- IPv4 structure
- Private vs Public IP ranges
- CIDR notation
- Subnet masks
- Network enumeration strategy

###  Practical Lab Demonstrations
- Network discovery
- Service enumeration
- Packet capture analysis
- Traffic inspection with Wireshark
- Attack surface identification

---

##  Lab Environment

All practical demonstrations were performed using:

- **Host OS:** CachyOS (Arch-based Linux)
- **Virtualization:** VirtualBox
- **Target VM:** Metasploitable2
- **Packet Analysis:** Wireshark on CachyOS

###  Tools Used

- Nmap
- Wireshark
- tcpdump
- Netcat
- curl
- ip / route commands


---

##  Skills Demonstrated

- Network enumeration
- Traffic analysis
- Protocol inspection
- Packet-level understanding
- Subnet calculation
- Attack surface mapping
- MITRE ATT&CK concept correlation
- Lab documentation

---

##  Why This Matters in Cybersecurity

Attackers don’t break applications first.  
They understand the network first.

- Misconfigured services
- Exposed ports
- Weak protocol implementations
- Trust relationships between systems

Networking knowledge turns random scanning into strategic enumeration.

---

##  Who This Is For

- Beginners entering cybersecurity
- Students preparing for Security+
- TryHackMe / HackTheBox learners
- Anyone transitioning into penetration testing
- Anyone who wants networking explained practically

---

##  Author

CookieSn1ffer
