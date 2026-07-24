# Experiment 10
# File Encryption, Digital Signatures and Basic Cryptanalysis using OpenSSL, GPG and Hash Analysis Tools

## Aim

To perform file and text encryption using modern cryptographic tools, generate digital signatures, verify file integrity using cryptographic hashes, and perform basic cryptanalysis using hash identification techniques.

---

## Course Outcome Mapping

**CO5:** Identify the impact of cryptographic techniques and perform basic cryptanalysis.

---

## Prerequisites

Students should be familiar with:

- Cryptography Basics
- Confidentiality
- Integrity
- Authentication
- Linux Commands
- File Handling

---

# Theory

Cryptography protects information from unauthorized access.

Modern security systems use:

- Symmetric Encryption
- Asymmetric Encryption
- Hash Functions
- Digital Signatures

Cryptanalysis attempts to analyze encrypted information without knowing the secret key.

This experiment demonstrates defensive cryptography rather than offensive attacks.

---

# Practical Scenario

You are working as a Security Engineer.

Your organization wants to securely exchange confidential files, verify document integrity, and ensure that important documents have not been modified during transmission.

Your task is to encrypt files, generate digital signatures, verify integrity using hashes, and analyze unknown hashes.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Kali Linux | Operating System |
| OpenSSL | Encryption |
| GnuPG (GPG) | Public Key Cryptography |
| Hash Identifier | Hash Analysis |
| CyberChef (Optional) | Encoding & Decoding |
| Terminal | Command Execution |

---

# Part A – Hashing

## Activity 1 – Create Sample File

```bash
echo "Ethical Hacking Lab" > sample.txt
```

---

## Activity 2 – Generate MD5 Hash

```bash
md5sum sample.txt
```

Record the generated hash.

---

## Activity 3 – Generate SHA-256 Hash

```bash
sha256sum sample.txt
```

Compare the output with the MD5 hash.

---

## Activity 4 – Verify File Integrity

Modify the file.

```bash
echo "New Content" >> sample.txt
```

Generate the SHA-256 hash again.

Observe how the hash value changes.

---

# Part B – Symmetric Encryption

## Activity 5 – Encrypt File using AES-256

```bash
openssl enc -aes-256-cbc \
-salt \
-in sample.txt \
-out sample.enc
```

Enter a password when prompted.

---

## Activity 6 – Decrypt the File

```bash
openssl enc -aes-256-cbc \
-d \
-in sample.enc \
-out decrypted.txt
```

Verify that the decrypted content matches the original.

---

# Part C – Public Key Cryptography

## Activity 7 – Generate GPG Key Pair

```bash
gpg --full-generate-key
```

Record:

- User ID
- Key Type
- Key Size

---

## Activity 8 – Encrypt a File

```bash
gpg --encrypt \
-r "Student Name" \
sample.txt
```

---

## Activity 9 – Decrypt the File

```bash
gpg --decrypt sample.txt.gpg
```

Verify the output.

---

# Part D – Digital Signature

## Activity 10 – Sign the File

```bash
gpg --detach-sign sample.txt
```

---

## Activity 11 – Verify Signature

```bash
gpg --verify sample.txt.sig sample.txt
```

Record the verification result.

---

# Part E – Basic Cryptanalysis

## Activity 12 – Identify Hash Type

Open:

```
hash-identifier
```

or

```bash
hashid
```

Provide the instructor-given hash.

Identify:

- MD5
- SHA1
- SHA256
- SHA512

Record your observations.

---

## Activity 13 – Analyze Hash Characteristics

Complete the following table.

| Algorithm | Length | Security Level |
|-----------|--------|----------------|
| MD5 | | |
| SHA1 | | |
| SHA256 | | |
| SHA512 | | |

---

# Investigation Challenges

### Challenge 1

What is the difference between hashing and encryption?

Answer:

______________________

---

### Challenge 2

Why does changing one character produce a completely different hash?

_____________________________________________________

---

### Challenge 3

Which algorithm is stronger: MD5 or SHA-256?

Explain briefly.

---

### Challenge 4

What is the purpose of AES encryption?

_____________________________________________________

---

### Challenge 5

Why is GPG considered asymmetric cryptography?

_____________________________________________________

---

### Challenge 6

What is the purpose of a digital signature?

_____________________________________________________

---

### Challenge 7

How can file integrity be verified?

_____________________________________________________

---

### Challenge 8

Why should MD5 not be used for modern security applications?

_____________________________________________________

---

### Challenge 9

What information can Hash Identifier provide?

_____________________________________________________

---

### Challenge 10

Mention five real-world applications of cryptography.

1.

2.

3.

4.

5.

---

# Observation Table

| Activity | Observation |
|-----------|-------------|
| MD5 Hash | |
| SHA-256 Hash | |
| AES Encryption Successful | |
| GPG Key Generated | |
| Digital Signature Verified | |
| Hash Type Identified | |
| Integrity Verified | |

---

# Sample Cryptography Report

| Parameter | Observation |
|-----------|-------------|
| Analyst | |
| Date | |
| File Name | |
| Encryption Method | |
| Hash Algorithm | |
| Signature Verified | |
| Recommendations | |

---

# Result

Successfully performed symmetric and asymmetric encryption, generated digital signatures, verified file integrity using cryptographic hashes, and identified hash algorithms using cryptanalysis tools in a controlled laboratory environment.

---

# Precautions

- Keep encryption passwords confidential.
- Securely store private keys.
- Never share private keys with others.
- Verify file integrity after transmission.
- Perform cryptographic operations only on instructor-provided files.

---

# Viva Questions

1. What is cryptography?
2. Differentiate encryption and hashing.
3. What is AES?
4. What is GPG?
5. What is a digital signature?
6. Why is SHA-256 preferred over MD5?
7. What is a public key?
8. What is a private key?
9. What is cryptanalysis?
10. Mention three applications of digital signatures.

---

# Conclusion

This experiment provided hands-on experience with modern cryptographic techniques, including hashing, symmetric encryption, public key encryption, digital signatures, and basic cryptanalysis. Students learned how to protect data confidentiality, verify integrity, authenticate files, and identify cryptographic algorithms used in secure communication.