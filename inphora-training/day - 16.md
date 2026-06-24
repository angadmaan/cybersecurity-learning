# Day 16 - Inphora Cybersecurity Training

## Overview

Today's session focused on understanding the fundamentals of **Penetration Testing (Pentesting)**, its various domains, and the standard phases followed during a security assessment.

The session provided an overview of how security professionals identify vulnerabilities, assess risks, and help organizations improve their security posture through authorized testing.

---

# What is Penetration Testing?

Penetration Testing (Pentesting) is an authorized security assessment conducted to identify vulnerabilities in systems, networks, applications, or human processes before malicious attackers can exploit them.

The primary objective is to simulate real-world attack scenarios and discover security weaknesses.

---

# Types of Penetration Testing

## 🌐 Network Penetration Testing

Focuses on identifying vulnerabilities within network infrastructure.

Examples:

* Open ports
* Misconfigured services
* Weak network security controls
* Insecure protocols

Common Tools:

* Nmap
* Wireshark

---

## 🖥️ Web Application Penetration Testing

Focuses on finding vulnerabilities in websites and web applications.

Examples:

* SQL Injection
* Cross-Site Scripting (XSS)
* Authentication flaws
* Session management issues

---

## 📡 Wireless Penetration Testing

Focuses on evaluating the security of wireless networks.

Examples:

* Weak Wi-Fi passwords
* Insecure encryption
* Rogue access points
* Misconfigured wireless devices

---

## 👥 Social Engineering Penetration Testing

Focuses on evaluating human security awareness.

Examples:

* Phishing simulations
* Impersonation attempts
* Information gathering through human interaction

The goal is to assess how susceptible users are to manipulation techniques.

---

# Phases of Penetration Testing

## 1. Information Gathering (Reconnaissance)

The first phase involves collecting information about the target.

Information may include:

* Domains
* IP addresses
* Subdomains
* Employee information
* Publicly exposed assets

Tools Discussed:

### Shodan

A search engine for internet-connected devices.

Used to discover:

* Servers
* Cameras
* Routers
* IoT devices
* Public services

### Hunter.io

A tool used to discover publicly available email addresses associated with domains.

Useful during reconnaissance and OSINT activities.

### Maltego

A powerful OSINT and link-analysis tool used to visualize relationships between domains, people, organizations, emails, and infrastructure.

---

## 2. Scanning and Enumeration

After gathering information, the next step is identifying active services and possible vulnerabilities.

### Nmap

Used for:

* Host discovery
* Port scanning
* Service detection
* Operating system identification

### Wireshark

Used for:

* Network traffic analysis
* Packet inspection
* Protocol analysis
* Troubleshooting network communications

---

## 3. Exploitation (Gaining Access)

In this phase, identified vulnerabilities may be tested in a controlled and authorized environment to validate their impact.

The objective is to determine whether discovered weaknesses can be successfully exploited.

---

## 4. Persistence

Persistence refers to understanding how attackers may attempt to maintain access after compromising a system.

This phase helps security professionals understand potential post-exploitation risks and defensive measures.

---

## 5. Reporting

The final and one of the most important phases of a penetration test.

A professional penetration testing report typically contains:

* Executive Summary
* Scope of Assessment
* Findings
* Risk Levels
* Evidence
* Recommendations
* Remediation Steps

The report helps organizations understand their security posture and prioritize improvements.

---

# Key Tools Discussed

| Tool      | Purpose                                      |
| --------- | -------------------------------------------- |
| Maltego   | OSINT and relationship mapping               |
| Shodan    | Search engine for internet-connected devices |
| Hunter.io | Email discovery and OSINT                    |
| Nmap      | Network scanning and enumeration             |
| Wireshark | Packet analysis and network monitoring       |

---

# Key Takeaways

* Penetration testing is a structured security assessment process.
* Reconnaissance is the foundation of every security engagement.
* Different types of pentesting target different attack surfaces.
* Reporting is as important as technical testing.
* Security professionals use OSINT techniques extensively before conducting assessments.
* Understanding attacker methodologies helps improve defensive security strategies.

---
