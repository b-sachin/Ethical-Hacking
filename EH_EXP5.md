# Experiment 5
# Privilege Escalation and Steganography using Metasploit Framework and Steghide

## Aim

To understand privilege escalation concepts using the Metasploit Framework in a controlled laboratory environment and to hide and retrieve confidential information using Steganography tools.

---

## Course Outcome Mapping

**CO3:** Prioritize vulnerabilities by severity and apply techniques for securing systems against unauthorized access.

---

## Prerequisites

Students should be familiar with:

- Linux Basics
- Windows User Accounts
- Metasploit Basics
- File Permissions
- Steganography Concepts
- Kali Linux

---

# Practical Scenario

You are working as a Penetration Tester.

After obtaining authorized access to a target machine during an internal security assessment, your next objective is to determine whether the current user privileges can be elevated. Additionally, your client requests a demonstration of how confidential information can be securely hidden inside an image for awareness purposes.

Perform all activities only in the instructor-provided laboratory environment.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Kali Linux | Operating System |
| Metasploit Framework | Post-Exploitation |
| Metasploitable2 / Windows Lab VM | Target Machine |
| Steghide | Image Steganography |
| OpenStego (Optional) | GUI Steganography |
| VirtualBox / VMware | Virtualization |

---

# Network Topology

```text
+-----------------------+          +-----------------------+
|     Kali Linux        |--------->|  Metasploitable2 VM   |
| (Metasploit Client)   |          |   Authorized Target   |
+-----------------------+          +-----------------------+
```

---

# Part A – Privilege Escalation

## Activity 1 – Verify Connectivity

Open Terminal.

Verify that the target machine is reachable.

```bash
ping <Target-IP>
```

Record the response.

---

## Activity 2 – Start Metasploit Framework

Execute:

```bash
msfconsole
```

Wait until the framework loads successfully.

---

## Activity 3 – Verify Existing Session

The instructor will provide an authorized Meterpreter session or demonstrate how it is obtained.

List active sessions.

```bash
sessions
```

Record the session ID.

---

## Activity 4 – Gather System Information

Interact with the session.

```bash
sessions -i <Session_ID>
```

Display system information.

```bash
sysinfo
```

Determine the current user.

```bash
getuid
```

Record your observations.

---

## Activity 5 – Enumerate the Target

Collect basic information.

```bash
pwd
```

```bash
ls
```

```bash
ipconfig
```

or

```bash
ifconfig
```

Record the findings.

---

## Activity 6 – Check Privileges

Determine whether the current user has administrative privileges.

Document your observations.

---

## Activity 7 – Privilege Escalation Demonstration

The instructor will demonstrate an authorized privilege escalation technique appropriate for the laboratory VM.

Observe:

- Initial User
- Elevated User
- Method Used
- Outcome

Record the observations.

---

# Part B – Steganography

## Activity 8 – Create a Secret Message

Create a text file.

```bash
nano secret.txt
```

Example:

```text
Confidential Report
Only Authorized Users.
```

Save the file.

---

## Activity 9 – Hide the Message inside an Image

Use Steghide.

```bash
steghide embed \
-cf image.jpg \
-ef secret.txt
```

Provide a passphrase when prompted.

Record the command output.

---

## Activity 10 – Verify the Image

Check the file size.

```bash
ls -lh image.jpg
```

Observe whether the image can still be opened normally.

---

## Activity 11 – Extract the Hidden Message

Execute:

```bash
steghide extract \
-sf image.jpg
```

Enter the passphrase.

Verify that the original message is recovered successfully.

---

## Activity 12 – Compare Original and Extracted Files

| Parameter | Observation |
|-----------|-------------|
| Original Message | |
| Extracted Message | |
| Passphrase Used | |
| Successful Extraction | Yes / No |

---

# Investigation Challenges

### Challenge 1

What is privilege escalation?

Answer:

_________________________

---

### Challenge 2

Why is privilege escalation dangerous?

_____________________________________________________

---

### Challenge 3

Which user account was initially logged in?

Answer:

_________________________

---

### Challenge 4

What information does the `sysinfo` command provide?

_____________________________________________________

---

### Challenge 5

What is Meterpreter?

_____________________________________________________

---

### Challenge 6

What is Steganography?

_____________________________________________________

---

### Challenge 7

Which file types are commonly used for Steganography?

Answer:

_________________________

---

### Challenge 8

What is the purpose of a passphrase in Steghide?

_____________________________________________________

---

### Challenge 9

Differentiate Encryption and Steganography.

_____________________________________________________

---

### Challenge 10

Mention three real-world applications of Steganography.

1.

2.

3.

---

# Observation Table

| Activity | Observation |
|----------|-------------|
| Target IP | |
| Current User | |
| Operating System | |
| Session ID | |
| Privilege Level | |
| Image Used | |
| Secret File | |
| Extraction Successful | |

---

# Sample Assessment Report

| Parameter | Observation |
|-----------|-------------|
| Analyst | |
| Date | |
| Target Machine | |
| Current User | |
| Elevated Privileges | |
| Steganography Tool Used | |
| Hidden File | |
| Result | |

---

# Result

Successfully explored privilege escalation concepts using the Metasploit Framework in an authorized laboratory environment and demonstrated image-based steganography using Steghide by securely embedding and extracting a confidential message.

---

# Precautions

- Perform all activities only on instructor-authorized virtual machines.
- Do not attempt privilege escalation on unauthorized systems.
- Do not create or distribute malicious payloads.
- Use Steganography only for educational purposes.
- Follow institutional ethical hacking policies.

---

# Viva Questions

1. What is privilege escalation?
2. Differentiate vertical and horizontal privilege escalation.
3. What is Meterpreter?
4. What is the purpose of the `sysinfo` command?
5. What is Steganography?
6. What is Steghide?
7. Differentiate Steganography and Cryptography.
8. Why is a passphrase used in Steghide?
9. Name two image formats supported by Steghide.
10. Mention two real-world applications of Steganography.

---

# Conclusion

This experiment introduced students to post-exploitation activities using the Metasploit Framework and demonstrated the concept of privilege escalation in a controlled environment. Students also learned how to securely hide and recover confidential information using image-based steganography, reinforcing practical cybersecurity techniques and ethical usage.