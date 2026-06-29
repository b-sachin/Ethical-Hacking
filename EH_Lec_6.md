# ETHICAL HACKING (2413CYM5T1)

# Module 1 – Introduction to Ethical Hacking

# Lecture 6

# Social Engineering Footprinting, Footprinting Tools, Countermeasures, Cyber Laws & Security Standards

---

# Module 1 Recap

So far, we have studied:

✔ Information Security

✔ CIA Triad

✔ Hacking & Ethical Hacking

✔ Threat, Vulnerability, Risk & Attack

✔ Traditional Hacking Cycle

✔ Cyber Kill Chain

✔ Reconnaissance

✔ Footprinting

✔ Search Engine Footprinting

✔ Web Service Footprinting

✔ Social Networking Footprinting

✔ Website Footprinting

✔ Email Footprinting

✔ Whois Footprinting

✔ DNS Footprinting

✔ Network Footprinting

---

# Today's Topics

* Footprinting through Social Engineering
* Footprinting Tools
* Footprinting Countermeasures
* Information Security Laws
* Information Security Standards

---

# Social Engineering

## Definition

Social Engineering is the psychological manipulation of people to obtain confidential information or persuade them to perform actions that compromise security.

Instead of attacking computers, attackers exploit **human behavior**.

---

# Why Humans?

Attackers often say:

> **"It is easier to fool a person than to break a well-secured computer."**

Humans may:

* Trust strangers
* Ignore security policies
* Share confidential information
* Click unknown links

Therefore, people are often called the **weakest link** in information security.

---

# Information Collected Through Social Engineering

Attackers attempt to collect:

* Employee names
* Email addresses
* Phone numbers
* Department details
* Organizational hierarchy
* Login procedures
* Security practices

---

# Common Social Engineering Techniques

```text
Social Engineering
        │
 ┌──────┼──────────┐
 │      │          │
Phishing  Pretexting  Tailgating
 │
 ├────────────┐
 │            │
Vishing    Smishing
```

---

# 1. Phishing

The attacker sends fake emails pretending to be a trusted organization.

### Example

> "Your bank account will be blocked.
>
> Click here to verify your account."

Victims unknowingly provide credentials.

---

# 2. Spear Phishing

A targeted phishing attack against a specific individual or organization.

### Example

An email sent specifically to the college Principal requesting urgent payment approval.

---

# 3. Vishing

Voice Phishing.

The attacker calls the victim pretending to be:

* Bank Officer
* IT Support
* Government Official

---

# 4. Smishing

Phishing using SMS.

Example:

> "Your parcel is waiting.
>
> Click the link to confirm delivery."

---

# 5. Pretexting

The attacker creates a believable story to obtain information.

### Example

"I am from the IT Department.
Please share your password so I can fix your account."

---

# 6. Tailgating

The attacker physically follows an authorized employee into a restricted area without authentication.

---

# Real Example

Suppose an attacker wants access to a college network.

Instead of hacking servers, the attacker:

* Visits the campus.
* Pretends to be a printer maintenance engineer.
* Talks to employees.
* Collects names and room numbers.
* Obtains internal contact information.

No software was attacked.

Only people were manipulated.

---

# Footprinting Tools

Ethical hackers use several authorized tools during reconnaissance.

---

# Common Footprinting Tools

| Tool                 | Purpose                                    |
| -------------------- | ------------------------------------------ |
| Google               | Search Engine Footprinting                 |
| Shodan               | Internet-connected Devices                 |
| Whois                | Domain Information                         |
| nslookup             | DNS Information                            |
| dig                  | DNS Queries                                |
| traceroute / tracert | Network Path Discovery                     |
| Nmap                 | Network Discovery & Service Identification |
| Maltego              | OSINT & Relationship Mapping               |
| theHarvester         | Email & Domain Enumeration                 |
| Recon-ng             | OSINT Framework                            |

---

# Example Workflow

```text
Google
     ↓
Website Information
     ↓
Whois
     ↓
DNS Lookup
     ↓
Network Discovery
     ↓
Nmap Scan
```

This represents a typical reconnaissance workflow performed by an ethical hacker.

---

# Footprinting Countermeasures

Organizations should reduce unnecessary information exposure.

---

# Best Practices

✔ Limit public information.

✔ Remove outdated documents.

✔ Hide internal contact details where appropriate.

✔ Secure DNS configuration.

✔ Restrict Whois information where possible.

✔ Disable unauthorized DNS Zone Transfers.

✔ Monitor social media.

✔ Conduct employee awareness training.

✔ Apply security patches regularly.

✔ Implement strong access control.

---

# Information Security Laws

Cybersecurity activities must always comply with applicable laws.

---

# Information Technology Act, 2000 (India)

The Information Technology Act, 2000 is India's primary cyber law.

---

# Objectives

* Legal recognition of electronic records.
* Legal recognition of digital signatures.
* Prevention of cyber crimes.
* Regulation of electronic commerce.
* Protection of digital information.

---

# Common Cyber Crimes Covered

* Unauthorized Access
* Identity Theft
* Hacking
* Data Theft
* Online Fraud
* Cyber Terrorism

---

# Ethical Responsibility

Ethical Hackers must:

✔ Obtain written permission.

✔ Work only within the authorized scope.

✔ Maintain confidentiality.

✔ Report vulnerabilities responsibly.

Unauthorized testing may violate legal provisions.

---

# Information Security Standards

Organizations follow international standards to improve information security.

---

# ISO/IEC 27001

ISO 27001 is an international standard for Information Security Management Systems (ISMS).

---

# Objectives

* Protect Confidentiality
* Protect Integrity
* Protect Availability
* Manage Information Security Risks
* Improve Security Continuously

---

# Benefits

✔ Risk Management

✔ Security Policies

✔ Business Continuity

✔ Customer Trust

✔ Regulatory Compliance

---

# Module 1 Summary

```text
Information Security
          ↓
Hacking
          ↓
Threat
          ↓
Vulnerability
          ↓
Risk
          ↓
Attack
          ↓
Cyber Kill Chain
          ↓
Reconnaissance
          ↓
Footprinting
          ↓
Search Engines
          ↓
Web Services
          ↓
Social Media
          ↓
Website
          ↓
Email
          ↓
Whois
          ↓
DNS
          ↓
Network
          ↓
Social Engineering
          ↓
Countermeasures
```

---

# Key Takeaways

✔ Ethical Hacking begins with Reconnaissance.

✔ Footprinting is the foundation of every cyber attack.

✔ Publicly available information is valuable to attackers.

✔ Human beings are often the weakest security link.

✔ Organizations must implement technical, administrative, and legal controls.

✔ Ethical hackers always operate within legal and authorized boundaries.

---

# University Questions

1. Explain Footprinting Tools and Countermeasures.
2. Explain Social Engineering techniques.
3. Explain ISO 27001.
4. Explain the objectives of the IT Act, 2000.
5. Explain Social Engineering with suitable examples.
6. Explain the Information Technology Act, 2000 and discuss the importance of Information Security Standards.
7. Discuss the complete Footprinting process and methods used during Reconnaissance.

---
