# Experiment 3
# Professional Vulnerability Assessment using OpenVAS (Greenbone)

## Aim

To perform a vulnerability assessment on an authorized target using OpenVAS (Greenbone Community Edition), identify security vulnerabilities, analyze the generated report, prioritize vulnerabilities based on severity, and recommend appropriate mitigation measures.

---

## Course Outcome Mapping

**CO2:** Develop the monitoring technique for network.

---

## Prerequisites

Students should be familiar with:

- IP Addressing
- Network Scanning
- Host Discovery
- CVE
- CVSS
- NVD
- Linux Basics

---

# Practical Scenario

You are working as a Security Analyst.

Your organization has deployed a new server and requests a vulnerability assessment before it is moved into production.

Your task is to perform an authorized vulnerability scan, analyze the findings, and prepare a professional assessment report.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Greenbone/OpenVAS Community Edition | Vulnerability Scanner |
| Kali Linux | Operating System |
| Metasploitable2 VM / DVWA VM | Target Machine |
| VirtualBox / VMware | Virtualization |

---

# Network Topology

```

+-------------------+

Kali Linux

(OpenVAS)

192.168.x.x

|

|

|

+-------------------+

Metasploitable2

(Target)

192.168.x.x

```

---

# Activity 1 – Verify Connectivity

Open Terminal.

Verify connectivity using Ping.

```bash
ping <Target-IP>
```

Record the response.

---

# Activity 2 – Login to Greenbone

Open Browser.

Visit

```
https://127.0.0.1:9392
```

Login using your credentials.

Take Screenshot-1.

---

# Activity 3 – Create Target

Navigate to

```
Configuration

↓

Targets

↓

New Target
```

Enter

- Target Name
- Target IP

Save.

Take Screenshot-2.

---

# Activity 4 – Create Scan Task

Navigate

```
Scans

↓

Tasks

↓

New Task
```

Select

- Target
- Scan Configuration

Save.

---

# Activity 5 – Run Vulnerability Scan

Click

```
Start Scan
```

Wait until completion.

Take Screenshot-3.

---

# Activity 6 – Analyze Scan Report

Record the following.

| Parameter | Observation |
|------------|-------------|
| Total Vulnerabilities | |
| Critical | |
| High | |
| Medium | |
| Low | |
| Log Messages | |

---

# Activity 7 – Study Individual Vulnerabilities

Choose any five vulnerabilities.

Complete the table.

| Vulnerability | CVE | Severity | Solution |
|---------------|-----|----------|----------|
| | | | |
| | | | |
| | | | |
| | | | |
| | | | |

---

# Activity 8 – Export Report

Export the report as

- PDF

or

- HTML

Attach the report with your journal.

---

# Activity 9 – Prioritize Remediation

Arrange vulnerabilities.

| Priority | Vulnerability | Reason |
|----------|---------------|--------|
| 1 | | |
| 2 | | |
| 3 | | |
| 4 | | |
| 5 | | |

---

# Investigation Challenges

### Challenge 1

How many vulnerabilities were discovered?

Answer

____________________

---

### Challenge 2

Which vulnerability has the highest CVSS score?

Answer

____________________

---

### Challenge 3

Which service generated the maximum vulnerabilities?

Answer

____________________

---

### Challenge 4

How many Critical vulnerabilities were detected?

Answer

____________________

---

### Challenge 5

Which vulnerability should be patched first?

Why?

_________________________________________

---

### Challenge 6

What remediation was suggested for the most severe vulnerability?

_________________________________________

---

### Challenge 7

Which CVE appeared multiple times?

Answer

____________________

---

### Challenge 8

Did the scan identify outdated software?

Answer

Yes / No

If Yes, mention the software.

____________________

---

### Challenge 9

Was the target considered secure?

Justify your answer.

_________________________________________

---

### Challenge 10

Suggest three recommendations to improve the target's security posture.

1.

2.

3.

---

# Observation Table

| Parameter | Observation |
|------------|-------------|
| Target IP | |
| Scanner Used | |
| Scan Duration | |
| Total Vulnerabilities | |
| Critical | |
| High | |
| Medium | |
| Low | |

---

# Sample Vulnerability Assessment Report

| Parameter | Observation |
|------------|-------------|
| Organization | |
| Analyst | |
| Date | |
| Target | |
| Scanner | |
| Highest CVSS | |
| Critical Issues | |
| Recommendation | |

---

# Result

Successfully performed an authorized vulnerability assessment using OpenVAS, analyzed the generated report, prioritized vulnerabilities according to severity, and documented recommendations for remediation.

---

# Precautions

- Scan only instructor-authorized targets.
- Never scan public IP addresses without permission.
- Do not modify the target system.
- Save all reports before closing the scanner.
- Follow responsible disclosure and ethical hacking practices.

---

# Viva Questions

1. What is a Vulnerability Assessment?
2. What is OpenVAS?
3. Differentiate Vulnerability Assessment and Penetration Testing.
4. What is CVSS?
5. What is a False Positive?
6. Why should vulnerabilities be prioritized?
7. What is Risk Rating?
8. What is Remediation?
9. Which report formats can OpenVAS generate?
10. Why should vulnerability scanning be performed regularly?

---

# Conclusion

This experiment provided hands-on experience in conducting a professional vulnerability assessment using OpenVAS. Students learned how to configure a scan, analyze findings, prioritize risks, and prepare remediation recommendations. The experiment reflects the workflow followed by security analysts during real-world vulnerability management and security assessment engagements.