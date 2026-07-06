# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 6

# Advanced Port Scanning Techniques

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain FIN, NULL, XMAS, ACK, UDP, and Idle Scans.
- Understand the working principle of each scan.
- Interpret responses from target systems.
- Select the appropriate scanning technique for different situations.
- Perform advanced scans using Nmap.

---

# Recap

Previously we studied:

- TCP Connect Scan (`-sT`)
- TCP SYN Scan (`-sS`)

Today we will study stealth and specialized scanning techniques.

---

# Why Do We Need Different Scanning Techniques?

Suppose an organization blocks SYN packets using a firewall.

Will SYN Scan work?

**No.**

Ethical Hackers try different packet types to understand:

- Is the port open?
- Is the firewall filtering traffic?
- Which services are accessible?

Different scan types help answer these questions.

---

# Overview of Advanced Scans

| Scan | Nmap Option | Purpose |
|------|-------------|---------|
| FIN Scan | `-sF` | Firewall Evasion |
| NULL Scan | `-sN` | Firewall Evasion |
| XMAS Scan | `-sX` | Firewall Evasion |
| ACK Scan | `-sA` | Firewall Rule Detection |
| UDP Scan | `-sU` | UDP Services |
| Idle Scan | `-sI` | Anonymous Scanning |

---

# 1. FIN Scan

## Concept

A FIN Scan sends a **FIN** packet to the target instead of a SYN packet.

Normally, FIN is used to terminate an existing TCP connection.

Sending a FIN packet to a port where no connection exists creates behavior that can be analyzed.

---

# Working

### Open Port

```text
Scanner

FIN
------------>

Open Port

(No Response)
```

Meaning:

The port is likely **Open**.

---

### Closed Port

```text
Scanner

FIN
------------>

Target

RST
<------------
```

Meaning:

The port is **Closed**.

---

# Practical Demonstration

```bash
sudo nmap -sF 192.168.10.25
```

---

## Advantages

- Quieter than Connect Scan.
- Can bypass some older firewalls.

---

## Limitations

- Modern firewalls often detect or block it.
- Windows systems generally respond differently, making FIN Scan less reliable.

---

# 2. NULL Scan

## Concept

A NULL Scan sends a TCP packet with **no flags set**.

Normal TCP communication always uses one or more flags.

A packet with no flags is unusual.

The target's response provides information about the port state.

---

# Working

```text
Packet Sent

No Flags

↓

Open Port

No Response

↓

Closed Port

RST
```

---

# Practical Demonstration

```bash
sudo nmap -sN 192.168.10.25
```

---

## Advantages

- Useful against some older filtering devices.
- Generates unusual traffic.

---

## Limitations

- Does not work reliably on Windows systems.
- Easily detected by modern IDS/IPS.

---

# 3. XMAS Scan

## Why is it Called XMAS Scan?

The TCP packet has multiple flags enabled:

- FIN
- PSH
- URG

These flags make the packet look like a Christmas tree with lights turned on.

Hence the name:

> XMAS Scan

---

# Packet Structure

```text
FIN = 1

PSH = 1

URG = 1
```

---

# Working

### Open Port

No Response

### Closed Port

RST Response

---

# Practical Demonstration

```bash
sudo nmap -sX 192.168.10.25
```

---

## Advantages

- Can bypass some simple packet filters.
- Useful during penetration testing.

---

## Limitations

- Less reliable on Windows.
- Modern security devices detect it.

---

# FIN vs NULL vs XMAS

| Feature | FIN | NULL | XMAS |
|---------|-----|------|------|
| FIN Flag | ✔ | ✖ | ✔ |
| PSH Flag | ✖ | ✖ | ✔ |
| URG Flag | ✖ | ✖ | ✔ |
| Open Port | No Response | No Response | No Response |
| Closed Port | RST | RST | RST |

---

# 4. ACK Scan

## Purpose

ACK Scan is **not** used to determine whether a port is open.

Instead, it helps determine whether a firewall is filtering traffic.

---

# Working

```text
Scanner

ACK
------------>

Target

RST

↓

Unfiltered
```

or

```text
No Response

↓

Filtered
```

---

# Practical Demonstration

```bash
sudo nmap -sA 192.168.10.25
```

---

# Interpretation

| Response | Meaning |
|-----------|---------|
| RST | Unfiltered |
| No Response | Filtered by Firewall |

---

# 5. UDP Scan

## Concept

UDP services do not establish a connection like TCP.

Therefore, UDP scanning is slower and often produces fewer responses.

---

# Common UDP Services

| Port | Service |
|------|----------|
| 53 | DNS |
| 67 | DHCP |
| 69 | TFTP |
| 123 | NTP |
| 161 | SNMP |

---

# Practical Demonstration

```bash
sudo nmap -sU 192.168.10.25
```

---

## Sample Output

```text
53/udp

open

domain
```

---

## Advantages

- Identifies UDP services.
- Useful for DNS, DHCP, SNMP assessments.

---

## Limitations

- Slow.
- High false positives.
- Firewall may silently drop UDP packets.

---

# 6. Idle Scan

## Concept

Idle Scan is one of the most advanced Nmap techniques.

Instead of scanning directly,

the attacker uses a third machine called a **Zombie Host**.

The target believes the scan originated from the Zombie.

---

# Working

```text
Attacker

↓

Zombie Host

↓

Target Server
```

The attacker's IP address is hidden.

---

# Practical Demonstration

```bash
sudo nmap -sI zombie_ip target_ip
```

Example:

```bash
sudo nmap -sI 192.168.10.50 192.168.10.25
```

---

## Advantages

- Highly anonymous.
- Hides the attacker's IP.
- Useful for advanced penetration testing.

---

## Limitations

- Requires a suitable idle (zombie) host.
- Difficult to perform in modern networks.

---

# Comparison of All Scan Types

| Scan | Option | Main Purpose | Detectability |
|------|---------|--------------|---------------|
| TCP Connect | `-sT` | Standard Scan | High |
| SYN Scan | `-sS` | Stealth Scan | Medium |
| FIN Scan | `-sF` | Firewall Evasion | Medium |
| NULL Scan | `-sN` | Firewall Evasion | Medium |
| XMAS Scan | `-sX` | Firewall Evasion | Medium |
| ACK Scan | `-sA` | Firewall Detection | Medium |
| UDP Scan | `-sU` | UDP Services | Medium |
| Idle Scan | `-sI` | Anonymous Scan | Low |

---

# Classroom Demonstration

Run the following commands one by one:

```bash
sudo nmap -sF scanme.nmap.org
```

```bash
sudo nmap -sN scanme.nmap.org
```

```bash
sudo nmap -sX scanme.nmap.org
```

```bash
sudo nmap -sA scanme.nmap.org
```

```bash
sudo nmap -sU scanme.nmap.org
```

Observe:

- Port state
- Service name
- Differences in output

> **Note:** Use `scanme.nmap.org` only for learning. Never scan systems without authorization.

---

# Ethical Considerations

These scanning techniques are valuable for:

- Security audits
- Penetration testing
- Vulnerability assessment

Using them without authorization is unethical and may violate laws and organizational policies.

---

# Quick Revision

✔ FIN, NULL and XMAS scans rely on unusual TCP flag combinations.

✔ ACK Scan helps identify firewall filtering.

✔ UDP Scan identifies UDP-based services.

✔ Idle Scan hides the attacker's identity by using a Zombie Host.

---

# University Questions

1. Explain XMAS Scan with a diagram.
2. Explain ACK Scan with suitable examples.
3. Compare FIN, NULL and XMAS Scans.
4. Explain advanced Port Scanning techniques using Nmap.
5. Compare different Port Scanning methods and their applications.
6. Discuss the advantages and limitations of TCP and UDP scanning techniques.

---

# Next Lecture

## Service Discovery and Banner Grabbing

Topics to be covered:

- What is a Service?
- Service Discovery using Nmap
- Banner Grabbing
- Active vs Passive Banner Grabbing
- Version Detection (`-sV`)
- Practical Examples