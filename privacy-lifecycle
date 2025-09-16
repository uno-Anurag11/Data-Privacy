```
private-key-lifecycle.md
```

---

````markdown
# 🔐 Private Key Lifecycle Documentation

This document describes the **lifecycle of private keys** used in cryptographic systems, their components, usage, and security practices. Understanding the private key lifecycle is critical for maintaining the confidentiality and integrity of encrypted communications, code signing, authentication, and digital identity.

---

## 📌 What is a Private Key?

A **private key** is a cryptographic key that is kept secret and used to:

- Decrypt data encrypted with a public key (in asymmetric encryption)
- Sign messages or documents
- Authenticate the identity of a system or individual

It must be kept **confidential** at all times. Exposure can lead to **compromise of data or identity**.

---

## 🔄 Private Key Lifecycle Overview

The private key lifecycle consists of **six primary phases**:

1. **Generation**
2. **Storage**
3. **Distribution**
4. **Usage**
5. **Rotation / Renewal**
6. **Destruction / Revocation**

Each phase is critical to maintaining the key's confidentiality and trustworthiness.

---

## 1️⃣ Key Generation

### 📌 Description

The key is created using a cryptographically secure method. It may be generated on a secure device like an HSM (Hardware Security Module) or using software-based libraries.

### ✅ Best Practices

- Use strong, modern algorithms (e.g., RSA 2048+, ECC 256+)
- Use secure random number generators
- Generate in a secure environment

### 💡 Example

```bash
# Generate RSA private key (2048-bit)
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048
````

---

## 2️⃣ Key Storage

### 📌 Description

The private key must be stored securely to prevent unauthorized access.

### ✅ Best Practices

* Store in secure hardware (e.g., HSM, TPM)
* If in software, encrypt at rest using a strong passphrase
* Apply OS-level access controls
* Avoid plaintext storage

### 💡 Example

```bash
# Encrypt private key with a passphrase
openssl rsa -aes256 -in private_key.pem -out private_key_encrypted.pem
```

---

## 3️⃣ Key Distribution

### 📌 Description

Private keys should **not** be distributed. Only the corresponding **public keys** should be shared.

If the key must be moved (e.g., between servers), it should be encrypted and transferred via secure channels.

### ✅ Best Practices

* Avoid sending via email or insecure channels
* Use secure copy (`scp`) or encrypted transfer protocols
* Limit access to specific, authorized systems or users

### 💡 Example

```bash
# Securely copy the key to a remote server (not recommended unless absolutely necessary)
scp private_key_encrypted.pem user@server:/secure/path/
```

---

## 4️⃣ Key Usage

### 📌 Description

The private key is used for:

* **Decryption** (e.g., TLS server decrypting data)
* **Signing** (e.g., code signing, JWTs, SSH authentication)

### ✅ Best Practices

* Limit execution environment access
* Use ephemeral keys when possible
* Monitor for abnormal usage

### 💡 Example: Signing a file

```bash
# Sign a file
openssl dgst -sha256 -sign private_key.pem -out signature.bin data.txt
```

---

## 5️⃣ Key Rotation / Renewal

### 📌 Description

Private keys should be rotated periodically or if there is any suspicion of compromise.

### ✅ Best Practices

* Define a key rotation policy (e.g., every 12 months)
* Automatically rotate using a key management system (KMS)
* Update all systems that use the key

### 💡 Example

```bash
# Generate a new key (same as generation step)
# Then update services or certificates with the new key
```

---

## 6️⃣ Key Destruction / Revocation

### 📌 Description

When a key is no longer needed, it must be **securely destroyed** to prevent any possible recovery.

If the key is associated with a certificate, it must also be **revoked**.

### ✅ Best Practices

* Overwrite or shred key files
* Use secure deletion tools (`shred`, `sdelete`)
* Revoke associated certificates (via CRL or OCSP)

### 💡 Example

```bash
# Securely delete a private key
shred -u private_key.pem
```

---

## 📚 Real-World Use Cases

### 🔒 TLS/SSL Web Server

* Private key stored on the server
* Used to decrypt session keys during HTTPS connections
* Must be protected against theft (e.g., during server compromise)

### 🔑 SSH Authentication

* Private key resides on the client
* Used to authenticate to remote servers
* Public key is placed in `~/.ssh/authorized_keys` on the server

### 📦 Code Signing

* Private key used to sign binaries or packages
* Ensures integrity and authenticity of software

---

## 🧠 Summary

| Phase        | Description                            | Key Concern         |
| ------------ | -------------------------------------- | ------------------- |
| Generation   | Creating a secure key                  | Entropy, algorithm  |
| Storage      | Keeping key safe at rest               | Encryption, access  |
| Distribution | Securely transferring (or avoiding it) | Confidentiality     |
| Usage        | When the key is active                 | Least privilege     |
| Rotation     | Replacing the key periodically         | Minimizing exposure |
| Destruction  | Securely deleting or revoking the key  | Prevent recovery    |

---

## 🛡️ Security Tips

* Use **hardware-based key storage** when possible
* Apply **least privilege** principle
* **Audit** key usage regularly
* Rotate keys and certificates on schedule
* Monitor for key **compromise** and respond quickly

---

*Contributions welcome. Please submit a pull request if you find something to improve!*

```
