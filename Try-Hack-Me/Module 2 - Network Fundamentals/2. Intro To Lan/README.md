# Intro to LAN

**TL;DR**  
Quick intro to how local area networks (LANs) are built — covers topologies, basic subnetting, ARP, and DHCP. Fast, entry‑level primer (≈15 minutes). ([TryHackMe Room](https://tryhackme.com/room/introtolan))

---

## Summary  
This TryHackMe room teaches the fundamentals behind private networks: common LAN topologies, how IP addressing/subnetting works in small networks, what ARP does (mapping IP → MAC), and the role of DHCP for handing out addresses. Great for beginners who want the conceptual scaffolding before deep‑diving into packet captures or enterprise networking.

---

## How I did it  
1. Read each task in order (Topologies → Subnetting → ARP → DHCP → OSI follow‑up).  
2. Took quick notes and sketched the small network diagrams (star vs bus vs ring).  
3. Practised a couple of commands locally to see ARP/DHCP behavior (listed in “Essentials” below).  
4. No hands‑on VM required for basic understanding — this room is concept / quiz focused and short.

---

## Essentials (cheat‑sheet)  
**Concepts**
‑ LAN topologies: **Star**, **Bus**, **Ring**, **Mesh** — star is most common for modern home/small office networks.  
‑ ARP = Address Resolution Protocol — resolves IPv4 addresses to MAC addresses on the same LAN.  
‑ DHCP = Dynamic Host Configuration Protocol — automatically assigns IPs, gateway, DNS to clients.  
‑ Subnetting basics: CIDR `/24` = 255.255.255.0 = 256 addresses (254 usable hosts).  
‑ Default gateway is the router IP on the LAN — traffic to other networks goes through it.

**Mini ASCII diagrams**  
Star (home/small office):
```
     [PC1]
       |
[PC2]-[Switch]-[Router]-Internet
       |
     [PC3]
```
Bus (older / legacy):
```
[PC1]---[PC2]---[PC3]---[Server]
```

---

## Key takeaways  
- LANs are mostly about *local* connectivity: mapping IPs to MACs (ARP) and assigning IPs (DHCP).  
- Subnetting determines which hosts are “local” — learn to calculate network, broadcast, and host ranges fast.  
- Troubleshooting stack: check IP config → check ARP table → check connectivity → check gateway/DHCP.  
- Understanding these basics makes later topics (routing, VLANs, Wi‑Fi issues) far easier.

---

## Tools & skills mentioned  
- Commands: `ip`, `arp`, `ip neigh`, `dhclient`, `ping`, `traceroute`.  
- Skills: basic subnetting, ARP/DHCP conceptual understanding, simple network troubleshooting.  
- (This write‑up used the room template as a baseline.)

---

## License / Author  
Author: Cookie  
License: MIT — see root `LICENSE` file.
