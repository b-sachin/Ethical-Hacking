# Experiment 6
# Static and Dynamic Malware Analysis in a Controlled Laboratory Environment

## Aim

To perform static and dynamic analysis of a malware sample in an isolated virtual environment, identify indicators of compromise (IOCs), understand malware behavior, and document the findings in a malware analysis report.

---

## Course Outcome Mapping

**CO3:** Prioritize vulnerabilities by severity and apply techniques for securing systems against unauthorized access.

---

## Prerequisites

Students should be familiar with:

- Malware Basics
- Windows Operating System
- Linux Basics
- File Hashing
- Virtual Machines
- Process Monitoring

---

# Theory

Malware analysis is the process of studying malicious software to understand:

- How it works
- What actions it performs
- How it spreads
- What damage it causes
- How it can be detected and prevented

Malware analysis generally consists of:

- Static Analysis
- Dynamic Analysis

Static analysis examines a file **without executing it**, while dynamic analysis observes its behavior during execution inside a secure sandbox or virtual machine.

---

# Practical Scenario

You are working as a Malware Analyst.

A suspicious executable file has been received by your organization's Security Operations Center (SOC).

Your task is to examine the sample without infecting production systems, identify its characteristics, observe its behavior in an isolated environment, and prepare an incident analysis report.

**The instructor will provide a safe malware sample or demonstration file.**

---

# Software Requirements

| Tool | Purpose |
|------|---------|
| Windows Virtual Machine | Malware Analysis Environment |
| Kali Linux (Optional) | Supporting Analysis |
| VirusTotal (Hash Lookup Only) | Reputation Check |
| PEStudio | Static Analysis |
| Detect It Easy (DIE) | File Inspection |
| Process Monitor (ProcMon) | Runtime Monitoring |
| Process Explorer | Process Analysis |
| Wireshark | Network Monitoring |
| HashMyFiles / sha256sum | File Hashing |

---

# Safety Guidelines

⚠ **Important**

- Perform the experiment **only inside an isolated virtual machine**.
- Never execute unknown malware on the host operating system.
- Do not connect the analysis VM to the public Internet unless instructed.
- Restore the VM snapshot after completing the experiment.

---

# Part A – Static Analysis

## Activity 1 – Calculate File Hash

Calculate the SHA-256 hash.

Windows PowerShell

```powershell
Get-FileHash sample.exe -Algorithm SHA256
```

Linux

```bash
sha256sum sample.exe
```

Record the hash.

---

## Activity 2 – Inspect File Properties

Record:

| Parameter | Observation |
|-----------|-------------|
| File Name | |
| File Size | |
| File Type | |
| Digital Signature | |
| Compilation Time | |

---

## Activity 3 – Analyze using PEStudio

Open the executable using PEStudio.

Identify:

- Imported DLLs
- Suspicious APIs
- Strings
- Indicators

Take Screenshot-1.

---

## Activity 4 – Analyze using Detect It Easy (DIE)

Determine:

- Executable Type
- Compiler
- Architecture
- Packers (if any)

Take Screenshot-2.

---

## Activity 5 – VirusTotal Hash Lookup

Open:

```
https://www.virustotal.com
```

Search **only using the SHA-256 hash** (do not upload files unless instructed).

Record:

| Parameter | Observation |
|-----------|-------------|
| Detection Ratio | |
| Malware Family | |
| Vendors Detecting | |

---

# Part B – Dynamic Analysis

## Activity 6 – Start Process Monitor

Launch Process Monitor before executing the sample.

Observe:

- File Operations
- Registry Operations
- Process Creation

---

## Activity 7 – Execute the Sample

Run the instructor-provided sample inside the virtual machine.

Observe:

- New Processes
- Registry Changes
- File Creation
- Temporary Files

Record observations.

---

## Activity 8 – Analyze Running Processes

Use Process Explorer.

Record:

| Parameter | Observation |
|-----------|-------------|
| Process Name | |
| Parent Process | |
| PID | |
| CPU Usage | |

---

## Activity 9 – Monitor Network Activity

Start Wireshark.

Observe whether the sample attempts to:

- Resolve DNS names
- Connect to remote IP addresses
- Send HTTP/HTTPS requests

Record your findings.

---

## Activity 10 – Identify Indicators of Compromise (IOCs)

Document the following:

| IOC Type | Observation |
|----------|-------------|
| File Hash | |
| Process Name | |
| Registry Key | |
| File Created | |
| IP Address | |
| Domain Name | |

---

# Investigation Challenges

### Challenge 1

What type of malware does the sample resemble?

Answer:

______________________

---

### Challenge 2

Was the executable digitally signed?

Yes / No

---

### Challenge 3

Did the malware create any new files?

Answer:

______________________

---

### Challenge 4

Did it modify the Windows Registry?

Answer:

______________________

---

### Challenge 5

Did the malware attempt any network communication?

Answer:

______________________

---

### Challenge 6

What Indicators of Compromise (IOCs) were identified?

_____________________________________________________

---

### Challenge 7

Which analysis technique is safer?

- Static Analysis
- Dynamic Analysis

Why?

_____________________________________________________

---

### Challenge 8

How can antivirus software detect similar malware?

_____________________________________________________

---

### Challenge 9

Suggest three mitigation techniques.

1.

2.

3.

---

### Challenge 10

Why should malware always be analyzed inside a virtual machine?

_____________________________________________________

---

# Observation Table

| Activity | Observation |
|----------|-------------|
| File Hash | |
| Executable Type | |
| Compiler | |
| Imported DLLs | |
| Detection Ratio | |
| Network Activity | |
| Registry Changes | |
| New Files Created | |

---

# Sample Malware Analysis Report

| Parameter | Observation |
|-----------|-------------|
| Analyst | |
| Date | |
| Sample Name | |
| SHA-256 Hash | |
| Malware Type | |
| IOCs Identified | |
| Severity | |
| Recommendations | |

---

# Result

Successfully performed static and dynamic malware analysis in an isolated virtual environment. The malware sample was examined, behavioral indicators were identified, and a structured malware analysis report was prepared.

---

# Precautions

- Use only instructor-provided malware samples.
- Never execute malware on production systems.
- Perform analysis only inside an isolated VM.
- Restore the VM snapshot after the experiment.
- Do not share malware samples outside the laboratory.

---

# Viva Questions

1. What is malware analysis?
2. Differentiate static and dynamic analysis.
3. What is an Indicator of Compromise (IOC)?
4. Why is SHA-256 hashing performed?
5. What is PEStudio?
6. What is Process Monitor used for?
7. Why is Process Explorer useful?
8. What information can VirusTotal provide?
9. Why should malware be analyzed inside a sandbox or VM?
10. What precautions should be taken while handling malware?

---

# Conclusion

This experiment provided practical exposure to malware analysis techniques used by cybersecurity professionals. Students learned how to perform static and dynamic analysis, identify indicators of compromise, observe malware behavior in a controlled environment, and prepare a structured malware analysis report while following safe and ethical laboratory practices.