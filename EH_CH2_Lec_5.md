# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 5

# Port Scanning Techniques (Part 1)

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain what Port Scanning is.
- Understand why Ethical Hackers perform Port Scanning.
- Explain TCP Connect Scan.
- Explain TCP SYN (Half-Open) Scan.
- Perform basic Port Scanning using Nmap.
- Interpret scan results.

---

# Recap

In the previous lecture, we learned:

- TCP Three-Way Handshake
- SYN, ACK, FIN and RST Flags
- Open, Closed and Filtered Ports

Now that we understand how TCP communication works, we can understand how attackers use this knowledge to discover open services.

---

# What is Port Scanning?

## Definition

**Port Scanning** is the process of sending specially crafted packets to a target system to determine which ports are open, closed, or filtered.

Port Scanning helps identify the services running on a target machine.

---

# Why Do Ethical Hackers Perform Port Scanning?

Imagine you arrive at a building with 100 doors.

Some doors are:

- Open
- Locked
- Guarded

Before entering, you first identify which doors are open.

Similarly,

A hacker first identifies which ports are open before attempting an attack.

---

# Port Scanning Workflow

```text
Host Discovery
        │
        ▼
Port Scanning
        │
        ├── Open Ports
        ├── Closed Ports
        └── Filtered Ports
                │
                ▼
Service Discovery
                │
                ▼
Vulnerability Assessment
```

---

# Information Obtained from Port Scanning

Port Scanning reveals:

- Open Ports
- Closed Ports
- Filtered Ports
- Running Services
- Potential Attack Surface

It does NOT directly reveal:

- Passwords
- Files
- User Accounts

Those require later attack stages.

---

# Types of Port Scanning

Some common Port Scanning techniques are:

```text
Port Scanning
      │
      ├── TCP Connect Scan
      ├── TCP SYN Scan
      ├── FIN Scan
      ├── NULL Scan
      ├── XMAS Scan
      ├── UDP Scan
      └── Idle Scan
```

Today we will study the two most common methods.

---

# 1. TCP Connect Scan

## Concept

TCP Connect Scan completes the **entire TCP Three-Way Handshake** before closing the connection.

Because the connection is fully established, it is simple but easier to detect.

---

# Working

```text
Scanner                        Target

SYN
------------------------------>

        SYN + ACK
<------------------------------

ACK
------------------------------>

Connection Established

RST
------------------------------>

Connection Closed
```

Notice that the connection is fully established.

---

# How Open and Closed Ports Respond

### Open Port

```text
Scanner               Target

SYN
--------------------->

      SYN + ACK
<---------------------

ACK
--------------------->

Port is OPEN
```

---

### Closed Port

```text
Scanner               Target

SYN
--------------------->

        RST
<---------------------

Port is CLOSED
```

---

# Practical Demonstration

## Command

```bash
nmap -sT 192.168.10.25
```

---

## Explanation

```
-sT
```

means

> TCP Connect Scan

Nmap completes the full TCP connection using the operating system's networking stack.

---

## Sample Output

```text
PORT      STATE    SERVICE

22/tcp    open     ssh

80/tcp    open     http

135/tcp   closed   msrpc

443/tcp   open     https
```

---

## Interpretation

| Port | State | Meaning |
|------|-------|---------|
| 22 | Open | SSH Service Running |
| 80 | Open | HTTP Service Running |
| 135 | Closed | No Service Listening |
| 443 | Open | HTTPS Service Running |

---

# Advantages

✔ Easy to Perform

✔ Reliable

✔ Works without Administrator Privileges

✔ Supported on almost every operating system

---

# Limitations

- Generates log entries.
- Easily detected by IDS/IPS.
- Creates a complete TCP connection.
- Slower than SYN Scan.

---

# Real World Example

Suppose an Ethical Hacker scans a college web server.

Output:

```text
80/tcp open

443/tcp open

22/tcp closed
```

Interpretation:

- Web Server Available
- HTTPS Enabled
- SSH Disabled

The attacker now knows which services can be investigated further.

---

# 2. TCP SYN Scan (Half-Open Scan)

## Concept

Instead of completing the TCP Three-Way Handshake,

the scanner stops immediately after receiving **SYN-ACK**.

Therefore,

the TCP connection is **never fully established**.

For this reason,

it is called

> Half-Open Scan

or

> Stealth Scan

---

# Working

```text
Scanner                    Target

SYN
-------------------------->

      SYN + ACK
<--------------------------

RST
-------------------------->

Connection Terminated
```

Notice

The final ACK is never sent.

Instead,

the scanner immediately sends

RST

to terminate the connection.

---

# Why is it Called Stealth Scan?

Since the TCP connection is never fully established,

many older firewalls and logging systems fail to record the connection.

Therefore,

SYN Scan is much more difficult to detect than TCP Connect Scan.

---

# Open Port Response

```text
SYN

↓

SYN + ACK

↓

RST

↓

Port Open
```

---

# Closed Port Response

```text
SYN

↓

RST

↓

Port Closed
```

---

# Practical Demonstration

## Command

```bash
sudo nmap -sS 192.168.10.25
```

---

## Explanation

```
-sS
```

means

> TCP SYN Scan

Administrator (root) privileges are required because Nmap crafts raw TCP packets.

---

## Sample Output

```text
PORT      STATE    SERVICE

22/tcp    open     ssh

80/tcp    open     http

443/tcp   open     https

3306/tcp  closed   mysql
```

---

## Interpretation

The scanner discovered:

- SSH Running
- HTTP Running
- HTTPS Running
- MySQL Service Not Running

Without completing the TCP connection.

---

# Advantages

✔ Fast

✔ Efficient

✔ Most Popular Scan

✔ Less Detectable

✔ Widely Used During Penetration Testing

---

# Limitations

- Requires Administrator Privileges.
- Modern IDS/IPS can still detect SYN Scans.
- Firewalls may block SYN packets.

---

# TCP Connect Scan vs TCP SYN Scan

| Feature | TCP Connect Scan | TCP SYN Scan |
|----------|------------------|--------------|
| Completes TCP Handshake | Yes | No |
| Speed | Moderate | Fast |
| Detection | Easy | Harder |
| Root Privileges Required | No | Yes |
| Nmap Option | `-sT` | `-sS` |

---

# Practical Classroom Demonstration

Run the following commands:

### TCP Connect Scan

```bash
nmap -sT scanme.nmap.org
```

Observe:

- Open Ports
- Closed Ports
- Service Names

---

### TCP SYN Scan

```bash
sudo nmap -sS scanme.nmap.org
```

Compare:

- Scan Speed
- Port States
- Output

Discuss why SYN Scan is called a **Half-Open Scan**.

> **Note:** `scanme.nmap.org` is a host provided by the Nmap project specifically for learning and testing. Always scan only systems you own or have explicit permission to test.

---

# Important Commands Summary

| Command | Purpose |
|----------|---------|
| `nmap -sT <target>` | TCP Connect Scan |
| `sudo nmap -sS <target>` | TCP SYN Scan |

---

# Quick Revision

✔ Port Scanning identifies open services.

✔ TCP Connect Scan completes the full handshake.

✔ TCP SYN Scan stops after SYN-ACK.

✔ SYN Scan is also called a Half-Open or Stealth Scan.

✔ `-sT` = TCP Connect Scan.

✔ `-sS` = TCP SYN Scan.

---

# University Questions

1. Explain TCP Connect Scan.
2. Explain TCP SYN Scan with a diagram.
3. Compare Connect Scan and SYN Scan.
4. Explain Port Scanning techniques with suitable diagrams.
5. Differentiate TCP Connect Scan and TCP SYN Scan.
6. Explain how Nmap performs Port Scanning using `-sT` and `-sS`.

---

# Next Lecture

## Advanced Port Scanning Techniques

Topics to be covered:

- FIN Scan (`-sF`)
- NULL Scan (`-sN`)
- XMAS Scan (`-sX`)
- UDP Scan (`-sU`)
- ACK Scan (`-sA`)
- Idle Scan (`-sI`)
- Advantages and limitations of each technique.