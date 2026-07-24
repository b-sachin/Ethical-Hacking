# Experiment 9
# Session Hijacking and Network Traffic Analysis using Bettercap and Wireshark

## Aim

To understand session hijacking techniques by performing ARP spoofing and network traffic analysis in an isolated laboratory environment using Bettercap and Wireshark, and to study methods used to protect user sessions.

---

## Course Outcome Mapping

**CO4:** Identify, analyze, and counteract different types of malware, threats and attacks.

---

## Prerequisites

Students should be familiar with:

- TCP/IP
- HTTP and HTTPS
- ARP Protocol
- Cookies
- Session Management
- Wireshark Basics

---

# Theory

A session is established after successful user authentication.

Instead of repeatedly asking the user to log in, the web server assigns a unique **Session ID**.

Example:

```
Client Login

↓

Username + Password

↓

Server Authentication

↓

Session ID Created

↓

Client Stores Session Cookie

↓

Subsequent Requests use Session Cookie
```

If an attacker steals the session cookie, they may gain unauthorized access without knowing the user's password.

This attack is called **Session Hijacking**.

Common techniques include:

- Session Sniffing
- Session Sidejacking
- ARP Spoofing
- Man-in-the-Middle (MITM)
- Session Fixation

---

# Practical Scenario

You are working as a Security Analyst.

The organization wants to understand how insecure network communication can expose user sessions.

Your task is to observe network traffic, capture session-related packets in a controlled environment, and recommend countermeasures to protect user sessions.

All activities must be performed only inside the instructor-provided laboratory network.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Kali Linux | Operating System |
| Bettercap | ARP Spoofing Demonstration |
| Wireshark | Packet Analysis |
| Firefox / Chrome | Web Browser |
| VirtualBox / VMware | Virtualization |

---

# Network Topology

```text
+--------------------+
|    Kali Linux      |
| Bettercap Client   |
+---------+----------+
          |
-----------------------------
          |
+---------+----------+
|  Victim Machine     |
+--------------------+
          |
+--------------------+
| Router / Gateway   |
+--------------------+
```

---

# Activity 1 – Verify Network Connectivity

Open Terminal.

Verify connectivity.

```bash
ping <Victim-IP>
```

Record the response.

---

# Activity 2 – Start Wireshark

Launch Wireshark.

Select the active network interface.

Start packet capture.

---

# Activity 3 – Identify ARP Traffic

Apply the filter:

```text
arp
```

Observe:

- ARP Request
- ARP Reply
- Source MAC Address
- Destination MAC Address

Record your observations.

---

# Activity 4 – Start Bettercap

Open Terminal.

Execute:

```bash
sudo bettercap -iface eth0
```

Replace **eth0** with the appropriate network interface if necessary.

---

# Activity 5 – Discover Network Devices

Inside Bettercap, execute:

```text
net.probe on
```

Display discovered hosts.

```text
net.show
```

Record:

- Gateway IP
- Victim IP
- MAC Addresses

---

# Activity 6 – Demonstrate ARP Spoofing

Enable ARP spoofing for the instructor-provided target.

```text
set arp.spoof.targets <Victim-IP>
```

```text
arp.spoof on
```

Observe network behavior.

**Note:** Perform only in the isolated laboratory environment.

---

# Activity 7 – Observe HTTP Traffic

Apply the following Wireshark filter:

```text
http
```

Observe:

- HTTP Requests
- HTTP Responses
- Cookies (if available)

Record your observations.

---

# Activity 8 – Compare HTTP and HTTPS

Visit one HTTP website and one HTTPS website (or instructor-provided demo).

Observe:

| Parameter | HTTP | HTTPS |
|-----------|------|-------|
| Encryption | | |
| Cookies Visible | | |
| URL Encrypted | | |
| Credentials Protected | | |

---

# Activity 9 – Analyze Session Cookies

If HTTP cookies are visible, identify:

- Cookie Name
- Session ID
- Domain
- Path

**Do not reuse or attempt to exploit any captured cookies.**

---

# Activity 10 – Stop Capture

Stop Wireshark.

Save the capture file as:

```
session_analysis.pcapng
```

---

# Investigation Challenges

### Challenge 1

What is a Session ID?

Answer:

______________________

---

### Challenge 2

Which protocol is more secure for session management?

- HTTP
- HTTPS

Explain briefly.

---

### Challenge 3

What information can be obtained from HTTP packets?

_____________________________________________________

---

### Challenge 4

What is ARP Spoofing?

_____________________________________________________

---

### Challenge 5

Which Wireshark filter displays HTTP packets?

Answer:

______________________

---

### Challenge 6

Why are HTTPS session cookies difficult to capture?

_____________________________________________________

---

### Challenge 7

Mention three countermeasures against Session Hijacking.

1.

2.

3.

---

### Challenge 8

Why should Secure and HttpOnly cookie attributes be enabled?

_____________________________________________________

---

### Challenge 9

Differentiate Session Hijacking and Session Fixation.

_____________________________________________________

---

### Challenge 10

Suggest five best practices for secure session management.

1.

2.

3.

4.

5.

---

# Observation Table

| Activity | Observation |
|-----------|-------------|
| Victim IP | |
| Gateway IP | |
| ARP Packets Observed | |
| HTTP Requests | |
| HTTPS Requests | |
| Cookies Observed | |
| Session ID Visible | Yes / No |
| Capture File Name | |

---

# Sample Session Security Assessment Report

| Parameter | Observation |
|-----------|-------------|
| Analyst | |
| Date | |
| Network Tested | |
| Traffic Captured | |
| HTTP Sessions | |
| HTTPS Sessions | |
| Security Risks Identified | |
| Recommendations | |

---

# Result

Successfully analyzed network traffic and demonstrated session hijacking concepts in a controlled laboratory environment. HTTP and HTTPS communications were compared, ARP spoofing behavior was observed, session-related information was analyzed, and suitable security recommendations were documented.

---

# Precautions

- Perform experiments only on instructor-authorized laboratory systems.
- Never intercept traffic on public or production networks.
- Use only isolated virtual laboratory environments.
- Do not reuse captured session cookies.
- Stop ARP spoofing immediately after completing the demonstration.
- Follow institutional ethical hacking policies.

---

# Viva Questions

1. What is Session Hijacking?
2. What is a Session Cookie?
3. What is ARP Spoofing?
4. What is Bettercap?
5. What is Wireshark?
6. Differentiate HTTP and HTTPS.
7. What are Secure and HttpOnly cookies?
8. What is Session Fixation?
9. How does HTTPS prevent session hijacking?
10. Mention five countermeasures against Session Hijacking.

---

# Conclusion

This experiment introduced students to session management and session hijacking concepts through controlled demonstrations using Bettercap and Wireshark. Students observed ARP traffic, analyzed HTTP and HTTPS communication, examined session-related information, and learned practical techniques to secure web sessions against interception and misuse.