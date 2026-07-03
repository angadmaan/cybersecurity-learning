# Deloitte Australia — Cyber Job Simulation

**Platform:** Forage
**Role:** Cyber Security Analyst (simulated)
**Scenario:** Investigating a potential data breach

## Overview
This simulation dropped me into an active investigation: a client reported a 
possible breach, and my job was to determine whether it originated from an 
external attacker or from inside the organization's own network — using 
nothing but raw web request logs.

## What I did

### 1. Framing the investigation
The core question was narrow and specific: could an external attacker have 
reached the target system directly, without going through the company VPN? 
That framing shaped which log entries actually mattered.

### 2. Log analysis
Worked through a web request log containing traffic from multiple internal 
IP addresses — logins, dashboard resource requests, and API calls to machine 
status endpoints, all timestamped. Looked for sequences that deviated from 
normal human browsing behavior.

### 3. Spotting the anomaly
Found one account making requests at suspiciously precise, fixed hourly 
intervals — no page-load resource requests, no frontend activity, nothing 
that looked like a person clicking through a UI. That pattern (exact 
timing, no incidental traffic) is a strong signature of an automated 
script rather than a human user.

### 4. Drawing the conclusion
Cross-referenced the flagged account's IP address against the company's 
internal network range. It matched — meaning the activity originated from 
inside the network, not from an external actor bypassing the VPN. Documented 
the affected user ID and the reasoning chain behind the conclusion.

## Key takeaway
Breach investigation is pattern recognition under ambiguity — the log doesn't 
announce "this is malicious." The tell was in what was *missing* (no frontend 
requests) as much as what was present (mechanical timing). Ruling out the 
external-attacker theory was just as important as finding the actual source, 
since it directly changed the nature of the response (insider threat / 
compromised internal account, not perimeter breach).

## Skills applied
Log Analysis · Incident Investigation · Network Security · Anomaly Detection
