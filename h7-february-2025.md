## H7 — February2025!

---

### x) Schneier (2015) Applied Cryptography
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
- Schneier, B. and Diffie, W. (2015). Applied Cryptography: protocols, algorithms, and Source Code in C. Indianapolis (Ind.): Wiley, Cop.

---

## a&b) Install Hashcat & Test with a Sample Hash
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

Source: Terokarvinen.com. (2022). Cracking Passwords with Hashcat. [online] Available at: https://terokarvinen.com/2022/cracking-passwords-with-hashcat/ [Accessed 6 Oct. 2025].

---

## p) Voluntary — Forbes 2019: Jackpotting ATM's (Automated Teller Machines) - Its easier than you might think

- Modern ATMs are basically standard Windows PCs with peripherals
- Only 4 major vendors dominate the market (Diebold Nixdorf, NCR, Siemens, Hitachi)
- Universal keys available online as physical security is terrible
- Most ATMs use XFS middleware that creates portable attacks
- There are some common attack methods like physical access via weak locks or forcing casings
- Network attacks also occur but 30% don't authenticate backend properly
- Hard drive swapping since most don't use full disk encryption
- Black box attacks involves attaching devices to control cash dispensers
- Man-in-the-middle attacks on network connections
- There are several shocking security gaps such as default passwords everywhere
- Outdated software which is rarely patched
- Poor network security using cheap routers
- No full disk encryption (less than 10% of ATMs)
- Weak physical installation
- Most cash theft still involves brute force
- Sophisticated attacks target backend systems to remove withdrawal limits
- Malware families exist that work across ATM brands
- Attacks often sniff card data first, then cash out later
- There are defense recommendations such as using full disk encryption with TPM
- Proper physical installation
- Network segmentation and proper firewalls
- Regular patching and updates
- Application whitelisting properly configured
- Mutual authentication for all components

My Reflection

- This talk really exposes how overestimated ATM security is in the public mind. What struck me most was how these critical financial systems rely on basic Windows computers with minimal hardening. The fact that universal keys are easily purchasable and full disk encryption is rarely used shows how security fundamentals are neglected even in high value targets.
- The homogeneity of systems means one successful attack can scale globally, which is both terrifying for security but also highlights where focused improvements could have massive impact. It's clear that physical and digital security can't be separated since weak locks undermine all the technical controls.
- Most concerning is the cultural issue where ATMs are treated as "working systems don't touch" rather than constantly evolving security threats. This presentation makes me realize that sometimes the biggest vulnerabilities aren't sophisticated zero-days, but basic hygiene failures at scale.

Source: Disobey (2019). Jackpotting ATM’s (Automated Teller Machines) - Its easier than you might think - Alexander Forbes. [online] YouTube. Available at: https://www.youtube.com/watch?v=ThPJrPf7O2s [Accessed 6 Oct. 2025].

‌


