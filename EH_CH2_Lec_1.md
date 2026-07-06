# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 1

# Introduction to Network Scanning

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

* Explain the concept of Network Scanning.
* Understand why scanning is performed.
* Differentiate between Footprinting and Scanning.
* Explain the objectives of Network Scanning.
* Identify different types of scanning.
* Understand the role of scanning in the Ethical Hacking lifecycle.

---

# Recap

In **Module 1**, we learned that every cyber attack begins with **Reconnaissance** and **Footprinting**.

During Footprinting, an attacker collects publicly available information such as:

* Domain Name
* IP Address
* Email Addresses
* Employee Details
* Website Information
* DNS Information

However, this information is **not sufficient** to launch an attack.

The attacker now wants to know:

* Which computers are online?
* Which ports are open? 
* Which services are running?
* Which operating system is installed?
* Which machines are vulnerable?

To answer these questions, the attacker performs **Network Scanning**.

---

# From Information Gathering to Scanning

```text
Reconnaissance
        ↓
Footprinting
        ↓
Network Scanning
        ↓
Enumeration
        ↓
Vulnerability Assessment
        ↓
System Hacking
```

**Important Observation**

Footprinting answers:

> **"Who is the target?"**

Scanning answers:

> **"What services and systems does the target expose?"**

---

# What is Network Scanning?

## Definition

**Network Scanning** is the process of discovering live hosts, open ports, running services, and operating systems on a network using authorized tools and techniques.

It helps security professionals identify network assets and detect potential security weaknesses.

---

# Why is Network Scanning Important?

Before attacking or securing a system, we must first understand the network.

Network Scanning helps to:

* Identify active devices.
* Discover open communication ports.
* Identify running network services.
* Detect operating systems.
* Locate potential vulnerabilities.
* Verify network configuration.
* Support security audits.

---

# Real-World Analogy

Imagine a thief planning to rob a house.

### Step 1 – Observation (Reconnaissance)

The thief observes:

* House location
* Owner's routine
* CCTV cameras
* Main entrance

### Step 2 – Inspection (Scanning)

The thief now checks:

* Which doors are unlocked?
* Which windows are open?
* Is the alarm active?
* Is anyone inside the house?

Only after gathering this information does the thief decide whether to proceed.

Similarly, hackers perform **Scanning** before attempting an attack.

---

# Objectives of Network Scanning

The primary objectives are:

* Discover live hosts.
* Identify open ports.
* Detect network services.
* Identify operating systems.
* Locate security weaknesses.
* Prepare for the next phase (Enumeration).

---

# Information Collected During Scanning

```text
Network Scanning
        │
        ├── Live Hosts
        ├── IP Addresses
        ├── MAC Addresses
        ├── Open Ports
        ├── Running Services
        ├── Operating System
        └── Network Topology
```

---

# Example

Suppose an attacker knows only the college website:

```
www.xyzcollege.edu.in
```

After scanning, the attacker discovers:

| Information      | Result    |
| ---------------- | --------- |
| IP Address       | 203.x.x.x |
| Port 80          | Open      |
| Port 443         | Open      |
| Port 22          | Closed    |
| Web Server       | Apache    |
| Operating System | Linux     |

The attacker now understands the target much better.

---

# Footprinting vs Network Scanning

| Footprinting                    | Network Scanning               |
| ------------------------------- | ------------------------------ |
| Collects public information     | Collects technical information |
| Mostly Passive                  | Mostly Active                  |
| Difficult to detect             | Easier to detect               |
| No direct interaction (usually) | Direct interaction with target |
| First step                      | Second step                    |

---

# Types of Network Scanning

Network Scanning can be broadly classified into four categories.

```text
Network Scanning
        │
 ┌──────┼─────────────┬────────────┐
 │      │             │            │
Host   Port       Service      OS
Discovery Discovery Discovery Discovery
```

---

# 1. Host Discovery

**Purpose**

Identify whether a system is online.

Typical Questions:

* Is the computer alive?
* Can it be reached?

**Example**

A company owns 500 computers.

Which of them are currently active?

Host Discovery provides the answer.

---

# 2. Port Discovery

Every service communicates using a port number.

Examples:

| Service | Port |
| ------- | ---- |
| HTTP    | 80   |
| HTTPS   | 443  |
| SSH     | 22   |
| FTP     | 21   |

The objective is to identify which ports are open.

---

# 3. Service Discovery

Knowing that Port 80 is open is useful.

Knowing **what is running** on Port 80 is even more useful.

Examples:

* Apache
* Nginx
* IIS
* MySQL
* PostgreSQL

---

# 4. Operating System Discovery

Attackers attempt to identify the operating system.

Examples:

* Windows Server
* Ubuntu Linux
* Red Hat Enterprise Linux
* Kali Linux

Different operating systems have different vulnerabilities.

---

# Active vs Passive Scanning

## Active Scanning

The scanner directly communicates with the target.

Examples:

* Ping
* TCP Connection
* Port Scan

Advantages:

* Accurate information.
* Fast.

Disadvantages:

* Easier to detect.

---

## Passive Scanning

Information is collected without sending packets to the target.

Examples:

* Traffic Monitoring
* Packet Capture
* Log Analysis

Advantages:

* Difficult to detect.

Disadvantages:

* Limited information.

---

# Ethical Use of Network Scanning

Network Scanning should only be performed:

* With written authorization.
* Within the approved scope.
* For security assessment.
* For vulnerability identification.

Unauthorized scanning may violate organizational policies and cyber laws.

---

# Applications of Network Scanning

Network Scanning is widely used for:

* Security Audits
* Asset Discovery
* Vulnerability Assessment
* Network Documentation
* Compliance Verification
* Risk Assessment

---

# Key Takeaways

✔ Scanning follows Footprinting.

✔ Scanning identifies technical details of the target.

✔ Four major scanning categories are:

* Host Discovery
* Port Discovery
* Service Discovery
* Operating System Discovery

✔ Scanning provides the foundation for Enumeration and Vulnerability Assessment.

✔ Ethical hackers perform scanning only with authorization.

---

# Memory Map

```text
Footprinting
      ↓
Scanning
      │
      ├── Host Discovery
      ├── Port Discovery
      ├── Service Discovery
      └── OS Discovery
              ↓
Enumeration
```

---

# University Questions

1. Explain the objectives of Network Scanning.
2. Differentiate Footprinting and Network Scanning.
3. Explain different types of Network Scanning.
4. Explain Network Scanning with suitable examples.
5. Explain the various types of Network Scanning.
6. Discuss the importance of Network Scanning in Ethical Hacking.

---

# Next Lecture

## Host Discovery

We will study:

* Why Host Discovery is required.
* ICMP Ping.
* ARP Discovery.
* TCP Discovery.
* UDP Discovery.
* Practical Host Discovery using scanning tools.
