# TryHackMe: Cryptography Concepts

## Room Summary

This room explores fundamental cryptographic principles, focusing on symmetric and asymmetric encryption, key exchange mechanics, public/private key pairs, and real-world implementations like SSL/TLS and SSH.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Cryptography Concepts |
| Difficulty | Very Easy / Info |
| Topic | Cryptography, Symmetric & Asymmetric Encryption, Key Management |
| Status | Completed |

## Skills Practiced

- Differentiating between Symmetric (secret key) and Asymmetric (public/private key) encryption
- Analyzing symmetric algorithms (AES, DES, 3DES) and asymmetric schemes (RSA, ECC)
- Understanding key distribution mechanisms, digital signatures, and Public Key Infrastructure (PKI)
- Encrypting and decrypting data using OpenSSL and GPG command-line tools
- Managing RSA and SSH key pairs for secure remote access and data transmission

## Hands-On & Command Reference

### Symmetric Encryption Operations (OpenSSL)

```bash
# Encrypt a file using AES-256-CBC with a passphrase
openssl enc -aes-256-cbc -salt -in confidential.txt -out confidential.enc

# Decrypt an AES-256-CBC encrypted file
openssl enc -d -aes-256-cbc -in confidential.enc -out decrypted.txt

```

### Asymmetric Encryption & Key Pair Management (GPG & OpenSSL)

```bash
# Generate a new RSA key pair using OpenSSL
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048

# Extract the corresponding public key from the private key
openssl rsa -pubout -in private_key.pem -out public_key.pem

# Encrypt data using a recipient's public key (OpenSSL)
openssl pkeyutl -encrypt -pubin -inkey public_key.pem -in secret.txt -out secret.enc

# Decrypt data using your private key (OpenSSL)
openssl pkeyutl -decrypt -inkey private_key.pem -in secret.enc -out secret.txt

```

### Digital Signatures & Verification

```bash
# Generate an asynchronous digital signature for a document using GPG
gpg --detach-sign --armor document.pdf

# Verify a signed document against the sender's public key
gpg --verify document.pdf.asc document.pdf

```

## Tools and Platforms Learned

* TryHackMe
* Cryptographic Libraries & CLI Tools (`openssl`, `gpg`, `ssh-keygen`)
* Asymmetric & Symmetric Ciphers (AES, RSA, ECC)

## Key Takeaways

* **Symmetric Encryption:** Uses a single shared secret key for encryption and decryption. High speed and efficiency make it ideal for bulk data transfer (e.g., AES).
* **Asymmetric Encryption:** Employs a mathematically linked key pair (Public Key for encryption/verification, Private Key for decryption/signing). Solves the secure key distribution problem.
* **Hybrid Cryptography:** Modern protocols (like TLS and SSH) combine both methods—using asymmetric encryption to establish a secure session key, then switching to symmetric encryption for fast data exchange.

## Defensive Learning

* Ensure secure private key storage by enforcing strict filesystem permissions (`chmod 600 id_rsa`).
* Enforce modern cryptographic standards (AES-256, RSA 3048/4096-bit, ECC curves) while deprecating legacy algorithms (DES, RC4, MD5).
* Protect key exchanges against Man-in-the-Middle (MitM) attacks by implementing robust Public Key Infrastructure (PKI) and SSL Pinning.

```

```
