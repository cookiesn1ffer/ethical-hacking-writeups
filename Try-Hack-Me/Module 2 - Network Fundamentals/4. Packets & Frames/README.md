---
Title: "Packets & Frames – TryHackMe Room Write‑Up"
Author: "Cookie"
Date: 2025-11-06
Tags:
  - TryHackMe
  - Networking
  - Packets & Frames
---

# Packets & Frames — README.md

**TL;DR**  
Clear, practical breakdown of how data is packaged at the Data Link and Network layers — covers the difference between frames and packets, encapsulation, MTU, fragmentation, and how switches and routers handle traffic. Short, hands‑on friendly room focused on how data moves on a LAN and across networks.

---

## Summary
This room explains the difference between a *frame* (Layer 2) and a *packet* (Layer 3), how encapsulation works, and why MTU/fragmentation matters. It covers the roles of switches (operate on frames using MAC addresses) and routers (operate on packets using IP addresses), and includes small exercises to identify headers and trace encapsulation in packet captures.

---

## How I did it
1. Read through the theory sections to understand frame vs packet distinctions.  
2. Examined provided examples of Ethernet frames and IP packets.  
3. Used packet capture snippets (or Wireshark where available) to map headers to OSI layers.  
4. Completed questions on MTU, fragmentation behavior, and how devices forward traffic.

---

## Essentials (cheat‑sheet)
**Core concepts**
- **Frame** — Layer 2 unit; includes MAC addresses, EtherType/length, payload, and CRC/FCS.  
- **Packet** — Layer 3 unit; contains IP header (source/destination IP, TTL, protocol) and payload (segment).  
- **Segment/Datagram** — Layer 4 payload: TCP segment or UDP datagram (ports, sequence numbers).  
- **Encapsulation** — Higher-layer data wrapped with lower-layer headers as it goes down the stack.  
- **MTU (Maximum Transmission Unit)** — Largest payload a layer 2 frame can carry without fragmentation (common Ethernet MTU = 1500 bytes).  
- **Fragmentation** — Splitting packets when size > MTU; reassembly happens at the destination (IPv4 supports fragmentation; IPv6 avoids it via PMTU discovery).

**Quick reference: header order (outer → inner on the wire)**
Ethernet header → IP header → TCP/UDP header → Application data

**Common fields to check in captures**
- Ethernet: src MAC, dst MAC, EtherType, FCS (if present)  
- IP: src IP, dst IP, Total Length, Identification, Flags, Fragment Offset, TTL, Protocol  
- TCP: src port, dst port, seq/ack numbers, flags (SYN/ACK/FIN)  
- UDP: src port, dst port, length

**Useful one‑liners (Wireshark / tcpdump)**
- `tcpdump -i <iface> -n -w capture.pcap` — capture traffic to file.  
- `tcpdump -r capture.pcap -nn` — read capture; numeric addresses/ports.  
- Wireshark filters: `eth.src == aa:bb:cc:dd:ee:ff`, `ip.addr == 10.0.0.5`, `tcp.port == 80`

---

## Key takeaways
- Frames are switched on MAC addresses at Layer 2; packets are routed on IP at Layer 3.  
- MTU limits and fragmentation can cause performance and troubleshooting headaches; always check path MTU for large transfers.  
- Encapsulation mapping in packet captures is the most reliable way to prove which layer a field belongs to.  
- TTL, fragmentation flags, and identification fields are useful for diagnosing packet traversal and reassembly issues.

---

## Recommended next steps
- Practice capturing traffic with `tcpdump` or Wireshark and label headers for several flows (HTTP, DNS, ICMP).  
- Experiment with MTU changes on virtual interfaces and observe fragmentation behavior.  
- Learn Path MTU Discovery and how ICMP "fragmentation needed" messages affect TCP.  
- Move on to rooms about switching behavior, VLANs, and routing fundamentals to see where frames/packets interact in real networks.

---

## Tools & skills mentioned
- Tools: Wireshark, tcpdump, tshark.  
- Skills: packet analysis, MTU troubleshooting, basic switching vs routing knowledge, encapsulation mapping.

---

## Personal note
This room is solid for turning abstract OSI talk into observable facts you can prove in a capture. If you want, I can add a short Wireshark lab section with example filters and expected output so you can paste it into your repo as a "Try this" exercise.

---

## License / Author
Author: Cookie  
License: MIT — see root `LICENSE` file.
