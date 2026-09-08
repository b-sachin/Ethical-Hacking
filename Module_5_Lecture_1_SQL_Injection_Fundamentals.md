# ETHICAL HACKING (2413CYM5T1)

# Module 5 – SQL Injection

# Lecture 1 – SQL Injection Fundamentals

**Course Outcome:** CO5  
**Duration:** 1 Hour

---

# Learning Outcomes

After completing this lecture, students will be able to:

- Explain the concept of SQL Injection.
- Understand how web applications interact with databases.
- Explain the root cause of SQL Injection.
- Differentiate between normal SQL queries and injected input.
- Identify major types of SQL Injection.
- Explain the impact of SQL Injection.
- Understand basic SQL Injection prevention techniques.

---

# 1. Introduction

Modern web applications commonly use databases to store information such as:

- User accounts
- Password information
- Product details
- Student records
- Customer information
- Transaction records

A web application communicates with the database using **SQL (Structured Query Language)**.

```text
User
  ↓
Web Application
  ↓
SQL Query
  ↓
Database
  ↓
Result
  ↓
Web Application
  ↓
User
```

If user input is handled incorrectly, an attacker may manipulate the SQL query.

This vulnerability is known as **SQL Injection**.

---

# 2. What is SQL Injection?

## Definition

**SQL Injection (SQLi)** is a web application vulnerability in which untrusted user input is improperly incorporated into an SQL query, allowing the query's intended logic to be altered.

### Simple Idea

```text
User Input
    ↓
Web Application
    ↓
SQL Query Construction
    ↓
Database
```

If the application treats user input as part of SQL syntax instead of data, SQL Injection may occur.

---

# 3. Why Does SQL Injection Occur?

The main cause is **improper handling of user input**.

Common causes include:

- Dynamic SQL query construction
- String concatenation
- Lack of input validation
- Lack of parameterized queries
- Poor database security configuration
- Excessive database privileges

---

# 4. Normal Database Authentication

Consider a login form:

```text
Username: alice
Password: ********
```

The application may conceptually create a query like:

```sql
SELECT * FROM users
WHERE username = 'alice'
AND password = 'password';
```

The database checks the supplied values and returns the result.

---

# 5. Vulnerable Query Construction

A poorly designed application may construct SQL using string concatenation.

Conceptually:

```text
"SELECT ... WHERE username = '" + username + "' ..."
```

The problem is that the application does not properly separate:

```text
SQL Code
   +
User Data
```

The user's input can therefore affect the structure or meaning of the SQL statement.

---

# 6. Secure Query Construction

A secure application uses **parameterized queries / prepared statements**.

Conceptually:

```text
SQL Statement
      +
Parameters
      ↓
Database
```

The SQL structure is defined separately from user-supplied data.

Example:

```sql
SELECT * FROM users
WHERE username = ? AND password = ?;
```

The values are supplied as parameters rather than being directly concatenated into the SQL statement.

---

# 7. Vulnerable vs Secure Approach

| Vulnerable Approach | Secure Approach |
|---|---|
| String concatenation | Parameterized queries |
| User input becomes part of SQL | User input treated as data |
| Higher SQLi risk | Strong SQLi protection |
| Difficult to maintain securely | Recommended practice |
| May allow query manipulation | Query structure remains fixed |

---

# 8. SQL Injection Attack Concept

The general concept is:

```text
Attacker-controlled Input
          ↓
      Web Application
          ↓
   Improperly Built Query
          ↓
        Database
          ↓
  Unexpected Query Behavior
```

The attacker attempts to make the database interpret input differently from what the developer intended.

---

# 9. Types of SQL Injection

SQL Injection can be broadly classified into:

```text
                  SQL Injection
                       │
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
    In-Band          Blind          Out-of-Band
        │              │
   ┌────┴────┐     ┌───┴────┐
   ↓         ↓     ↓        ↓
Error-Based Union  Boolean  Time-Based
```

---

# 10. In-Band SQL Injection

In **In-Band SQL Injection**, the attacker uses the same communication channel to send input and receive results.

Two common forms are:

- Error-Based SQL Injection
- Union-Based SQL Injection

---

# 11. Error-Based SQL Injection

**Error-Based SQL Injection** uses database error messages to obtain information about the database or query.

### Example Concept

```text
Malicious / Unexpected Input
          ↓
     Database Query
          ↓
      Database Error
          ↓
   Error Information
```

Detailed database errors may reveal:

- Database type
- Table or column information
- Query structure
- Internal application details

### Prevention

Applications should:

- Hide detailed database errors from users.
- Log errors securely on the server.
- Display generic error messages.

---

# 12. Union-Based SQL Injection

**Union-Based SQL Injection** abuses the SQL `UNION` operator to combine results from compatible queries.

### Concept

```text
Original Query
      +
Additional SELECT
      ↓
Combined Result
```

The application may unintentionally return database information that was not supposed to be exposed.

### Prevention

- Use parameterized queries.
- Validate input.
- Avoid dynamically constructed SQL.
- Apply least-privilege database permissions.

---

# 13. Blind SQL Injection

In **Blind SQL Injection**, the application does not directly display useful database errors or query results.

The attacker instead infers information from the application's behavior.

Two common forms are:

### Boolean-Based Blind SQLi

The attacker observes differences between:

```text
Condition TRUE
     ↓
Application Response A

Condition FALSE
     ↓
Application Response B
```

### Time-Based Blind SQLi

The attacker observes differences in application response time.

```text
Input
 ↓
Database Processing
 ↓
Response Time
 ↓
Inference
```

> Blind SQL Injection can be difficult to detect because the application may not display obvious database errors.

---

# 14. Out-of-Band SQL Injection

**Out-of-Band SQL Injection** uses a separate communication channel to obtain information from a vulnerable database/application environment.

It generally depends on specific database features and network conditions.

### Important Point

Out-of-band techniques are less common than in-band and blind SQL Injection.

---

# 15. SQL Injection Methodology – Overview

A security assessment generally follows a controlled process:

```text
Identify Application
        ↓
Identify Input Points
        ↓
Understand Application Behavior
        ↓
Check for Input Handling Issues
        ↓
Confirm Vulnerability Safely
        ↓
Assess Impact
        ↓
Recommend Remediation
        ↓
Retest
```

All testing must be performed only on systems for which authorization has been provided.

---

# 16. Common Input Points

SQL Injection may potentially occur wherever user-controlled input reaches database queries.

Examples:

- Login forms
- Search boxes
- Product filters
- URL parameters
- Form fields
- API parameters
- Cookies or headers, depending on application design

---

# 17. Impact of SQL Injection

A successful SQL Injection vulnerability may lead to:

- Unauthorized access
- Unauthorized data retrieval
- Data modification
- Data deletion
- Authentication bypass
- Exposure of sensitive information
- Loss of data integrity
- Application compromise

### Impact Flow

```text
SQL Injection
      ↓
Database Query Manipulation
      ↓
Unauthorized Database Operations
      ↓
Confidentiality / Integrity / Availability Impact
```

---

# 18. SQL Injection and CIA Triad

SQL Injection can affect all three components of the **CIA Triad**.

| CIA Component | Possible Impact |
|---|---|
| Confidentiality | Unauthorized data disclosure |
| Integrity | Unauthorized modification |
| Availability | Data deletion or service disruption |

---

# 19. Detection – Basic Indicators

Developers and security testers may look for:

- Unexpected database errors
- Different responses for different inputs
- Unusual application behavior
- Unexpected query results
- Suspicious database activity
- Repeated abnormal requests

Detection should be performed using authorized testing and monitoring.

---

# 20. SQL Injection Prevention

## 1. Parameterized Queries

The most important defense is to use:

**Prepared Statements / Parameterized Queries**

```text
SQL Structure
     +
Parameters
     ↓
Database
```

---

## 2. Input Validation

Validate input according to the application's requirements.

Examples:

- Expected data type
- Expected length
- Allowed format
- Allowed character set

> Input validation is useful, but it should not replace parameterized queries.

---

## 3. Least Privilege

The application database account should have only the permissions it actually requires.

```text
Application Account
        ↓
Minimum Required Permissions
        ↓
Reduced Impact
```

---

## 4. Safe Error Handling

Do not expose detailed database errors to end users.

Instead:

```text
User
 ↓
Generic Error Message

Server
 ↓
Detailed Error Logged Securely
```

---

## 5. Secure Coding Practices

Developers should:

- Avoid dynamic SQL where unnecessary.
- Use parameterized queries.
- Validate input.
- Review database permissions.
- Perform security testing.
- Keep frameworks and database software updated.

---

# 21. Defense-in-Depth

SQL Injection protection should not depend on one control.

```text
              SQL Injection Defense
                       │
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
 Secure Coding     Database        Monitoring
       │            Security            │
       ↓               ↓                ↓
Parameterized      Least Privilege   Logging
 Queries            Access Control    Alerts
 Validation         Secure Config     Detection
```

---

# 22. SQL Injection vs XSS

| SQL Injection | Cross-Site Scripting (XSS) |
|---|---|
| Targets database/query processing | Targets web browser/client-side execution |
| Exploits unsafe database query construction | Exploits unsafe handling of web content |
| Can expose or modify database data | Can affect users through injected browser-side content |
| Main defense: parameterized queries | Main defenses: output encoding, safe handling, CSP, etc. |

---

# 23. Important Terms

| Term | Meaning |
|---|---|
| SQL | Structured Query Language |
| SQL Injection | Manipulation of SQL through unsafe input handling |
| SQLi | Short form of SQL Injection |
| In-Band SQLi | Input and results use the same channel |
| Error-Based SQLi | Uses database error information |
| Union-Based SQLi | Uses SQL UNION behavior to combine results |
| Blind SQLi | Information inferred from application behavior |
| Boolean-Based SQLi | Inference based on true/false responses |
| Time-Based SQLi | Inference based on response timing |
| Parameterized Query | SQL query with separately supplied parameters |
| Prepared Statement | Predefined SQL statement executed with parameters |
| Least Privilege | Giving only required permissions |

---

# 24. Key Takeaways

✔ SQL Injection is caused by unsafe handling of user input in SQL queries.

✔ The major root cause is mixing **SQL code and user data**.

✔ Major types include:

- In-Band
- Blind
- Out-of-Band

✔ In-Band SQL Injection includes:

- Error-Based
- Union-Based

✔ Blind SQL Injection includes:

- Boolean-Based
- Time-Based

✔ SQL Injection can affect confidentiality, integrity, and availability.

✔ **Parameterized queries / prepared statements** are the primary defense.

✔ Input validation, least privilege, safe error handling, logging, and monitoring provide additional protection.

✔ SQL Injection testing must always be performed in an authorized environment.

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
           SQLi Risk
              ↓
     Parameterized Queries
              +
       Input Validation
              +
        Least Privilege
```

---

# Frequently Asked University Questions

## 2 Marks

1. Define SQL Injection.
2. What is SQLi?
3. What is Blind SQL Injection?
4. What is Error-Based SQL Injection?
5. What is a parameterized query?

---

## 5 Marks

1. Explain SQL Injection with a suitable example.
2. Explain different types of SQL Injection.
3. Differentiate between Error-Based and Union-Based SQL Injection.
4. Explain Blind SQL Injection and its types.
5. Explain SQL Injection countermeasures.

---

## 10 Marks

1. Explain SQL Injection, its types, impact, and countermeasures.
2. Explain the causes and prevention of SQL Injection in web applications.
3. Explain In-Band and Blind SQL Injection with suitable diagrams.

---

# Viva Questions

1. What is SQL Injection?
2. Why does SQL Injection occur?
3. What is the difference between SQL code and user data?
4. What is In-Band SQL Injection?
5. What is Error-Based SQL Injection?
6. What is Union-Based SQL Injection?
7. What is Blind SQL Injection?
8. What is Boolean-Based SQL Injection?
9. What is Time-Based SQL Injection?
10. What is a prepared statement?
11. Why are parameterized queries important?
12. What is the principle of least privilege?

---

# Next Lecture

## Module 5 – Lecture 2: SQL Injection Types & Methodology

We will study:

- In-Band SQL Injection in detail
- Blind SQL Injection in detail
- SQL Injection Methodology
- Authentication-related risks
- Impact assessment
- Detection approaches
- Authorized testing tools
- SQL Injection countermeasures
