# Day 22

## Overview

Today I completed the final section of the **Cross-Site Scripting (XSS)** learning path on **PortSwigger Web Security Academy**. Unlike the previous labs, today's exercises focused on real-world exploitation techniques, demonstrating how attackers leverage XSS vulnerabilities to steal sensitive information, bypass security controls, and compromise user accounts.

The labs also introduced **Content Security Policy (CSP)** bypasses and **AngularJS Sandbox Escape**, showing that even applications implementing modern security mechanisms can remain vulnerable if they are not configured correctly.

By completing these advanced labs, I gained a deeper understanding of how XSS can be chained with other vulnerabilities to perform serious attacks against web applications.

---

# Objectives

Today's objectives were to:

- Understand real-world impacts of XSS
- Learn how attackers steal session cookies
- Capture user credentials through malicious scripts
- Exploit XSS to bypass CSRF protections
- Study AngularJS Sandbox Escape techniques
- Learn the purpose of Content Security Policy (CSP)
- Understand common CSP bypass techniques
- Explore advanced browser security concepts

---

# Advanced XSS Exploitation

Unlike beginner labs where the goal was simply executing JavaScript, today's focus shifted toward **using JavaScript as a weapon**.

Once attackers gain JavaScript execution inside a victim's browser, they can:

- Read page content
- Modify webpages
- Capture user input
- Send requests on behalf of the victim
- Access sensitive information
- Perform authenticated actions
- Deliver phishing attacks

This demonstrates why Cross-Site Scripting remains one of the most dangerous web vulnerabilities.

---

# Labs Completed

## 1. Exploiting Cross-Site Scripting to Steal Cookies

### Objective

Use an XSS vulnerability to access session cookies belonging to another user.

### What I Learned

Most web applications identify logged-in users using **session cookies**.

If these cookies are accessible through JavaScript, an attacker can steal them and potentially impersonate the victim.

This lab demonstrated how a simple XSS vulnerability can quickly become an account takeover attack.

### Real-World Impact

- Session Hijacking
- Account Takeover
- Unauthorized Access
- Identity Theft

### Prevention

- HttpOnly Cookies
- Secure Cookie Flags
- Content Security Policy
- Input Validation

---

# 2. Exploiting Cross-Site Scripting to Capture Passwords

### Objective

Use JavaScript to capture user credentials.

### What I Learned

Attackers can modify webpages dynamically by injecting fake login forms or monitoring existing input fields.

Victims often cannot distinguish these fake forms from legitimate website content because the malicious code executes within the trusted application.

### Security Lesson

Even trusted websites become dangerous when XSS vulnerabilities exist.

---

# 3. Exploiting XSS to Bypass CSRF Defenses

### Objective

Use JavaScript execution to defeat Cross-Site Request Forgery protections.

### What I Learned

Many applications rely on CSRF tokens to verify legitimate requests.

However, if JavaScript executes inside the victim's browser through XSS, the malicious script can access these tokens and include them in forged requests.

This demonstrates that **XSS can completely undermine CSRF protection**.

### Key Concepts

- CSRF Tokens
- Same-Origin Policy
- Authenticated Requests
- Browser Sessions

---

# 4. Reflected XSS with AngularJS Sandbox Escape (Without Strings)

### Objective

Escape AngularJS restrictions and execute JavaScript.

### What I Learned

AngularJS originally attempted to isolate template expressions inside a security sandbox.

Researchers discovered methods to escape these restrictions and execute arbitrary JavaScript.

This lab demonstrated why relying solely on framework security mechanisms is insufficient.

---

# 5. Reflected XSS with AngularJS Sandbox Escape and CSP

### Objective

Bypass both AngularJS sandbox restrictions and Content Security Policy.

### What I Learned

Security mechanisms can interact in unexpected ways.

Even when CSP is enabled, weaknesses in AngularJS expression evaluation may still allow code execution.

Defense in depth requires secure framework usage as well as proper browser security policies.

---

# 6. Reflected XSS with Event Handlers and href Attributes Blocked

### Objective

Execute JavaScript despite filters blocking common event handlers.

### What I Learned

Applications often blacklist specific HTML attributes such as:

- onclick
- onload
- href

Attackers can search for alternative browser features that remain permitted.

This lab emphasized the importance of comprehensive validation rather than selective blocking.

---

# 7. Reflected XSS in JavaScript URL

### Objective

Exploit JavaScript execution through URL-based contexts.

### What I Learned

Browsers interpret URLs differently depending on their protocol.

Unsafe handling of JavaScript URLs may result in script execution instead of normal navigation.

Developers should validate URL schemes carefully before rendering them inside webpages.

---

# 8. Reflected XSS Protected by Strict CSP (Dangling Markup Attack)

### Objective

Understand how attackers abuse HTML parsing even when CSP is enabled.

### What I Learned

Content Security Policy significantly improves browser security.

However, incorrect implementations may still expose applications to attacks such as Dangling Markup Injection.

This attack manipulates browser parsing behavior rather than directly executing JavaScript.

---

# 9. Reflected XSS Protected by CSP with CSP Bypass

### Objective

Study methods attackers use to bypass weak Content Security Policies.

### What I Learned

CSP is only effective when configured correctly.

Weak directives, unsafe exceptions, or trusted third-party domains may provide opportunities for attackers.

The lab demonstrated that security headers require continuous review and testing.

---

# Understanding Content Security Policy (CSP)

## What is CSP?

Content Security Policy is a browser security mechanism that controls which resources can execute inside a webpage.

It reduces the impact of:

- Cross-Site Scripting
- Data Injection
- Inline Script Execution
- Third-party Script Abuse

Instead of trusting every script, the browser follows rules defined by the server.

---

# Why CSP Matters

Without CSP:

Any injected JavaScript may execute.

With CSP:

Only trusted sources are allowed.

This significantly reduces attack opportunities.

---

# Common CSP Mistakes

- Allowing unsafe-inline
- Allowing unsafe-eval
- Trusting unnecessary domains
- Weak default policies
- Improper script whitelisting

Even strong security mechanisms become ineffective if configured incorrectly.

---

# AngularJS Sandbox Escape

AngularJS originally introduced a sandbox to restrict expression execution.

Researchers later discovered techniques to escape these restrictions.

Although newer versions improved security, legacy applications may still contain vulnerable implementations.

This demonstrates an important cybersecurity principle:

**Frameworks reduce risk but do not eliminate it.**

---

# Skills Practiced

- Advanced Cross-Site Scripting
- Session Hijacking Concepts
- Browser Security
- Cookie Security
- CSRF Analysis
- AngularJS Security
- Content Security Policy
- CSP Bypass Analysis
- Client-Side Exploitation
- Secure Web Application Testing

---

# Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Google Chrome Developer Tools

---

# Key Takeaways

- XSS becomes significantly more dangerous when combined with authentication mechanisms.
- Session cookies should always be protected using HttpOnly and Secure flags.
- XSS can completely bypass CSRF protections.
- AngularJS sandbox restrictions should never be considered a complete security solution.
- Content Security Policy is an important defense layer but requires proper configuration.
- Browser security depends on multiple defensive mechanisms working together.
- Real-world attackers often chain multiple vulnerabilities together rather than relying on a single flaw.

---

# Conclusion

Completing the advanced XSS labs provided practical experience with modern web application attacks and defensive techniques. Beyond simply triggering JavaScript execution, these exercises demonstrated how Cross-Site Scripting can lead to session hijacking, credential theft, CSRF bypass, and exploitation of framework-specific weaknesses.

This learning reinforced the importance of secure coding practices, proper output encoding, strong browser security policies, and thorough testing of client-side functionality. Understanding both offensive techniques and defensive strategies is essential for building and securing modern web applications.

---

## Status

**Platform:** PortSwigger Web Security Academy

**Module:** Cross-Site Scripting (XSS)

**Focus Area:** Advanced XSS Exploitation, Cookie Theft, CSP Bypass, AngularJS Sandbox Escape, and Client-Side Security

**Status:** ✅ Completed Successfully
