# Offensive Security — Short Intro

> “To outsmart a hacker, you need to think like one.”

## What is Offensive Security?
Offensive security is a proactive cybersecurity approach that uses the same tactics as malicious actors to find and fix vulnerabilities before they can be exploited. It includes activities such as controlled break-ins, vulnerability exploitation, and penetration testing — always performed with authorization and a clearly defined scope.

## Why practice in a lab?
Platforms like **TryHackMe** provide safe, legal, isolated environments where you can practice offensive techniques. In this repository we document short, focused writeups for lab rooms (for example, a simulated bank website) so you can learn how real-world attacks work without any legal risk.

---

## Your first hack — Gobuster
We’ll use a command-line tool called **Gobuster** to brute-force hidden pages and directories on a web server.

**What is Gobuster?**  
Think of Gobuster as trying a giant ring of keys on a locked door: each key is a candidate page or directory name from a wordlist, and the website is the lock. When a key fits (the server returns a positive response), you’ve found a hidden page.

### Example Gobuster command
```bash
gobuster dir -u http://TARGET_IP_OR_DOMAIN -w /usr/share/wordlists/dirb/common.txt -x php,txt,html -t 50 -o gobuster_results.txt
```
- `-u` target URL  
- `-w` wordlist path (see Wordlist tips)  
- `-x` extensions to try (e.g., php, html, txt)  
- `-t` threads (speed)  
- `-o` output file

### Wordlist tips
- Start with curated lists such as **SecLists** (`/usr/share/wordlists/` on many distros).  
- Begin with smaller lists to limit noise, then move to larger lists if needed.  
- Customize and combine lists for the target (e.g., append common admin paths).

---

## Career snapshot (short)
- **Penetration Tester** — tests systems to find exploitable vulnerabilities and reports remediation steps.  
- **Red Teamer** — simulates real-world adversaries to evaluate an organization’s detection and response.  
- **Security Engineer** — designs and maintains security controls to prevent attacks and reduce risk.

---

## Legal & Ethical Note (must include)
Only perform offensive testing on systems you own or have **explicit permission** to test. Unauthorized hacking is illegal and unethical.

---

## TL;DR
- Offensive security = authorized, ethical hacking to find and fix vulnerabilities.  
- Gobuster = fast directory/file discovery using wordlists (keys → lock).  
- Practice in lab environments (TryHackMe, Hack The Box). Always get permission.

---

## Resources
- TryHackMe / Hack The Box — practice labs  
- SecLists — curated wordlists for enumerations  
- Community writeups and walkthroughs — use for learning and inspiration, not copying solutions

---

## Quick pasteable Gobuster one-liner
```bash
gobuster dir -u http://10.10.10.10 -w /usr/share/wordlists/dirb/common.txt -x php,txt,html -t 50 -o results.txt
```

---

License / Author
Author: cookiesn1ffer  
License: MIT — see root `LICENSE` file.

---
