---
Title: "OSI Model – TryHackMe Room Write‑Up"
Author: "Cookie"
Date: 2025-11-06
Tags:
  - TryHackMe
  - Networking
  - OSI
---

# OSI Model

**TL;DR**  
A foundational overview of the seven layers that define how data travels across networks — from physical signals to user applications. Essential knowledge for network engineers, security professionals, and anyone studying computer networking.

---

## Summary  
The OSI (Open Systems Interconnection) Model provides a logical framework to understand network communication. It divides the process of data transmission into seven layers, each with specific functions. The model improves interoperability, troubleshooting, and comprehension of network protocols by clearly separating responsibilities between software and hardware layers.

---

## How I did it  
1. Reviewed each OSI layer from Application (Layer 7) to Physical (Layer 1).  
2. Summarized their primary functions, common protocols, and tools.  
3. Created quick-reference notes and a mnemonic to remember the layer order.  
4. Answered conceptual questions focusing on which layer each function or protocol operates in.

---

## Essentials (Cheat Sheet)

### The Seven Layers (Top to Bottom)
| Layer | Name | Function | Examples |
|-------|------|-----------|-----------|
| 7 | Application | Provides network services directly to users or applications. | HTTP, DNS, SMTP |
| 6 | Presentation | Handles data translation, encryption, and compression. | SSL/TLS, MIME |
| 5 | Session | Manages sessions between applications. | NetBIOS, RPC |
| 4 | Transport | Ensures reliable or best-effort delivery using ports and sequencing. | TCP, UDP |
| 3 | Network | Manages logical addressing and routing of packets. | IP, ICMP, OSPF |
| 2 | Data Link | Handles framing, physical addressing, and error detection. | Ethernet, ARP |
| 1 | Physical | Deals with actual hardware transmission: signals, media, and cabling. | Cables, Fiber, Radio |

### Encapsulation Flow  
Data moves from Application → Physical (each layer adds its own header).  
When received, the process reverses from Physical → Application (decapsulation).

---

## Key Takeaways  
- The OSI model structures networking into manageable concepts that can be analyzed individually.  
- Layers interact only with their adjacent layers, simplifying design and troubleshooting.  
- Understanding encapsulation helps map how data is wrapped and transmitted between devices.  
- Mapping tools and protocols to OSI layers enhances diagnostic accuracy in both offensive and defensive security.  

---

## Recommended Next Steps  
- Study the TCP/IP model and its relation to OSI (condensed 4-layer version).  
- Analyze packet captures in Wireshark and map frame, packet, and segment data to their respective layers.  
- Explore how OSI concepts apply in real-world protocols like HTTPS, SSH, and DNS tunneling.  
- Proceed to deeper networking labs involving routing, switching, and segmentation.

---

## Tools & Skills Mentioned  
- Protocols: TCP, UDP, IP, ARP, ICMP, DNS, HTTP, TLS.  
- Skills: Network troubleshooting, protocol identification, packet analysis.  
- Tools: Wireshark, tcpdump, ping, traceroute.

---

## Personal Note  
This room was a crisp conceptual refresher. The OSI model might feel theoretical, but once you map it to real-world traffic, it clicks instantly. Understanding where things break (and why) becomes way easier once you think in layers.

---

## License / Author  
Author: Cookie  
License: MIT — see root `LICENSE` file.
