#  HASHING BASICS — TryHackMe Notes

##  What is Hashing

- One-way cryptographic function
- Takes input of ANY size → outputs fixed-length digest
- Used for password storage & integrity checking
- Cannot be reversed
- Small changes in input cause large change in hash (avalanche effect)

---

#  Properties of Hash Functions

- **Deterministic** — same input always → same output
- **Fixed output length** — independent of input size
- **Pre-image resistance** — cannot retrieve input from hash
- **Collision resistance** — hard to find 2 inputs with same hash
- **Fast computation**

---

#  Hashing vs Encryption vs Encoding

| Concept | Reversible? | Use-case |
| --- | --- | --- |
| Hashing |  NO | Passwords, integrity |
| Encryption |  YES (with key) | Confidentiality |
| Encoding |  YES | Data formatting |

---

#  What is Salt?

- Random string added to password before hashing
- Purpose: prevent identical passwords from having identical hashes
- Salt is stored *with* the hash
- Salt is NOT secret
- Makes pre-computed rainbow table attacks useless

Example format:

```
$6$salt$hash

```

---

#  Using Hashcat

Hashcat syntax:

```
hashcat -m <mode> -a 0 <hashfile> <wordlist>

```

- `m` = hash type (mode)
- `a 0` = straight dictionary attack

Common wordlist:

```
/usr/share/wordlists/rockyou.txt

```

---

#  Hash Identification (VISUAL recognition)

### MD5

- 32 hex chars
- Example:
    
    `b6b0d451bbf6fed658659a9e7e5598fe`
    
- Mode: `m 0`

---

### SHA-1

- 40 hex chars
- Example:
    
    `5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8`
    
- Mode: `m 100`

---

### SHA-256

- 64 hex chars
- Example:
    
    `9eb7ee7f551d2f0ac684981bd1f1e2fa4a37590199636753efe614d4db30e8e1`
    
- Mode: `m 1400`

---

### SHA-512

- 128 hex chars
- Mode: `m 1700`

---

#  Linux Password Hash Formats (`/etc/shadow`)

Always start with `$`

| Prefix | Meaning | Mode |
| --- | --- | --- |
| `$1$` | MD5-crypt | `-m 500` |
| `$5$` | SHA-256-crypt | `-m 7400` |
| `$6$` | SHA-512-crypt | `-m 1800` |

Format:

```
$<type>$<salt>$<hash>

```

Example:

```
$6$GQXVvW4EuM$ehD6jWiMsfNorxy5SI...

```

- `$6$` = SHA512-crypt
- `GQXVvW4EuM` = salt
- remaining = salted hash

---

#  General Steps for Cracking Hashes with Hashcat

1. Identify the hash type
2. Determine the correct `m` mode
3. Ensure hash is in a text file
4. Choose wordlist (rockyou.txt)
5. Run hashcat
6. If:
    - **Status: Cracked** → success
    - **Status: Exhausted** → try different list
    - **Status: Aborted** → wrong mode / format

---

#  How to identify hash type when unsure

1. Look for `$` prefixes
2. Count characters
3. Examine character set

This lets you identify ~90% of hash types instantly.
