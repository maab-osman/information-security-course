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

```bash
# Update packages
sudo apt update

# Install OpenSSH server
sudo apt install openssh-server -y

# Start and enable the ssh service
sudo systemctl start ssh
sudo systemctl enable ssh

# Test connection to localhost
ssh $(whoami)@localhost

```

## b) Automate SSH with Public Keys

```bash
# Generate an Ed25519 SSH key pair (if none exists)
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519 -N ""

# Copy public key to authorized_keys for passwordless auth
ssh-copy-id $(whoami)@localhost

# Test passwordless login
ssh $(whoami)@localhost
```

## c) Password Manager — KeePassXC

```bash

# Install KeePassXC
sudo apt update
sudo apt install keepassxc -y
```

