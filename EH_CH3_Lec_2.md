# Ethical Hacking (2413CYM5T1)

# Module 3
# Lecture 2
# SNMP, LDAP, SMTP and DNS Enumeration

**Duration:** 1 Hour

**Module:** 3

**CO Mapping:** CO3

---

# Recap of Previous Lecture

In the previous lecture, we studied:

- Enumeration Concepts
- Difference between Scanning and Enumeration
- NetBIOS Enumeration
- NetBIOS Tools
- Enumeration Countermeasures

Today we will learn how attackers enumerate other important network services.

---

# What is Protocol Enumeration?

After identifying open ports, attackers interact with specific network protocols to extract useful information.

Different protocols reveal different types of information.

```text
Port Scanning

↓

Open Ports Found

↓

Protocol Enumeration

↓

Users
Services
Configurations
Resources
```

---

# Common Enumeration Protocols

| Protocol | Port | Information Obtained |
|----------|------|----------------------|
| SNMP | 161 | Devices, Interfaces, Routing Information |
| LDAP | 389 | Users, Groups, Active Directory |
| SMTP | 25 | Email Users |
| DNS | 53 | Hostnames, Domains, DNS Records |

---

# SNMP Enumeration

## What is SNMP?

**SNMP (Simple Network Management Protocol)** is used to monitor and manage network devices such as:

- Routers
- Switches
- Firewalls
- Printers
- Servers
- Wireless Access Points

Administrators use SNMP to monitor the health and performance of devices remotely.

---

## Why Do Attackers Target SNMP?

If SNMP is poorly configured, it may expose valuable information such as:

- Device Name
- Operating System
- Running Services
- Network Interfaces
- Routing Tables
- ARP Cache
- Software Version
- System Uptime
- Contact Information
- Device Location

---

# SNMP Architecture

```text
                SNMP Manager

                     │

         Request / Response

                     │

               UDP Port 161

                     │

                SNMP Agent

                     │

              Network Device
```

The **SNMP Manager** requests information, while the **SNMP Agent** on the device responds.

---

# SNMP Versions

| Version | Security |
|----------|----------|
| SNMPv1 | Weak |
| SNMPv2c | Community String Authentication |
| SNMPv3 | Authentication + Encryption (Recommended) |

---

# Community Strings

SNMP uses **Community Strings** as passwords.

Common default values:

```
public

private
```

If these are not changed, attackers can easily gather sensitive information.

---

# SNMP Enumeration Tool

Tool:

```
snmpwalk
```

---

## Example 1

Retrieve system information.

```bash
snmpwalk -v2c -c public 192.168.1.10
```

Explanation:

- `-v2c` → SNMP Version
- `-c public` → Community String
- `192.168.1.10` → Target IP

---

### Sample Output

```text
Hostname : Router01

Location : Server Room

Contact : admin@example.com

Uptime : 5 Days
```

---

## Example 2

Retrieve interface information.

```bash
snmpwalk -v2c -c public 192.168.1.10 interfaces
```

Possible information:

- Interface Name
- MAC Address
- Bandwidth
- Status

---

# Real-World Example

Suppose a company router is configured with:

```
Community String

public
```

An attacker runs:

```bash
snmpwalk -v2c -c public 192.168.1.1
```

The router reveals:

- Device Name
- IOS Version
- Uptime
- Routing Information
- Interfaces

Without exploiting any vulnerability, the attacker now understands the internal network infrastructure.

---

# LDAP Enumeration

## What is LDAP?

**LDAP (Lightweight Directory Access Protocol)** is used to access and manage directory services.

It is widely used in **Microsoft Active Directory** environments.

---

## Information Stored in LDAP

- User Accounts
- Groups
- Organizational Units (OU)
- Computers
- Password Policies
- Email Addresses
- Departments

---

# LDAP Architecture

```text
User

↓

LDAP Client

↓

LDAP Server

↓

Active Directory Database
```

---

# Why is LDAP Important?

Attackers use LDAP Enumeration to discover:

- Domain Users
- Administrator Accounts
- Security Groups
- Domain Structure
- Computer Objects

---

# LDAP Enumeration Tool

Linux command:

```bash
ldapsearch
```

Example:

```bash
ldapsearch -x -h 192.168.1.20
```

Possible Output:

```text
Domain

Employees

Users

Groups

HR Department

Finance Department
```

---

# Real-World Example

An ethical hacker performing an authorized assessment discovers:

- 350 Employee Accounts
- Domain Administrators
- Finance Department
- Human Resources Department

This information may later be used to verify security configurations or identify unnecessary exposure.

---

# SMTP Enumeration

## What is SMTP?

**SMTP (Simple Mail Transfer Protocol)** is the standard protocol used for **sending email** over a network.

- Default Port: **25**
- Secure Ports:
  - **465 (SMTPS)**
  - **587 (Submission with STARTTLS)**

SMTP is responsible only for **sending emails**. Receiving emails is handled by protocols such as **POP3** and **IMAP**.

---

# Why Do Attackers Enumerate SMTP?

Many SMTP servers reveal information about valid users if they are improperly configured.

An attacker may identify:

- Valid Email Addresses
- Existing User Accounts
- Mail Server Information
- Domain Names

This information is often used in:

- Phishing Attacks
- Password Attacks
- Business Email Compromise (BEC)
- Social Engineering

---

# SMTP Enumeration Process

```text
Attacker

      │

Connects to SMTP Server

      │

Issues SMTP Commands

      │

Server Responds

      │

Valid Users
Email Accounts
Mail Server Information
```

---

# SMTP Enumeration Commands

Some SMTP servers support user verification commands.

### VRFY Command

Checks whether a mailbox exists.

Example:

```text
VRFY sachin
```

Possible Response:

```text
250 User Exists
```

or

```text
550 User Unknown
```

---

### EXPN Command

Expands a mailing list.

Example:

```text
EXPN accounts
```

Possible Output:

```text
rahul@example.com
priya@example.com
amit@example.com
```

Many modern mail servers disable this command for security reasons.

---

# Connecting to an SMTP Server

Using Telnet:

```bash
telnet mail.example.com 25
```

After connecting:

```text
HELO attacker

VRFY admin

QUIT
```

> **Note:** Demonstrate only in a controlled laboratory environment or explain using screenshots if Telnet is unavailable.

---

# Real-World Example

Suppose an organization has the following email addresses:

```
hr@company.com

finance@company.com

admin@company.com
```

An attacker discovers that **admin@company.com** exists.

Instead of sending phishing emails to random users, the attacker can now target a specific administrator.

This demonstrates how seemingly harmless information can support more advanced attacks.

---

# DNS Enumeration

## What is DNS?

**DNS (Domain Name System)** translates human-readable domain names into IP addresses.

Example:

```
www.google.com

↓

142.250.xxx.xxx
```

Without DNS, users would have to remember IP addresses instead of domain names.

---

# Why is DNS Enumeration Important?

DNS can reveal valuable information about an organization.

Examples include:

- Host Names
- Web Servers
- Mail Servers
- Name Servers
- Internal Subdomains
- IP Addresses

---

# DNS Architecture

```text
User

↓

DNS Resolver

↓

DNS Server

↓

IP Address Returned
```

---

# Common DNS Records

| Record | Purpose |
|----------|----------|
| A | Maps Domain to IPv4 Address |
| AAAA | Maps Domain to IPv6 Address |
| MX | Mail Server |
| NS | Name Server |
| CNAME | Alias Record |
| TXT | Text Information (SPF, DKIM, etc.) |

---

# DNS Enumeration Tools

Common Linux commands:

```bash
nslookup
```

```bash
dig
```

```bash
host
```

---

# Example 1 – nslookup

```bash
nslookup google.com
```

Sample Output:

```text
Name:

google.com

Address:

142.250.xxx.xxx
```

Purpose:

Retrieves the IP address of a domain.

---

# Example 2 – host

```bash
host google.com
```

Possible Output:

```text
google.com has address 142.250.xxx.xxx
```

---

# Example 3 – dig

```bash
dig google.com
```

This command provides detailed DNS information including:

- Query Time
- Name Server
- TTL
- DNS Records

---

# Example 4 – MX Record Lookup

```bash
dig google.com MX
```

Sample Output:

```text
10 smtp.google.com
```

This identifies the organization's mail server.

---

# Example 5 – Name Server Lookup

```bash
dig google.com NS
```

Possible Output:

```text
ns1.google.com

ns2.google.com
```

---

# Example 6 – Reverse DNS Lookup

```bash
dig -x 8.8.8.8
```

Purpose:

Find the domain name associated with an IP address.

---

# Real-World Example

Suppose an attacker performs DNS enumeration on:

```
example.com
```

The attacker discovers:

- mail.example.com
- vpn.example.com
- dev.example.com
- test.example.com

The **development** or **test** servers may have weaker security than production systems.

This information helps prioritize further security assessments.

---

# Comparison of Enumeration Protocols

| Protocol | Default Port | Information Obtained |
|----------|-------------:|----------------------|
| NetBIOS | 137–139 | Computer Names, Shares |
| SNMP | 161 | Device Configuration |
| LDAP | 389 | Users, Groups, Domain Information |
| SMTP | 25 | Email Users, Mail Server |
| DNS | 53 | Hostnames, DNS Records |

---

# Enumeration Countermeasures

Organizations should adopt the following practices:

- Disable unnecessary services.
- Change default SNMP community strings.
- Use **SNMPv3** instead of SNMPv1/v2c.
- Disable SMTP user verification commands (`VRFY`, `EXPN`) where possible.
- Restrict LDAP access to authorized users.
- Prevent unauthorized DNS zone transfers.
- Apply the latest security patches.
- Monitor logs for repeated enumeration attempts.
- Configure firewalls to restrict unnecessary access.

---

# Quick Revision

```text
Enumeration

↓

SNMP

↓

Device Information

↓

LDAP

↓

Users & Active Directory

↓

SMTP

↓

Email Accounts

↓

DNS

↓

Hostnames & DNS Records
```

---

# Summary

In this lecture, we studied:

- Protocol Enumeration
- SNMP Enumeration
- SNMP Community Strings
- LDAP Enumeration
- SMTP Enumeration
- DNS Enumeration
- Enumeration Tools
- Practical Commands
- Security Countermeasures

---

# Think Like an Ethical Hacker

During an authorized penetration test, the following information was collected:

```
SNMP:
Router01
Location: Server Room

LDAP:
Administrator
HR Department
Finance Department

SMTP:
admin@company.com

DNS:
vpn.company.com
mail.company.com
```

### Discussion Questions

1. Which information is the most sensitive?
2. Which system would you assess first?
3. What security recommendations would you provide to the organization?

Discuss your answers before proceeding to the next lecture.

---

# Viva Questions

1. What is SNMP?
2. What is the purpose of SNMP?
3. What is a community string?
4. Differentiate SNMPv2c and SNMPv3.
5. What is LDAP?
6. What information is stored in Active Directory?
7. What is SMTP?
8. What are the `VRFY` and `EXPN` commands?
9. What is DNS Enumeration?
10. Differentiate `dig`, `host`, and `nslookup`.
11. What is an MX record?
12. Why should DNS zone transfers be restricted?

---

# University Examination Questions

## 5 Marks

1. Explain SNMP Enumeration with suitable commands and examples.
2. Explain LDAP Enumeration and its significance in Active Directory environments.
3. Explain DNS Enumeration using suitable tools and commands.
4. Describe SMTP Enumeration and discuss the associated security risks.

---

## 3 Marks

1. What is a community string in SNMP?
2. List any four DNS record types.
3. State any four countermeasures against protocol enumeration attacks.

---

# Conclusion

Enumeration extends beyond discovering hosts and open ports—it involves extracting meaningful information from network services such as **SNMP, LDAP, SMTP, and DNS**. Ethical hackers use these protocols during authorized security assessments to identify unnecessary information exposure, while defenders secure these services through proper configuration, strong authentication, access controls, and continuous monitoring.