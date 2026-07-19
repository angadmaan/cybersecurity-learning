# Day 20

## Overview

Today I started learning one of the most common and dangerous vulnerabilities found in web applications—**Cross-Site Scripting (XSS)**—using **PortSwigger Web Security Academy**.

The session focused on understanding how JavaScript injected by an attacker can execute inside another user's browser because of improper input validation and output encoding. Instead of simply reading about XSS, I solved multiple hands-on labs that demonstrated how different types of XSS vulnerabilities occur and how attackers exploit them.

The labs covered three major categories of XSS:

- Reflected XSS
- Stored XSS
- DOM-Based XSS

By completing these labs, I gained practical experience in identifying vulnerable inputs, understanding browser behavior, and exploiting client-side vulnerabilities in a controlled environment.

---

# What is Cross-Site Scripting (XSS)?

Cross-Site Scripting, commonly known as **XSS**, is a web application vulnerability that allows an attacker to inject malicious JavaScript into a webpage viewed by other users.

Unlike SQL Injection, which targets the server, XSS primarily targets the **browser**.

When the application accepts user input without properly validating or encoding it, the browser treats the injected JavaScript as trusted code and executes it.

This enables attackers to perform actions on behalf of victims, steal sensitive information, or manipulate webpage content.

---

# Why is XSS Dangerous?

Although XSS may appear to be "just JavaScript," its impact can be severe.

An attacker can:

- Steal session cookies
- Hijack user accounts
- Capture usernames and passwords
- Redirect users to phishing websites
- Perform actions as the logged-in user
- Modify webpage content
- Display fake login forms
- Deliver malware
- Bypass certain security mechanisms

Since JavaScript executes inside the victim's browser, the application often cannot distinguish between legitimate actions and malicious ones.

---

# How XSS Works

A typical XSS attack follows these steps:

1. The attacker identifies an input field that accepts user-controlled data.
2. Instead of normal text, malicious JavaScript is entered.
3. The application stores or reflects this input without proper sanitization.
4. Another user loads the vulnerable page.
5. The browser interprets the injected code as part of the webpage.
6. The JavaScript executes automatically.

Because browsers trust code received from the website, they execute the malicious script.

---

# Types of XSS

## 1. Reflected XSS

Reflected XSS occurs when user input is immediately reflected back in the server response.

Example:

```
https://example.com/search?q=test
```

If the application displays the value of `q` without encoding it, injected JavaScript executes immediately.

Characteristics:

- Requires victim interaction
- Usually delivered through malicious links
- Payload is not stored on the server

---

## 2. Stored XSS

Stored XSS occurs when malicious input is permanently saved by the application.

Examples include:

- Comments
- User profiles
- Forums
- Reviews
- Chat messages

Whenever another user views that content, the malicious JavaScript executes.

Stored XSS is generally considered more dangerous because victims do not need to click a specially crafted link.

---

## 3. DOM-Based XSS

DOM XSS happens entirely inside the browser.

The server may never process the malicious payload.

Instead, JavaScript running on the page reads attacker-controlled data such as:

- URL parameters
- URL fragments
- Cookies
- Local Storage

and inserts it into the webpage using unsafe DOM functions.

---

# Important XSS Terminology

## Source

A source is any location where attacker-controlled input originates.

Examples:

- `location.search`
- `location.hash`
- Cookies
- Form input
- URL parameters

---

## Sink

A sink is the location where data is written into the webpage.

Common dangerous sinks include:

- innerHTML
- document.write()
- eval()
- outerHTML
- insertAdjacentHTML()

If attacker-controlled input reaches a dangerous sink without validation, XSS becomes possible.

---

## Context

Context refers to where user input appears.

Examples include:

- HTML Context
- Attribute Context
- JavaScript Context
- CSS Context
- URL Context

Different contexts require different encoding techniques.

---

# Labs Completed

## Lab 1 - Reflected XSS into HTML Context with Nothing Encoded

### Objective

Exploit a search feature that reflects user input directly into the webpage.

### Vulnerability

The application inserted user input directly inside the HTML page without performing any sanitization or encoding.

Because the browser interpreted the input as HTML, injected JavaScript executed immediately.

### What I Learned

This was my first practical experience with Reflected XSS.

I understood that even a simple search box becomes dangerous if user input is rendered directly inside HTML.

### Real-World Impact

An attacker could send victims a specially crafted URL containing malicious JavaScript.

When opened, the script executes in the victim's browser.

### Prevention

- Encode HTML output
- Validate user input
- Use Content Security Policy (CSP)

---

# Lab 2 - Stored XSS into HTML Context with Nothing Encoded

### Objective

Inject JavaScript into a comment section.

### Vulnerability

The application permanently stored user input and displayed it to every visitor without sanitization.

Whenever another user viewed the page, the browser executed the stored JavaScript.

### What I Learned

Stored XSS is significantly more dangerous than Reflected XSS because the payload persists inside the application.

Victims do not need to click malicious links.

Simply opening the affected page is enough.

### Prevention

- Escape HTML before displaying user content
- Sanitize rich-text input
- Validate all stored data

---

# Lab 3 - DOM XSS in document.write() using location.search

### Objective

Exploit JavaScript that reads the URL parameter and writes it directly into the page.

### Vulnerability

The application used:

- `location.search` as the source
- `document.write()` as the sink

Because no validation occurred, attacker-controlled input became executable JavaScript.

### What I Learned

Unlike previous labs, the vulnerability existed entirely inside the browser.

The server was not responsible for executing the payload.

This introduced me to the concept of **Sources** and **Sinks**, which are fundamental in DOM-based XSS testing.

---

# Lab 4 - DOM XSS in innerHTML using location.search

### Objective

Exploit unsafe use of the `innerHTML` property.

### Vulnerability

The webpage copied URL data directly into `innerHTML`.

Since `innerHTML` parses HTML instead of displaying plain text, injected elements and scripts became executable.

### What I Learned

I learned why developers should avoid assigning untrusted input directly to `innerHTML`.

Safer alternatives such as `textContent` prevent script execution.

---

# Lab 5 - DOM XSS in jQuery href Attribute

### Objective

Exploit a vulnerable jQuery function that updates an anchor (`href`) attribute using user input.

### Vulnerability

The application trusted attacker-controlled URL parameters and inserted them into hyperlink attributes without validation.

This allowed malicious JavaScript URLs to execute when interacted with.

### What I Learned

Even HTML attributes can become dangerous if developers fail to validate input properly.
