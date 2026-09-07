# ETHICAL HACKING (2413CYM5T1)

# Module 4 – Malware, Sniffing & Social Engineering

# Lecture 3 – Social Engineering

**Course Outcome:** CO4  
**Duration:** 1 Hour

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain the concept of Social Engineering.
- Identify common Social Engineering techniques.
- Explain Insider Threats.
- Understand Social-Network Impersonation.
- Explain Identity Theft.
- Suggest suitable countermeasures against Social Engineering attacks.

---

# 1. Introduction to Social Engineering

## Definition

**Social Engineering** is the practice of manipulating people into revealing information, performing an action, or providing unauthorized access.

Instead of directly attacking a technical system, the attacker targets the **human element**.

### Key Idea

> **Social Engineering attacks people rather than systems.**

---

# 2. Why is Social Engineering Effective?

Organizations may have:

- Firewalls
- Antivirus
- Intrusion Detection Systems
- Strong passwords
- Encryption

But an attacker may bypass these controls by **tricking an authorized person**.

### Common Human Factors Exploited

- Trust
- Fear
- Urgency
- Curiosity
- Authority
- Greed

---

# 3. Social Engineering Attack Flow

```text
Target Identification
        ↓
Building Trust
        ↓
Manipulation
        ↓
Victim Performs an Action
        ↓
Information / Access Obtained
```

---

# 4. Common Social Engineering Techniques

```text
                 Social Engineering
                         │
       ┌─────────┬───────┼────────┬─────────┐
       ↓         ↓       ↓        ↓         ↓
   Phishing   Vishing  Smishing  Baiting  Pretexting
       │
       ├── Spear Phishing
       └── Whaling

   Other Techniques
       ├── Quid Pro Quo
       └── Tailgating
```

---

# 5. Phishing

## Definition

**Phishing** is a fraudulent attempt to trick users into revealing sensitive information or performing an unsafe action, commonly through deceptive messages or websites.

### Common Characteristics

- Fake sender identity
- Urgent message
- Suspicious link
- Request for sensitive information
- Fake login page
- Unexpected attachment

### Example

A user receives a message claiming:

> "Your account will be blocked today. Verify your account immediately."

The message contains a suspicious link.

---

# 6. Spear Phishing

**Spear Phishing** is a targeted phishing attack directed at a specific person or organization.

Unlike general phishing, the attacker researches the target before sending the message.

### Example

An attacker sends a customized message pretending to be the victim's manager.

```text
General Phishing
       ↓
Large number of users
       ↓
Generic message

Spear Phishing
       ↓
Specific target
       ↓
Customized message
```

---

# 7. Whaling

**Whaling** is a targeted phishing attack against a high-level executive or important individual.

### Typical Targets

- CEO
- CFO
- Director
- Senior Manager
- Administrator

### Example

An attacker impersonates a senior executive and attempts to convince an employee to perform an unauthorized action.

---

# 8. Vishing

**Vishing = Voice + Phishing**

Vishing uses **voice communication**, usually phone calls, to manipulate victims.

### Example

An attacker pretends to be:

- Bank representative
- IT support
- Government official
- Company employee

The attacker attempts to obtain sensitive information.

---

# 9. Smishing

**Smishing = SMS + Phishing**

Smishing uses SMS or text messages to deceive users.

### Example

A user receives:

```text
"Your delivery could not be completed.
Please verify your information."
```

The message may contain a suspicious link.

---

# 10. Pretexting

**Pretexting** involves creating a false story or situation to obtain information or influence a victim.

The attacker creates a believable **pretext**.

### Example

An attacker pretends to be an employee from the IT department and asks a user to confirm account details.

### Key Idea

```text
False Identity
      +
Believable Story
      ↓
Victim Trusts Attacker
```

---

# 11. Baiting

**Baiting** uses something attractive or interesting to tempt the victim into performing an unsafe action.

### Examples

- Free software
- Fake rewards
- Attractive downloads
- Unknown USB device

### Example

An unknown USB drive is labeled:

```text
"Salary_Information"
```

A curious employee connects it to a computer.

---

# 12. Quid Pro Quo

**Quid Pro Quo** means **"something in return for something."**

The attacker offers a benefit or service in exchange for information or an action.

### Example

An attacker pretends to provide technical support and asks the user to share information as part of the fake service.

---

# 13. Tailgating

**Tailgating** is a physical Social Engineering technique where an unauthorized person follows an authorized person into a restricted area.

### Example

```text
Employee
   ↓
Opens Secure Door
   ↓
Attacker follows
   ↓
Restricted Area
```

### Countermeasures

- Access cards
- Security guards
- Visitor identification
- Security awareness
- Mantrap / controlled entry systems

---

# 14. Insider Threat

An **Insider Threat** occurs when a person with legitimate access misuses that access or unintentionally causes a security incident.

### Types

| Type | Description |
|------|-------------|
| Malicious Insider | Intentionally causes harm |
| Negligent Insider | Accidentally causes a security incident |
| Compromised Insider | Attacker uses a legitimate user's account |

---

# 15. Insider Threat Example

Consider an employee who has access to confidential company data.

```text
Employee
   │
   ├── Legitimate Access
   │
   ↓
Sensitive Information
   │
   ├── Misuse
   └── Accidental Exposure
```

### Possible Impact

- Data leakage
- Financial loss
- Intellectual property theft
- Reputation damage
- Regulatory problems

---

# 16. Social-Network Impersonation

**Social-Network Impersonation** occurs when an attacker creates or controls an account pretending to be another person or organization.

### Common Targets

- Employees
- Managers
- Company representatives
- Public figures
- Students

### Example

An attacker creates a fake profile using an employee's:

- Name
- Photograph
- Job title
- Organization details

The fake identity is then used to gain trust.

---

# 17. Identity Theft

**Identity Theft** occurs when someone obtains and misuses another person's personal information without authorization.

### Information That May Be Misused

- Name
- Phone number
- Email address
- Passwords
- Identification details
- Financial information

### Possible Consequences

```text
Stolen Personal Information
          ↓
Unauthorized Use
          ↓
Financial / Account / Reputation Damage
```

---

# 18. Social Engineering vs Technical Attack

| Social Engineering | Technical Attack |
|---|---|
| Targets people | Targets systems |
| Exploits human psychology | Exploits technical weaknesses |
| Uses deception | Uses technical techniques |
| May require little technical knowledge | Often requires technical knowledge |
| Example: Phishing | Example: SQL Injection |

---

# 19. Phishing vs Spear Phishing vs Whaling

| Technique | Target | Nature |
|---|---|---|
| Phishing | Large/general group | Generic |
| Spear Phishing | Specific person/group | Customized |
| Whaling | Senior executive | Highly targeted |

### Memory Trick

```text
Phishing
   ↓
General Target

Spear Phishing
   ↓
Specific Target

Whaling
   ↓
High-Value Target
```

---

# 20. Vishing vs Smishing

| Vishing | Smishing |
|---|---|
| Voice-based | SMS/text-based |
| Usually phone calls | Usually text messages |
| Attacker uses conversation | Attacker uses deceptive message |
| Example: Fake bank call | Example: Fake delivery SMS |

---

# 21. Social Engineering Countermeasures

Social Engineering cannot be prevented using technology alone.

A combination of **people, processes, and technology** is required.

### Major Countermeasures

- Security awareness training
- Verify unexpected requests
- Do not share passwords or OTPs
- Avoid suspicious links and attachments
- Use Multi-Factor Authentication (MFA)
- Follow access-control policies
- Verify identity before granting access
- Use strong password policies
- Monitor unusual activities
- Report suspicious messages
- Control physical access
- Maintain visitor management

---

# 22. Defense-in-Depth Against Social Engineering

```text
              Social Engineering Defense
                       │
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
      People         Process         Technology
       │               │                │
 Training          Policies            MFA
 Awareness         Verification        Email Filtering
 Reporting         Access Control      Monitoring
```

Security should not depend on a single control.

---

# 23. Golden Rules for Users

### Always:

✔ Verify the identity of the requester.

✔ Think before clicking links.

✔ Check unexpected attachments carefully.

✔ Use MFA.

✔ Report suspicious activity.

✔ Follow organizational security policies.

### Never:

✘ Share passwords.

✘ Share OTPs.

✘ Trust unexpected urgent requests.

✘ Connect unknown USB devices.

✘ Allow unknown persons into restricted areas.

---

# 24. Integrated Social Engineering Scenario

Consider a company employee receiving a suspicious message.

```text
Attacker
   ↓
Collects Public Information
   ↓
Creates a believable identity
   ↓
Sends deceptive message
   ↓
Builds trust / creates urgency
   ↓
Victim performs unsafe action
   ↓
Information or Access Compromised
```

### Lesson

The attacker does not necessarily need to break the firewall.

The attacker may instead **convince a legitimate user to bypass security controls**.

---

# 25. Important Terminology

| Term | Meaning |
|---|---|
| Social Engineering | Manipulation of people |
| Phishing | Deceptive electronic communication |
| Spear Phishing | Targeted phishing |
| Whaling | Phishing targeting executives |
| Vishing | Voice-based phishing |
| Smishing | SMS-based phishing |
| Pretexting | False story or identity |
| Baiting | Attractive lure |
| Quid Pro Quo | Benefit exchanged for information/action |
| Tailgating | Following an authorized person into a restricted area |
| Insider Threat | Threat involving an authorized user |
| Identity Theft | Misuse of another person's identity |

---

# 26. Key Takeaways

✔ Social Engineering targets the **human element**.

✔ Attackers commonly exploit:

- Trust
- Fear
- Urgency
- Curiosity
- Authority
- Greed

✔ Important techniques include:

- Phishing
- Spear Phishing
- Whaling
- Vishing
- Smishing
- Pretexting
- Baiting
- Quid Pro Quo
- Tailgating

✔ Insider threats may be malicious, negligent, or compromised.

✔ Social-Network Impersonation can be used to establish false trust.

✔ Identity Theft involves unauthorized misuse of personal information.

✔ Effective protection requires **people + process + technology**.

---

# Memory Map

```text
Social Engineering
        │
        ├── Phishing
        │     ├── Spear Phishing
        │     └── Whaling
        │
        ├── Vishing
        ├── Smishing
        ├── Pretexting
        ├── Baiting
        ├── Quid Pro Quo
        └── Tailgating
                 ↓
          Human Manipulation
                 ↓
        Information / Access
                 ↓
        Security Incident
```

---

# Frequently Asked University Questions

## 2 Marks

1. Define Social Engineering.
2. What is Phishing?
3. What is Vishing?
4. What is Smishing?
5. What is Tailgating?
6. Define Insider Threat.
7. What is Identity Theft?

---

## 5 Marks

1. Explain different Social Engineering techniques.
2. Differentiate Phishing, Spear Phishing, and Whaling.
3. Explain Insider Threats and their types.
4. Explain Identity Theft with suitable examples.
5. Explain Social Engineering countermeasures.

---

## 10 Marks

1. Explain Social Engineering attacks and various techniques with suitable examples.
2. Discuss different Social Engineering techniques and their countermeasures.
3. Explain Insider Threats, Social-Network Impersonation, and Identity Theft.
4. Explain how organizations can protect themselves against Social Engineering attacks.

---

# Viva Questions

1. What is Social Engineering?
2. Why is Social Engineering considered a human-based attack?
3. What is the difference between phishing and spear phishing?
4. What is whaling?
5. What is the difference between vishing and smishing?
6. What is pretexting?
7. What is baiting?
8. What is tailgating?
9. What is an Insider Threat?
10. What is Identity Theft?
11. Why is security awareness important?
12. Why is MFA useful against Social Engineering?

---

# Module 4 – Final Revision

```text
                 MODULE 4
                    │
        ┌───────────┼────────────┐
        ↓           ↓            ↓
     Malware      Sniffing   Social Engineering
        │           │            │
   Virus/Worm     ARP/DNS      Phishing
   Trojan         Spoofing     Vishing
   APT            Poisoning    Smishing
   Fileless       Tools        Pretexting
        │           │           Baiting
        ↓           ↓           Tailgating
    Analysis    Counter-        Insider Threat
    & Defense   measures        Identity Theft
                                 │
                                 ↓
                            Countermeasures
```

---

# Module 4 Complete

### Topics Covered

- Malware
- Virus
- Worm
- Trojan
- APT
- Fileless Malware
- Malware Analysis
- Sniffing
- MAC/DHCP/ARP Poisoning
- Spoofing
- DNS Poisoning
- Sniffing Tools
- Sniffing Countermeasures
- Social Engineering
- Phishing
- Spear Phishing
- Whaling
- Vishing
- Smishing
- Pretexting
- Baiting
- Quid Pro Quo
- Tailgating
- Insider Threats
- Social-Network Impersonation
- Identity Theft
- Social Engineering Countermeasures

---

# Next Module

## Module 5 – SQL Injection

We will study:

- SQL Injection Basics
- Types of SQL Injection
- Blind SQL Injection
- SQL Injection Methodology
- SQL Injection Tools
- Signature Evasion
- Detection Techniques
- Network Troubleshooting
- Network Security Monitoring
- Tech Support Scams
- SQL Injection Countermeasures
