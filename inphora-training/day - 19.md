# Day 19

## Overview

Today I continued exploring **OAuth 2.0** vulnerabilities through hands-on labs on **PortSwigger Web Security Academy**. The focus was on identifying weaknesses in OAuth implementations and understanding how attackers can exploit authentication and authorization flaws to compromise user accounts.

Instead of learning OAuth only from theory, these labs demonstrated how insecure implementations can result in account takeover, token theft, and Server-Side Request Forgery (SSRF).

-----

# Difference Between Authentication and Authorization

| Authentication | Authorization |
|---------------|---------------|
| Confirms who the user is | Determines what the user can access |
| Login process | Permission process |
| Uses credentials | Uses access tokens |

OAuth is primarily an **authorization protocol**, although many websites use it for authentication.

---

# Labs Completed

## 1. Authentication Bypass via OAuth Implicit Flow

### Difficulty
Apprentice

### Objective

Exploit weaknesses in the OAuth Implicit Flow to bypass normal authentication.

### What I Learned

- How the Implicit Flow works
- Why tokens are returned directly to the browser
- Risks of exposing access tokens
- Why the Authorization Code Flow is preferred today

### Key Concepts

- Access Token
- Implicit Flow
- Browser Storage
- OAuth Response Types

---

# 2. SSRF via OpenID Dynamic Client Registration

### Difficulty

Practitioner

### Objective

Exploit OpenID's Dynamic Client Registration feature to perform Server-Side Request Forgery.

### What I Learned

OpenID allows applications to register dynamically.

If user-controlled URLs are not validated, the OAuth server may send requests to internal systems.

This creates an SSRF vulnerability.

### Key Concepts

- OpenID Connect
- Dynamic Client Registration
- SSRF
- URL Validation

---

# 3. Forced OAuth Profile Linking

### Difficulty

Practitioner

### Objective

Force a victim account to become linked with an attacker's OAuth account.

### What I Learned

Some applications allow users to connect OAuth accounts after logging in.

If proper CSRF protection or state validation is missing, an attacker can trick another user into linking the wrong account.

### Impact

- Account takeover
- Unauthorized account linking
- Identity confusion

### Security Lesson

Always validate the **state** parameter during OAuth flows.

---

# 4. OAuth Account Hijacking via redirect_uri

### Difficulty

Practitioner

### Objective

Abuse an insecure `redirect_uri` parameter to hijack another user's OAuth session.

### What I Learned

Some OAuth implementations fail to validate redirect URIs.

An attacker can redirect authorization codes or tokens to their own controlled website.

### Impact

- Account takeover
- Authorization code theft
- Session compromise

### Security Lesson

Only allow pre-approved redirect URIs.

Never trust user-controlled redirect destinations.

---

# 5. Stealing OAuth Access Tokens via an Open Redirect

### Difficulty

Practitioner

### Objective

Use an open redirect vulnerability to steal OAuth access tokens.

### What I Learned

Even if OAuth is implemented correctly, an open redirect elsewhere in the application can expose access tokens.

The attacker redirects the victim to a trusted page, which immediately redirects to an attacker-controlled website.

The access token travels with the redirect.

### Impact

- Token theft
- Account compromise
- Unauthorized API access

### Security Lesson

Open Redirect vulnerabilities can become much more dangerous when combined with OAuth.

---

# 6. Stealing OAuth Access Tokens via a Proxy Page

### Difficulty

Expert

### Objective

Capture OAuth access tokens using a vulnerable proxy page.

### What I Learned

Some applications proxy external content without proper validation.

An attacker can abuse this behavior to intercept OAuth tokens.

This demonstrates how unrelated application features can become security vulnerabilities.

### Key Concepts

- Proxy Pages
- Token Leakage
- OAuth Security
- Secure Application Design

---

# Important OAuth Components

## Authorization Server

Authenticates the user and issues tokens.

Example:
Google
GitHub
Microsoft

---

## Resource Server

Stores protected resources.

Example

User profile

Email

Contacts

Files

---

## Client Application

The application requesting authorization.

Example

Spotify

Discord

Notion

---

## Access Token

A temporary credential that allows limited access to protected resources.

---

## Authorization Code

A temporary code exchanged for an access token.

More secure than the Implicit Flow.

---

## Redirect URI

The URL where users are sent after authentication.

Improper validation can result in account hijacking.

---

## State Parameter

A random value used to prevent CSRF attacks.

Always validate it.

---

# Skills Practiced

- OAuth 2.0
- OpenID Connect (OIDC)
- Web Authentication Testing
- Burp Suite
- HTTP Request Analysis
- Token Security
- Redirect Validation
- Authorization Flow Analysis
- SSRF Identification
- Web Application Security

---

# Tools Used

- Burp Suite Community Edition
- PortSwigger Web Security Academy
- Browser Developer Tools

---

# Key Takeaways

- OAuth security depends on correct implementation.
- Never trust user-controlled redirect URIs.
- Validate the `state` parameter.
- Prevent open redirects.
- Protect access tokens.
- Prefer Authorization Code Flow over Implicit Flow.
- Dynamic client registration should be carefully validated.
- Small implementation mistakes can lead to complete account compromise.

---

## Status

✅ Completed Successfully

**Platform:** PortSwigger Web Security Academy

**Focus Area:** OAuth 2.0 Security & Authentication Vulnerabilities
