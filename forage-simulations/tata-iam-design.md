# Tata Consultancy Services — Cybersecurity Analyst Job Simulation

**Platform:** Forage
**Role:** IAM Developer (simulated)
**Client:** TechCorp Enterprises (fictional)

## Overview
This simulation put me in the role of an Identity and Access Management (IAM) 
developer at TCS, tasked with strengthening TechCorp Enterprises' security 
posture. IAM is the layer that decides who gets access to what — get it wrong 
and you've either locked out legitimate users or left a door open for 
attackers.

## What I did

### 1. Theoretical foundation
Worked through IAM fundamentals — authentication vs. authorization, the 
principle of least privilege, and how access control ties into broader 
compliance requirements.

### 2. IAM readiness assessment
Evaluated TechCorp's existing access management setup across a multinational 
context — multiple business units, inconsistent access policies, and no 
centralized visibility into who had access to what. Identified this lack of 
centralization as the core risk.

### 3. Designing the solution
Built a custom IAM solution centered on:
- **Role-Based Access Control (RBAC)** — redefined permissions around job 
  function instead of ad hoc grants, cutting down on excess access
- **Multi-Factor Authentication (MFA)** — scoped to privileged accounts and 
  high-risk applications, not blanket-applied (balancing security against 
  user friction)
- **Approval workflows** — built into access requests and periodic 
  recertification, so access doesn't just get granted once and forgotten

### 4. Integration roadmap
Translated the design into a phased rollout plan: governance and scope 
definition first, then a technical baseline assessment (cataloguing 
applications, data flows, and existing authentication schemas), followed by 
staged deployment.

## Key takeaway
The technical part of IAM (RBAC rules, MFA configs) is the easy half. The 
harder part is designing something that survives contact with a real 
organization — getting stakeholder buy-in, phasing the rollout so it doesn't 
break existing workflows, and building in recertification so access doesn't 
silently drift out of date. This is the part textbooks don't usually cover.

## Skills applied
Identity and Access Management · RBAC · MFA · Access Governance · Compliance
