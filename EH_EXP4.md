# Experiment 4
# Password Auditing and Password Cracking using John the Ripper and Hashcat

## Aim

To perform authorized password auditing by assessing password strength and recovering passwords from provided password hashes using John the Ripper and Hashcat in a controlled laboratory environment.

---

## Course Outcome Mapping

**CO2:** Develop the monitoring technique for network.

---

## Prerequisites

Students should be familiar with:

- Authentication
- Password Hashing
- Linux Commands
- MD5, SHA-1 and SHA-256
- Basic Terminal Commands

---

# Practical Scenario

You are working as a Security Auditor.

The system administrator has requested a password audit to identify weak passwords used within the organization. You have been provided with a list of password hashes generated in a laboratory environment.

Your task is to recover weak passwords (where feasible), identify weak password practices, and recommend improvements.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Kali Linux | Operating System |
| John the Ripper | Password Auditing |
| Hashcat | GPU Password Recovery (optional) |
| rockyou.txt Wordlist | Dictionary Attack |
| Terminal | Command Execution |

---

# Files Required

The instructor will provide:

- Sample password hash file (`hashes.txt`)
- Dictionary file (`rockyou.txt`)

---

# Activity 1 – Identify the Hash Type

Open Terminal.

Examine the provided hash file.

```bash
cat hashes.txt
```

Record the observed hash format.

---

# Activity 2 – Identify Hash Type using John

Execute:

```bash
john --show hashes.txt
```

If required, use:

```bash
john --format=<format> hashes.txt
```

Record the detected hash type.

---

# Activity 3 – Perform Dictionary Attack

Run:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

Wait for the process to complete.

---

### Expected Observation

Students should observe recovered passwords (if any).

---

# Activity 4 – Display Cracked Passwords

Execute:

```bash
john --show hashes.txt
```

Record the recovered passwords.

---

# Activity 5 – Perform Incremental Attack

Run:

```bash
john --incremental hashes.txt
```

Observe how password guessing differs from the dictionary attack.

---

# Activity 6 – Password Strength Analysis

Classify the recovered passwords.

| Password | Weak | Medium | Strong |
|----------|------|--------|--------|
| | | | |
| | | | |
| | | | |

---

# Activity 7 – (Optional) Hashcat Demonstration

Identify available devices:

```bash
hashcat -I
```

Perform a dictionary attack:

```bash
hashcat -m <hash_mode> hashes.txt /usr/share/wordlists/rockyou.txt
```

Display recovered passwords:

```bash
hashcat --show hashes.txt
```

---

# Investigation Challenges

### Challenge 1

Which hash algorithm was used?

Answer:

________________________

---

### Challenge 2

How many hashes were successfully recovered?

Answer:

________________________

---

### Challenge 3

Which password was the weakest?

Answer:

________________________

---

### Challenge 4

Which attack recovered passwords more quickly?

- Dictionary Attack
- Incremental Attack

---

### Challenge 5

Suggest five characteristics of a strong password.

1.
2.
3.
4.
5.

---

### Challenge 6

Why should passwords be stored as hashes instead of plain text?

_____________________________________________________

---

### Challenge 7

What are the limitations of dictionary attacks?

_____________________________________________________

---

### Challenge 8

How does password length affect security?

_____________________________________________________

---

### Challenge 9

Which password policy would you recommend for an organization?

_____________________________________________________

---

### Challenge 10

How can Multi-Factor Authentication (MFA) reduce password-related risks?

_____________________________________________________

---

# Observation Table

| Parameter | Observation |
|-----------|-------------|
| Hash Type | |
| Total Hashes | |
| Passwords Recovered | |
| Dictionary Attack Successful | |
| Incremental Attack Successful | |
| Strong Passwords | |
| Weak Passwords | |

---

# Sample Password Audit Report

| Parameter | Observation |
|-----------|-------------|
| Organization | |
| Analyst | |
| Date | |
| Total Password Hashes | |
| Weak Passwords | |
| Strong Passwords | |
| Recommendations | |

---

# Result

Successfully performed an authorized password audit using John the Ripper (and optionally Hashcat). Weak passwords were identified, password strength was evaluated, and recommendations were prepared to improve organizational password security.

---

# Precautions

- Use only instructor-provided password hashes.
- Do not attempt password recovery on unauthorized systems.
- Protect recovered credentials and do not disclose them.
- Follow institutional ethical hacking policies.
- Use password auditing only with explicit authorization.

---

# Viva Questions

1. What is password hashing?
2. What is the difference between hashing and encryption?
3. What is John the Ripper?
4. What is Hashcat?
5. What is a dictionary attack?
6. What is a brute-force attack?
7. Why is salting used in password storage?
8. What is the purpose of the `rockyou.txt` wordlist?
9. How does MFA improve security?
10. Why is password auditing important?

---

# Conclusion

This experiment provided practical experience in password auditing using John the Ripper and Hashcat. Students learned to identify hash types, perform dictionary-based password recovery on authorized hashes, evaluate password strength, and recommend stronger authentication practices. The exercise emphasized ethical and legal password assessment in controlled environments.