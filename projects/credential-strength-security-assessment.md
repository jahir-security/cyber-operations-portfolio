# Security Assessment Report: Credential Strength via Password Hash Analysis

**Date:** 07-29-2026

**Environment:** Controlled lab environment with simulated scenario.

---

## Scenario

As part of a routine security audit, a password hash file was made available for review., recovered from a system during an audit process. The objective was to analyze the hashes to determine password strength across accounts, and identify any credentials that would pose a risk if the hash database were ever exposed or leaked.

---

## Investigation

Before attempting to crack anything, I first identified the hash type, since using the wrong mode either causes the tool to fail outright or run indefinitely without success. I confirmed those hash types using `hash-id.py`.

The hashes originated from the system's `/etc/shadow` file rather than 
`/etc/passwd`, since modern Linux systems store actual password hashes in the shadow file specifically — it requires elevated privileges to read, unlike `/etc/passwd`, which now only holds usernames and account metadata.

I started with John the Ripper, running a dictionary attack against the **rockyou.txt** wordlist. Dictionary attacks are the fastest way to catch weak, commonly reused passwords, making them the logical first step before resorting to slower, more exhaustive methods.

This immediately cracked 6 out of the 10 password hashes I received.

For any hashes that resisted the dictionary attack, I switched to `Hashcat`, using its GPU-accelerated brute-force/mask attack mode. Hashcat significantly outperforms John's CPU-based approach once a simple wordlist attack fails and a larger keyspace needs to be tested systematically.

This cracked other 3 password hashes. And one hash remained completely uncracked.

---

## Commands/Tools Used

```bash
# Locating the hash file
cat /etc/shadow

# To identify hash type
python3 hash-id.py

# John the Ripper (Jumbo John) - dictionary attack
john --format=[hash format] --wordlist=[path to wordlist rockyou.txt] [path to the hash file]

# Hashcat - brute-force attack (using man hashcat to find the hash type code to use. eg. -m 1000)
hashcat -m <hash_type_code> -a 3 <path_to_hash_file> <mask>

```

---

## Findings

- 6 of 10 hash(es) cracked using a dictionary attack alone — indicates weak, commonly-used passwords vulnerable to fast, low-effort attacks.
- 3 hash(es) required brute-force cracking — indicates moderately stronger 
  password choices, though still ultimately crackable given enough time/compute.
- 1 hash that resisted both methods indicates strong, non-dictionary password practice, consistent with good password hygiene.

**Sample Data Block**

| Account | Hash | Hash Type | Cracked Password | Method |
| :--- | :--- | :--- | :--- | :--- |
| `msfadmin` | `$1$XN10Zj2c$Rt/Ih5CG1J1P0A4A0B7x.` | MD5crypt (Linux `$1$`) | `msfadmin` | Dictionary (`rockyou.txt`) |
| `user1` | `$1$O3JMY.Tj$q/E4hG9V3d0i0zE1kR28B/` | MD5crypt (Linux `$1$`) | `qwerty` | Dictionary (`rockyou.txt`) |
| `service` | `$1$28772684$iEwNO1bZIMSRgXCsvOxoI/` | MD5crypt (Linux `$1$`) | `hashcat` | Brute-Force / Mask (`-a 3`) |
| `root` | `$6$T1qN.4tW$s/PZ0y5xL3m3rC7k0Q8j7B5h6Y1d4W2x6V0z9T3n8L5p1M7k4F0c3V9b2X5g8Z1y4R7t0D6m5J2l8H5n.` | SHA512crypt (Linux `$6$`) | *[Uncracked]* | Resisted both methods |

---

## MITRE ATT&CK Mapping

**T1110.002: Password Cracking**

---

## Analyst Notes

This assessment highlights why password policy enforcement matters even when credentials are stored as hashes — weak, dictionary-based passwords remain crackable within minutes using widely available wordlists, regardless of the hashing algorithm used. In a real environment, I would recommend enforcing multi-factor authentication as an additional control, since password strength alone should not be relied upon as the sole line of defense against credential compromise.
