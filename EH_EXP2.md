# Experiment 2
# Vulnerability Research using CVE, NVD and CVSS

## Aim

To perform vulnerability research using publicly available vulnerability databases, identify security vulnerabilities associated with software products, and assess their severity using the Common Vulnerability Scoring System (CVSS).

---

## Course Outcome Mapping

**CO1:** Develop a foundational understanding of ethical hacking principles and practices.

---

## Prerequisites

Students should be familiar with:

- Basic Cyber Security Concepts
- Vulnerabilities and Threats
- CVE (Common Vulnerabilities and Exposures)
- NVD (National Vulnerability Database)
- CVSS (Common Vulnerability Scoring System)
- Web Browsers

---

# Theory

Security vulnerabilities are weaknesses in software, hardware, operating systems, or network devices that may be exploited by attackers.

Cybersecurity professionals continuously monitor vulnerability databases to identify newly discovered vulnerabilities and determine their impact before attackers can exploit them.

Three important standards used worldwide are:

- **CVE (Common Vulnerabilities and Exposures)** – Provides a unique identifier for publicly known vulnerabilities.
- **NVD (National Vulnerability Database)** – Maintained by NIST and provides detailed vulnerability information along with CVSS scores.
- **CVSS (Common Vulnerability Scoring System)** – Standard framework used to measure the severity of vulnerabilities.

---

# Practical Scenario

You are working as a Security Analyst in an organization.

The IT department has deployed several software applications across the organization. Before performing vulnerability assessment or penetration testing, your task is to research publicly disclosed vulnerabilities affecting these products and prioritize them based on their severity.

Use publicly available vulnerability databases to complete the investigation.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Web Browser | Internet Access |
| NVD Website | Vulnerability Database |
| CVE Website | Vulnerability Information |
| CVSS Calculator | Severity Assessment |
| Internet Connection | Research |

---

# Websites Used

| Website | URL |
|----------|-----|
| CVE Database | https://www.cve.org |
| National Vulnerability Database | https://nvd.nist.gov |
| CVSS Calculator | https://www.first.org/cvss/calculator/3.1 |

---

# Procedure

## Activity 1 – Explore the CVE Database

1. Open a web browser.
2. Visit:

```
https://www.cve.org
```

3. Search for the following software:

- Windows 11
- Google Chrome
- Mozilla Firefox
- Apache HTTP Server
- OpenSSH

4. Record one vulnerability associated with each software.

---

### Observation

| Software | CVE ID |
|----------|--------|
| Windows 11 | |
| Google Chrome | |
| Mozilla Firefox | |
| Apache HTTP Server | |
| OpenSSH | |

---

## Activity 2 – Analyze a CVE Record

Choose any one CVE from Activity 1.

Record the following information.

| Parameter | Observation |
|-----------|-------------|
| CVE ID | |
| Published Date | |
| Last Modified | |
| Vulnerability Description | |
| Affected Product | |
| Vendor | |

Take Screenshot-1.

---

## Activity 3 – Explore the National Vulnerability Database (NVD)

Visit

```
https://nvd.nist.gov
```

Search using the selected CVE ID.

Record the following information.

| Parameter | Observation |
|-----------|-------------|
| CVSS Version | |
| Base Score | |
| Severity | |
| Attack Vector | |
| Attack Complexity | |
| Privileges Required | |
| User Interaction | |
| Confidentiality Impact | |
| Integrity Impact | |
| Availability Impact | |

Take Screenshot-2.

---

## Activity 4 – Interpret the CVSS Score

Using the CVSS score obtained from NVD, classify the vulnerability.

| CVSS Score | Severity |
|------------|----------|
| 0.0 | None |
| 0.1 – 3.9 | Low |
| 4.0 – 6.9 | Medium |
| 7.0 – 8.9 | High |
| 9.0 – 10.0 | Critical |

Record your observation.

---

## Activity 5 – Analyze Multiple Vulnerabilities

Select any **three different CVE records** and complete the following table.

| CVE ID | Product | CVSS Score | Severity | Brief Description |
|--------|----------|------------|----------|-------------------|
| | | | | |
| | | | | |
| | | | | |

---

## Activity 6 – Compare Vulnerabilities

Compare the vulnerabilities identified.

Answer the following:

- Which vulnerability has the highest CVSS score?
- Which vulnerability requires user interaction?
- Which vulnerability has the greatest impact on confidentiality?
- Which vulnerability affects availability the most?

---

## Activity 7 – Prioritize Vulnerabilities

Assume you are responsible for patch management.

Arrange the selected vulnerabilities in the order in which they should be fixed.

| Priority | CVE ID | Justification |
|----------|--------|---------------|
| 1 | | |
| 2 | | |
| 3 | | |

---

## Activity 8 – CVSS Calculator

Visit

```
https://www.first.org/cvss/calculator/3.1
```

Open the CVSS Calculator.

Select any vulnerability.

Observe how changing parameters affects the overall CVSS score.

Record your observations.

---

# Investigation Challenges

### Challenge 1

What does CVE stand for?

Answer:

________________________

---

### Challenge 2

Who maintains the National Vulnerability Database?

Answer:

________________________

---

### Challenge 3

What is the purpose of CVSS?

Answer:

________________________

---

### Challenge 4

Which vulnerability in your analysis had the highest CVSS score?

Answer:

________________________

---

### Challenge 5

Which vulnerability requires user interaction?

Answer:

________________________

---

### Challenge 6

Which attack vector was most commonly observed?

Answer:

________________________

---

### Challenge 7

Which vulnerability would you patch first? Why?

Answer:

_____________________________________________________

---

### Challenge 8

Can two vulnerabilities have the same CVSS score but different impacts? Justify your answer.

_____________________________________________________

---

### Challenge 9

What information does a CVE ID provide?

Answer:

________________________

---

### Challenge 10

How can vulnerability research help an organization improve cybersecurity?

_____________________________________________________

---

# Observation Table

| Activity | Observation |
|----------|-------------|
| CVEs Identified | |
| Highest CVSS Score | |
| Lowest CVSS Score | |
| Critical Vulnerabilities | |
| Medium Vulnerabilities | |
| High Vulnerabilities | |
| Attack Vector Observed | |
| Patch Priority | |

---

# Sample Vulnerability Assessment Report

| Parameter | Observation |
|-----------|-------------|
| Organization | |
| Date | |
| Analyst | |
| Software Reviewed | |
| Number of CVEs Found | |
| Critical Vulnerabilities | |
| Highest CVSS Score | |
| Recommended Action | |

---

# Result

Successfully performed vulnerability research using the CVE and NVD databases. The identified vulnerabilities were analyzed using CVSS scores, prioritized based on severity, and documented to support effective vulnerability management and patch planning.

---

# Precautions

- Use only publicly available vulnerability databases.
- Do not attempt to exploit any identified vulnerabilities.
- Record CVE information accurately.
- Always verify vulnerability information from trusted sources.
- Perform vulnerability research only for educational or authorized purposes.

---

# Viva Questions

1. What is a vulnerability?
2. What is CVE?
3. What is the purpose of the National Vulnerability Database (NVD)?
4. What is CVSS?
5. How is the CVSS score interpreted?
6. What is the difference between CVE and CVSS?
7. Why is vulnerability prioritization important?
8. What is meant by Attack Vector in CVSS?
9. Why should organizations regularly monitor vulnerability databases?
10. How does vulnerability research support patch management?

---

# Conclusion

This experiment introduced students to vulnerability research using globally recognized security resources such as CVE, NVD, and CVSS. Students learned how to identify publicly disclosed vulnerabilities, interpret CVSS metrics, compare vulnerability severity, and prioritize remediation efforts. These activities form the foundation of vulnerability assessment and proactive cybersecurity management.

