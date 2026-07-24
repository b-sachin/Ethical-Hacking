# Experiment 11
# Mini Penetration Testing and Security Assessment

## Aim

To perform a structured security assessment of an instructor-provided target system by applying ethical hacking techniques including reconnaissance, vulnerability assessment, network scanning, password auditing, web application testing, and security analysis, and to prepare a professional penetration testing report.

---

## Course Outcome Mapping

**CO6:** Integrate ethical hacking, vulnerability assessment, and network security techniques to design and develop a secure system as a capstone project.

---

## Prerequisites

Students should be familiar with:

- Footprinting
- Network Scanning
- Vulnerability Assessment
- Password Security
- Malware Concepts
- SQL Injection
- Network Traffic Analysis
- Cryptography
- Penetration Testing Methodology

---

# Theory

A penetration test is an authorized security assessment performed to identify vulnerabilities before attackers can exploit them.

A typical penetration testing lifecycle includes:

```text
Planning
      ↓
Reconnaissance
      ↓
Scanning
      ↓
Vulnerability Assessment
      ↓
Verification
      ↓
Risk Analysis
      ↓
Recommendations
      ↓
Final Report
```

Unlike attackers, ethical hackers document every finding and provide mitigation recommendations.

---

# Practical Scenario

You are working as a Security Consultant.

A client has requested a security assessment of a newly deployed laboratory server before it is moved to production.

Your team has received written authorization to assess the target.

Your objective is to identify security weaknesses, assess their impact, recommend remediation measures, and prepare a professional penetration testing report.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Kali Linux | Testing Platform |
| Nmap | Network Scanning |
| OpenVAS / Greenbone | Vulnerability Assessment |
| Nikto | Web Server Assessment |
| SQLMap | SQL Injection Testing |
| Wireshark | Traffic Analysis |
| John the Ripper | Password Audit (Instructor Files) |
| Firefox / Chrome | Web Testing |

---

# Target Environment

The instructor will provide one of the following:

- DVWA Server
- Metasploitable2
- OWASP Broken Web Applications
- Instructor-created vulnerable VM

---

# Activity 1 – Define Scope

Record:

| Parameter | Details |
|-----------|---------|
| Target IP | |
| Target Name | |
| Assessment Date | |
| Analyst Name | |

---

# Activity 2 – Host Discovery

Identify whether the target system is online.

```bash
ping <Target-IP>
```

or

```bash
nmap -sn <Target-IP>
```

Record your observations.

---

# Activity 3 – Port Scanning

Perform a TCP SYN scan.

```bash
sudo nmap -sS <Target-IP>
```

Record:

- Open Ports
- Closed Ports
- Filtered Ports

---

# Activity 4 – Service Enumeration

Identify services and versions.

```bash
sudo nmap -sV <Target-IP>
```

Record your findings.

---

# Activity 5 – Operating System Detection

Execute:

```bash
sudo nmap -O <Target-IP>
```

Record the detected operating system.

---

# Activity 6 – Vulnerability Assessment

Perform an authorized vulnerability scan using OpenVAS (or instructor-approved scanner).

Document:

- Critical Vulnerabilities
- High Vulnerabilities
- Medium Vulnerabilities
- Low Vulnerabilities

---

# Activity 7 – Web Application Assessment

If a web server is available:

Run Nikto.

```bash
nikto -h http://<Target-IP>
```

Record:

- Server Information
- Missing Security Headers
- Outdated Components
- Misconfigurations

---

# Activity 8 – SQL Injection Verification

If DVWA or an instructor-approved vulnerable application is available:

Test using SQLMap.

```bash
sqlmap -u "<Target-URL>"
```

Record:

- Injection Point
- Database Identified
- Risk Level

---

# Activity 9 – Password Audit

Using the instructor-provided password hash file:

```bash
john hashes.txt
```

Record:

- Password Strength
- Weak Passwords Identified

---

# Activity 10 – Risk Assessment

Classify findings.

| Severity | Number of Findings |
|----------|--------------------|
| Critical | |
| High | |
| Medium | |
| Low | |

---

# Activity 11 – Security Recommendations

Provide recommendations for each identified vulnerability.

Example:

| Vulnerability | Recommendation |
|--------------|----------------|
| Weak Password | Enforce strong password policy |
| Open Telnet | Disable Telnet and use SSH |
| Missing Updates | Apply latest security patches |
| SQL Injection | Use parameterized queries |
| Information Disclosure | Disable unnecessary services |

---

# Activity 12 – Prepare Penetration Testing Report

Include:

- Executive Summary
- Scope
- Methodology
- Findings
- Evidence (Screenshots)
- Risk Rating
- Recommendations
- Conclusion

---

# Investigation Challenges

### Challenge 1

What is the purpose of a penetration test?

Answer:

________________________

---

### Challenge 2

Which tool identified the largest number of vulnerabilities?

Answer:

________________________

---

### Challenge 3

Which open port represents the highest security risk?

Explain briefly.

---

### Challenge 4

How many critical vulnerabilities were identified?

Answer:

________________________

---

### Challenge 5

Suggest three methods to reduce the attack surface.

1.

2.

3.

---

### Challenge 6

Why should penetration testing always require written authorization?

_____________________________________________________

---

### Challenge 7

Differentiate Vulnerability Assessment and Penetration Testing.

_____________________________________________________

---

### Challenge 8

Which recommendation would you implement first and why?

_____________________________________________________

---

### Challenge 9

What evidence should be included in a penetration testing report?

_____________________________________________________

---

### Challenge 10

Why is reporting as important as finding vulnerabilities?

_____________________________________________________

---

# Observation Table

| Assessment Phase | Observation |
|------------------|-------------|
| Host Discovery | |
| Open Ports | |
| Services | |
| Operating System | |
| Vulnerabilities | |
| Password Audit | |
| Web Assessment | |
| Final Risk Rating | |

---

# Penetration Testing Report Template

## Executive Summary

_____________________________________________________

---

## Scope

_____________________________________________________

---

## Methodology

_____________________________________________________

---

## Findings

| Vulnerability | Severity | Evidence | Recommendation |
|--------------|----------|----------|----------------|
| | | | |

---

## Overall Risk Rating

☐ Critical

☐ High

☐ Medium

☐ Low

---

## Conclusion

_____________________________________________________

---

# Result

Successfully performed an authorized penetration testing exercise on the instructor-provided target system. Security weaknesses were identified, analyzed, prioritized based on risk, and documented in a professional penetration testing report along with appropriate remediation recommendations.

---

# Precautions

- Perform testing only on instructor-authorized systems.
- Never scan public or production networks without written permission.
- Document all findings accurately.
- Avoid modifying or damaging the target system.
- Maintain confidentiality of collected information.
- Follow institutional ethical hacking policies.

---

# Viva Questions

1. What is penetration testing?
2. Differentiate vulnerability assessment and penetration testing.
3. What are the phases of a penetration test?
4. Why is reconnaissance important?
5. What is the purpose of Nmap?
6. What is OpenVAS used for?
7. Why should findings be prioritized?
8. What should a penetration testing report contain?
9. Why is evidence important during a security assessment?
10. Mention three ethical responsibilities of a penetration tester.

---

# Conclusion

This capstone experiment integrated the concepts learned throughout the Ethical Hacking laboratory course. Students applied reconnaissance, scanning, vulnerability assessment, password auditing, web application testing, and risk analysis techniques to perform a structured security assessment. The experiment emphasized ethical practices, professional documentation, and practical recommendations for improving the security posture of an information system.