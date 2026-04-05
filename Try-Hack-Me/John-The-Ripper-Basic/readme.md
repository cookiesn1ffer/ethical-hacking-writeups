#  JOHN THE RIPPER BASICS — Unified Notes

##  Concept & Purpose

John the Ripper (JtR) is a password-cracking tool used to recover passwords from **hashes**. It’s especially good for:

- Linux `/etc/shadow` hashes
- salted crypt hashes
- unsalted hashes
- simple hash dumps
- CTF password challenges
- offline password retrieval for auditing

---

##  Recognizing Supported Hashes

![https://upload.wikimedia.org/wikipedia/commons/1/19/Passwd_screenshot.png](https://upload.wikimedia.org/wikipedia/commons/1/19/Passwd_screenshot.png)

![https://pub.mdpi-res.com/applsci/applsci-10-07306/article_deploy/html/images/applsci-10-07306-g001.png?1603106128=](https://pub.mdpi-res.com/applsci/applsci-10-07306/article_deploy/html/images/applsci-10-07306-g001.png?1603106128=)

4

[https://media.licdn.com/dms/image/v2/D4D12AQE5X0S_VDv7aA/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1706453352264?e=2147483647&t=uKoN9E2W2hrgoVqbKJwH56Bt6lT9ThCbt4iBSOkrXIM&v=beta](https://media.licdn.com/dms/image/v2/D4D12AQE5X0S_VDv7aA/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1706453352264?e=2147483647&t=uKoN9E2W2hrgoVqbKJwH56Bt6lT9ThCbt4iBSOkrXIM&v=beta)

John handles:

- `$1$...` → MD5-crypt
- `$5$...` → SHA-256-crypt
- `$6$...` → SHA-512-crypt
- Pure hex hash (no $ sign)
- Windows LM/NTLM
- SHA1, SHA256, MD5 (raw hashes)
- Hundreds more formats

---

#  Hash Format Detection (John’s strength)

If you don’t know the hash type:

```
john --format=auto hashfile.txt

```

John will attempt to guess the format.

You can also list supported formats:

```
john --list=formats

```

---

#  Core Cracking Commands

## 1. Crack using wordlist

```
john --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt

```

## 2. Use rules (mutate words automatically)

```
john --wordlist=rockyou.txt --rules hashfile.txt

```

Rules try variants:

- password → password1
- secret → Secret
- monkey → m0nkey

## 3. See cracked passwords

```
john --show hashfile.txt

```

## 4. Monitor progress while running

```
john --status

```

---

#  What’s Happening Under the Hood

John is:

- taking each word in wordlist
- applying rules (if enabled)
- hashing it using same algorithm
- comparing against given hash
- repeating until match found

This is like hashcat, but CPU-based.

---

#  Practical TryHackMe Guidance

Inside this room, you’ll typically:

- receive multiple hash files
- identify hash type
- run John with correct settings
- crack a weak password
- observe difference between salted vs unsalted hashes
- test how rule-based mutation succeeds when normal wordlist fails

Examples THM uses:

- MD5 hashes
- SHA-512 `$6$` shadow hashes
- salted crypt hashes

THM expects you to:

- check the hash visually
- pick correct cracking method
- interpret results

---

#  SALT & SHADOW HASHES

Linux stores passwords in `/etc/shadow` like:

```
$6$somesalt$hashedpassword

```

- `$6$` → SHA-512 crypt
- `somesalt` → unique random salt
- `hashedpassword` → salted result

John automatically extracts the salt — you don’t need to.

---

#  When to Use John vs Hashcat

| Situation | Use John | Use hashcat |
| --- | --- | --- |
| Cracking Linux shadow hash | ✔️ | ✔️ |
| No GPU available | ✔️ | ❌ |
| GPU cracking required | ❌ | ✔️ |
| Legacy/uncommon hash format | ✔️ | ❓ |
| Learning fundamentals | ✔️ | ✔️ |

---

#  Sample Workflow (Full)

### Step 1 — Look at the hash

```
cat hash1.txt

```

### Step 2 — Identify format

```
john --format=auto hash1.txt

```

### Step 3 — Crack

```
john --wordlist=rockyou.txt hash1.txt

```

### Step 4 — Display results

```
john --show hash1.txt

```

---

#  Takeaways to Remember

- John can autodetect many hash types
- It can handle salted hashes easily
- It can use mutation rules to increase chances
- Cracking depends heavily on wordlists
- You must analyze the hash, not just run commands
- If it fails: choose different list or apply rules

---

#  Mental Skill You’re Building

By doing these rooms, you’re learning to:

- recognize hash formats

- choose matching cracking method

- know when dictionary is insufficient

- interpret output

- develop intuition in password cracking
