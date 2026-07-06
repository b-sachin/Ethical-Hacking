# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 8

# Operating System Discovery (OS Fingerprinting)

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain the concept of OS Discovery.
- Differentiate Active and Passive OS Fingerprinting.
- Understand TCP/IP Stack Fingerprinting.
- Explain how TTL, Window Size, and TCP Options help identify an OS.
- Perform OS Detection using Nmap.
- Interpret OS Fingerprinting results.

---

# Recap

In the previous lecture, we discovered:

✔ Open Ports

✔ Running Services

✔ Service Versions

Now another important question arises:

> **Which Operating System is running on the target machine?**

Finding the operating system helps an Ethical Hacker choose the correct tools, exploits, and defense recommendations.

---

# What is Operating System Discovery?

## Definition

**Operating System (OS) Discovery** is the process of identifying the operating system running on a target device by analyzing its network responses.

The goal is to determine whether the target is running:

- Windows
- Linux
- macOS
- Cisco IOS
- Unix
- Android
- Other network operating systems

---

# Why is OS Discovery Important?

Different operating systems have different:

- File Systems
- Services
- Security Features
- Vulnerabilities
- Patch Levels

Example:

```text
Windows Server

↓

SMB Services

↓

Possible SMB Vulnerabilities
```

```text
Linux Server

↓

SSH Service

↓

Possible OpenSSH Vulnerabilities
```

Knowing the operating system helps narrow the focus of further testing.

---

# Real World Analogy

Imagine you see a parked vehicle from a distance.

Without opening it, you may identify:

- Car
- Bike
- Truck

by observing:

- Shape
- Wheels
- Headlights
- Size

Similarly,

Ethical Hackers identify an operating system by observing its network behaviour.

---

# Types of OS Fingerprinting

There are two major approaches.

```text
OS Fingerprinting

│

├── Active Fingerprinting

└── Passive Fingerprinting
```

---

# Active OS Fingerprinting

The scanner actively sends specially crafted packets to the target.

The target replies.

The replies are analyzed to identify the operating system.

Examples:

- Nmap
- Xprobe2

---

# Advantages

✔ Highly Accurate

✔ Fast

✔ Provides detailed information

---

# Limitations

- Generates network traffic.
- Can be detected by IDS/IPS.
- May trigger firewall logs.

---

# Passive OS Fingerprinting

No packets are sent to the target.

Instead,

the attacker observes existing network traffic.

The analysis focuses on:

- TTL
- TCP Window Size
- TCP Options
- Packet Size

Examples:

- Wireshark
- p0f

---

# Advantages

✔ Difficult to Detect

✔ No Direct Interaction

---

# Limitations

- Requires access to network traffic.
- Accuracy depends on available packets.

---

# TCP/IP Stack Fingerprinting

Every operating system implements the TCP/IP protocol slightly differently.

These small differences create a unique "fingerprint."

Examples include:

- Initial TTL
- TCP Window Size
- TCP Options
- ICMP Responses
- Packet Fragmentation Behaviour

By analyzing these characteristics, the scanner estimates the operating system.

---

# Initial TTL Values

TTL stands for

> **Time To Live**

It limits the number of routers a packet can pass through before being discarded.

Different operating systems typically use different default TTL values.

| Operating System | Typical Initial TTL |
|------------------|---------------------|
| Windows | 128 |
| Linux | 64 |
| macOS | 64 |
| Cisco IOS | 255 |

**Important Note:**  
The TTL observed at your machine may be lower because it decreases by **1 at each router hop**.

---

# Practical Demonstration

## Windows

```cmd
ping 192.168.10.25
```

Example Output

```text
Reply from 192.168.10.25

TTL=128
```

Possible Interpretation:

Target may be Windows.

---

## Linux

```bash
ping -c 4 192.168.10.25
```

Example Output

```text
64 bytes from 192.168.10.25

ttl=64
```

Possible Interpretation:

Target may be Linux.

---

# TCP Window Size

TCP Window Size determines how much data can be received before an acknowledgment is required.

Different operating systems use different default window sizes.

Example (simplified):

| OS | Typical Window Size |
|----|----------------------|
| Windows | 65535 |
| Linux | 29200 or higher (varies by kernel) |
| Cisco | Different optimized values |

This is one parameter used in fingerprinting, but not by itself.

---

# TCP Options

Operating systems also differ in:

- Maximum Segment Size (MSS)
- Window Scaling
- Selective Acknowledgment (SACK)
- Timestamps

Nmap compares these options with its fingerprint database.

---

# Active OS Detection using Nmap

## Command

```bash
sudo nmap -O 192.168.10.25
```

---

## Explanation

```
-O
```

means

> Enable Operating System Detection

Nmap sends multiple probe packets and compares the responses with its fingerprint database.

---

# Sample Output

```text
Starting Nmap...

Host is up.

OS details:

Linux 5.x

Network Distance: 1 hop

Device type:

general purpose
```

---

# Interpretation

From the scan we learn:

- Host is alive.
- Operating System is Linux.
- Approximate Kernel Family is 5.x.
- Device Type is General Purpose Computer.
- One router hop away.

---

# Aggressive Scan

Nmap also provides an aggressive scan that combines multiple techniques.

## Command

```bash
sudo nmap -A 192.168.10.25
```

---

## What does `-A` include?

- OS Detection (`-O`)
- Version Detection (`-sV`)
- Default NSE Scripts
- Traceroute

This option is commonly used during authorized penetration testing because it gathers a large amount of information in one scan.

---

# OS Fingerprinting vs Service Discovery

| OS Fingerprinting | Service Discovery |
|-------------------|------------------|
| Identifies Operating System | Identifies Running Services |
| Uses TCP/IP Behavior | Uses Application Responses |
| Example: Linux | Example: Apache 2.4.57 |

---

# Factors Affecting Accuracy

OS Detection may become inaccurate when:

- Firewalls modify responses.
- IDS/IPS filters packets.
- Virtual Machines alter network behavior.
- Custom TCP/IP stacks are used.

Therefore,

Nmap often reports:

```text
OS Guess
```

instead of an exact identification.

---

# Practical Classroom Demonstration

### Step 1

Run OS Detection.

```bash
sudo nmap -O scanme.nmap.org
```

Observe:

- Device Type
- OS Guess
- Network Distance

---

### Step 2

Run Aggressive Scan.

```bash
sudo nmap -A scanme.nmap.org
```

Compare:

- Services
- Versions
- OS Details
- Traceroute Information

Discuss why `-A` reveals much more information than `-O`.

> **Note:** `scanme.nmap.org` is provided by the Nmap project for educational testing.

---

# Ethical Considerations

OS Fingerprinting is useful for:

- Security Audits
- Asset Identification
- Vulnerability Assessment
- Penetration Testing

It should only be performed on systems where authorization has been granted.

---

# Important Commands Summary

| Command | Purpose |
|----------|---------|
| `nmap -O target` | Operating System Detection |
| `nmap -A target` | Aggressive Scan (OS + Version + Scripts + Traceroute) |
| `ping target` | Observe TTL |
| `ping -c 4 target` | Observe TTL (Linux) |

---

# Quick Revision

✔ OS Discovery identifies the target operating system.

✔ Active Fingerprinting sends probe packets.

✔ Passive Fingerprinting analyzes existing traffic.

✔ TTL, Window Size and TCP Options help identify an OS.

✔ `-O` performs OS Detection.

✔ `-A` performs Aggressive Scanning.

---

# University Questions

1. Explain Active and Passive OS Fingerprinting.
2. Explain the role of TTL in OS Detection.
3. Explain OS Detection using Nmap.
4. Explain OS Fingerprinting techniques with suitable diagrams.
5. Discuss TCP/IP Stack Fingerprinting and its importance.
6. Explain OS Discovery using Nmap with practical examples.

---

# Next Lecture

## Scanning Beyond IDS and Firewalls

Topics to be covered:

- What are Firewalls?
- What is an IDS?
- What is an IPS?
- Firewall Evasion Techniques (Conceptual)
- IDS Evasion Techniques (Conceptual)
- Nmap Timing Templates
- Packet Fragmentation (`-f`)
- Decoy Scans (`-D`)
- Source Port Manipulation (`--source-port`)
- Ethical considerations and defensive perspective