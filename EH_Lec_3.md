# ETHICAL HACKING (2413CYM5T1)

# Module 1 – Introduction to Ethical Hacking

# Lecture 3

# Footprinting and Reconnaissance

---

# Recap

In the previous lecture, we studied:

* Threat
* Vulnerability
* Risk
* Attack
* Traditional Hacking Cycle
* Cyber Kill Chain

We observed that both attack models begin with:

```text
Reconnaissance
```

Before launching an attack, an attacker first collects information about the target.

This process is known as **Footprinting**.

---

# Why Information Gathering?

Imagine you are participating in a cricket match.

Would you go directly to bat without knowing:

* Opponent's bowling attack?
* Pitch condition?
* Field placement?

Probably not.

Similarly,

A hacker never attacks blindly.

The hacker first gathers as much information as possible.

The better the information, the higher the chances of a successful attack.

---

# Reconnaissance

## Definition

Reconnaissance is the process of collecting information about a target before attempting an attack.

It is the **first phase** of every cyber attack.

---

## Objectives of Reconnaissance

* Identify target systems
* Identify employees
* Discover IP addresses
* Find domain information
* Identify technologies used
* Understand network structure

---

# What is Footprinting?

## Definition

Footprinting is the process of collecting detailed information about a target organization, network, system or individual.

Footprinting is a part of the Reconnaissance phase.

---

# Objectives of Footprinting

* Gather publicly available information
* Identify possible vulnerabilities
* Reduce attack effort
* Plan future attacks

---

# Real Example

Suppose an attacker targets a college.

The attacker collects:

* College Website
* Faculty Details
* Student Portal
* ERP URL
* Email Addresses
* Social Media Accounts

The attacker has not attacked anything yet.

Only information has been collected.

This is Footprinting.

---

# Reconnaissance vs Footprinting

| Reconnaissance                      | Footprinting                             |
| ----------------------------------- | ---------------------------------------- |
| Overall information gathering phase | Techniques used to collect information   |
| First phase of attack               | Activity performed during reconnaissance |
| Broad concept                       | Specific process                         |

---

# Types of Footprinting

```text
Footprinting
      │
      ├───────────────┐
      │               │
Passive         Active
```

---

# Passive Footprinting

## Definition

Passive Footprinting is the process of collecting information **without directly interacting** with the target system.

The target usually does not know information is being collected.

---

## Sources

* Google Search
* Company Website
* LinkedIn
* Facebook
* Instagram
* Job Portals
* News Articles

---

## Advantages

* Safe
* Difficult to detect
* No direct communication

---

## Disadvantages

* Information may be outdated
* Limited technical details

---

# Example

Searching:

```
ABC Engineering College Official Website
```

Reading publicly available information.

No attack.

No interaction.

Passive Footprinting.

---

# Active Footprinting

## Definition

Active Footprinting involves directly interacting with the target to obtain information.

---

## Examples

* DNS Queries
* Port Scanning
* Network Scanning
* Banner Grabbing
* Ping Sweep

---

## Advantages

* Accurate information
* More technical details

---

## Disadvantages

* Easier to detect
* May trigger IDS or Firewall alerts

---

# Example

Running:

```
ping example.com
```

or

```
nslookup example.com
```

The target system receives your request.

Therefore,

Active Footprinting.

---

# Passive vs Active Footprinting

| Passive               | Active                |
| --------------------- | --------------------- |
| No direct interaction | Direct interaction    |
| Difficult to detect   | Easier to detect      |
| Safe                  | Can trigger alarms    |
| Public information    | Technical information |

---

# Search Engine Footprinting

One of the easiest methods of passive footprinting.

Search engines contain enormous amounts of publicly available information.

Attackers use advanced search techniques to discover hidden information.

---

# Information Found Using Search Engines

* Official Website
* Email Addresses
* Phone Numbers
* PDF Files
* Login Pages
* Images
* Employee Information
* Public Documents

---

# Search Operators

Google provides special search operators.

Examples:

### Search a specific website

```
site:example.com
```

---

### Search PDF files

```
site:example.com filetype:pdf
```

---

### Search login pages

```
site:example.com login
```

---

### Search contact information

```
site:example.com contact
```

---

# Note on Google Dorking

Google Dorking (Google Hacking) uses advanced search operators to locate publicly available information.

It does **not** mean hacking Google's servers.

It simply means using Google's search capabilities more effectively.

**Ethical Note:**

Use these techniques only for authorized security assessments.

---

# OSINT (Open Source Intelligence)

## Definition

OSINT is the process of collecting information from publicly available sources.

Examples:

* Websites
* Government Records
* Social Media
* News
* Blogs
* Public Documents

---

# Why is OSINT Important?

Organizations unknowingly publish valuable information.

Examples:

* Employee email IDs
* Office locations
* Internal phone numbers
* Technology stack
* Job advertisements

Attackers combine all this information to prepare future attacks.

---


# Summary

✓ Every cyber attack begins with Reconnaissance.

✓ Footprinting is part of Reconnaissance.

✓ Passive Footprinting does not directly interact with the target.

✓ Active Footprinting directly communicates with the target.

✓ Search Engines are powerful footprinting tools.

✓ OSINT plays an important role in information gathering.

---

# University Questions

* Differentiate Passive and Active Footprinting.
* Explain Objectives of Footprinting.
* Explain Search Engine Footprinting.
* Define Footprinting and Explain Footprinting with suitable examples.
* Explain Reconnaissance and types of Footprinting.
* Explain Search Engine Footprinting and its significance in Ethical Hacking.

---

# Next Lecture

Website Footprinting

Email Footprinting

Whois Footprinting

DNS Footprinting
