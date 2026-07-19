# Day 24

## Overview

Today I completed the **Authentication** module in **PortSwigger Web Security Academy**, focusing on advanced authentication vulnerabilities that are commonly found in modern web applications. Unlike the previous session, which introduced authentication flaws and username enumeration, today's labs demonstrated how attackers can exploit weak authentication logic to bypass security controls, crack passwords, compromise persistent login mechanisms, and defeat Two-Factor Authentication (2FA).

The exercises emphasized that authentication security extends beyond login forms. Features such as "Remember Me" cookies, password reset functionality, middleware processing, and account recovery mechanisms can all become attack vectors if they are not implemented securely.

By completing these labs, I gained practical experience in identifying authentication weaknesses, analyzing login mechanisms, testing persistent sessions, and understanding how attackers chain multiple vulnerabilities together to compromise user accounts.

---

# Objectives

The primary objectives of today's labs were to:

- Understand weaknesses in advanced authentication mechanisms.
- Learn how attackers exploit persistent login cookies.
- Study password cracking techniques.
- Analyze password reset vulnerabilities.
- Explore authentication brute-force bypass techniques.
- Understand how poorly implemented Two-Factor Authentication can be defeated.
- Learn secure authentication best practices.

---

# Authentication Security Beyond Login

Authentication does not end after a user enters a username and password.

Modern web applications include many additional authentication-related features, including:

- Remember Me functionality
- Session cookies
- Password recovery
- Password reset
- Multi-Factor Authentication
- Account recovery
- Session management

If any one of these mechanisms contains a vulnerability, attackers may gain unauthorized access without ever knowing the user's original password.

---

# Labs Completed

---

# 1. 2FA Broken Logic

## Objective

Exploit weaknesses in the application's Two-Factor Authentication implementation.

## Vulnerability

Although the application required a verification code, flaws in the authentication workflow allowed the attacker to bypass parts of the verification process.

The application trusted user navigation instead of verifying authentication state on every request.

## What I Learned

Two-Factor Authentication is only effective when every authenticated request verifies that the second authentication factor has been successfully completed.

Poor application logic can completely defeat MFA.

## Prevention

- Verify authentication status server-side
- Never trust client-side workflow
- Validate every authenticated request

---

# 2. Brute-Forcing a Stay-Logged-In Cookie

## Objective

Recover valid authentication information from a persistent login cookie.

## Vulnerability

The application's "Remember Me" cookie contained predictable information that could be brute-forced.

Instead of generating secure random tokens, the application stored weak authentication data.

## What I Learned

Persistent login cookies should never contain predictable values.

Authentication tokens must be random, unique, and securely generated.

## Prevention

- Use cryptographically secure random tokens
- Rotate persistent tokens
- Store token references instead of sensitive information
- Set Secure and HttpOnly flags

---

# 3. Offline Password Cracking

## Objective

Recover user passwords from leaked password hashes.

## Vulnerability

Instead of attacking the login page directly, password hashes were obtained and cracked offline.

Because no interaction with the server is required, account lockouts and rate limits become ineffective.

## What I Learned

Offline password cracking is often much faster than online brute-force attacks.

Weak passwords and weak hashing algorithms dramatically increase the attacker's success rate.

## Prevention

- Use strong password hashing algorithms
- Salt every password
- Encourage long passwords
- Implement password complexity requirements

---

# 4. Password Reset Poisoning via Middleware

## Objective

Exploit weaknesses in the password reset process using manipulated HTTP headers.

## Vulnerability

The application generated password reset links using information provided by client-controlled headers.

An attacker could manipulate these values and cause password reset links to point to an attacker-controlled domain.

## What I Learned

Applications should never trust HTTP headers supplied by clients when generating security-sensitive URLs.

Password reset functionality must always use trusted server-side configuration.

## Prevention

- Validate Host headers
- Use predefined server URLs
- Ignore client-controlled redirect information
- Verify password reset requests

---

# 5. Password Brute-Force via Password Change

## Objective

Exploit flaws in the password change functionality.

## Vulnerability

The password change page allowed repeated password guesses for the current password without implementing proper protections.

Instead of attacking the login page, attackers could brute-force passwords through another application feature.

## What I Learned

Every feature requiring password verification must implement brute-force protection.

Attackers often search for alternative authentication endpoints.

## Prevention

- Apply rate limiting everywhere
- Require re-authentication
- Monitor abnormal password change requests

---

# 6. Broken Brute-Force Protection (Multiple Credentials per Request)

## Objective

Bypass brute-force protections by submitting multiple credentials within a single HTTP request.

## Vulnerability

The application's security mechanisms counted requests rather than password attempts.

By including multiple credential combinations inside one request, attackers bypassed request-based rate limiting.

## What I Learned

Security controls should measure authentication attempts rather than HTTP requests.

Improper rate limiting creates opportunities for large-scale automated attacks.

## Prevention

- Count password attempts
- Monitor authentication behavior
- Limit credential submissions
- Detect automation patterns

---

# 7. 2FA Bypass Using a Brute-Force Attack

## Objective

Defeat Two-Factor Authentication by brute-forcing verification codes.

## Vulnerability

The application failed to properly rate-limit verification attempts.

Attackers could repeatedly submit verification codes until the correct one was discovered.

## What I Learned

Short verification codes without rate limiting provide very little protection.

Authentication systems must limit repeated verification attempts.

## Prevention

- Limit verification attempts
- Lock accounts after repeated failures
- Use longer verification codes
- Expire OTPs quickly

---

# Important Concepts Learned

## Persistent Login Cookies

Persistent login cookies allow users to remain authenticated after closing their browsers.

These cookies should:

- Be random
- Expire after a reasonable period
- Use Secure flag
- Use HttpOnly flag
- Be protected against theft

---

## Password Hashing

Passwords should never be stored in plaintext.

Instead, applications store password hashes generated using secure algorithms.

Modern password hashing algorithms include:

- Argon2
- bcrypt
- scrypt
- PBKDF2

These algorithms slow down password cracking attacks.

---

## Password Salting

A salt is a random value added before hashing passwords.

Salting prevents attackers from using rainbow tables and ensures identical passwords produce different hashes.

---

## Brute-Force Protection

Effective brute-force protection includes:

- Rate limiting
- Progressive delays
- CAPTCHA
- Account monitoring
- Device fingerprinting
- Behavioral analysis

Blocking only IP addresses is rarely sufficient.

---

## Two-Factor Authentication (2FA)

2FA strengthens authentication by requiring a second verification factor.

Examples include:

- Authenticator Apps
- SMS OTP
- Hardware Tokens
- Biometrics

However, weak implementation can completely undermine its security.

---

# Skills Practiced

- Authentication Testing
- Burp Suite
- Password Security Analysis
- Session Cookie Testing
- Password Reset Testing
- Middleware Analysis
- Two-Factor Authentication Testing
- Brute-Force Analysis
- Web Application Security
- Secure Authentication Design

---

# Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Google Chrome Developer Tools

---

# Best Practices for Secure Authentication

- Implement Multi-Factor Authentication correctly.
- Use secure session management.
- Protect cookies with Secure and HttpOnly flags.
- Use strong password hashing algorithms.
- Apply rate limiting to all authentication endpoints.
- Use cryptographically secure random tokens.
- Protect password reset functionality.
- Validate every authenticated request server-side.
- Monitor suspicious login activity.
- Implement proper logging and alerting.

---

# Key Takeaways

- Authentication vulnerabilities often exist outside the login page.
- Every authentication-related feature should be treated as security-sensitive.
- Persistent login cookies require the same protection as passwords.
- Weak password reset implementations frequently lead to account compromise.
- Brute-force protection should focus on authentication attempts rather than request counts.
- Properly implemented Multi-Factor Authentication significantly improves security.
- Secure authentication requires multiple defensive layers working together.

---

# Conclusion

Today's labs demonstrated that authentication security extends far beyond verifying usernames and passwords. Features such as persistent login cookies, password reset mechanisms, and Two-Factor Authentication introduce additional attack surfaces that require careful implementation.

By exploiting broken authentication logic, weak session management, insecure password recovery, and ineffective brute-force protections, I gained practical experience in identifying vulnerabilities that commonly appear in real-world web applications.

Completing this module strengthened my understanding of authentication security and reinforced the importance of secure design, consistent server-side validation, strong cryptographic practices, and layered defense mechanisms for protecting user accounts.

---

## Status

**Platform:** PortSwigger Web Security Academy

**Module:** Authentication

**Focus Area:** Advanced Authentication Vulnerabilities, Password Security, Session Management, Two-Factor Authentication, Brute-Force Protection, and Secure Authentication Design

**Status:** ✅ Completed Successfully
