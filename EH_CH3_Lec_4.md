# Ethical Hacking (2413CYM5T1)

# Module 3
# Lecture 4
# Vulnerability Assessment Concepts, Classification, CVE, CVSS, CWE and NVD

**Duration:** 1 Hour

**Module:** 3

**CO Mapping:** CO3

---

# Recap

In the previous lectures we completed the Enumeration phase.

```text
Footprinting

↓

Scanning

↓

Enumeration

↓

Vulnerability Assessment   ← Today's Topic

↓

System Hacking
```

After gathering information about the target, the next step is identifying security weaknesses.

---

# What is a Vulnerability?

A **vulnerability** is a weakness or flaw in a system, application, network, or process that can be exploited to compromise confidentiality, integrity, or availability.

Examples:

- Weak Password
- Unpatched Software
- Misconfigured Firewall
- SQL Injection
- Open Ports
- Default Credentials

---

# What is Vulnerability Assessment?

**Vulnerability Assessment (VA)** is the systematic process of identifying, analyzing, classifying, and prioritizing vulnerabilities in systems and networks.

Unlike hacking, the purpose is **to identify weaknesses before attackers do.**

---

# Definition

> Vulnerability Assessment is a systematic process of identifying, evaluating, and prioritizing security weaknesses in an organization's IT infrastructure so that appropriate remediation measures can be implemented.

---

# Why Perform Vulnerability Assessment?

Organizations perform Vulnerability Assessment to:

- Identify security weaknesses
- Reduce cyber risk
- Meet compliance requirements
- Improve system security
- Prioritize remediation efforts
- Prevent cyber attacks

---

# Real-World Analogy

Imagine visiting a doctor for a routine health check-up.

The doctor:

- Measures blood pressure
- Checks blood sugar
- Reviews cholesterol
- Suggests further tests if required

The doctor identifies health issues but does **not** perform surgery.

Similarly,

**Vulnerability Assessment identifies security problems but does not exploit them.**

---

# Vulnerability Assessment Process

```text
Identify Assets

↓

Discover Vulnerabilities

↓

Analyze Findings

↓

Assign Severity

↓

Generate Report

↓

Recommend Fixes

↓

Reassess
```

This cycle should be repeated regularly as systems and threats evolve.

---

# Asset Identification

Before scanning, identify the assets that need assessment.

Examples:

- Servers
- Desktop Computers
- Laptops
- Routers
- Firewalls
- Databases
- Web Applications
- Cloud Resources

Without knowing what assets exist, it is impossible to assess their security.

---

# Vulnerability Discovery

Tools scan the identified assets to detect:

- Missing Security Updates
- Weak Configurations
- Default Passwords
- Outdated Software
- Open Ports
- Insecure Services

The output is a list of potential vulnerabilities.

---

# Vulnerability Analysis

Not every vulnerability poses the same level of risk.

Security analysts evaluate:

- Ease of Exploitation
- Potential Impact
- Business Importance
- Existing Security Controls

This helps determine which vulnerabilities require immediate attention.

---

# Vulnerability Prioritization

Organizations cannot fix every issue at once.

Therefore, vulnerabilities are prioritized based on severity.

Example:

| Severity | Action |
|----------|--------|
| Critical | Fix Immediately |
| High | Fix as Soon as Possible |
| Medium | Schedule Remediation |
| Low | Monitor and Fix Later |
| Informational | Record for Reference |

---

# Vulnerability Assessment vs Penetration Testing

These two concepts are often confused.

| Vulnerability Assessment | Penetration Testing |
|--------------------------|---------------------|
| Identifies weaknesses | Exploits weaknesses |
| Defensive approach | Simulated attack |
| Broad coverage | Focused testing |
| Generates reports | Demonstrates impact |
| Lower operational risk | Higher operational risk |
| Usually automated | Mostly manual with automation |

---

# Example

Suppose a web server has an outdated version of Apache.

**Vulnerability Assessment**

Reports:

```
Apache Version 2.4.49

Known Vulnerability Detected
```

**Penetration Testing**

Attempts to exploit the vulnerability (only with authorization) to verify whether unauthorized access is possible.

---

# Types of Vulnerabilities

Security weaknesses can exist in different areas.

| Category | Example |
|----------|----------|
| Operating System | Missing Security Patch |
| Network | Open Ports |
| Web Application | SQL Injection |
| Database | Weak Authentication |
| Wireless | Weak Wi-Fi Password |
| Human | Social Engineering |
| Configuration | Default Credentials |
| Cloud | Public Storage Bucket |

---

# Vulnerability Lifecycle

```text
Vulnerability Created

↓

Discovered

↓

Reported

↓

Patch Released

↓

Patch Applied

↓

Verified

↓

Closed
```

Sometimes organizations delay applying patches, increasing the risk of exploitation.

---

# Think Like an Ethical Hacker

Suppose you scan a company's server and discover:

- Open SSH Port
- Default Administrator Password
- Outdated Apache Version
- Missing Windows Security Updates

Which issue should be fixed first?

---

# Common Vulnerabilities and Exposures (CVE)

## What is CVE?

**CVE (Common Vulnerabilities and Exposures)** is a publicly available catalog of known cybersecurity vulnerabilities.

Each vulnerability is assigned a **unique CVE ID**.

Example:

```
CVE-2021-44228
```

(Commonly known as the **Log4Shell** vulnerability.)

---

# Why is CVE Important?

Imagine thousands of organizations discovering the same vulnerability but giving it different names.

This would create confusion.

CVE provides a **standard naming system** so that everyone refers to the same vulnerability using the same identifier.

Benefits:

- Standardized identification
- Easier communication
- Faster vulnerability management
- Better security reporting
- Global recognition

---

# CVE Format

Example:

```
CVE-2024-6387
```

Explanation:

| Field | Meaning |
|--------|----------|
| CVE | Common Vulnerabilities and Exposures |
| 2024 | Year of publication |
| 6387 | Unique vulnerability number |

---

# Real-World Example 1

## Log4Shell

```
CVE-2021-44228
```

Affected Software

- Apache Log4j

Impact

- Remote Code Execution (RCE)

Possible Consequences

- Complete server compromise
- Malware installation
- Data theft
- Ransomware attacks

This vulnerability affected millions of systems worldwide because Log4j was widely used in enterprise applications.

---

# Real-World Example 2

## OpenSSH Vulnerability

```
CVE-2024-6387
```

Nicknamed:

```
regreSSHion
```

Possible Impact

- Remote Code Execution
- Unauthorized Access

Organizations using vulnerable OpenSSH versions were advised to update immediately.

---

# Common Weakness Enumeration (CWE)

## What is CWE?

**CWE (Common Weakness Enumeration)** is a catalog of common software and hardware weaknesses.

Unlike CVE, which identifies **specific vulnerabilities**, CWE describes **general categories of weaknesses** that can lead to vulnerabilities.

---

# Difference Between CVE and CWE

| CVE | CWE |
|------|------|
| Specific vulnerability | General weakness |
| Assigned to a discovered flaw | Describes a class of flaws |
| Used for patch management | Used for secure software development |
| Example: CVE-2024-6387 | Example: CWE-89 (SQL Injection) |

---

# Common CWE Examples

| CWE ID | Weakness |
|---------|----------|
| CWE-79 | Cross-Site Scripting (XSS) |
| CWE-89 | SQL Injection |
| CWE-119 | Buffer Overflow |
| CWE-287 | Improper Authentication |
| CWE-798 | Hardcoded Credentials |

Developers use the CWE catalog to write more secure software and avoid introducing common weaknesses.

---

# Relationship Between CWE and CVE

```text
Programming Mistake

↓

Weakness

(CWE)

↓

Software Released

↓

Attacker Discovers Issue

↓

Specific Vulnerability

(CVE)
```

Example:

```text
Improper Input Validation

↓

CWE-89

↓

Application Released

↓

SQL Injection Found

↓

Assigned a CVE Number
```

---

# Common Vulnerability Scoring System (CVSS)

## What is CVSS?

**CVSS (Common Vulnerability Scoring System)** is an industry-standard method used to measure the severity of a vulnerability.

It helps organizations prioritize remediation efforts.

---

# CVSS Score Range

| Score | Severity |
|--------|-----------|
| 0.0 | None |
| 0.1 – 3.9 | Low |
| 4.0 – 6.9 | Medium |
| 7.0 – 8.9 | High |
| 9.0 – 10.0 | Critical |

---

# Example

Suppose a vulnerability receives:

```
CVSS Score

9.8
```

Severity

```
Critical
```

Recommended Action

```
Patch Immediately
```

---

# Factors Considered in CVSS

The score is calculated using several factors, including:

- Attack Vector
- Attack Complexity
- Privileges Required
- User Interaction
- Confidentiality Impact
- Integrity Impact
- Availability Impact

Higher impact generally results in a higher CVSS score.

---

# Example Severity Comparison

| Vulnerability | CVSS | Priority |
|---------------|------|----------|
| SQL Injection | 9.8 | Immediate |
| Weak Password Policy | 6.5 | Medium |
| Information Disclosure | 3.7 | Low |

This helps security teams decide which issues should be addressed first.

---

# National Vulnerability Database (NVD)

## What is NVD?

The **National Vulnerability Database (NVD)** is a U.S. government repository maintained by the **National Institute of Standards and Technology (NIST)**.

It contains detailed information about publicly disclosed vulnerabilities.

The NVD enriches CVE entries with:

- CVSS Scores
- Severity Ratings
- Technical Descriptions
- Affected Products
- References
- Remediation Information

---

# Relationship Between CVE and NVD

```text
Vulnerability Found

↓

Assigned CVE ID

↓

Added to NVD

↓

CVSS Score Assigned

↓

Security Teams Apply Patches
```

---

# Practical Demonstration

Visit the NVD website.

Search for:

```
CVE-2021-44228
```

Observe:

- Description
- CVSS Score
- Severity
- References
- Affected Products

Discuss how this information helps organizations prioritize security updates.

---

# Real-World Case Study

A company performs a vulnerability assessment.

The scan identifies:

| Vulnerability | CVSS |
|---------------|------|
| SQL Injection | 9.8 |
| Apache Outdated | 8.4 |
| Weak Password Policy | 6.1 |
| Information Disclosure | 3.4 |

Question:

Which vulnerability should be fixed first?

Answer:

The **SQL Injection** vulnerability should be addressed first because it has the highest CVSS score and may allow attackers to access or manipulate the database.

---

# Summary

In this lecture, we learned:

- Vulnerability Assessment Concepts
- Vulnerability Lifecycle
- Vulnerability Classification
- Difference between Vulnerability Assessment and Penetration Testing
- CVE
- CWE
- CVSS
- NVD
- Vulnerability Prioritization

---

# Quick Revision

```text
Weakness

↓

CWE

↓

Specific Vulnerability

↓

CVE

↓

Severity

↓

CVSS

↓

Details & References

↓

NVD
```

---

# Viva Questions

1. What is a vulnerability?
2. Define Vulnerability Assessment.
3. Differentiate Vulnerability Assessment and Penetration Testing.
4. What is CVE?
5. What information does a CVE ID provide?
6. What is CWE?
7. Differentiate CVE and CWE.
8. What is CVSS?
9. Explain the CVSS severity levels.
10. What is the purpose of the NVD?
11. Why is vulnerability prioritization important?
12. What factors influence a CVSS score?

---

# University Examination Questions

## 5 Marks

1. Explain the Vulnerability Assessment process with a neat diagram.
2. Differentiate Vulnerability Assessment and Penetration Testing.
3. Explain CVE, CWE, CVSS, and NVD with suitable examples.
4. Describe different types of vulnerabilities and their classifications.

---

## 3 Marks

1. What is a CVE? Give one example.
2. State the CVSS severity levels.
3. Differentiate CVE and CWE.

---

# Conclusion

Vulnerability Assessment enables organizations to identify and prioritize security weaknesses before attackers exploit them. Standards such as **CVE**, **CWE**, **CVSS**, and the **NVD** provide a common language for identifying, classifying, scoring, and managing vulnerabilities. By using these standards, security professionals can make informed decisions about remediation priorities and strengthen the overall security posture of an organization.

---