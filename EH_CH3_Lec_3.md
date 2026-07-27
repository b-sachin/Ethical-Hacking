# Ethical Hacking (2413CYM5T1)

# Module 3
# Lecture 3
# NFS & NTP Enumeration, Enumeration Countermeasures and Case Study

**Duration:** 1 Hour

**Module:** 3

**CO Mapping:** CO3

---

# Recap

So far we have studied:

- NetBIOS Enumeration
- SNMP Enumeration
- LDAP Enumeration
- SMTP Enumeration
- DNS Enumeration

Today's lecture completes the Enumeration phase.

---

# NFS Enumeration

## What is NFS?

**Network File System (NFS)** is a file sharing protocol developed by Sun Microsystems.

It allows one Linux/Unix system to access files stored on another system over a network.

Default Port

```
2049
```

---

# Why Do Attackers Enumerate NFS?

If NFS is improperly configured, attackers may discover:

- Shared Directories
- Backup Files
- Configuration Files
- Sensitive Documents
- User Home Directories

Sometimes these directories are accessible without authentication.

---

# NFS Architecture

```text
Client

      │

Mount Request

      │

NFS Server

      │

Shared Directory
```

---

# NFS Enumeration Tool

Linux provides the following utility.

```bash
showmount
```

---

## Example 1

Display exported directories.

```bash
showmount -e 192.168.1.20
```

Sample Output

```text
Export list

/home

/shared

/backup
```

Observation

The attacker now knows which folders are shared over the network.

---

## Example 2

Display connected clients.

```bash
showmount -a 192.168.1.20
```

Possible Output

```text
192.168.1.15

192.168.1.18
```

This reveals systems currently accessing the NFS server.

---

# rpcinfo Command

NFS relies on Remote Procedure Call (RPC).

To identify RPC services:

```bash
rpcinfo -p 192.168.1.20
```

Sample Output

```text
Program

Port

mountd

2049

nfs

2049
```

---

# Real-World Example

Suppose a backup server exports:

```
/backup
```

without proper access restrictions.

An attacker could access:

- Database Backups
- Source Code
- Password Files
- Employee Documents

No exploitation is required—the data is exposed due to poor configuration.

---

# NTP Enumeration

## What is NTP?

**Network Time Protocol (NTP)** synchronizes the clocks of computers connected to a network.

Default Port

```
UDP 123
```

Accurate system time is essential for:

- Logging
- Authentication
- Digital Certificates
- Distributed Systems

---

# Why Do Attackers Enumerate NTP?

NTP may reveal:

- Server Time
- Software Version
- Connected Clients
- Synchronization Sources

Although limited, this information helps attackers understand the target environment.

---

# NTP Architecture

```text
Client

      │

Time Request

      │

NTP Server

      │

Current Time
```

---

# NTP Enumeration Tool

Linux command:

```bash
ntpq
```

---

## Example

Display NTP peers.

```bash
ntpq -p 192.168.1.20
```

Possible Output

```text
Remote Server

Delay

Offset

Jitter
```

This shows synchronization details between systems.

---

# Why is Time Synchronization Important?

Imagine three servers:

```text
Web Server

10:00:05

↓

Database Server

09:59:45

↓

Firewall

10:01:20
```

If a cyberattack occurs, inconsistent timestamps make forensic investigation difficult.

Correct time synchronization helps investigators reconstruct events accurately.

---

# Complete Enumeration Workflow

Ethical hackers generally perform enumeration in the following order.

```text
Host Discovery

↓

Port Scanning

↓

Service Detection

↓

NetBIOS Enumeration

↓

SNMP Enumeration

↓

LDAP Enumeration

↓

SMTP Enumeration

↓

DNS Enumeration

↓

NFS Enumeration

↓

NTP Enumeration

↓

Vulnerability Assessment
```

Each step builds on the information gathered in the previous phase.

---

# Enumeration Case Study

## Scenario

A company has deployed a new file server.

An authorized penetration tester performs enumeration.

### Findings

```
NetBIOS

↓

FILESERVER01

SNMP

↓

Cisco IOS Version

LDAP

↓

Administrator Accounts

SMTP

↓

admin@company.com

DNS

↓

backup.company.com

NFS

↓

/backup

NTP

↓

Internal Time Server
```

---

## Analysis

Although no passwords were cracked and no vulnerabilities were exploited, the tester now knows:

- The server name
- Administrator accounts
- Internal email addresses
- Backup server
- Shared directories
- Network infrastructure

This demonstrates why organizations must limit unnecessary information disclosure.

---

# Enumeration Countermeasures

Organizations should implement multiple defensive measures.

## Disable Unnecessary Services

Remove unused protocols such as:

- NetBIOS
- Telnet
- FTP

---

## Restrict Access

Limit access to:

- LDAP
- SNMP
- NFS
- SMTP

using firewalls and Access Control Lists (ACLs).

---

## Secure SNMP

- Disable default community strings.
- Use SNMPv3.
- Restrict management access.

---

## Secure DNS

- Disable Zone Transfers.
- Restrict Recursive Queries.
- Monitor DNS Logs.

---

## Secure SMTP

- Disable VRFY and EXPN commands.
- Enable SMTP Authentication.
- Use TLS encryption.

---

## Secure NFS

- Export only required directories.
- Restrict client IP addresses.
- Use proper file permissions.

---

## Monitor Logs

Detect repeated enumeration attempts using:

- IDS
- IPS
- SIEM

---

## Apply Security Updates

Regularly patch:

- Operating Systems
- Network Devices
- Servers
- Applications

---

# Best Practices for Ethical Hackers

- Obtain written authorization.
- Perform only approved activities.
- Minimize impact on target systems.
- Document every command executed.
- Protect collected information.
- Report findings responsibly.

---

# Summary

In this lecture we covered:

- NFS Enumeration
- NTP Enumeration
- Enumeration Workflow
- Enumeration Case Study
- Enumeration Countermeasures
- Best Practices

Enumeration is now complete.

The next step is:

```text
Enumeration

↓

Vulnerability Assessment
```

---

# Quick Revision

| Protocol | Port | Information Obtained |
|----------|------|----------------------|
| NetBIOS | 137–139 | Computer Names |
| SNMP | 161 | Device Information |
| LDAP | 389 | Users & Groups |
| SMTP | 25 | Email Accounts |
| DNS | 53 | DNS Records |
| NFS | 2049 | Shared Directories |
| NTP | 123 | Time Information |

---

# Viva Questions

1. What is NFS?
2. Which port is used by NFS?
3. What is the purpose of `showmount`?
4. What is `rpcinfo` used for?
5. What is NTP?
6. Which port is used by NTP?
7. Why is time synchronization important?
8. What information can be obtained from NFS Enumeration?
9. Mention four Enumeration countermeasures.
10. Why is Enumeration important before Vulnerability Assessment?

---

# University Examination Questions

## 5 Marks

1. Explain NFS Enumeration with suitable commands and examples.
2. Explain NTP Enumeration and discuss its security implications.
3. Describe Enumeration Countermeasures adopted by organizations.
4. Explain the complete Enumeration methodology used during penetration testing.

---

## 3 Marks

1. State any four Enumeration protocols.
2. What is the purpose of `showmount`?
3. Mention any four countermeasures against Enumeration attacks.

---

# Conclusion

Enumeration provides attackers and ethical hackers with detailed information about systems, users, services, and network resources. Understanding how protocols such as NetBIOS, SNMP, LDAP, SMTP, DNS, NFS, and NTP expose information enables security professionals to identify weaknesses, reduce unnecessary information disclosure, and strengthen the organization's overall security posture.

In the next lecture, we move from **collecting information** to **evaluating weaknesses** through **Vulnerability Assessment**, where we will learn how to identify, classify, and prioritize security vulnerabilities before they are exploited.