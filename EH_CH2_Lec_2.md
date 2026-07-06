# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 2

# Host Discovery

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain the concept of Host Discovery.
- Understand why Host Discovery is required.
- Explain various Host Discovery techniques.
- Perform Host Discovery using basic networking tools.
- Interpret the results of Host Discovery.
- Differentiate between ICMP, ARP, TCP and UDP Host Discovery.

---

# Recap

In the previous lecture, we studied **Network Scanning**.

Scanning is the second phase of Ethical Hacking after Reconnaissance.

During scanning, an attacker tries to discover:

- Live Hosts
- Open Ports
- Running Services
- Operating System
- Possible Vulnerabilities

However, before scanning ports or services, one important question must be answered.

> **Is the target machine actually alive?**

The process of answering this question is called **Host Discovery**.

---

# Position of Host Discovery in Ethical Hacking

```text
Reconnaissance
       │
       ▼
Footprinting
       │
       ▼
Host Discovery
       │
       ▼
Port Scanning
       │
       ▼
Service Discovery
       │
       ▼
OS Discovery
       │
       ▼
Enumeration
```

Think of Host Discovery as knocking on the door before entering the house.

---

# What is Host Discovery?

## Definition

**Host Discovery** is the process of identifying active (live) hosts on a network before performing detailed scanning.

It helps determine whether a target system is reachable and responding.

---

# Why is Host Discovery Required?

Suppose an organization owns **1000 computers**.

Will an Ethical Hacker scan all 1000 systems?

No.

First, the hacker identifies which systems are currently online.

Then only those systems are scanned.

This approach:

- Saves Time
- Saves Network Bandwidth
- Reduces Scan Duration
- Improves Efficiency
- Reduces Unnecessary Traffic

---

# Real World Analogy

Imagine you are delivering courier parcels to an apartment.

Do you knock on every apartment?

No.

You first identify the apartment where the customer actually lives.

Similarly,

Host Discovery identifies which computers actually exist on the network.

Only then does further scanning begin.

---

# Objectives of Host Discovery

Host Discovery is performed to:

- Discover active hosts
- Ignore inactive hosts
- Reduce scanning time
- Prepare for Port Scanning
- Create a list of target machines

---

# Information Obtained During Host Discovery

Host Discovery can reveal:

- IP Address
- Reachability
- Response Time
- MAC Address (LAN only)
- Live Systems

Notice that Host Discovery **does not** tell us:

❌ Which ports are open

❌ Which operating system is installed

❌ Which services are running

Those topics will be covered in the next lectures.

---

# Types of Host Discovery

There are four major Host Discovery techniques.

```text
Host Discovery
      │
      ├──────── ICMP Discovery
      ├──────── ARP Discovery
      ├──────── TCP Discovery
      └──────── UDP Discovery
```

Each technique works differently and is useful in different network environments.

---

# 1. ICMP Host Discovery

## What is ICMP?

ICMP stands for

> **Internet Control Message Protocol**

It is a Network Layer protocol used for:

- Reporting Errors
- Network Diagnostics
- Connectivity Testing

The most common ICMP messages are:

- Echo Request
- Echo Reply

These messages are used by the **Ping** command.

---

# How ICMP Host Discovery Works

```text
Attacker
     │
     │ ICMP Echo Request
     ▼
Target Computer
     │
     │ ICMP Echo Reply
     ▼
Attacker
```

If an Echo Reply is received,

the target is considered **Alive**.

If no reply is received,

the host may:

- Be Offline
- Block ICMP Requests
- Be Protected by Firewall

---

# Real Example

Suppose an Ethical Hacker wants to know whether the college web server is online.

The server IP is:

```
192.168.10.25
```

The attacker sends an ICMP Echo Request.

If the server replies,

the system is alive.

Otherwise,

additional techniques such as TCP Discovery may be used.

---

# Practical Demonstration

## Purpose

To verify whether a remote system is reachable using ICMP.

---

## Command (Windows)

```cmd
ping 192.168.10.25
```

---

## Command (Linux / Kali)

```bash
ping -c 4 192.168.10.25
```

Explanation

```
-c 4
```

means

> Send only 4 ICMP Echo Requests.

Without this option,

Linux continues sending Ping packets until interrupted.

---

## Sample Output

```text
Pinging 192.168.10.25 with 32 bytes of data:

Reply from 192.168.10.25:
bytes=32 time=2ms TTL=64

Reply from 192.168.10.25:
bytes=32 time=1ms TTL=64

Reply from 192.168.10.25:
bytes=32 time=3ms TTL=64

Reply from 192.168.10.25:
bytes=32 time=2ms TTL=64

Ping statistics for 192.168.10.25

Packets Sent = 4

Packets Received = 4

Lost = 0
```

---

## Interpretation

| Output | Meaning |
|----------|---------|
| Reply Received | Host is Alive |
| Request Timed Out | Host may be Offline or ICMP blocked |
| Destination Host Unreachable | No route to target |

---

# ICMP Host Discovery using Nmap

Ethical Hackers generally prefer Nmap over the Ping command because it can scan multiple hosts simultaneously.

---

## Command

```bash
sudo nmap -sn 192.168.10.0/24
```

---

## Explanation

```
-sn
```

means

> Ping Scan

Nmap performs **Host Discovery only**.

It **does not perform Port Scanning**.

---

## Sample Output

```text
Starting Nmap...

Nmap scan report for 192.168.10.1

Host is up.

Nmap scan report for 192.168.10.8

Host is up.

Nmap scan report for 192.168.10.25

Host is up.

Nmap done:
256 IP addresses scanned
3 hosts up
```

---

## Interpretation

The output indicates:

- Total IP Addresses Checked → 256

- Active Systems Found → 3

Only these three systems will be scanned further.

---

# Advantages of ICMP Discovery

- Very Fast
- Easy to Perform
- Supported by Almost Every Operating System
- Excellent for Basic Connectivity Testing

---

# Limitations of ICMP Discovery

Many organizations configure firewalls to block ICMP packets.

Therefore,

No Ping Reply

**does not always mean**

Host is Offline.

Ethical Hackers therefore use additional discovery methods such as:

- ARP Discovery
- TCP Discovery
- UDP Discovery

---

# 2. ARP Host Discovery

## What is ARP?

ARP stands for

> **Address Resolution Protocol**

ARP is responsible for mapping an **IP Address** to its corresponding **MAC Address** within a Local Area Network (LAN).

Every device connected to an Ethernet network has:

- An IP Address (Logical Address)
- A MAC Address (Physical Address)

Before communication begins, the sender must know the destination's MAC Address.

ARP performs this mapping automatically.

---

# How ARP Works

Suppose Computer A wants to communicate with Computer B.

Computer A knows only the IP Address.

```
Computer A
IP : 192.168.10.5

        │
        │ Who has 192.168.10.20 ?
        ▼

Network

        │
        ▼

Computer B
IP  : 192.168.10.20
MAC : 00:1A:2B:3C:4D:5E

        ▲
        │
        │ I am 192.168.10.20
        │ MAC = 00:1A:2B:3C:4D:5E
```

Computer A now stores this information in its **ARP Cache**.

---

# Why ARP is Useful for Host Discovery

Unlike ICMP,

ARP requests are generally **not blocked** inside a Local Area Network.

Therefore,

ARP is considered one of the **most reliable Host Discovery techniques** in LAN environments.

---

# Real World Example

Suppose you are connected to your college computer laboratory.

Network:

```
192.168.10.0/24
```

You want to identify which computers are currently ON.

Instead of sending Ping requests,

your computer sends ARP Requests.

Every active computer replies with its MAC Address.

This immediately tells you:

- Which computers are Alive
- Their IP Address
- Their MAC Address

---

# Practical Demonstration

## Purpose

Display the ARP Cache maintained by your computer.

---

## Command (Windows)

```cmd
arp -a
```

---

## Command (Linux)

```bash
arp -a
```

or

```bash
ip neigh
```

---

## Sample Output

```text
Interface: 192.168.10.5

Internet Address      Physical Address

192.168.10.1      00-50-56-C0-00-08

192.168.10.20     08-00-27-84-91-2B

192.168.10.30     40-B0-76-4D-11-22
```

---

## Interpretation

| Field | Meaning |
|--------|---------|
| Internet Address | IP Address |
| Physical Address | MAC Address |

Each entry indicates that communication has already taken place with that device.

---

# ARP Host Discovery using Nmap

Nmap automatically uses ARP requests when scanning hosts on the same Local Area Network.

---

## Command

```bash
sudo nmap -PR 192.168.10.0/24
```

or simply

```bash
sudo nmap -sn 192.168.10.0/24
```

When scanning the local network,

Nmap automatically switches to ARP Discovery because it is more reliable than ICMP.

---

## Sample Output

```text
Nmap scan report for 192.168.10.1

Host is up.

MAC Address:
00:50:56:C0:00:08

Nmap scan report for 192.168.10.20

Host is up.

MAC Address:
08:00:27:84:91:2B
```

---

## Advantages of ARP Discovery

✔ Very Reliable

✔ Very Fast

✔ Difficult to Block inside LAN

✔ Provides MAC Address

---

## Limitations

ARP works only inside a Local Area Network.

It **cannot** discover hosts across the Internet.

---

# ICMP vs ARP Discovery

| ICMP | ARP |
|------|------|
| Uses Ping | Uses ARP Request |
| Works across Networks | Works only in LAN |
| Can be blocked by Firewall | Rarely blocked |
| Returns Reachability | Returns Reachability + MAC Address |

---

# 3. TCP Host Discovery

Many organizations disable ICMP Ping.

If Ping fails,

does it mean the host is offline?

**No.**

The host may simply be blocking ICMP packets.

In such cases,

Ethical Hackers use **TCP Host Discovery**.

---

# Concept

Instead of sending ICMP packets,

the attacker sends a **TCP SYN packet** to commonly used ports.

Examples:

- Port 80 (HTTP)
- Port 443 (HTTPS)
- Port 22 (SSH)

If the target responds,

the host is alive.

---

# Working

```
Attacker

TCP SYN
   │
   ▼

Target

SYN-ACK

   ▲
   │

Attacker
```

The important point is:

Even if the port is closed,

a TCP Reset (RST) still indicates

> **The host exists and is reachable.**

---

# Real Example

Suppose the college web server blocks Ping.

However,

Port 443 (HTTPS)

is open.

Instead of Ping,

Nmap sends a TCP SYN packet.

The server responds,

therefore the host is confirmed to be alive.

---

# Practical Demonstration

## Command

```bash
sudo nmap -PS80,443 192.168.10.25
```

---

## Explanation

```
-PS
```

means

> TCP SYN Ping

```
80,443
```

means

Send TCP SYN packets to

- HTTP
- HTTPS

---

## Sample Output

```text
Starting Nmap...

Host is up.

Latency:
0.0015 seconds
```

---

## Interpretation

The host responded to TCP packets.

Therefore,

the system is Alive,

even if Ping was blocked.

---

# TCP ACK Discovery

Another technique uses TCP ACK packets.

---

## Command

```bash
sudo nmap -PA80 192.168.10.25
```

---

## Explanation

```
-PA
```

means

TCP ACK Ping

Useful when SYN packets are filtered by Firewall.

---

## Advantages

✔ Works when ICMP is blocked

✔ Effective in Enterprise Networks

✔ Very Common during Penetration Testing

---

## Limitations

- May trigger IDS
- May trigger Firewall Alerts

Therefore,

Ethical Hackers perform TCP Discovery only with proper authorization.

---

---

# 4. UDP Host Discovery

## What is UDP?

UDP stands for

> **User Datagram Protocol**

It is a **connectionless transport layer protocol**.

Unlike TCP, UDP does **not establish a connection** before sending data.

There is:

- No Three-Way Handshake
- No Acknowledgement
- No Guarantee of Delivery

Because of this, UDP communication is **faster** but **less reliable** than TCP.

---

# Why Use UDP for Host Discovery?

Some systems block:

- ICMP Requests
- TCP Requests

However, they may still respond to UDP packets.

Therefore, Ethical Hackers also use UDP-based Host Discovery.

---

# How UDP Host Discovery Works

The scanner sends a UDP packet to a target port.

Possible responses are:

### Case 1

The host replies.

```
Scanner
    │
UDP Packet
    │
    ▼

Target

UDP Response

    ▲
    │

Scanner
```

Result

> Host is Alive.

---

### Case 2

The target replies with

```
ICMP Port Unreachable
```

This means:

- The Port is Closed
- But the Host is Alive

---

### Case 3

No Response

Possible reasons:

- Firewall blocked the packet.
- UDP packet ignored.
- Host is Offline.

Further investigation is required.

---

# Real World Example

Suppose a DNS Server is running inside an organization.

DNS uses

```
Port 53 (UDP)
```

Instead of sending Ping,

the Ethical Hacker sends a UDP packet to Port 53.

If a DNS response is received,

the server is confirmed to be alive.

---

# Practical Demonstration

## Purpose

Identify live hosts using UDP packets.

---

## Command

```bash
sudo nmap -PU53 192.168.10.25
```

---

## Explanation

```
-PU
```

means

> UDP Ping

```
53
```

means

Send UDP packets to

DNS Service.

---

## Sample Output

```text
Starting Nmap...

Host is up.

Latency:
0.0023 seconds
```

---

## Interpretation

The host responded to UDP packets.

Therefore,

the system is reachable.

---

# Advantages

✔ Useful when ICMP is blocked.

✔ Useful for discovering UDP Services.

✔ Works well against DNS Servers.

---

# Limitations

- Slower than TCP.

- Many UDP services do not reply.

- Firewall may silently drop UDP packets.

- Output is sometimes difficult to interpret.

---

# Comparison of Host Discovery Techniques

| Technique | Protocol | Best Used For | Limitation |
|-----------|----------|---------------|------------|
| ICMP | ICMP | General Connectivity Testing | Often blocked by Firewalls |
| ARP | ARP | Local Area Networks | Cannot cross Routers |
| TCP | TCP | Enterprise Networks | May trigger IDS/Firewall |
| UDP | UDP | DNS and UDP Services | Slow and Limited Responses |

---

# Host Discovery vs Port Discovery

Students often confuse these two concepts.

| Host Discovery | Port Discovery |
|---------------|----------------|
| Identifies whether a host is alive | Identifies which ports are open |
| First step in Scanning | Performed after Host Discovery |
| Faster | More Detailed |
| Finds Systems | Finds Services |

---

# Choosing the Appropriate Technique

```text
                    Need Host Discovery
                           │
        ┌──────────────────┴──────────────────┐
        │                                     │
Same LAN?                                Different Network?
        │                                     │
       Yes                                   Yes
        │                                     │
Use ARP Discovery                  Is ICMP Allowed?
                                          │
                              ┌───────────┴───────────┐
                              │                       │
                             Yes                     No
                              │                       │
                       Use ICMP Discovery     Use TCP or UDP Discovery
```

---

# Common Nmap Host Discovery Options

| Command | Purpose |
|----------|---------|
| `nmap -sn` | Ping Scan (Host Discovery Only) |
| `nmap -PR` | ARP Discovery |
| `nmap -PS80` | TCP SYN Ping |
| `nmap -PA80` | TCP ACK Ping |
| `nmap -PU53` | UDP Ping |

---

# Classroom Demonstration

Perform the following commands sequentially in Kali Linux.

### Step 1 – ICMP Discovery

```bash
ping -c 4 192.168.10.25
```

Observe:

- Reply
- Time
- TTL

---

### Step 2 – View ARP Cache

```bash
arp -a
```

or

```bash
ip neigh
```

Observe:

- IP Address
- MAC Address

---

### Step 3 – Discover Live Hosts

```bash
sudo nmap -sn 192.168.10.0/24
```

Observe:

- Number of Active Hosts

---

### Step 4 – TCP Discovery

```bash
sudo nmap -PS80 192.168.10.25
```

Observe:

Host responds even if Ping is blocked.

---

### Step 5 – UDP Discovery

```bash
sudo nmap -PU53 192.168.10.25
```

Observe:

Host Discovery using UDP packets.

---

# Important Commands Summary

| Command | Description |
|----------|-------------|
| `ping 192.168.10.25` | ICMP Connectivity Test |
| `arp -a` | View ARP Cache |
| `ip neigh` | View Neighbor Table (Linux) |
| `nmap -sn` | Host Discovery Only |
| `nmap -PR` | ARP Discovery |
| `nmap -PS80` | TCP SYN Discovery |
| `nmap -PA80` | TCP ACK Discovery |
| `nmap -PU53` | UDP Discovery |

---

# Ethical Considerations

Host Discovery is an essential step in penetration testing.

However, it should only be performed:

- With written authorization.
- Within the approved scope.
- During security assessments.
- Following organizational security policies.

Unauthorized scanning may violate cyber laws and organizational policies.

---

# Memory Map

```text
Network Scanning
        │
        ▼
Host Discovery
        │
 ┌──────┼──────────┬──────────┐
 │      │          │          │
ICMP   ARP       TCP        UDP
 │      │          │          │
Ping  LAN Scan  SYN/ACK    UDP Probe
```

---

# University Questions

1. Explain ICMP Host Discovery with a suitable example.
2. Explain ARP Host Discovery with its advantages.
3. Explain TCP Host Discovery.
4. Differentiate ICMP and ARP Discovery.
5. Explain various Host Discovery techniques with suitable diagrams and examples.
6. Compare ICMP, ARP, TCP, and UDP Host Discovery methods.
7. Discuss the role of Host Discovery in Network Scanning.

---

# Next Lecture

# Port Discovery

Topics to be covered:

- What is a Port?
- Types of Ports
- TCP Three-Way Handshake
- Open, Closed, and Filtered Ports
- Port Scanning Techniques
- Common Port Numbers
- Introduction to Nmap Port Scanning
