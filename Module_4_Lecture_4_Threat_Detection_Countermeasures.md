# Ethical Hacking (2413CYM5T1)

# Module 4 – Threats & Attacks

# Lecture 4 – Threat Detection, Countermeasures & Revision

**Duration:** 1 Hour  
**Module:** 4  
**Course Outcome:** CO4

---

# 1. Learning Objectives

By the end of this lecture, students will be able to:

- Summarize the major threats covered in Module 4.
- Identify common indicators of malware and network attacks.
- Explain suitable preventive and detective controls.
- Analyze simple attack scenarios.
- Differentiate prevention, detection, and response.
- Apply security controls to real-world situations.

---

# 2. Module 4 – Quick Recap

Module 4 covers:

```text
                 THREATS & ATTACKS
                        |
        +---------------+---------------+
        |               |               |
        v               v               v
     Malware          Sniffing     Social Engineering
        |               |               |
   Virus/Worm/       MAC/DHCP/      Phishing/
     Trojan           ARP/DNS       Vishing/
        |             Spoofing       Smishing/
   Fileless/APT                      Pretexting
        |                              |
    Analysis                    Insider Threats
        |                       Identity Theft
 Countermeasures
```

---

# 3. Malware – Quick Revision

**Malware** is malicious software designed to damage, disrupt, spy on, or gain unauthorized access to systems.

Common types:

- Virus
- Worm
- Trojan Horse
- Ransomware
- Spyware
- Rootkit
- Fileless Malware

---

# 4. Virus vs Worm vs Trojan Horse

| Feature | Virus | Worm | Trojan Horse |
|---|---|---|---|
| Self-replication | Requires a host/program | Yes | No |
| Main method | Attaches to files | Spreads through networks | Pretends to be legitimate |
| User action | Often required | Usually not required | Often required |
| Main idea | Infects | Spreads | Disguises |

### Easy Memory Trick

```text
Virus  → Attaches
Worm   → Spreads
Trojan → Pretends
```

---

# 5. Advanced Malware Concepts

## Advanced Persistent Threat (APT)

An **APT** is a prolonged and targeted cyberattack in which an attacker attempts to maintain access to a specific organization or system.

Characteristics:

- Targeted
- Persistent
- Stealthy
- Long-term

## Fileless Malware

**Fileless Malware** operates primarily through memory and legitimate system tools instead of relying heavily on traditional executable files.

Examples of tools that may be abused:

- PowerShell
- WMI
- Command-line utilities

### Countermeasures

- Endpoint Detection and Response (EDR)
- Application control
- PowerShell logging
- Least privilege
- Behavior-based detection
- Regular patching

---

# 6. Malware Analysis

Malware analysis helps security professionals understand malicious software.

```text
Malware Analysis
       |
       +-- Static Analysis
       |
       +-- Dynamic Analysis
```

## Static Analysis

The malware is examined without executing it.

Analysts may examine:

- Hash values
- File properties
- Strings
- Imports
- Code structure

## Dynamic Analysis

The malware is executed in a controlled environment.

Analysts observe:

- Processes
- Network connections
- File changes
- System behavior

**Important:** Malware analysis should be performed only in an isolated and authorized laboratory environment.

---

# 7. Sniffing – Quick Revision

**Sniffing** is the process of capturing and analyzing network traffic.

Uses include:

- Network troubleshooting
- Security monitoring
- Incident investigation
- Protocol analysis

Common tools:

- Wireshark
- tcpdump
- TShark

---

# 8. Network Attacks Covered

```text
Network Attacks
      |
      +-- MAC Attacks
      +-- DHCP Attacks
      +-- ARP Poisoning
      +-- DNS Poisoning
      +-- Spoofing
```

---

# 9. MAC Attacks

MAC-based attacks exploit weaknesses in how network switches learn and use MAC addresses.

Possible impacts:

- Network disruption
- Device impersonation
- Weak access-control bypass

### Countermeasures

- Switch port security
- Network Access Control
- MAC address monitoring
- Proper authentication

---

# 10. DHCP Attacks

DHCP automatically provides network configuration to clients.

A malicious DHCP server may provide incorrect network information.

Possible consequences:

- Incorrect gateway
- Incorrect DNS server
- Traffic redirection
- Network disruption

### Countermeasures

- DHCP Snooping
- Trusted DHCP ports
- Network monitoring
- Switch security

---

# 11. ARP Poisoning

ARP maps IP addresses to MAC addresses within a local network.

In ARP poisoning, false ARP information may cause traffic to be associated with an attacker's device.

```text
Victim
  |
  | Traffic
  v
Attacker
  |
  v
Gateway
```

Possible impacts:

- Traffic interception
- Man-in-the-middle attacks
- Communication disruption

### Countermeasures

- Dynamic ARP Inspection
- Encryption
- Network segmentation
- Network monitoring

---

# 12. DNS Poisoning

DNS converts domain names into IP addresses.

DNS poisoning attempts to cause incorrect DNS information to be used.

```text
User
  |
  v
DNS Request
  |
  v
Incorrect DNS Information
  |
  v
Wrong Destination
```

### Countermeasures

- DNSSEC
- Secure DNS configuration
- DNS monitoring
- HTTPS/TLS
- Trusted DNS infrastructure

---

# 13. Spoofing – Quick Revision

**Spoofing** means pretending to be a trusted source, device, user, or service.

Common types:

```text
Spoofing
   |
   +-- IP Spoofing
   +-- MAC Spoofing
   +-- DNS Spoofing
   +-- Email Spoofing
   +-- Website Spoofing
```

### Easy Memory Trick

```text
IP      → Fake IP identity
MAC     → Fake device identity
DNS     → Fake DNS information
Email   → Fake sender identity
Website → Fake website identity
```

---

# 14. Social Engineering – Quick Revision

**Social Engineering** attacks people rather than directly attacking technology.

Attackers may exploit:

- Trust
- Fear
- Urgency
- Curiosity
- Authority
- Greed

---

# 15. Major Social Engineering Techniques

| Technique | Meaning |
|---|---|
| Phishing | Fraudulent electronic message |
| Spear Phishing | Targeted phishing |
| Whaling | Phishing aimed at senior personnel |
| Vishing | Voice-based phishing |
| Smishing | SMS-based phishing |
| Pretexting | False identity or story |
| Baiting | Attractive bait used to trick victim |
| Quid Pro Quo | Fake benefit offered in exchange |
| Tailgating | Following an authorized person into a restricted area |

---

# 16. Insider Threats

An **Insider Threat** occurs when a person with legitimate access causes or enables a security incident.

Types:

```text
Insider Threat
      |
      +-- Malicious Insider
      +-- Negligent Insider
      +-- Compromised Insider
```

### Malicious Insider

Intentionally misuses authorized access.

### Negligent Insider

Accidentally causes a security incident.

### Compromised Insider

An attacker gains control of a legitimate user's account or device.

---

# 17. Identity Theft

**Identity Theft** occurs when someone's personal information is obtained and misused without authorization.

Information may include:

- Name
- Account details
- Identification information
- Financial information
- Login credentials

Common causes:

- Phishing
- Data breaches
- Social Engineering
- Fake websites
- Unsafe sharing of information

---

# 18. Attack Indicators

Security professionals should recognize suspicious indicators.

## Malware Indicators

- Unexpected processes
- Unusual system slowdown
- Unknown applications
- Unexpected network connections
- Unexpected file changes

## Network Attack Indicators

- Unusual ARP changes
- Unexpected DHCP activity
- Strange DNS responses
- Unknown devices
- Unusual network traffic

## Social Engineering Indicators

- Urgent requests
- Suspicious links
- Unexpected attachments
- Requests for passwords or OTPs
- Requests to bypass normal procedures

---

# 19. Prevention vs Detection vs Response

Security is not only about preventing attacks.

```text
Prevent
   ↓
Detect
   ↓
Respond
   ↓
Recover
   ↓
Improve
```

## Prevention

Stops or reduces the possibility of an attack.

Examples:

- MFA
- Encryption
- Patch management
- Least privilege
- Security awareness

## Detection

Identifies suspicious activity.

Examples:

- IDS/IPS
- EDR
- SIEM
- Network monitoring
- Log analysis

## Response

Takes action after detecting an incident.

Examples:

- Isolate affected system
- Disable compromised account
- Block malicious traffic
- Investigate logs
- Remove malware

---

# 20. Defense in Depth

**Defense in Depth** means using multiple layers of security controls.

```text
                 Organization
                      |
              +-------+-------+
              |               |
          Technology        People
              |               |
       +------+-----+     Training
       |      |     |
     Firewall EDR  MFA
       |
   Network
 Segmentation
       |
    Monitoring
```

If one control fails, another layer can still provide protection.

---

# 21. Security Controls for Module 4

| Threat | Important Controls |
|---|---|
| Malware | Anti-malware, EDR, patching |
| Virus | Endpoint protection, safe software |
| Worm | Network segmentation, patching |
| Trojan | Application control, user awareness |
| Sniffing | Encryption, secure protocols |
| MAC Attack | Port security |
| DHCP Attack | DHCP Snooping |
| ARP Poisoning | Dynamic ARP Inspection |
| DNS Poisoning | DNSSEC, monitoring |
| Spoofing | Authentication, filtering |
| Phishing | Awareness, email filtering, MFA |
| Insider Threat | Least privilege, monitoring, DLP |
| Identity Theft | MFA, privacy, account monitoring |

---

# 22. Case Study – Phishing

An employee receives:

```text
URGENT!

Your company account will be disabled today.

Click the link below and verify your password.
```

### Questions

1. What type of attack is this?
2. What psychological technique is being used?
3. What should the employee do?

### Expected Answer

1. Phishing
2. Urgency / fear
3. Do not click the link. Verify the request through an official channel.

---

# 23. Case Study – ARP Poisoning

A security analyst notices unusual ARP mappings and users experience unexpected network behavior.

### Questions

1. Which attack may be suspected?
2. What is the possible impact?
3. Name two countermeasures.

### Expected Answer

1. ARP Poisoning
2. Traffic interception or communication disruption
3. Dynamic ARP Inspection and network monitoring

---

# 24. Case Study – Malware

A user installs a free application from an unknown website.

After installation:

- The computer becomes slow.
- An unknown process starts.
- Unexpected network connections appear.

### Questions

1. What security threat may be present?
2. What should the security team do?
3. Which controls can reduce the risk?

### Expected Answer

1. Possible malware infection
2. Isolate and investigate the system
3. EDR/anti-malware, application control, patching, and user awareness

---

# 25. Case Study – Insider Threat

An employee accidentally sends confidential information to the wrong email address.

### Questions

1. Is this a malicious insider?
2. What type of insider threat is involved?
3. Suggest suitable controls.

### Expected Answer

1. No
2. Negligent insider
3. Data Loss Prevention, email controls, security awareness, and data-handling procedures

---

# 26. Integrated Attack Scenario

An attack may involve multiple stages:

```text
Attacker
   |
   v
Phishing Email
   |
   v
Employee
   |
   v
Credentials Stolen
   |
   v
Account Compromised
   |
   v
Unauthorized Access
   |
   v
Sensitive Data
```

Possible controls:

```text
Phishing Email
      ↓
Email Filtering
      ↓
User Awareness
      ↓
MFA
      ↓
Login Monitoring
      ↓
Least Privilege
      ↓
Data Protection
```

---

# 27. Incident Response – Basic Process

When a security incident is identified:

```text
1. Identify
     ↓
2. Contain
     ↓
3. Investigate
     ↓
4. Eradicate
     ↓
5. Recover
     ↓
6. Learn
```

### Identify

Determine what happened.

### Contain

Limit further damage.

### Investigate

Determine the cause and scope.

### Eradicate

Remove the threat.

### Recover

Restore normal operations.

### Learn

Improve security controls and procedures.

---

# 28. Important Security Principles

## Least Privilege

Users should receive only the access required to perform their work.

## Defense in Depth

Use multiple layers of security.

## Strong Authentication

Use MFA where possible.

## Encryption

Protect data during transmission and storage.

## Patch Management

Regularly update systems and applications.

## Security Awareness

Train users to recognize suspicious activity.

---

# 29. Module 4 Memory Map

```text
                    MODULE 4
               THREATS & ATTACKS
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
      Malware        Sniffing     Social Engineering
        |              |              |
   +----+----+      +--+--+       +---+---+
   |    |    |      |  |  |       |   |   |
 Virus Worm Trojan  MAC DHCP ARP  Phishing Vishing
   |                         |      Smishing
   |                         |      Pretexting
 Fileless                   DNS      Baiting
 Malware                   Spoofing  Tailgating
   |
 Analysis
   |
Countermeasures
```

---

# 30. Important Differences

## Virus vs Worm vs Trojan

```text
Virus  → Needs a host and commonly requires execution
Worm   → Self-replicates and spreads
Trojan → Pretends to be legitimate software
```

## Phishing vs Spear Phishing vs Whaling

```text
Phishing       → Broad targets
Spear Phishing → Specific target
Whaling        → High-value / senior target
```

## Sniffing vs Spoofing

```text
Sniffing → Capturing / observing traffic

Spoofing → Pretending to be another source
```

## Malware vs Social Engineering

```text
Malware
   ↓
Malicious software

Social Engineering
   ↓
Manipulation of people
```

---

# 31. University Exam – Important Questions

## 2 Marks

1. Define Malware.
2. What is Sniffing?
3. What is Spoofing?
4. Define Social Engineering.
5. What is an Insider Threat?
6. What is DNS Poisoning?

## 5 Marks

1. Differentiate between Virus, Worm, and Trojan Horse.
2. Explain DNS Poisoning and its countermeasures.
3. Explain different types of Spoofing attacks.
4. Explain major Social Engineering techniques.
5. Explain Insider Threats and their types.
6. Explain Sniffing attacks and suitable countermeasures.

## 10 Marks

1. Explain different Malware threats and their countermeasures.
2. Explain Sniffing attacks including MAC, DHCP, ARP, and DNS attacks with countermeasures.
3. Analyze different Social Engineering techniques and their impact on organizations. Suggest suitable countermeasures.
4. Explain Spoofing attacks and discuss appropriate security controls.
5. Discuss Malware, Sniffing, and Social Engineering threats and explain a defense-in-depth approach.

---

# 32. Viva Questions

1. What is malware?
2. What is the difference between a virus and a worm?
3. What is a Trojan Horse?
4. What is an APT?
5. What is fileless malware?
6. What is static malware analysis?
7. What is dynamic malware analysis?
8. What is sniffing?
9. What is ARP Poisoning?
10. What is DHCP Snooping?
11. What is DNS Poisoning?
12. What is spoofing?
13. What is phishing?
14. What is spear phishing?
15. What is vishing?
16. What is smishing?
17. What is pretexting?
18. What is an insider threat?
19. What is identity theft?
20. What is defense in depth?

---

# 33. Final Revision – One Page

```text
MODULE 4 – THREATS & ATTACKS

MALWARE
│
├── Virus
├── Worm
├── Trojan
├── APT
├── Fileless Malware
├── Malware Analysis
└── Countermeasures

SNIFFING
│
├── Sniffing Concepts
├── MAC Attacks
├── DHCP Attacks
├── ARP Poisoning
├── DNS Poisoning
├── Spoofing
├── Wireshark / tcpdump
└── Countermeasures

SOCIAL ENGINEERING
│
├── Phishing
├── Spear Phishing
├── Whaling
├── Vishing
├── Smishing
├── Pretexting
├── Baiting
├── Quid Pro Quo
├── Tailgating
├── Insider Threats
├── Impersonation
└── Identity Theft
```

---

# 34. Key Takeaways

- Malware uses malicious software to compromise systems.
- Viruses attach to hosts, worms spread independently, and Trojans disguise themselves as legitimate software.
- Sniffing involves capturing and analyzing network traffic.
- MAC, DHCP, ARP, and DNS attacks can affect network security.
- Spoofing involves impersonating a trusted source.
- Social Engineering targets human behavior and trust.
- Phishing, vishing, smishing, pretexting, and baiting are common social engineering techniques.
- Insider threats may be malicious, negligent, or caused by compromised accounts.
- Effective security requires prevention, detection, response, and recovery.
- Defense in depth combines people, processes, and technology.

---

# End of Module 4
