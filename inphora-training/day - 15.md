# Day 15

## Overview

Today's session focused on understanding the fundamentals of Denial of Service (DoS) attacks in a controlled lab environment and learning how attackers attempt to exhaust server resources. The objective was not offensive use but to understand attack methodologies so that defensive measures can be implemented more effectively in real-world environments.

---

## Topics Covered

* Introduction to Denial of Service (DoS) attacks
* Understanding Slowloris-style attacks
* Basic reconnaissance using Pentmenu
* Controlled testing against a demo application
* Importance of attack simulation for defensive learning
* Introduction to practical cybersecurity labs on TryHackMe

---

## Lab Environment

For educational and ethical purposes, all testing was conducted against a deliberately vulnerable demo application:

* Target: Hackazon Demo Website
* Environment: Controlled Lab Setup
* Purpose: Learning attack behavior and defensive concepts

---

## Tool Used

### Pentmenu

Pentmenu is a penetration testing utility that provides various modules for reconnaissance, stress testing, and security assessments.

Activities performed:

* Reconnaissance module exploration
* DoS module exploration
* Understanding available testing options
* Observing the impact of resource exhaustion techniques

---

## Key Observations

### Slow Connection-Based Attacks

During the lab, I observed how connection-based resource exhaustion techniques can affect web applications.

Findings:

* Multiple incomplete connections can consume server resources.
* Web applications may become noticeably slower.
* Legitimate users can experience delays when resources are exhausted.
* Monitoring and rate-limiting are important defensive controls.

This exercise helped me understand the importance of:

* Web Application Firewalls (WAFs)
* Rate Limiting
* Load Balancing
* Connection Timeout Policies
* Intrusion Detection and Monitoring

---

## Defensive Takeaways

Understanding how attacks work provides valuable insight into how organizations defend against them.

Key lessons learned:

* Identify abnormal traffic patterns.
* Monitor server resource utilization.
* Configure appropriate timeout settings.
* Implement rate-limiting controls.
* Use DDoS protection services where appropriate.
* Continuously monitor logs and alerts.

---

## TryHackMe Journey Begins

Towards the end of the session, we started working on TryHackMe labs.

Goals:

* Strengthen cybersecurity fundamentals through hands-on practice.
* Apply networking and Linux concepts in realistic scenarios.
* Improve problem-solving and analytical skills.
* Gain practical exposure to security tools and methodologies.

I look forward to using TryHackMe to bridge the gap between theory and practical cybersecurity skills.

---

## Reflection

Today's session reinforced an important cybersecurity principle:

> To defend against attacks effectively, it is essential to understand how they work.

Learning attack behavior in controlled environments helps build a stronger defensive mindset and provides valuable insight into how security teams detect, analyze, and mitigate threats.
