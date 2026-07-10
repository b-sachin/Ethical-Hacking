# Ethical Hacking Lab (2413CYM5L1)

# Experiment 1

## Title

### 1.1 Discover Digital Footprints Found Both Online and in Metadata Using Appropriate Tools

### 1.2 Practice Investigative Procedures Including Bagging and Tagging Evidence, Maintaining Chain of Custody, and Photographing Evidence at the Scene

---

## Course Outcome

**CO1:** Develop a foundational understanding of ethical hacking principles and practices.

---

# Aim

- Discover publicly available digital footprints of an organization.
- Extract metadata from publicly available documents.
- Understand digital evidence handling procedures.
- Practice preparing evidence documentation.

---

# Learning Objectives

After completing this experiment, students will be able to:

- Perform passive footprinting.
- Collect publicly available information using OSINT.
- Analyze metadata present in digital files.
- Prepare Chain of Custody documentation.
- Understand proper evidence handling procedures.

---

# Software / Tools Required

- Google Search
- WHOIS Lookup (https://who.is/)
- DNS Lookup (https://dnschecker.org/)
- Metadata2Go (https://www.metadata2go.com/)
- Windows File Properties
- Internet Connection

---

# Problem Statement

You are part of an Ethical Hacking team hired by an organization to perform an **authorized preliminary security assessment**.

Before performing any vulnerability assessment, you need to collect publicly available information about the organization without directly attacking its systems.

In addition, you are required to understand how digital evidence should be collected and documented during a cybercrime investigation.

---

# Part A – Digital Footprinting

## Task 1 – Select Target Organization

Choose **any one** organization.

Examples

- Google
- Microsoft
- TCS
- Infosys
- OpenAI
- D. Y. Patil University
- Your College Website

Write the organization details below.

| Information | Details |
|------------|---------|
| Organization Name | |
| Website | |

---

## Task 2 – Basic Information Gathering

Using Google Search, collect the following information.

| Information | Observation |
|------------|-------------|
| Official Website | |
| Headquarters | |
| Contact Email | |
| Contact Number | |
| Careers Page | |
| LinkedIn Page | |
| Facebook / X / Instagram | |

---

## Task 3 – WHOIS Lookup

Visit

https://who.is/

Search for the selected domain.

Record the following information.

| Field | Observation |
|--------|-------------|
| Domain Name | |
| Registrar | |
| Registration Date | |
| Expiry Date | |
| Name Servers | |

**Take Screenshot-1**

---

## Task 4 – DNS Lookup

Visit

https://dnschecker.org/

Find the following records.

| Record | Observation |
|---------|-------------|
| A Record | |
| MX Record | |
| NS Record | |
| TXT Record (If Available) | |

**Take Screenshot-2**

---

## Task 5 – Google Dorking (Passive)

Search using the following operators.

```text
site:example.com
```

Observe

- Indexed Pages
- PDFs
- Documents

---

Search

```text
site:example.com filetype:pdf
```

Download **one public PDF**.

Record its filename.

| File Name | |
|-----------|-|

---

# Part B – Metadata Analysis

Open the downloaded PDF.

Use either

- Windows → Properties → Details

OR

- https://www.metadata2go.com/

Extract the following metadata.

| Metadata Field | Observation |
|---------------|-------------|
| Author | |
| Producer | |
| Software Used | |
| Date Created | |
| Date Modified | |

**Take Screenshot-3**

---

# Part C – Digital Evidence Handling

## Scenario

A laptop suspected of being used in a cybercrime has been seized from an office.

As a Digital Forensics Investigator, prepare the necessary documentation before sending the device to the forensic laboratory.

---

## Task 6 – Prepare Evidence Tag

| Field | Value |
|--------|-------|
| Evidence ID | |
| Description | |
| Date | |
| Time | |
| Investigator Name | |
| Location | |

---

## Task 7 – Prepare Chain of Custody

| Date | Time | Evidence ID | From | To | Signature |
|------|------|-------------|------|----|-----------|
| | | | | | |

---

## Task 8 – Evidence Collection Procedure

Draw the following flow diagram in your journal.

```text
Crime Scene

      │

      ▼

Photograph Evidence

      │

      ▼

Collect Device

      │

      ▼

Bag the Evidence

      │

      ▼

Attach Evidence Tag

      │

      ▼

Seal Evidence

      │

      ▼

Transport to Forensic Lab
```

---

# Observation Table

## Digital Footprinting

| Activity | Completed (✓/✗) |
|----------|-----------------|
| Google Search | |
| WHOIS Lookup | |
| DNS Lookup | |
| Google Dork Search | |
| PDF Download | |

---

## Metadata Analysis

| Metadata Available? | Yes / No |
|---------------------|----------|

---

## Evidence Handling

| Document Prepared | Yes / No |
|-------------------|----------|
| Evidence Tag | |
| Chain of Custody | |
| Flow Diagram | |

---

# Analysis Questions

1. Which information obtained from WHOIS can be useful to an attacker?
2. What information was revealed through metadata?
3. Why should organizations remove metadata before publishing documents?
4. Why is Chain of Custody important in Digital Forensics?
5. Which footprinting activity provided the most useful information? Justify your answer.

---

# Challenge Activity (Optional)

Repeat the experiment for another organization.

Compare

- WHOIS Information
- DNS Records
- Metadata Availability

Write your observations.

---

# Result

Successfully performed

- Digital Footprinting
- WHOIS Lookup
- DNS Lookup
- Metadata Analysis
- Digital Evidence Documentation

---

# Submission Checklist

Students must submit:

- □ Filled Observation Tables
- □ Screenshot of WHOIS Lookup
- □ Screenshot of DNS Lookup
- □ Screenshot of Metadata Analysis
- □ Completed Evidence Tag
- □ Completed Chain of Custody
- □ Flow Diagram
- □ Analysis Questions

---

# Viva Questions

1. What is Digital Footprinting?
2. Differentiate Active and Passive Footprinting.
3. What is WHOIS?
4. What are DNS Records?
5. What is Metadata?
6. Name any four metadata fields.
7. What is Chain of Custody?
8. What is Bagging and Tagging?
9. Why should digital evidence be photographed?
10. Why should only passive footprinting be performed without authorization?

---

# Precautions

- Perform **only passive information gathering**.
- Do **not** scan or attack any system.
- Use only publicly available information.
- Do not modify downloaded documents.
- Follow ethical hacking guidelines and applicable laws.

