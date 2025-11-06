# What is Networking?

**TL;DR**  
A concise, hands-on intro to computer networking: what networks are, IP vs MAC, IPv4 vs IPv6, and basic troubleshooting with `ping`. ~30 minutes — great for beginners and a solid refresher.

---

## Summary
This TryHackMe room breaks networking into the essentials: networks are collections of connected devices, the Internet is many networks joined together, devices identify themselves with IP and MAC addresses, IPv4 vs IPv6 differences, and a couple of tiny labs that show MAC spoofing and `ping` in practice. I kept notes on the core concepts so I don’t forget the basics.

---

## How I did it
1. Read each task in order and used the interactive deployable labs on the room.  
2. Completed the MAC-spoofing exercise to observe how MAC filtering can be bypassed.  
3. Ran `ping` (ICMP) against the target addresses provided in the lab to confirm reachability and capture the flag.  
4. Took quick notes on public vs private addressing, the permanence (and spoofability) of MACs, and why IPv6 exists.

> I didn’t paste flags here — keep TryHackMe answers private.

---

## Key takeaways
- A **network** is simply devices connected so they can exchange data; the **Internet** is many networks interconnected.  
- Devices commonly use two identifiers: **IP address** (logical, routable) and **MAC address** (hardware, layer-2).  
- **MAC addresses** can be spoofed — MAC filtering alone is not a secure access control.  
- `ping` uses **ICMP** to check reachability and measure basic latency; it’s the first troubleshooting tool I reach for.  
- **IPv4** is limited in address space; **IPv6** expands addressing massively (and changes some operational details).

---

## Tools & skills mentioned
- `ping` / ICMP  
- ARP basics  
- MAC address concepts & MAC spoofing  
- Basic lab deployment (TryHackMe deployables)

---

License / Author
Author: cookiesn1ffer  
License: MIT — see root `LICENSE` file.

---
