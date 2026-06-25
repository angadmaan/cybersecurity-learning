# Day 17

## Overview

Today's session focused on understanding how **Brute Force attacks** work in a controlled lab environment. We created a local login application using **Node.js**, intercepted HTTP requests with **Burp Suite**, and automated login attempts using Burp Suite's attack features to understand how attackers perform password guessing attacks and how defenders can identify and prevent them.

> **Note:** All activities were performed in a local lab environment for educational and defensive cybersecurity learning purposes.

---

# Topics Covered

* Burp Suite Basics
* Understanding Brute Force Attacks
* Setting up a Local Login Page
* Installing Node.js
* Running a Node.js Server (`server.js`)
* Burp Suite Intercept
* Capturing Login Requests
* Automating Login Attempts
* Password Wordlists
* Defensive Perspective Against Brute Force

---

# 1. Setting up the Lab Environment

To simulate a login page for testing, we first installed **Node.js** and used a simple `server.js` file to host a local authentication page.

Example:

```bash
node server.js
```

This started a localhost web application that accepted a username and password.

---

# 2. Understanding Burp Suite Intercept

We learned how Burp Suite sits between the browser and the web server by acting as a proxy.

Workflow followed:

* Turn **Intercept ON**
* Submit the login form
* Capture the HTTP request
* Forward the request
* Turn **Intercept OFF**
* Log in normally to understand the complete request flow

This helped visualize exactly what data is sent during authentication.

---

# 3. Capturing Login Requests

After submitting credentials, Burp Suite captured the HTTP POST request containing:

* Username
* Password
* HTTP Headers
* Request Body

This captured request became the template for automated testing.

---

# 4. Understanding Brute Force

A **Brute Force Attack** is a technique where an attacker repeatedly tries different username and password combinations until valid credentials are discovered.

During today's lab, we observed how Burp Suite can automate repeated login attempts against a test application.

The objective was to understand:

* How brute force attacks operate
* How automated tools send repeated requests
* Why weak passwords are dangerous
* Why rate limiting and account lockouts are important

---

# 5. Automated Login Attempts

We generated approximately **1000 username/password combinations** and supplied them to Burp Suite for automated testing against the local login application.

This demonstrated:

* High-speed request automation
* Credential testing
* Login response comparison
* Success vs failure responses

---

# Tools Used

* Burp Suite
* Node.js
* Local Node.js Server (`server.js`)
* Localhost Login Application

---

# Concepts Learned

* HTTP Request Interception
* Login Request Analysis
* Brute Force Attack Workflow
* Automated Request Generation
* Credential Testing
* Authentication Security
* Defensive Security Awareness

---

# Key Commands Used

Start the local Node.js server:

```bash
node server.js
```

---

# Key Takeaways

* Learned how Burp Suite intercepts HTTP traffic between the client and server.
* Understood the complete workflow of a brute force attack in a safe lab environment.
* Set up a local login application using Node.js for testing purposes.
* Observed how automated login attempts work using multiple credential combinations.
* Understood why organizations implement account lockouts, rate limiting, CAPTCHA, and strong password policies to defend against brute force attacks.
* Reinforced the importance of learning offensive techniques to build stronger defensive skills.

---
