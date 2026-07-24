# Experiment 8
# Denial-of-Service (DoS) Analysis and Mitigation in a Controlled Laboratory Environment

## Aim

To understand the impact of Denial-of-Service (DoS) attacks by generating controlled network traffic in a laboratory environment, monitoring system behavior, analyzing performance degradation, and recommending mitigation techniques.

---

## Course Outcome Mapping

**CO4:** Identify, analyze, and counteract different types of malware, threats, and attacks.

---

## Prerequisites

Students should be familiar with:

- TCP/IP
- ICMP
- HTTP
- Network Monitoring
- Wireshark
- Linux Commands

---

# Theory

A Denial-of-Service (DoS) attack attempts to make a computer system or network service unavailable by exhausting its resources.

Unlike malware, the primary objective of a DoS attack is not data theft but disruption of service availability.

Common DoS attacks include:

- ICMP Flood
- SYN Flood
- UDP Flood
- HTTP Flood
- Slowloris

In this experiment, students will observe the effects of controlled traffic generation against an instructor-authorized laboratory server and analyze the impact using monitoring tools.

---

# Practical Scenario

You are a Cybersecurity Analyst.

Your organization wants to understand how excessive network traffic affects a web server before deploying it in production.

Your task is to:

- Generate controlled traffic.
- Monitor server behavior.
- Analyze network packets.
- Recommend mitigation techniques.

All activities must be performed only within the instructor-provided laboratory environment.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Kali Linux | Traffic Generation |
| Apache/Nginx Test Server | Target |
| Wireshark | Packet Analysis |
| hping3 | Packet Generation |
| Apache Bench (ab) | HTTP Load Testing |
| Task Manager / htop | Resource Monitoring |
| VirtualBox / VMware | Virtualization |

---

# Network Topology

```text
+---------------------+         +----------------------+
|    Kali Linux       |-------> |   Web Server VM      |
| Traffic Generator   |         | (Instructor Target)  |
+---------------------+         +----------------------+
```

---

# Activity 1 – Verify Connectivity

Open Terminal.

Verify connectivity.

```bash
ping <Server-IP>
```

Record the response time.

---

# Activity 2 – Monitor Server Resources

On the server machine:

Linux

```bash
htop
```

or

Windows

```
Task Manager
```

Observe:

- CPU Usage
- Memory Usage
- Network Usage

Record the initial values.

---

# Activity 3 – Capture Network Traffic

Start Wireshark.

Capture traffic on the active network interface.

---

# Activity 4 – Generate Controlled ICMP Traffic

Execute:

```bash
ping <Server-IP>
```

Observe:

- RTT
- Packet Loss

---

# Activity 5 – Generate Controlled HTTP Requests

Execute:

```bash
ab -n 100 -c 10 http://<Server-IP>/
```

Where:

- `-n` → Total Requests
- `-c` → Concurrent Requests

Record:

- Requests Per Second
- Failed Requests
- Time Per Request

---

# Activity 6 – Generate Controlled TCP SYN Traffic

Execute:

```bash
sudo hping3 -S <Server-IP> -p 80 -c 100
```

Observe:

- TCP SYN packets
- Server response

Record observations.

---

# Activity 7 – Analyze Packets

Apply Wireshark filters:

```text
icmp
```

```text
tcp.flags.syn==1
```

```text
http
```

Observe packet behavior.

---

# Activity 8 – Compare Resource Utilization

Complete the table.

| Parameter | Before | During Test | After Test |
|-----------|--------|-------------|------------|
| CPU Usage | | | |
| Memory Usage | | | |
| Network Usage | | | |
| Response Time | | | |

---

# Activity 9 – Identify Mitigation Techniques

Suggest suitable mitigation measures for the observed traffic.

Examples:

- Rate Limiting
- Firewall Rules
- Load Balancer
- CDN
- Web Application Firewall
- IDS/IPS

---

# Investigation Challenges

### Challenge 1

What is the difference between DoS and DDoS?

Answer:

________________________

---

### Challenge 2

Which protocol generated the highest traffic during the experiment?

Answer:

________________________

---

### Challenge 3

How did CPU utilization change during the traffic generation?

_____________________________________________________

---

### Challenge 4

How many packets were captured?

Answer:

________________________

---

### Challenge 5

Which Wireshark filter displays TCP SYN packets?

Answer:

________________________

---

### Challenge 6

Did the server remain responsive during testing?

Yes / No

Explain briefly.

---

### Challenge 7

Suggest three techniques to mitigate DoS attacks.

1.

2.

3.

---

### Challenge 8

Why is DDoS more difficult to defend against than DoS?

_____________________________________________________

---

### Challenge 9

What is the purpose of Apache Bench (`ab`)?

_____________________________________________________

---

### Challenge 10

How can network monitoring help detect DoS attacks?

_____________________________________________________

---

# Observation Table

| Activity | Observation |
|----------|-------------|
| Server IP | |
| Initial CPU Usage | |
| Peak CPU Usage | |
| HTTP Requests | |
| Packets Captured | |
| Average RTT | |
| Packet Loss | |
| Recommended Mitigation | |

---

# Sample DoS Assessment Report

| Parameter | Observation |
|-----------|-------------|
| Analyst | |
| Date | |
| Target Server | |
| Test Performed | |
| Performance Impact | |
| Packet Analysis | |
| Recommendations | |

---

# Result

Successfully generated controlled network traffic in a laboratory environment, observed its impact on server performance, analyzed captured packets using Wireshark, and identified appropriate mitigation strategies for Denial-of-Service attacks.

---

# Precautions

- Perform testing only on instructor-authorized systems.
- Never generate DoS traffic toward public IP addresses.
- Keep packet generation within instructor-defined limits.
- Stop testing immediately if unintended network disruption occurs.
- Follow institutional ethical hacking policies.

---

# Viva Questions

1. What is a DoS attack?
2. Differentiate DoS and DDoS.
3. What is SYN Flood?
4. What is ICMP Flood?
5. What is Apache Bench (`ab`) used for?
6. What is `hping3`?
7. How can Wireshark help analyze DoS attacks?
8. Mention three DoS mitigation techniques.
9. Why is rate limiting effective?
10. What role does a Web Application Firewall (WAF) play in mitigating attacks?

---

# Conclusion

This experiment demonstrated the effects of controlled network traffic on server performance in a safe laboratory environment. Students monitored resource utilization, analyzed network packets, and evaluated practical mitigation strategies, reinforcing the concepts of service availability and defensive cybersecurity practices.