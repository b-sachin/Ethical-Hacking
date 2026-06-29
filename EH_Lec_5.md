# ETHICAL HACKING (2413CYM5T1)

# Module 1 – Introduction to Ethical Hacking

# Lecture 5

# Email, Whois, DNS and Network Footprinting

---

# Recap

In the previous lectures, we studied:

* Reconnaissance
* Footprinting
* Passive & Active Footprinting
* Search Engine Footprinting
* Web Service Footprinting
* Social Network Footprinting
* Website Footprinting

Today, we will explore how attackers gather technical information about organizations using email systems, domain registration details, DNS, and network infrastructure.

---

# Footprinting Techniques Covered Today

```text
Footprinting
      │
      ├────────── Email
      ├────────── Whois
      ├────────── DNS
      └────────── Network
```

---

# 1. Email Footprinting

## Definition

Email Footprinting is the process of collecting information about individuals or organizations through their email addresses and email infrastructure.

Attackers use email information to prepare phishing, impersonation, and social engineering attacks.

---

# Information Obtained

* Email addresses
* Naming conventions
* Mail servers
* Organization domains
* Employee roles
* Contact details

---

# Real Example

Suppose a college website displays:

```
principal@abccollege.edu.in
hodit@abccollege.edu.in
examcell@abccollege.edu.in
```

The attacker understands:

* The organization's domain is **abccollege.edu.in**
* Email naming conventions are predictable.
* The college has dedicated functional mailboxes.

Now the attacker can create convincing phishing emails.

---

# Email Header Analysis

Every email contains hidden header information.

It may reveal:

* Sender IP Address
* Mail Server
* Time Stamp
* Email Route
* Authentication Results

---

# Example

A user receives an email claiming to be from a bank.

By checking the email header, the security analyst discovers:

* It originated from another country.
* The sender's domain is fake.
* SPF/DKIM verification failed.

This indicates a phishing attempt.

---

# Countermeasures

* Hide unnecessary email addresses.
* Use role-based email IDs where appropriate.
* Enable SPF, DKIM, and DMARC.
* Train users to identify phishing emails.

---

# 2. Whois Footprinting

## Definition

Whois Footprinting is the process of obtaining publicly available domain registration information.

---

# Information Available

* Domain Name
* Registrar
* Registration Date
* Expiry Date
* Name Servers
* Organization Details (if public)

---

# Real Example

Suppose the attacker searches:

```
abccollege.edu.in
```

Whois may reveal:

* Domain Registrar
* Registration Date
* Name Servers
* Administrative Contact

This helps the attacker understand the organization's infrastructure.

---

# Why is Whois Useful?

Attackers can identify:

* Related domains
* Hosting providers
* Name servers
* Potential attack surface

Ethical hackers use Whois during reconnaissance to map organizational assets.

---

# Countermeasures

* Use privacy protection services where applicable.
* Avoid exposing unnecessary administrative details.
* Regularly review domain registration information.

---

# 3. DNS Footprinting

## What is DNS?

DNS (Domain Name System) translates human-readable domain names into IP addresses.

Example:

```
www.example.com
        ↓
93.184.216.34
```

Without DNS, users would need to remember numerical IP addresses.

---

# DNS Footprinting

## Definition

DNS Footprinting is the process of collecting information from DNS records.

---

# Common DNS Records

| Record | Purpose                                          |
| ------ | ------------------------------------------------ |
| A      | Maps domain to IPv4 address                      |
| AAAA   | Maps domain to IPv6 address                      |
| MX     | Mail Server                                      |
| NS     | Name Server                                      |
| CNAME  | Alias                                            |
| TXT    | Additional information (SPF, verification, etc.) |

---

# Real Example

Suppose a company owns:

```
abccompany.com
```

DNS records reveal:

```
mail.abccompany.com
vpn.abccompany.com
erp.abccompany.com
```

The attacker now knows multiple publicly accessible services.

---

# DNS Zone Transfer

A DNS Zone Transfer copies DNS information from one server to another.

If misconfigured, it may expose:

* Internal servers
* Subdomains
* Network structure

Ethical hackers check whether zone transfers are properly secured.

---

# Countermeasures

* Disable unauthorized zone transfers.
* Restrict DNS queries.
* Monitor DNS logs.
* Remove unused DNS records.

---

# 4. Network Footprinting

## Definition

Network Footprinting is the process of identifying network-related information about a target.

---

# Information Collected

* IP Addresses
* Network Range
* Routers
* Firewalls
* Open Services
* Operating Systems

---

# Objectives

* Understand network architecture.
* Identify active devices.
* Discover exposed services.
* Prepare for vulnerability assessment.

---

# Real Example

Suppose an organization uses the following devices:

```
Router
Firewall
Web Server
Database Server
Mail Server
```

The attacker attempts to identify:

* Which systems are publicly accessible?
* Which ports are open?
* Which services are running?

---

# Network Mapping

```text
Internet
     │
 Firewall
     │
 ├─────────────┬──────────────┐
 │             │              │
Web Server   Mail Server   Database Server
```

This is called network mapping.

---

# Countermeasures

* Close unused ports.
* Configure firewalls correctly.
* Disable unnecessary services.
* Monitor network traffic.
* Use Intrusion Detection Systems (IDS).

---

# Comparison of Footprinting Techniques

| Technique | Information Collected           |
| --------- | ------------------------------- |
| Email     | Email IDs, Mail Servers         |
| Whois     | Domain Registration             |
| DNS       | DNS Records, Name Servers       |
| Network   | Devices, IP Addresses, Services |

---

# Ethical Considerations

Ethical hackers perform footprinting only:

* With written authorization.
* Within the defined scope.
* Without modifying target systems.
* Following organizational policies and applicable laws.

Unauthorized reconnaissance may violate legal and organizational policies.

---

# Key Takeaways

✔ Email Footprinting helps identify communication patterns.

✔ Whois reveals publicly available domain registration details.

✔ DNS translates domain names into IP addresses and exposes useful records.

✔ Network Footprinting identifies systems and services.

✔ Ethical hackers use these techniques to strengthen security, not to misuse information.

---

# University Examination Questions

1. Explain Whois Footprinting.
2. Explain DNS Footprinting.
3. Explain Email Footprinting.
4. Explain Network Footprinting.
5. Explain different technical footprinting techniques with suitable examples.
6. Explain DNS Footprinting and discuss its security implications.
7. Explain Whois, Email, and Network Footprinting with appropriate examples.

---
