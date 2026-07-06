# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 4

# TCP Three-Way Handshake and Port States

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain why TCP requires a connection.
- Understand the TCP Three-Way Handshake.
- Explain the purpose of SYN, ACK and FIN flags.
- Differentiate between Open, Closed and Filtered Ports.
- Understand why Ethical Hackers study TCP communication.
- Relate the handshake to Port Scanning.

---

# Recap

In the previous lecture, we learned that:

- Every application communicates through a Port.
- One computer can run multiple services.
- Ports identify the destination application.
- Ethical Hackers discover open ports to identify running services.

Before scanning ports, we must understand how TCP communication actually works.

---

# Why Does TCP Need a Connection?

Suppose you call your friend.

Do you immediately start talking?

No.

The conversation usually begins like this:

```
You: Hello?

Friend: Hello.

You: Can you hear me?

Friend: Yes.

Conversation Starts...
```

Only after confirming that both parties are ready does communication begin.

TCP follows exactly the same principle.

Before data transmission,

both computers establish a connection.

This process is called the

> TCP Three-Way Handshake.

---

# What is TCP?

TCP stands for

> Transmission Control Protocol

TCP is a

- Connection-Oriented Protocol
- Reliable Protocol
- Error Checking Protocol

TCP guarantees that

- Data reaches the destination.
- Data arrives in the correct order.
- Lost packets are retransmitted.

Examples of TCP Applications

- HTTP
- HTTPS
- FTP
- SSH
- SMTP

---

# What is the TCP Three-Way Handshake?

The TCP Three-Way Handshake is the process used to establish a reliable connection between a client and a server before data transmission.

It consists of three steps.

---

# TCP Three-Way Handshake

```text
Client                          Server

   SYN  ----------------------->

        <-------------------  SYN + ACK

   ACK  ----------------------->

Connection Established
```

---

# Step 1 – SYN

The Client sends a

```
SYN
```

packet.

Meaning

> "I want to establish a connection."

Example

A browser wants to connect to

```
www.google.com

Port 443
```

The browser sends

```
SYN
```

to Google's web server.

---

# Step 2 – SYN + ACK

The Server replies

```
SYN + ACK
```

Meaning

> "I received your request and I am ready."

The server also asks

> "Can you receive my packets?"

---

# Step 3 – ACK

The Client replies

```
ACK
```

Meaning

> "Yes, I received your response."

Now,

both systems know

communication is possible.

The connection is established.

---

# Visual Representation

```text
Client                       Server

SYN
----------------------------->

        SYN + ACK
<-----------------------------

ACK
----------------------------->

===========

Connection Ready

===========

Data Transfer Begins
```

---

# Why Three Steps?

Students often ask

"Why not one step?"

Because both systems must verify

- Sender is Ready
- Receiver is Ready

The handshake confirms that both parties can send and receive data reliably.

---

# Real World Example

Suppose you visit

```
https://www.amazon.in
```

Your browser performs

```
TCP Handshake

↓

HTTPS Connection

↓

SSL/TLS Negotiation

↓

Website Opens
```

Without the TCP Handshake,

the browser cannot start communication.

---

# Practical Demonstration

Display all TCP connections.

Windows

```cmd
netstat -an
```

Linux

```bash
netstat -ant
```

or

```bash
ss -ant
```

---

# Sample Output

```text
Proto Local Address

TCP

192.168.10.5:51234

192.168.10.25:443

ESTABLISHED
```

---

# Interpretation

This means

```
Your Computer

↓

Temporary Port

51234

↓

Connected to

192.168.10.25

↓

HTTPS

Port 443
```

---

# TCP Flags

TCP communication is controlled using Flags.

The important flags are

| Flag | Meaning |
|------|----------|
| SYN | Start Connection |
| ACK | Acknowledgement |
| FIN | Close Connection |
| RST | Reset Connection |
| PSH | Push Data Immediately |
| URG | Urgent Data |

Students should remember these flags because Nmap uses them extensively.

---

# Closing a TCP Connection

Communication does not continue forever.

The connection must also be closed.

TCP uses

```
FIN
```

packets.

Example

```
Browser

↓

Website Loaded

↓

FIN

↓

Connection Closed
```

---

# Port States

When scanning,

Nmap classifies ports into different states.

The three most important states are

- Open
- Closed
- Filtered

---

# Open Port

An Open Port means

- Service Running
- Application Listening
- Connection Accepted

Example

```
Port 80

↓

Apache Running
```

or

```
Port 443

↓

HTTPS Running
```

These ports are attractive targets for attackers because a service is actively accepting connections.

---

# Closed Port

A Closed Port means

- No application is listening.
- The operating system responds with a TCP RST packet.

Example

```
Port 23

↓

Telnet Service Stopped
```

The host is alive,

but that service is not available.

---

# Filtered Port

A Filtered Port means

A Firewall or Packet Filter blocks communication.

The scanner cannot determine whether the port is open or closed because no useful response is received.

Example

```
Internet

↓

Firewall

↓

Server
```

The Firewall silently drops packets.

---

# Comparison of Port States

| Open | Closed | Filtered |
|-------|---------|-----------|
| Service Running | No Service | Firewall Blocking |
| Connection Accepted | RST Returned | No Response |
| High Attack Surface | Low Attack Surface | Unknown State |

---

# Why is TCP Handshake Important in Ethical Hacking?

Port scanning techniques are based on observing how a target responds during the handshake.

Example

```
SYN

↓

SYN + ACK

↓

Port Open
```

```
SYN

↓

RST

↓

Port Closed
```

```
SYN

↓

No Response

↓

Filtered
```

This simple behaviour forms the basis of many Nmap scanning techniques.

---

# Quick Revision

✔ TCP is Connection-Oriented.

✔ TCP uses a Three-Way Handshake.

✔ SYN starts communication.

✔ SYN + ACK confirms readiness.

✔ ACK establishes the connection.

✔ Open Ports accept connections.

✔ Closed Ports return RST.

✔ Filtered Ports are protected by Firewalls.

---

# University Questions

1. Explain the TCP Three-Way Handshake.
2. Differentiate Open, Closed and Filtered Ports.
3. Explain the TCP Three-Way Handshake with a suitable diagram.
4. Explain various Port States with examples.

---

# Next Lecture

## Port Scanning Techniques

Topics to be covered:

- Connect Scan
- SYN Scan (Half Open Scan)
- FIN Scan
- NULL Scan
- XMAS Scan
- UDP Scan
- Idle Scan
- Introduction to Nmap Port Scanning