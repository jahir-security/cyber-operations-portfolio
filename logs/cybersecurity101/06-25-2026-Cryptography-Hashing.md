## Cryptography, Hashing, and Basics of Hashcat and John the Ripper (Jumbo John) - [06-25-2026]

### What This Covers
This room covers the basics of cryptography, including the workings of public key ciphers like RSA and their application in SSH. It also introduces hash functions, their various types, and the basics of using password-cracking tools like Hashcat and John the Ripper (Jumbo John).

### Key Concepts
* Importance of cryptography
* History of ciphers
* Types of Encryption
* Basic mathematical understanding of cryptography
* Use of Asymmetric Encryption
* RSA, Diffie-Hellman Key Exchange
* SSH
* Digital Signatures and Certificates
* PGP and GPG
* Hash Functions and their use cases
* Hashing for integrity
* Password cracking using Hashcat
* Using John the Ripper (Jumbo John) to crack: Basic Hashes, Windows Authentication Hashes, /etc/shadow Hashes
* Single crack mode
* Custom rules
* Cracking zip files and rar archives
* Cracking SSH keys

### Commands/Tools Used
```bash
hashcat -m <hash_type> -a <attack_mode> hashfile wordlist
sha256sum
ssh2john [id_rsa private key file] > [output file]
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt
python3 hash-id.py
john --format=[format] --wordlist=[path to wordlist] [path to file]
john --list=formats | grep -iF "md5"
unshadow local_passwd local_shadow > unshadowed.txt
john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
```
### What I Learned

I learned how cryptography and hashes are used in real life, the underlying basic principles of math that make them work, and the methods behind public key cryptography. I now understand why both asymmetric and symmetric encryption are needed, exactly how they provide security, and how they can be attacked. Additionally, I learned the basics of using Hashcat and John the Ripper to successfully crack passwords, hashes, zip files, and rar archives.
