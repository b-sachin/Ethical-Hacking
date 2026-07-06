# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 7

# Service Discovery and Banner Grabbing

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain the concept of Service Discovery.
- Differentiate between Port Discovery and Service Discovery.
- Understand Banner Grabbing.
- Perform Service Version Detection using Nmap.
- Perform Banner Grabbing using Telnet, Netcat and Curl.
- Interpret service information for vulnerability assessment.

---

# Recap

In previous lectures we learned:

✔ Host Discovery

✔ Port Discovery

✔ TCP Handshake

✔ Port Scanning Techniques

Now suppose Nmap reports

```text
80/tcp open
```

Does that mean

Apache?

Nginx?

IIS?

Tomcat?

Python Server?

No.

We only know

Port 80 is open.

We still need to identify

**which application is running.**

---

# What is Service Discovery?

## Definition

**Service Discovery** is the process of identifying the application or service running on an open port.

It tells us:

- Service Name
- Software Version
- Sometimes Operating System
- Sometimes Configuration Information

---

# Real World Analogy

Imagine a building with many rooms.

Port Scanning tells you

```
Room No. 101

Door is Open
```

Service Discovery tells you

```
Room 101

Principal Office
```

Similarly,

Port Scanning tells us

```
Port 80 Open
```

Service Discovery tells us

```
Apache HTTP Server

Version 2.4.57
```

---

# Why is Service Discovery Important?

Suppose

```
Port 22

Open
```

Questions

- SSH?
- OpenSSH?
- Dropbear SSH?
- Cisco SSH?

Different software versions may contain different vulnerabilities.

Therefore,

identifying the service is extremely important.

---

# Port Discovery vs Service Discovery

| Port Discovery | Service Discovery |
|----------------|------------------|
| Finds Open Ports | Finds Running Services |
| Uses TCP/UDP Responses | Uses Application Responses |
| Faster | Slightly Slower |
| Example: Port 80 Open | Example: Apache 2.4.57 |

---

# How Service Discovery Works

```text
Scanner

↓

Connect to Port

↓

Receive Service Banner

↓

Identify Application

↓

Determine Version
```

---

# What is a Banner?

A **Banner** is information returned by a service when a connection is established.

A banner may contain:

- Software Name
- Version Number
- Operating System
- Hostname
- Protocol Information

---

# Example Banner

```text
220 FTP Server Ready

vsFTPd 3.0.5
```

From this banner,

we immediately know

- FTP Service
- Software = vsFTPd
- Version = 3.0.5

---

# Banner Grabbing

## Definition

**Banner Grabbing** is the technique of collecting information about a service by reading its banner.

Ethical Hackers use banner grabbing to identify:

- Software
- Version
- Configuration
- Possible Vulnerabilities

---

# Types of Banner Grabbing

There are two methods.

```text
Banner Grabbing

│

├── Active Banner Grabbing

└── Passive Banner Grabbing
```

---

# Active Banner Grabbing

The attacker directly connects to the target service.

Examples

- Telnet
- Netcat
- Nmap
- Curl

Advantages

✔ Accurate

✔ Fast

Limitations

- Generates network traffic.
- May be logged.

---

# Passive Banner Grabbing

The attacker observes network traffic without interacting with the target.

Example Tools

- Wireshark
- Tcpdump

Advantages

✔ Difficult to Detect

Limitations

- Requires access to network traffic.

---

# Service Discovery using Nmap

Nmap performs Service Detection using

```
-sV
```

---

# Practical Demonstration

## Command

```bash
sudo nmap -sV 192.168.10.25
```

---

## Explanation

```
-sV
```

means

> Version Detection

Nmap communicates with open services and compares responses against its service fingerprint database.

---

# Sample Output

```text
PORT      STATE SERVICE VERSION

22/tcp    open  ssh     OpenSSH 9.2

80/tcp    open  http    Apache httpd 2.4.57

443/tcp   open  https   Apache httpd 2.4.57
```

---

# Interpretation

From the output we know

| Port | Service | Version |
|------|----------|----------|
| 22 | OpenSSH | 9.2 |
| 80 | Apache HTTP | 2.4.57 |
| 443 | Apache HTTPS | 2.4.57 |

Notice

Earlier we only knew

```
Port 80 Open
```

Now we know

```
Apache HTTP Server

Version 2.4.57
```

---

# Banner Grabbing using Telnet

Many services immediately display their banner after a connection is established.

---

## Command

```bash
telnet 192.168.10.25 25
```

---

## Sample Output

```text
220 mail.college.edu

ESMTP Postfix
```

---

## Interpretation

The target is running

- SMTP
- Postfix Mail Server

---

# Banner Grabbing using Netcat (nc)

Netcat is one of the most popular networking tools used by Ethical Hackers.

---

## Command

```bash
nc 192.168.10.25 80
```

After connecting,

type

```text
HEAD / HTTP/1.0
```

Press Enter twice.

---

## Sample Output

```text
HTTP/1.1 200 OK

Server: Apache/2.4.57

Content-Type: text/html
```

---

## Interpretation

Banner reveals

- Apache Server
- Version 2.4.57

---

# Banner Grabbing using Curl

Curl is commonly used for HTTP and HTTPS services.

---

## Command

```bash
curl -I http://192.168.10.25
```

---

## Sample Output

```text
HTTP/1.1 200 OK

Server: Apache/2.4.57

Date:

Content-Type: text/html
```

---

## Interpretation

The

```
Server:
```

header reveals

the web server software.

---

# Banner Grabbing using Netcat (FTP Example)

```bash
nc 192.168.10.25 21
```

---

## Sample Output

```text
220 vsFTPd 3.0.5 ready.
```

Immediately,

the FTP software and version become known.

---

# Common Services and Their Default Ports

| Port | Service | Protocol |
|------|----------|----------|
| 21 | FTP | TCP |
| 22 | SSH | TCP |
| 23 | Telnet | TCP |
| 25 | SMTP | TCP |
| 53 | DNS | UDP |
| 80 | HTTP | TCP |
| 110 | POP3 | TCP |
| 143 | IMAP | TCP |
| 443 | HTTPS | TCP |
| 3306 | MySQL | TCP |

Students should memorize these ports.

---

# Why Version Detection Matters

Suppose

```
Apache

Version 2.2
```

Security researchers know

Apache 2.2 has multiple known vulnerabilities.

Therefore,

finding the version helps Ethical Hackers determine

whether the software requires updates.

---

# Ethical Considerations

Banner Grabbing should only be performed

- During authorized penetration testing.
- During security audits.
- On systems where permission has been granted.

Unauthorized information gathering may violate organizational policies and applicable laws.

---

# Important Commands Summary

| Command | Purpose |
|----------|---------|
| `nmap -sV target` | Service Version Detection |
| `telnet IP port` | Read Service Banner |
| `nc IP port` | Banner Grabbing |
| `curl -I URL` | Retrieve HTTP Headers |

---

# Quick Revision

✔ Service Discovery identifies running applications.

✔ Banner Grabbing collects service information.

✔ `-sV` enables Version Detection in Nmap.

✔ Telnet, Netcat and Curl can retrieve banners.

✔ Service versions help identify potential vulnerabilities.

---

# University Questions

1. Explain Banner Grabbing with examples.
2. Differentiate Active and Passive Banner Grabbing.
3. Explain Service Discovery using Nmap.
4. Explain Banner Grabbing techniques with suitable examples.
5. Explain Service Discovery and Version Detection using Nmap.
6. Compare Port Discovery and Service Discovery.

---

# Next Lecture

## Operating System Discovery (OS Fingerprinting)

Topics to be covered:

- What is OS Fingerprinting?
- Active vs Passive OS Detection
- TCP/IP Stack Fingerprinting
- TTL, Window Size, TCP Options
- Nmap OS Detection (`-O`)
- Practical Demonstration