# ETHICAL HACKING (2413CYM5T1)

# Module 1 – Introduction to Ethical Hacking

# Lecture 4

# Footprinting through Web Services, Social Networking Sites & Website Footprinting

---

# Recap

In the previous lecture, we studied:

* Reconnaissance
* Footprinting
* Passive Footprinting
* Active Footprinting
* Search Engine Footprinting
* OSINT

Today we will learn how attackers gather information from publicly available online services.

---

# Information Sources Used by Attackers

```text
                Internet
                    │
    ┌───────────────┼────────────────┐
    │               │                │
Search Engine   Web Services   Social Media
                    │
                 Websites
```

Every publicly available source may reveal valuable information.

---

# I. Web Service Footprinting

## Definition

Web Service Footprinting is the process of collecting information from online services that provide publicly accessible information about an organization or domain.

Examples include:

* Google Maps
* GitHub
* Shodan
* Pastebin
* Archive.org
* Certificate Transparency Logs

---

# Why Do Attackers Use Web Services?

They help identify:

* Domain ownership
* Server information
* Open services
* Exposed source code
* Public documents
* Historical website versions

---

# Example 1 – GitHub

Many developers accidentally upload:

* API Keys
* Passwords
* Database Credentials
* Source Code

An attacker searches GitHub before attacking.

---

# Example 2 – Google Maps

Google Maps provides:

* Office Location
* Working Hours
* Contact Numbers
* Photos
* Employee Reviews

Even physical security information can help attackers.

---

# Example 3 – Archive.org (Wayback Machine)

Old versions of websites may reveal:

* Deleted pages
* Hidden directories
* Old login portals
* Previous contact details

Sometimes information removed from the current website is still publicly available.

---

# Example 4 – Shodan

Shodan is called the **Search Engine for Internet-connected Devices**.

It indexes:

* Web Servers
* Routers
* CCTV Cameras
* IoT Devices
* Firewalls

Security professionals use it to identify exposed systems.

Attackers may misuse it to locate vulnerable devices.

> **Ethical Note:** Use Shodan only for authorized security assessments.

---

# II. Social Networking Footprinting

## Definition

Social Networking Footprinting is the process of collecting information from social media platforms.

---

# Popular Sources

* LinkedIn
* Facebook
* Instagram
* X (formerly Twitter)
* YouTube

---

# Information Collected

Attackers may discover:

* Employee Names
* Email IDs
* Designations
* Office Locations
* Technologies Used
* Organizational Structure

---

# Real Example

A faculty member posts:

> "Successfully deployed a new Moodle server running Ubuntu 24.04."

An attacker now knows:

* The organization uses Moodle.
* The operating system is Ubuntu.
* The server may become a future target if vulnerabilities are found.

This demonstrates how harmless posts can reveal valuable technical information.

---

# LinkedIn – A Gold Mine for Attackers

Employees often share:

* Job Titles
* Skills
* Technologies
* Certificates
* Projects

Example:

> "Working as Network Administrator using Cisco ASA Firewall."

This helps attackers understand the organization's infrastructure.

---

# Identity Theft

Sometimes attackers create fake profiles.

Purpose:

* Gain trust
* Collect confidential information
* Launch phishing attacks

---

# III. Website Footprinting

## Definition

Website Footprinting is the process of collecting technical and non-technical information from a website.

---

# Information Gathered

* Domain Name
* Contact Details
* Email Addresses
* Technologies Used
* Login Pages
* Directory Structure
* Public Documents
* Forms
* Subdomains

---

# Website Components Examined

```text
Website
   │
   ├── Home Page
   ├── Contact Page
   ├── Login Page
   ├── About Us
   ├── Downloads
   └── PDF Files
```

---

# Real Example

Suppose the college website contains:

* Faculty Email IDs
* ERP Login Portal
* Staff Directory
* Downloadable PDFs
* Academic Calendar

An attacker now has useful information for planning phishing attacks.

---

# Public Documents

Many organizations upload:

* PDF Files
* Word Documents
* Excel Sheets

These files may contain metadata such as:

* Author Name
* Software Used
* Computer Name
* Creation Date

Metadata can reveal valuable information.

---

# Robots.txt

Many websites include a file named:

```text
robots.txt
```

Its purpose is to guide search engine crawlers.

Sometimes administrators mistakenly list sensitive directories.

Example:

```text
Disallow: /admin/
Disallow: /backup/
```

Although intended for search engines, these entries may reveal hidden locations.

---

# Ethical Note

Collecting publicly available information is not always illegal.

However:

* Accessing restricted resources
* Bypassing authentication
* Downloading confidential data
* Exploiting discovered information without authorization

is unethical and may violate the law.

Ethical hackers perform footprinting **only with proper authorization**.

---

# Summary

Today we learned:

* Web Service Footprinting
* Social Networking Footprinting
* Website Footprinting
* Metadata
* robots.txt
* Identity Theft
* Information Leakage

---


# University Examination Questions


1. Explain Website Footprinting.
2. Explain Social Networking Footprinting.
3. Explain Web Service Footprinting.
4. Explain different sources used in Footprinting with suitable examples.
5. Explain Website Footprinting and the information that can be gathered from websites.
6. Explain Social Networking Footprinting and discuss its security implications.

---
