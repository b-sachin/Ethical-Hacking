# ETHICAL HACKING (2413CYM5T1)

# Module 2 – Monitoring

# Lecture 9

# Scanning Beyond IDS & Firewalls | Security Audits | Risk Management

**Course Outcome:** CO2

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain the purpose of Firewalls, IDS, and IPS.
- Understand how network scans are detected.
- Explain the concept of Firewall and IDS evasion (conceptually).
- Describe Security Audits.
- Explain Risk Management and Risk Assessment.
- Differentiate Vulnerability Assessment and Penetration Testing.

---

# Recap

Until now we learned

```
Host Discovery

↓

Port Discovery

↓

Service Discovery

↓

OS Fingerprinting
```

The next question is

> Can an organization detect that someone is scanning its network?

The answer is **Yes.**

Organizations use

- Firewalls
- IDS
- IPS
- SIEM Systems

to monitor and detect suspicious activities.

---

# What is a Firewall?

## Definition

A **Firewall** is a security device (hardware or software) that monitors and controls incoming and outgoing network traffic based on predefined security rules.

It acts as a barrier between a trusted network and an untrusted network.

---

# Real World Analogy

Imagine the entrance gate of a college.

Every visitor is checked before entering.

- Student → Allowed
- Faculty → Allowed
- Unknown Person → Verified
- Suspicious Person → Denied

A Firewall performs a similar function for network traffic.

---

# Firewall Working

```text
Internet

      │

      ▼

+------------------+
|    FIREWALL      |
+------------------+

      │

      ▼

Internal Network
```

The Firewall examines every packet before allowing or blocking it.

---

# Types of Firewalls

## 1. Packet Filtering Firewall

- Examines source IP, destination IP, protocol, and port number.
- Makes decisions based on predefined rules.
- Fast but provides basic protection.

---

## 2. Stateful Inspection Firewall

Tracks the state of active connections.

It understands whether a packet belongs to an existing session.

More secure than simple packet filtering.

---

## 3. Application Layer Firewall (Proxy Firewall)

Operates at the Application Layer.

Can inspect HTTP, HTTPS, FTP, SMTP, and other application traffic.

Provides deeper inspection.

---

## 4. Next-Generation Firewall (NGFW)

Modern firewalls combine:

- Packet Filtering
- Stateful Inspection
- Deep Packet Inspection
- Intrusion Prevention
- Malware Detection
- Application Awareness

Examples:

- Palo Alto
- Fortinet
- Cisco Firepower

---

# What is IDS?

IDS stands for

> Intrusion Detection System

An IDS monitors network traffic and generates alerts when suspicious activity is detected.

It does **not** block the traffic.

---

# Working of IDS

```text
Network Traffic

      │

      ▼

IDS

      │

      ▼

Alert Generated

↓

Administrator Investigates
```

---

# What is IPS?

IPS stands for

> Intrusion Prevention System

Unlike IDS,

an IPS can automatically

- Block
- Drop
- Reject

malicious traffic.

---

# IDS vs IPS

| IDS | IPS |
|------|------|
| Detects attacks | Detects and blocks attacks |
| Generates alerts | Takes preventive action |
| Passive | Active |
| Monitoring | Protection |

---

# How are Port Scans Detected?

A scanner may send requests to many ports within a short period.

Example:

```text
Port 20

↓

Port 21

↓

Port 22

↓

Port 23

↓

Port 80

↓

Port 443
```

A firewall or IDS may recognize this pattern as scanning behavior and generate an alert.

---

# Why Do Ethical Hackers Learn About Scan Detection?

During an authorized penetration test,

understanding how defensive systems react helps security teams:

- Tune IDS rules.
- Reduce false positives.
- Improve firewall policies.
- Validate monitoring effectiveness.

The objective is to strengthen defenses, not bypass them.

---

# Common Defensive Measures

Organizations can reduce scanning risks by:

- Blocking unused ports.
- Enabling firewall logging.
- Updating IDS/IPS signatures.
- Restricting administrative services.
- Segmenting networks.
- Monitoring unusual traffic patterns.

---

# What is a Security Audit?

## Definition

A **Security Audit** is a systematic examination of an organization's information systems to verify whether security controls are properly implemented and effective.

---

# Objectives of a Security Audit

- Identify security weaknesses.
- Verify compliance with policies.
- Check configuration errors.
- Ensure data protection.
- Recommend improvements.

---

# Security Audit Process

```text
Planning

↓

Information Gathering

↓

Assessment

↓

Report Generation

↓

Recommendations

↓

Follow-up
```

---

# Types of Security Audits

- Internal Audit
- External Audit
- Compliance Audit
- Technical Security Audit
- Network Security Audit

---

# What is Risk?

## Definition

Risk is the possibility that a threat will exploit a vulnerability and cause damage to an asset.

---

# Risk Components

```text
Asset

↓

Threat

↓

Vulnerability

↓

Risk
```

---

# Example

Asset

```
College ERP Server
```

Threat

```
Ransomware
```

Vulnerability

```
Outdated Operating System
```

Result

```
Risk of Data Loss
```

---

# What is Risk Assessment?

Risk Assessment is the process of:

- Identifying assets.
- Identifying threats.
- Identifying vulnerabilities.
- Estimating the impact.
- Prioritizing risks.

---

# Risk Assessment Process

```text
Identify Assets

↓

Identify Threats

↓

Identify Vulnerabilities

↓

Analyze Risk

↓

Prioritize Risk

↓

Apply Controls
```

---

# Risk Matrix

A common way to prioritize risks is by considering:

- Likelihood
- Impact

| Likelihood | Impact | Risk Level |
|------------|--------|------------|
| Low | Low | Low |
| High | Low | Medium |
| Low | High | Medium |
| High | High | Critical |

This helps organizations decide which issues should be addressed first.

---

# Vulnerability Assessment vs Penetration Testing

| Vulnerability Assessment | Penetration Testing |
|--------------------------|---------------------|
| Identifies vulnerabilities | Attempts to exploit vulnerabilities (with authorization) |
| Focuses on discovery | Focuses on validation |
| Lower risk | Higher risk |
| Produces a list of weaknesses | Demonstrates real-world impact |

---

# Real World Example

A college wants to assess the security of its website.

Security team performs:

- Host Discovery
- Port Scanning
- Service Discovery
- Vulnerability Assessment

Audit Report:

- SSH enabled
- Apache version outdated
- Weak TLS configuration

Recommendations:

- Update Apache.
- Disable unused services.
- Enforce strong TLS settings.
- Enable regular security monitoring.

---

# Ethical Responsibilities

Ethical Hackers must:

- Obtain written authorization.
- Follow organizational policies.
- Protect confidential information.
- Report findings responsibly.
- Avoid disrupting normal operations.

---

# Quick Revision

✔ Firewall controls network traffic.

✔ IDS detects attacks.

✔ IPS detects and blocks attacks.

✔ Security Audits evaluate security controls.

✔ Risk = Threat exploiting a Vulnerability affecting an Asset.

✔ Risk Assessment helps prioritize security improvements.

✔ Vulnerability Assessment identifies weaknesses, while Penetration Testing validates their impact.

---

# University Questions

1. Explain different types of Firewalls.
2. Differentiate IDS and IPS.
3. Explain the Risk Assessment process.
4. Explain the Security Audit process.
5. Explain Firewalls, IDS, and IPS with suitable diagrams.
6. Explain the Security Audit process and its objectives.
7. Discuss Risk Management with a suitable example.
8. Differentiate Vulnerability Assessment and Penetration Testing.

---

# Module 2 Summary

You have now learned:

- Network Scanning Concepts
- Host Discovery
- TCP/IP Fundamentals
- Port Scanning
- Service Discovery
- Banner Grabbing
- OS Fingerprinting
- Firewalls
- IDS & IPS
- Security Audits
- Risk Management

These concepts form the **Information Gathering and Monitoring** phase of an Ethical Hacking engagement.

---

# Next Module (Module 3)

**Enumeration, Vulnerability Assessment & System Hacking**