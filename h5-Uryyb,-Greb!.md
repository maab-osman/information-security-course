# Uryyb, Greb! - Homework Report


---

### x.1) Schneier 2015 - *Applied Cryptography*: Chapter 1: Foundations

- Plaintext to Ciphertext transformation using algorithms and keys.
- Security goals include confidentiality, authentication and integrity.
- Kerckhoffs's principle ensures Security through key secrecy, not algorithm secrecy.
- There are 2 algorithm types, Symmetric vs Public-key.
- Bits vs characters as basic units
- Attack types include ciphertext-only, Known-plaintext, Chosen-plaintext and Adaptive-chosen-plaintext
- Security levels include unconditionally secure and computationally secure
- We can break complexity by measuring data, processing, and storage requirements
- All classical ciphers are vulnerable to frequency analysis and modern cryptanalysis
- Simple XOR is defined as the trivial to break despite commercial popularity
- One time Pad is the perfect secrecy if keys are truly random and never reused
- Modern algorithims include DES (symmetric), RSA (public-key) and DSA (digital signatures)
- Public algorithms withstand scrutiny better than secret ones
- One-time pads provide unconditional security but are impractical for most uses
- Many "new" commercial algorithms are just recycled weak classical ciphers
- Cryptographic security depends on making attacks computationally infeasible.
- Cryptography evolved from character manipulation to mathematical bit operations
- Steganography hides existence of message entirely

Reflection Question:
Since one time pads are perfectly secure but too hard to use for most people today, what does this show us about the balance between perfect security and what actually works in real life?

**Reference:** CHAPTER 1: Foundations (2025). Applied Cryptography: Protocols, Algorithms and Source Code in C, 20th Anniversary Edition. [online] O’Reilly Online Learning. Available at: https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/08_chap01.html#chap01-sec001.

---

### x.2) *PGP: Send Encrypted and Signed Message*

- PGP/GPG provides both encryption and signing.
- Public key cryptography enables secure communication without pre-shared secrets
- public keys can be shared openly, private keys must remain secret
- Each user creates their own keypair using gpg --gen-key
- Public keys are exported and shared.
- Fingerprints must be verified out-of-band to establish trust
- Messages encrypted with the recipient's public key, signed with sender's private key
- Recipient decrypts with their private key, verifies signature with sender's public key

Key Commands Demonstrated:
```bash

gpg --gen-key                    # Generate keypair
gpg --export --armor --output key.pub  # Export public key
gpg --import key.pub             # Import others' public keys
gpg --encrypt --sign --recipient user@email.com message.txt  # Encrypt & sign
gpg --decrypt encrypted.pgp      # Decrypt & verify
```


Thoughts & Insights:
- Trust establishment is the hardest part as cryptographic security means nothing if you verify the wrong key

**Reference:** Terokarvinen.com. (2023). PG
P - Send Encrypted and Signed Message - gpg. [online] Available at: https://terokarvinen.com/2023/pgp-encrypt-sign-verify/ [Accessed 20 Sep. 2025].


---

## a) Install OpenSSH Server & Connect

I started by installing the OpenSSH server on my Debian system. After ensuring the package manager was updated, I installed the SSH server and enabled it to start automatically on boot.

```bash

sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl enable ssh
```
<br></br>

The screenshot below shows my first SSH connection to localhost. I encountered the expected host key verification warning since this was the first time connecting. I verified the ED25519 fingerprint and accepted it by typing "yes".

<img width="598" height="40" alt="Screenshot 2025-09-22 at 10 01 54 PM" src="https://github.com/user-attachments/assets/cb6afd75-e862-44b8-bc6e-92145dd9c914" />

<br></br>

Tutorial Source: www.digitalocean.com. (n.d.). How To Use SSH to Connect to a Remote Server | DigitalOcean. [online] Available at: https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server.

‌
## b) Automate SSH with Public Keys

To eliminate the need for password authentication, I set up public key authentication. I generated an ED25519 SSH key pair, accepting the default storage location. Then I copied my public key to the remote host's authorized_keys file using ssh-copy-id.

```bash
ssh-keygen -t ed25519  
ssh-copy-id maabo@localhost
ssh maabo@localhost  # Verified passwordless login worked
```

<br></br>
<img width="627" height="99" alt="Screenshot 2025-09-22 at 9 54 33 PM" src="https://github.com/user-attachments/assets/984b3dd6-928f-4148-bff7-881e380c04c4" />

<br></br>

Tutorial Source: NeuralNine (2024). SSH Key Authentication on Linux Server: Easy Setup Tutorial. [online] YouTube. Available at: https://www.youtube.com/watch?v=6vTcH_kMrhU [Accessed 21 Sep. 2025].


## c) Password Manager
I first attempted to install KeePassXC, which is a popular graphical password manager:

```bash

# Install KeePassXC
sudo apt update
sudo apt install keepassxc -y
```
<br></br>

When I tried to launch KeePassXC, I got a Qt display error because I was working in a terminal-only SSH environment without a graphical interface. This taught me that tool selection must match the environment constraints.


<img width="1426" height="139" alt="Screenshot 2025-09-22 at 10 46 42 PM" src="https://github.com/user-attachments/assets/efd996c9-1381-403c-88e7-7564764f75a9" />
<br></br>

Since I needed a solution that worked in my terminal environment, I installed pass, a command-line password manager that integrates with GPG called "pass" (www.passwordstore.org, n.d.).

```bash

sudo apt install pass -y

```


<img width="685" height="297" alt="Screenshot 2025-09-22 at 10 21 10 PM" src="https://github.com/user-attachments/assets/1da02aa3-956e-48e1-8226-ec1c8da506cb" />

<br></br>
I initialized my password store using the fingerprint of my newly created GPG key. This ensures all my passwords will be encrypted using strong public-key cryptography.


<img width="627" height="301" alt="Screenshot 2025-09-22 at 10 35 24 PM" src="https://github.com/user-attachments/assets/be95fcd9-cdc3-4cac-aa95-cafb0855ac43" />

<br></br>

I then tested the password manager by creating actual entries:

```bash

pass insert firstExample       # Added my account password
pass generate new 20 # Generated a strong 20-character password
pass ls                         # Listed all my stored passwords
```

<br></br>
Using the last prompt, it revealed all of my stored passwords as seen below in the screenshot:

<img width="272" height="91" alt="Screenshot 2025-09-22 at 10 42 29 PM" src="https://github.com/user-attachments/assets/44df0a2c-a97c-4879-9bfa-075192142c72" />

<br></br>

According to the National Cyber Security Centre (NCSC), password managers are essential because they allow users to create and store strong, unique passwords for each of their online accounts without having to remember them all. This is important because reusing passwords across different accounts increases the risk that if one account is compromised, others could be as well. Password managers also offer features such as:
- Automatic password generation for strong, unique passwords.
- Autofill functionality, which helps protect against phishing by only filling passwords on legitimate sites.
- Synchronization across devices, making it easier to log in securely from anywhere.
- Compromise warnings if a password has been breached or leaked.

These tools make it practical to follow best security practices, such as using different passwords for every account, which would otherwise be difficult or impossible to manage manually (NCSC, 2025).

References: 
- GitHub. (2022). KeePassXC. [online] Available at: https://github.com/keepassxreboot/keepassxc.
- National Cyber Security Centre (2018). Password managers: How they help you secure passwords. [online] www.ncsc.gov.uk. Available at: https://www.ncsc.gov.uk/collection/top-tips-for-staying-secure-online/password-managers.
-  www.passwordstore.org. (n.d.). Pass: The Standard Unix Password Manager. [online] Available at: https://www.passwordstore.org/.


‌---

## Voluntary: t) ROT13 Analysis

If I use ROT13 to hide a message, it shifts each letter by 13 places in the alphabet. 

I wanted to see what happens if I use ROT13 twice, so I tried it in Python. I wrote a short program with the codecs library. When I used ROT13 once on the word HELLO, it changed to URYYB. When I ran ROT13 again on that result, it turned back into HELLO. This showed me that double ROT13 just gives the original text, so it doesn’t add any extra security.

```bash

import codecs

word = "HELLO"
once = codecs.encode(word, 'rot_13')
twice = codecs.encode(once, 'rot_13')

print("Original:", word)
print("Once:", once)
print("Twice:", twice)

```
<br></br>

These were the results below:
<img width="340" height="111" alt="Screenshot 2025-09-23 at 1 11 28 PM" src="https://github.com/user-attachments/assets/9258933d-bbf8-4d60-86cb-8c17c495abd9" />

So double ROT13 is not extra security at all. It’s basically like not encrypting the message.

Reference: GeeksforGeeks (2017). ROT13 cipher. [online] GeeksforGeeks. Available at: https://www.geeksforgeeks.org/dsa/rot13-cipher/.

‌

