##### Uryyb, Greb! - Homework Report


---

### x.1) Schneier 2015 - *Applied Cryptography*: Chapter 1: Foundations

- Plaintext to Ciphertext transformation using algorithms and keys.
- Security goals include confidentiality, authentication and integrity.
- Kerckhoffs's principle ensures Security through key secrecy, not algorithm secrecy.
- There are 2 algorithim types, Symmetric (same key) vs Public-key (different keys).
- Bits vs characters as basic units
- Attack types include ciphertext-only, Known-plaintext, Chosen-plaintext and Adaptive-chosen-plaintext
- Security levels include unconditionally secure and Computationally secure
- We can break complexity by Measured by data, processing, and storage requirements
- All classical ciphers vulnerable to frequency analysis and modern cryptanalysis
- Simple XOR is defined as the trivial to break despite commercial popularity
- One-time Pad is the perfect secrecy if keys are truly random and never reused
- Modern algorithims include DES (symmetric), RSA (public-key) and DSA (digital signatures)
- Public algorithms withstand scrutiny better than secret ones
- One-time pads provide unconditional security but are impractical for most uses
- Many "new" commercial algorithms are just recycled weak classical ciphers
- Cryptographic security depends on making attacks computationally infeasible.
- Cryptography evolved from character manipulation to mathematical bit operations
- Steganography hides existence of message entirely

Reflection Question:
Since one-time pads are perfectly secure but too hard to use for most people today, what does this show us about the balance between perfect security and what actually works in real life?

**Reference:** Bruce Schneier — *Applied Cryptography* (Ch.1)

---

### x.2) *PGP: Send Encrypted and Signed Message*

- PGP/GPG provides both encryption and signing.
- Public key cryptography enables secure communication without pre-shared secrets
- public keys can be shared openly, private keys must remain secret
- Each user creates their own keypair using gpg --gen-key
- Public keys are exported and shared.
- Fingerprints must be verified out-of-band to establish trust
- Messages encrypted with recipient's public key, signed with sender's private key
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
- Trust Establishment is the hardest part as cryptographic security means nothing if you verify the wrong key

**Reference:** Karvinen 2023 — PGP guide

---

## a) Install OpenSSH Server & Connect

I started by installing the OpenSSH server on my Debian system. After ensuring the package manager was updated, I installed the SSH server and enabled it to start automatically on boot.

```bash

sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl enable ssh
```

The screenshot below shows my first SSH connection to localhost. I encountered the expected host key verification warning since this was the first time connecting. I verified the ED25519 fingerprint and accepted it by typing "yes".

<img width="598" height="40" alt="Screenshot 2025-09-22 at 10 01 54 PM" src="https://github.com/user-attachments/assets/cb6afd75-e862-44b8-bc6e-92145dd9c914" />

## b) Automate SSH with Public Keys

To eliminate the need for password authentication, I set up public key authentication. I generated an ED25519 SSH key pair, accepting the default storage location. Then I copied my public key to the remote host's authorized_keys file using ssh-copy-id.

```bash
ssh-keygen -t ed25519  
ssh-copy-id maabo@localhost
ssh maabo@localhost  # Verified passwordless login worked
```
<img width="627" height="99" alt="Screenshot 2025-09-22 at 9 54 33 PM" src="https://github.com/user-attachments/assets/984b3dd6-928f-4148-bff7-881e380c04c4" />



## c) Password Manager — KeePassXC
I first attempted to install KeePassXC, which is a popular graphical password manager:

```bash

# Install KeePassXC
sudo apt update
sudo apt install keepassxc -y
```

When I tried to launch KeePassXC, I got a Qt display error because I was working in a terminal-only SSH environment without a graphical interface. This taught me that tool selection must match the environment constraints.


<img width="1426" height="139" alt="Screenshot 2025-09-22 at 10 46 42 PM" src="https://github.com/user-attachments/assets/efd996c9-1381-403c-88e7-7564764f75a9" />

Since I needed a solution that worked in my terminal environment, I installed pass, a command-line password manager that integrates with GPG:

```bash

sudo apt install pass -y

```


<img width="685" height="297" alt="Screenshot 2025-09-22 at 10 21 10 PM" src="https://github.com/user-attachments/assets/1da02aa3-956e-48e1-8226-ec1c8da506cb" />

I initialized my password store using the fingerprint of my newly created GPG key. This ensures all my passwords will be encrypted using strong public-key cryptography.


<img width="627" height="301" alt="Screenshot 2025-09-22 at 10 35 24 PM" src="https://github.com/user-attachments/assets/be95fcd9-cdc3-4cac-aa95-cafb0855ac43" />

I then tested the password manager by creating actual entries:

```bash

pass insert firstExample       # Added my account password
pass generate new 20 # Generated a strong 20-character password
pass ls                         # Listed all my stored passwords
```
Using the last prompt, it revealed all of my stored passwords as seen below in the screenshot:
<img width="272" height="91" alt="Screenshot 2025-09-22 at 10 42 29 PM" src="https://github.com/user-attachments/assets/44df0a2c-a97c-4879-9bfa-075192142c72" />
