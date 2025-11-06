# Defensive Security — TryHackMe Writeup Collection

**Short, focused writeups for the TryHackMe room _Introduction to Defensive Security_.**

> Practical blue-team notes: concise, actionable, and safe to use in an isolated lab environment.

---

## Quick overview
**Defensive security** is the practice of protecting systems, networks, and data from cyberattacks using a mix of proactive and reactive controls: prevention, detection, response, and recovery.

### Core concepts
- **Prevention** — stop attacks before they start (patching, firewalls, hardening, least privilege).
- **Detection** — identify intrusions quickly (logging, SIEM, IDS/IPS, EDR).
- **Response** — contain and investigate incidents (isolate hosts, block C2, perform forensics).
- **Recovery** — restore systems and services, validate integrity, and close root causes.

---

## Why practice in a lab?
Platforms like **TryHackMe** provide safe, legal, isolated environments where you can practice offensive techniques. In this repository we document short, focused writeups for lab rooms (for example, a simulated bank website) so you can learn how real-world attacks work without any legal risk.

---

## Typical defensive responsibilities
- **Monitoring & Detection** — continuous log and traffic analysis for suspicious activity.
- **Incident Response** — runbooks, containment, remediation, and post‑incident review.
- **Threat Intelligence** — use TTPs and IOCs to tune controls and detection rules.
- **Vulnerability Management** — identify and patch/remediate vulnerabilities.
- **Investigation & Analysis** — timeline creation, artifact collection, and root cause analysis.

---

## Defense-in-depth (example controls)
- **Physical**: locked racks, access controls.
- **Network**: segmentation, firewalls, IDS/IPS, VPN hardening.
- **Endpoint**: EDR/AV, application allow‑listing, disk encryption.
- **Identity & Access**: MFA, least privilege, centralized auth.
- **Data**: backups, encryption, secure backups retention.

---

## Practical — Defend the Bank (lab summary)
This lab simulates a small banking environment ("fakebank"). The practical focuses on:
- Observing baseline logs and traffic
- Identifying anomalies and indicators of compromise (IOCs)
- Applying containment (blocking IPs, isolating VMs)
- Remediating vulnerable services and applying patches
- Performing a basic forensic timeline and recovering clean images

---

License / Author
Author: cookiesn1ffer  
License: MIT — see root `LICENSE` file.

---
