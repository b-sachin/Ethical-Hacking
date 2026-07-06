# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 3

# Computer Ports and TCP/IP Fundamentals

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain what a Port is.
- Differentiate IP Address and Port Number.
- Understand Socket Address.
- Explain why Port Numbers are required.
- Differentiate TCP and UDP.
- Understand Client-Server Communication.

---

# Recap

In the previous lecture we learned how to identify live hosts using:

- ICMP
- ARP
- TCP
- UDP

Once a host is confirmed to be alive,

the next question is:

> **Which services are running on the host?**

To answer this,

we first need to understand **Ports**.

---

# Why Do We Need Ports?

Imagine a college building.

The college has only one postal address.

```
XYZ College
Mumbai
```

But inside the college there are many departments.

- Principal Office
- Accounts
- Library
- IT Department
- Examination Cell

How does a courier know where to deliver a letter?

The building address alone is not sufficient.

The department number is also required.

Similarly,

A computer has one IP Address

but many applications.

Ports help the operating system decide

which application should receive the incoming data.

---

# IP Address vs Port Number

Think of it this way.

```
House Address
        =
IP Address

Room Number
        =
Port Number
```

Without the room number,

the courier reaches the building

but cannot identify the correct room.

Similarly,

without the port number,

data reaches the computer

but not the correct application.

---

# What is a Port?

## Definition

A Port is a **16-bit logical communication endpoint** used by the Transport Layer (TCP or UDP) to identify a specific application or service running on a computer.

Since a port is 16 bits,

the total number of possible ports is

```
2^16 = 65,536

Port Numbers

0 to 65535
```

---

# Why is a Port Called a Logical Address?

A Port has

- No physical existence.
- No hardware.
- No cable.

It is simply a number maintained by the operating system.

Therefore,

it is called a

> Logical Communication Endpoint.

---

# Real World Example

Suppose you open your browser

and type

```
www.google.com
```

Your computer connects to

```
Google IP Address

+

Port 443
```

because HTTPS uses

```
Port 443
```

If you open Gmail,

YouTube,

or Google Maps,

all use different sessions,

but the destination port remains

```
443
```

---

# Client Server Communication

```
Browser

     │

     │ Request

     ▼

Google Server

Port 443

     │

     │ Response

     ▼

Browser
```

Notice

The browser communicates with

the **HTTPS Service**

not the operating system.

The Port Number tells the operating system

which application should receive the data.

---

# Socket

A Socket uniquely identifies a communication.

It consists of

```
IP Address

+

Port Number
```

Example

```
192.168.10.25:80
```

This means

Computer

```
192.168.10.25
```

Service

```
HTTP
```

---

# Practical Demonstration

Windows

```cmd
netstat -ano
```

Linux

```bash
netstat -tuln
```

or

```bash
ss -tuln
```

---

# Sample Output

```text
Proto Local Address

TCP 0.0.0.0:80

TCP 0.0.0.0:22

TCP 0.0.0.0:443

UDP 0.0.0.0:53
```

---

# Interpretation

The system currently has

- HTTP Running
- SSH Running
- HTTPS Running
- DNS Running

Each service is listening on a different Port Number.

---

# Types of Port Numbers

Ports are divided into three categories.

```
0 — 1023

Well Known Ports

----------------------

1024 — 49151

Registered Ports

----------------------

49152 — 65535

Dynamic / Ephemeral Ports
```

---

# Well Known Ports

These are reserved for common services.

| Port | Service |
|------|----------|
| 20 | FTP Data |
| 21 | FTP |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 110 | POP3 |
| 143 | IMAP |
| 443 | HTTPS |

Students should remember these ports for exams.

---

# Registered Ports

Used by

- Database Servers
- Enterprise Applications
- Vendor Applications

Examples

```
3306

MySQL

5432

PostgreSQL
```

---

# Dynamic Ports

Temporary ports assigned automatically.

Used by

- Browser
- Email Client
- FTP Client

These ports change every session.

---

# Why Do Ethical Hackers Study Ports?

Because every running service

creates an opportunity for attack.

For example

```
Port 21 Open

↓

FTP Running

↓

Anonymous Login Possible?
```

```
Port 22 Open

↓

SSH Running

↓

Weak Password?
```

```
Port 80 Open

↓

Website Running

↓

SQL Injection?
```

Thus,

Port Discovery tells us

**what can potentially be attacked**.

---

# Quick Revision

✔ Every computer has one IP Address.

✔ One computer can run many services.

✔ Ports identify applications.

✔ Port numbers range from

0 to 65535.

✔ Socket = IP Address + Port Number.

✔ Ethical Hackers study ports to identify running services.

---

# University Questions

1. Explain Port Numbers with suitable examples.

2. Differentiate IP Address and Port Number.

3. Explain Computer Ports and their classification with suitable examples.

---

# Next Lecture

TCP Three-Way Handshake

Open, Closed and Filtered Ports

Port Scanning Fundamentals
