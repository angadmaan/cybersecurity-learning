# Day 21

## Overview

Today I continued learning **Cross-Site Scripting (XSS)** through the PortSwigger Web Security Academy by solving several **Practitioner-level labs**. Unlike the beginner labs, today's challenges focused on bypassing security filters, exploiting JavaScript contexts, understanding DOM-based vulnerabilities, and discovering how attackers evade common input validation techniques.

These labs demonstrated that simply blocking `<script>` tags or encoding certain characters is not enough to stop XSS attacks. Modern attackers can abuse HTML attributes, SVG elements, JavaScript template literals, AngularJS expressions, and browser APIs to execute malicious code.

The session provided a deeper understanding of how browsers parse HTML and JavaScript, how web applications process user input, and why secure output encoding is more important than simple input filtering.

---

# What I Learned Today

Today's learning focused on:

- DOM-Based XSS
- Browser parsing behavior
- HTML filtering bypasses
- JavaScript contexts
- HTML encoding
- SVG-based XSS
- Event handler injection
- AngularJS expressions
- Template literal injection
- Secure output encoding

Unlike previous labs where vulnerabilities were obvious, these labs required understanding how browsers interpret different contexts and how attackers adapt their payloads when common characters or tags are blocked.

---

# Labs Completed

## 1. DOM XSS in document.write() inside a Select Element

### Objective

Exploit a DOM-based vulnerability where user input was inserted into a `<select>` element using `document.write()`.

### What I Learned

Although the payload appeared inside a dropdown menu, it was still interpreted by the browser because the application trusted user-controlled input.

This lab showed that HTML structure does not automatically prevent JavaScript execution.

### Security Lesson

Never write untrusted input directly into the DOM using `document.write()`.

---

# 2. DOM XSS in AngularJS Expression

### Objective

Exploit AngularJS template expressions that evaluate user input.

### What I Learned

AngularJS expressions are capable of executing JavaScript-like operations.

If applications insert user input directly into Angular templates without sanitization, attackers can execute malicious expressions.

### Key Concepts

- AngularJS
- Template Expressions
- Client-side Framework Security

---

# 3. Reflected DOM XSS

### Objective

Identify a reflected DOM vulnerability executed entirely within the browser.

### What I Learned

Unlike traditional reflected XSS, the server never generated the malicious HTML.

Instead, client-side JavaScript processed attacker-controlled data and inserted it into the page.

This demonstrated why browser-side JavaScript should be reviewed during security assessments.

---

# 4. Stored DOM XSS

### Objective

Exploit DOM manipulation using previously stored attacker-controlled data.

### What I Learned

This lab combined characteristics of Stored XSS and DOM XSS.

The payload remained stored inside the application but execution occurred through unsafe JavaScript running inside the browser.

---

# 5. Reflected XSS with Most Tags and Attributes Blocked

### Objective

Bypass input filters that blocked common HTML tags.

### What I Learned

Many developers rely on blacklists.

However, blocking only common tags does not eliminate XSS because browsers support numerous HTML elements.

Attackers simply look for tags that remain allowed.

### Security Lesson

Whitelist validation and proper output encoding are more effective than blacklists.

---

# 6. Reflected XSS with Custom HTML Tags

### Objective

Exploit applications that blocked every standard HTML tag except custom elements.

### What I Learned

Modern browsers support custom HTML elements.

Even when traditional tags are filtered, attackers may still abuse browser parsing behavior.

This highlighted why developers should never assume unknown tags are harmless.

---

# 7. Reflected XSS with SVG Markup

### Objective

Use allowed SVG elements to execute JavaScript.

### What I Learned

SVG is XML-based but fully supported inside browsers.

Because SVG supports events and scripting features, attackers frequently abuse it when `<script>` tags are blocked.

### Security Lesson

SVG content should be sanitized just like HTML.

---

# 8. Reflected XSS in Canonical Link Tag

### Objective

Inject malicious input into the Canonical Link element.

### What I Learned

Metadata elements are often ignored during security reviews.

This lab demonstrated that any location accepting untrusted input deserves careful validation.

---

# 9. Reflected XSS inside JavaScript String

### Objective

Exploit JavaScript code where quotes and special characters were escaped.

### What I Learned

Encoding some characters does not automatically prevent XSS.

Attackers often identify alternative methods for escaping JavaScript strings.

Understanding JavaScript syntax is essential for identifying these vulnerabilities.

---

# 10. Reflected XSS with HTML Encoding and Escaping

### Objective

Break out of encoded JavaScript contexts.

### What I Learned

Applications frequently encode HTML while forgetting JavaScript-specific escaping rules.

Every output context requires different encoding methods.

---

# 11. Stored XSS inside onclick Event

### Objective

Inject JavaScript into an event handler.

### What I Learned

HTML event attributes execute JavaScript automatically.

If applications insert attacker-controlled input inside these attributes, malicious code may execute without using `<script>` tags.

Examples include:

- onclick
- onload
- onmouseover
- onfocus

---

# 12. Reflected XSS using Template Literals

### Objective

Exploit JavaScript Template Literals.

### What I Learned

Modern JavaScript uses template literals enclosed by backticks.

Applications that properly escape quotes may still become vulnerable if template literals are overlooked.

This lab demonstrated that modern language features introduce new attack surfaces.

---

# Important Concepts Learned

## HTML Encoding

Encoding converts dangerous characters into safe representations.

Example:

```
<
```

becomes

```
&lt;
```

This prevents browsers from interpreting user input as HTML.

---

## Output Encoding

Different contexts require different encoding.

Examples include:

- HTML Encoding
- JavaScript Encoding
- URL Encoding
- CSS Encoding

One encoding method cannot protect every context.

---

## Browser Parsing

Browsers continuously switch between parsing:

- HTML
- CSS
- JavaScript
- SVG
- XML

Understanding browser parsing behavior helps identify XSS vulnerabilities.

---

## DOM-Based Vulnerabilities

DOM XSS exists entirely inside browser JavaScript.

Common Sources:

- location.search
- location.hash
- document.URL
- Cookies

Common Sinks:

- innerHTML
- outerHTML
- document.write()
- eval()

---

# Skills Practiced

- Cross-Site Scripting (XSS)
- DOM Analysis
- HTML Context Testing
- JavaScript Context Testing
- AngularJS Security
- Browser Security
- Input Validation Testing
- Output Encoding Analysis
- DOM Manipulation
- Client-Side Security Testing

---

# Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Browser Developer Tools
- Google Chrome

---

# Key Takeaways

- Blocking `<script>` tags alone does not prevent XSS.
- Browsers support many executable contexts beyond HTML.
- SVG, AngularJS, template literals, and event handlers can all become attack vectors.
- Every output context requires its own encoding strategy.
- DOM-based vulnerabilities often exist entirely in client-side JavaScript.
- Secure coding practices are more effective than relying on input blacklists.
- Understanding browser behavior is essential for identifying advanced XSS vulnerabilities.

---

## Status

✅ Completed Successfully

**Platform:** PortSwigger Web Security Academy

**Focus Area:** Advanced Cross-Site Scripting (XSS), DOM-Based XSS, Filter Bypass Techniques, and Client-Side Security.
