# ETHICAL HACKING (2413CYM5T1)

# Module 5 – SQL Injection

# Lecture 2 – SQL Injection Types, Methodology & Detection

**Course Outcome:** CO5  
**Duration:** 1 Hour

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain major types of SQL Injection in detail.
- Differentiate In-Band and Blind SQL Injection.
- Explain Boolean-Based and Time-Based Blind SQL Injection.
- Describe the general methodology of SQL Injection assessment.
- Identify common indicators of SQL Injection.
- Understand the role of authorized SQL Injection testing tools.
- Explain the security impact of SQL Injection.

---

# 1. Recap of Lecture 1

In Lecture 1, we learned:

- SQL Injection is a web application vulnerability.
- It occurs when untrusted input is improperly incorporated into SQL queries.
- Dynamic SQL and string concatenation increase SQL Injection risk.
- Parameterized queries are the primary defense.
- SQL Injection can affect the CIA Triad.

```text
User Input
    ↓
Web Application
    ↓
SQL Query
    ↓
Database
```

If user input is incorrectly handled, the intended SQL logic may be altered.

---

# 2. Classification of SQL Injection

SQL Injection can be classified according to how information is obtained.

```text
                    SQL Injection
                         │
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
       In-Band          Blind       Out-of-Band
          │              │
      ┌───┴───┐      ┌───┴────┐
      ↓       ↓      ↓        ↓
    Error   Union  Boolean   Time
```

---

# 3. In-Band SQL Injection

In **In-Band SQL Injection**, the attacker sends input through the application and receives the resulting information through the same communication channel.

### Two common forms:

1. Error-Based SQL Injection
2. Union-Based SQL Injection

---

# 4. Error-Based SQL Injection

Error-Based SQL Injection relies on database error messages or abnormal responses.

```text
Input
  ↓
Application
  ↓
Database
  ↓
Database Error
  ↓
Application Response
```

If detailed errors are displayed, they may reveal information about:

- Database technology
- Tables
- Columns
- Query structure
- Application configuration

### Example

Instead of showing:

```text
Database error: detailed internal information...
```

A secure application should show:

```text
An error occurred. Please try again later.
```

Detailed information should be recorded securely in server-side logs.

---

# 5. Union-Based SQL Injection

The SQL `UNION` operator combines results from compatible `SELECT` statements.

In a vulnerable application, improper input handling may allow an attacker to influence the query structure and cause unintended data to appear in the response.

### Concept

```text
Original Query
      +
Unexpected Query Component
      ↓
Combined Database Result
      ↓
Application Response
```

### Important Point

The security problem is not the `UNION` operator itself.

The problem is **untrusted input being allowed to alter SQL query structure**.

---

# 6. Blind SQL Injection

In **Blind SQL Injection**, useful database information is not directly displayed in the application's response.

The tester instead observes application behavior.

```text
Input
  ↓
Application
  ↓
Database
  ↓
Application Behavior
  ↓
Information Inferred
```

Two important forms are:

- Boolean-Based Blind SQL Injection
- Time-Based Blind SQL Injection

---

# 7. Boolean-Based Blind SQL Injection

Boolean-Based Blind SQL Injection relies on differences in application behavior based on whether a condition evaluates to **TRUE** or **FALSE**.

### Concept

```text
Condition
    │
 ┌──┴──┐
 ↓     ↓
TRUE  FALSE
 ↓     ↓
Response A
      Response B
```

The application might produce:

- Different page content
- Different result counts
- Different status messages
- Different response behavior

### Security Concern

Even without displaying database errors or data, application behavior may unintentionally reveal information.

---

# 8. Time-Based Blind SQL Injection

Time-Based Blind SQL Injection uses differences in response time to infer information.

### Concept

```text
Input
  ↓
Database Processing
  ↓
Response Delay
  ↓
Tester Observes Timing
  ↓
Information Inferred
```

### Important Point

Time-based techniques can be affected by:

- Network latency
- Server load
- Database performance
- Application architecture

Therefore, response timing must be interpreted carefully during authorized testing.

---

# 9. Error-Based vs Blind SQL Injection

| Error-Based SQLi | Blind SQLi |
|---|---|
| Uses error information | Does not require visible database errors |
| Database errors may reveal details | Information is inferred indirectly |
| Often easier to identify | May be harder to detect |
| Depends on verbose error handling | Depends on application behavior |

---

# 10. Boolean-Based vs Time-Based SQL Injection

| Boolean-Based | Time-Based |
|---|---|
| Observes TRUE/FALSE behavior | Observes response timing |
| Uses differences in application responses | Uses differences in response delays |
| May compare page content/status | May compare response time |
| Depends on observable response differences | Depends on measurable timing differences |

---

# 11. Out-of-Band SQL Injection

**Out-of-Band SQL Injection** uses a separate communication channel to obtain information from a vulnerable environment.

It generally depends on:

- Database capabilities
- Network configuration
- Application environment
- Available external communication mechanisms

### Important Point

Out-of-band SQL Injection is less common than In-Band and Blind SQL Injection.

---

# 12. SQL Injection Methodology

A security professional generally follows a structured assessment process.

```text
1. Identify Target Application
             ↓
2. Identify Input Points
             ↓
3. Understand Normal Behavior
             ↓
4. Test Input Handling
             ↓
5. Confirm Vulnerability Safely
             ↓
6. Assess Potential Impact
             ↓
7. Document Findings
             ↓
8. Recommend Remediation
             ↓
9. Retest After Fix
```

> All testing must be performed only on systems for which explicit authorization has been provided.

---

# 13. Step 1 – Identify the Application

First understand:

- Application purpose
- Technology stack
- Database-dependent features
- Authentication mechanisms
- User input points

Examples of input areas:

- Login forms
- Search forms
- Product filters
- URL parameters
- API parameters
- Form submissions

---

# 14. Step 2 – Identify Input Points

An **Input Point** is any location where user-controlled data enters an application.

```text
                User Input
                    │
        ┌───────────┼───────────┐
        ↓           ↓           ↓
      Forms       URLs         APIs
        │           │           │
        └───────────┼───────────┘
                    ↓
             Web Application
                    ↓
                Database
```

Not every input point is vulnerable.

The application must be tested to determine how the input is processed.

---

# 15. Step 3 – Understand Normal Behavior

Before security testing, understand how the application normally behaves.

Observe:

- Normal response
- Error response
- Status code
- Page content
- Response time
- Result count

This provides a **baseline** for comparison.

---

# 16. Step 4 – Test Input Handling

During authorized testing, security professionals check whether user input is safely handled.

The objective is to determine:

> **Does user input remain data, or can it influence SQL query structure?**

Testing should be controlled and performed in a dedicated lab or authorized environment.

---

# 17. Step 5 – Confirm the Vulnerability

A suspected SQL Injection should be confirmed carefully.

The tester should determine:

- Whether input affects query behavior.
- What type of SQL Injection may be present.
- Whether the behavior is reproducible.
- What level of impact exists.

Avoid unnecessary access to real sensitive information.

---

# 18. Step 6 – Assess Impact

Once a vulnerability is confirmed, determine the possible security impact.

Consider:

- Confidentiality
- Integrity
- Availability
- Authentication
- Authorization
- Sensitive data exposure

```text
SQL Injection
      ↓
Query Manipulation
      ↓
Database Impact
      ↓
CIA / Authentication / Data Risk
```

---

# 19. Step 7 – Document Findings

A security assessment report should contain:

- Vulnerability name
- Affected component
- Description
- Risk/impact
- Evidence
- Severity
- Recommended remediation
- Retest status

A good report should allow developers to understand and fix the issue.

---

# 20. Step 8 – Remediation and Retesting

After the developer applies a fix:

```text
Vulnerability Found
       ↓
Fix Applied
       ↓
Security Retesting
       ↓
Vulnerability Resolved?
       │
    ┌──┴──┐
    ↓     ↓
   Yes    No
    ↓     ↓
 Close   Fix Again
```

Retesting confirms that the vulnerability has actually been addressed.

---

# 21. SQL Injection Detection

Detection can be performed using several approaches.

### Application-Level Detection

Look for:

- Unexpected database errors
- Abnormal responses
- Different results for similar requests
- Unusual response timing
- Unexpected database-related messages

### Security Monitoring

Monitor:

- Web server logs
- Application logs
- Database logs
- WAF alerts
- Suspicious request patterns

---

# 22. SQL Injection Testing Tools

Security professionals may use specialized tools in **authorized environments**.

Examples include:

- Burp Suite
- OWASP ZAP
- sqlmap
- Web application security scanners

### Important

Tools should be used only against:

- Personal laboratory systems
- Intentionally vulnerable applications
- Systems for which testing authorization exists

The purpose is to identify and remediate vulnerabilities.

---

# 23. Role of Automated Tools

Automated tools can help with:

- Detecting potential injection points
- Repeating controlled tests
- Collecting evidence
- Supporting vulnerability assessment
- Verifying fixes

However:

> **Automated tools do not replace security understanding.**

A security professional must understand the application's behavior and validate tool results.

---

# 24. Common Indicators of SQL Injection

| Indicator | Possible Meaning |
|---|---|
| Database error | Unsafe query handling |
| Unexpected response | Input may affect query behavior |
| Different result count | Query logic may have changed |
| Unusual response time | Possible time-based behavior |
| Repeated suspicious requests | Possible automated testing/attack |
| WAF alert | Suspicious request detected |

These indicators do not automatically prove SQL Injection. Further authorized investigation is required.

---

# 25. SQL Injection Impact

A SQL Injection vulnerability may allow an attacker to:

- Access unauthorized data
- Modify database records
- Delete data
- Bypass application authentication
- Expose sensitive information
- Affect application availability

### CIA Impact

```text
          SQL Injection
                │
       ┌────────┼────────┐
       ↓        ↓        ↓
Confidentiality Integrity Availability
       ↓        ↓        ↓
 Data Leak   Data      Service/Data
             Change    Disruption
```

---

# 26. Basic Prevention

The primary defense remains:

## Parameterized Queries

```text
SQL Structure
      +
Parameters
      ↓
Database
```

The SQL structure is separated from user-provided values.

---

## Additional Controls

### Input Validation

Check:

- Type
- Length
- Format
- Allowed values

### Least Privilege

Give the database account only the permissions required by the application.

### Safe Error Handling

Do not expose detailed database errors to users.

### Secure Configuration

Use secure application and database configurations.

### Monitoring

Monitor application and database activity for suspicious behavior.

---

# 27. Defense-in-Depth

```text
              SQL Injection Defense
                       │
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
   Secure Coding   Database       Monitoring
        │           Security          │
        ↓              ↓              ↓
 Parameterized    Least Privilege  Logging
 Queries          Access Control    Alerts
 Validation       Secure Config     Detection
```

No single control should be considered sufficient.

---

# 28. Important Differences

## SQL Injection vs Blind SQL Injection

| SQL Injection | Blind SQL Injection |
|---|---|
| General category | Specific SQL Injection category |
| Information may be directly visible | Information is inferred indirectly |
| May expose errors/results | Often relies on behavior |

---

## SQL Injection vs Authentication Bypass

SQL Injection is a **vulnerability/attack technique**.

Authentication bypass is a **possible impact or outcome**.

```text
SQL Injection
      ↓
Query Manipulation
      ↓
Possible Authentication Bypass
```

Not every SQL Injection vulnerability results in authentication bypass.

---

# 29. Secure Development Principle

The most important principle is:

> **Treat all external input as untrusted.**

```text
External Input
      ↓
     Untrusted
      ↓
Validation
      ↓
Parameterized Query
      ↓
Database
```

---

# 30. Classroom Scenario

Consider a college student-management application.

The application allows students to search records.

```text
Student
   ↓
Search Form
   ↓
Web Application
   ↓
Database
```

If the application directly inserts search input into a dynamically constructed SQL statement, improper input handling may create SQL Injection risk.

A secure application instead uses:

```text
Student Input
      ↓
Parameterized Query
      ↓
Database
      ↓
Safe Result
```

### Lesson

The security problem is primarily caused by **unsafe query construction**, not by SQL itself.

---

# 31. Key Takeaways

✔ SQL Injection occurs when untrusted input can improperly influence SQL query structure.

✔ Major categories are:

- In-Band
- Blind
- Out-of-Band

✔ In-Band includes:

- Error-Based
- Union-Based

✔ Blind SQL Injection includes:

- Boolean-Based
- Time-Based

✔ SQL Injection assessment follows a structured methodology.

✔ Detection can use application behavior, logs, WAFs, and authorized security tools.

✔ SQL Injection can affect confidentiality, integrity, availability, and authentication.

✔ Parameterized queries are the primary defense.

✔ Least privilege, validation, safe error handling, and monitoring provide additional protection.

---

# Memory Map

```text
                 SQL Injection
                       │
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
    In-Band           Blind        Out-of-Band
       │               │
   ┌───┴───┐       ┌───┴────┐
   ↓       ↓       ↓        ↓
 Error   Union  Boolean    Time
   │       │       │        │
   └───────┴───────┴────────┘
              ↓
          Assessment
              ↓
      Detection & Impact
              ↓
      Parameterized Queries
              ↓
           Retesting
```

---

# Frequently Asked University Questions

## 2 Marks

1. What is Blind SQL Injection?
2. What is Error-Based SQL Injection?
3. What is Union-Based SQL Injection?
4. What is Boolean-Based SQL Injection?
5. What is Time-Based SQL Injection?
6. What is Out-of-Band SQL Injection?

---

## 5 Marks

1. Explain different types of SQL Injection.
2. Differentiate Error-Based and Blind SQL Injection.
3. Explain Boolean-Based and Time-Based Blind SQL Injection.
4. Explain the methodology of SQL Injection assessment.
5. Explain methods for detecting SQL Injection.

---

## 10 Marks

1. Explain different types of SQL Injection with suitable diagrams.
2. Explain SQL Injection assessment methodology and detection techniques.
3. Explain Blind SQL Injection and its different types.
4. Discuss the impact and detection of SQL Injection.

---

# Viva Questions

1. What is SQL Injection?
2. What is In-Band SQL Injection?
3. What is Error-Based SQL Injection?
4. What is Union-Based SQL Injection?
5. What is Blind SQL Injection?
6. What is Boolean-Based Blind SQL Injection?
7. What is Time-Based Blind SQL Injection?
8. What is Out-of-Band SQL Injection?
9. What is an input point?
10. Why is understanding normal application behavior important?
11. What is the purpose of retesting?
12. Name some authorized SQL Injection testing tools.
13. What is the primary defense against SQL Injection?
14. Why is least privilege important?
15. How can SQL Injection affect the CIA Triad?

---

# Next Lecture

## Module 5 – Lecture 3: Advanced SQL Injection & Defense

We will study:

- SQL Injection Signature Evasion
- Limitations of Simple Filters
- Detection and Monitoring
- Secure Coding Practices
- Parameterized Queries
- Stored Procedures
- Least Privilege
- WAF and Defense-in-Depth
- SQL Injection Applications
- Network Troubleshooting
- Network Security Monitoring
- Tech Support Scams
- Case Study
- Module 5 Revision
