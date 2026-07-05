# AIG — Shields Up: Cybersecurity Job Simulation

**Platform:** Forage
**Role:** Cybersecurity Analyst (simulated)
**Team:** AIG Cyber & Information Security

## Overview
This simulation put me in the role of a Cybersecurity Analyst at AIG, responding 
to a real, publicly documented vulnerability — Log4Shell (CVE-2021-44228) — and 
then handling the fallout when it got exploited. It combined technical research, 
stakeholder communication, and hands-on scripting in a single incident arc, 
which made it feel less like a lab exercise and more like an actual incident 
timeline.

## What I did

### 1. Responding to a zero-day vulnerability
Started by reviewing CISA's published advisories (in coordination with the FBI 
and NSA) on the Apache Log4j vulnerability. Researched what Log4Shell actually 
was — a critical remote code execution flaw in a widely used Java logging 
library — and why it was rated so severely.

### 2. Scoping the impact
Cross-referenced an internal infrastructure list against the vulnerable Log4j 
versions to identify which systems and product teams were actually exposed. 
Flagged the Product Development Staging Environment as an at-risk system 
tied to a specific infrastructure owner.

### 3. Communicating the risk
Drafted a formal security advisory email to the affected team's owner — 
written for a non-technical stakeholder, not a fellow analyst. Kept it clear 
and action-oriented: what the vulnerability was, why it mattered, and what 
needed to happen next (patching to a fixed Log4j version).

### 4. Responding to exploitation
The scenario escalated: despite the advisory, the vulnerability was exploited 
before remediation completed, and a ransomware payload encrypted a file on a 
compromised server. Paying the ransom wasn't an option — no guarantee of 
recovery, and no guarantee the attacker wouldn't come back.

### 5. Bypassing the ransomware
Given intel suggesting the attacker used a low-effort, likely weak encryption 
approach, I wrote a Python script to brute-force the password on the encrypted 
file using a candidate password list — successfully recovering the contents 
without paying the ransom.

## Key takeaway
This simulation connected two things that usually get taught separately: 
technical vulnerability response and stakeholder communication. Finding the 
vulnerability and understanding it technically was only half the job — the 
advisory email had to be clear enough that a non-technical infrastructure 
owner would actually act on it fast. And when prevention failed, the response 
shifted from "stop it" to "recover from it without paying," which is its own 
skill: reasoning about attacker behavior (sloppy, reused payloads → likely 
weak encryption) rather than just running a generic brute-force tool.

## Skills applied
Vulnerability Research · Incident Response · Stakeholder Communication · 
Python Scripting · Log4j / CVE Analysis · Ransomware Recovery
