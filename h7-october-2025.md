#### H7 — February2025!

> **Legal & ethics:** Perform cracking exercises only on hashes/files you are explicitly allowed to test (your own test files, course lab files, or other authorized material). Do not attempt to crack real user passwords or files you do not own.

---

### Schneier (2015) Applied Cryptography
#### 2.3 One-Way Functions

  - A one-way function is easy to compute but hard to reverse. You can get f(x) from x easily, but not the other way around.
  - “Hard” means it would take an unrealistic amount of time even with all computers combined.
  - There’s no solid proof that true one-way functions exist, but many seem to behave that way in practice.
  - They can’t be used directly for encryption since no one could decrypt the message.
  - A trapdoor one-way function includes a secret key that allows reversing it easily.
    
My thoughts

This subchapter basically explains the foundation of encryption which is a one-way functions. They are like the “locks,” and trapdoors are the “keys” that make public-key crypto work.

---

#### 2.4 One-Way Hash Functions
 - Takes a variable length input and produces a fixed length output (hash).
 - Used to “fingerprint” data if even one bit changes, the hash looks totally different.
 - One way means that easy to make the hash, hard to find the original input or another input with the same hash (collision).
 - Hashing doesn’t need secrecy, it’s the mathematical hardness that makes it secure.
 - Great for verifying data without sending the full data.
 - A MAC (Message Authentication Code) adds a secret key, so only someone with the key can verify the hash.
    
My thoughts

Hashes are like digital symbolized as fingerprints as they super useful for checking integrity and authenticity, not secrecy.

**References**
- Schneier, B. (2015). *Applied Cryptography* — Sections 2.3 & 2.4

---

## a) Install Hashcat & Test with a Sample Hash
- I started by reading Tero's article about hashcat and understanding its capabilities for password cracking and recovery.
- The first challenge was installing hashcat on my Linux system and understanding the different hash modes. I used the command down below:

```bash
sudo apt update

# Install hashcat
sudo apt install -y hashcat

# Verify installation
hashcat --version
```
- I saved the target hash to a file called "hash"
- Then, I downloaded and extracted the RockYou wordlist by running the commands

```bash
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
tar xf rockyou.txt.tar.gz
rm rockyou.txt.tar.gz
```
- I used hashid to find out what kind of hash it is:

<img width="620" height="403" alt="Screenshot 2025-10-06 at 11 53 59 PM" src="https://github.com/user-attachments/assets/891e712e-ef74-416b-8a8d-4ef1eda05a23" />

- It showed possible types like:
  - MD2
  - MD5
  - MD4

- I decided to use MD5 because it’s the most common.

- I ran Hashcat to crack the hash:

  <img width="735" height="236" alt="Screenshot 2025-10-06 at 11 56 01 PM" src="https://github.com/user-attachments/assets/9eb6700c-b906-4491-8e78-59dc5109d25f" />

- Hashcat started testing passwords from the wordlist.
- When it finished, I checked the result:
  <img width="549" height="40" alt="Screenshot 2025-10-06 at 11 55 35 PM" src="https://github.com/user-attachments/assets/3b62eacb-8982-466d-b9de-6e65535b4314" />

- cat solved, This means the hash was successfully cracked.
  
#### What I Learned
- If I had just followed a tutorial without understanding the theory, I would have missed why certain hashes take exponentially longer to crack.
- I also learned that throwing maximum computing power at the problem was inefficient. Learning to use targeted dictionary attacks and rules will save hours of computation time.
- MD5 is not secure anymore because it’s too fast and easy to brute-force.
- Using longer and unique passwords can protect against such attacks.

---

## Voluntary (easy) — Crack a ZIP file password

- I created a test folder and put one file inside:
  ```bash
  mkdir zip-test
  echo "This is a test file for the course" > zip-test/readme.txt
```




