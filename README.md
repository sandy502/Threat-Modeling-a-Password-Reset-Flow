# Threat Modeling a Password Reset Flow

## Overview

This project presents a **basic threat modeling exercise** focused on a
**password reset (forgot password) workflow**, a feature that exists in
almost every web application and is frequently targeted by attackers.

The goal of this repository is to demonstrate how security risks can be
identified at the **design stage**, before implementation, by analyzing
how the flow could be abused and how those risks can be reduced.

The system modeled is **fictional but realistic**, created for learning
and portfolio demonstration purposes.

---

## Why Password Reset Matters

Password reset flows are a common source of:
- account takeovers,
- user enumeration,
- token abuse,
- phishing-style attacks.

Even well-built authentication systems can fail if the password reset
logic is weak. This makes it an excellent candidate for basic threat
modeling.

---

## System Description

The password reset flow works as follows:

1. User clicks “Forgot Password”
2. User enters their email address
3. Backend generates a reset token
4. A reset link is sent via email
5. User clicks the link and sets a new password

No assumptions are made about advanced protections unless explicitly
mentioned.

---

## Assets

Assets are elements that must be protected to prevent security or
business impact.

Key assets in this system include:

- User accounts
- Password reset tokens
- Email addresses
- New passwords
- Password reset audit logs

---

## Trust Boundaries

The following trust boundaries are identified:

1. User → Public Internet
2. Internet → Backend service
3. Backend → Email service
4. Reset link → Browser session

Each boundary represents a potential attack surface.

---

## Threat Modeling Approach

Threats were identified using structured reasoning:

- Understanding attacker goals
- Applying STRIDE concepts where relevant
- Reviewing common real-world password reset failures
- Focusing on logic and workflow abuse rather than code bugs

The emphasis is on **clarity and realism**, not exhaustive coverage.

---

## Key Threats Identified

### User Enumeration
The system reveals whether an email address exists through error
messages or response timing.

**Impact:** Enables targeted attacks against valid users.

---

### Reset Token Guessing
Reset tokens are predictable, short, or poorly generated.

**Impact:** Unauthorized password resets.

---

### Token Reuse
A reset token remains valid after use or for too long.

**Impact:** Account takeover even after password change.

---

### Phishing via Reset Links
Attackers abuse the reset process to trick users into clicking
malicious links.

**Impact:** Credential theft.

---

### Missing Monitoring
Password reset attempts are not logged or monitored.

**Impact:** Attacks remain undetected.

---

## Mitigations

Design-level mitigations include:

- Generic responses for password reset requests
- Strong, random, single-use reset tokens
- Short token expiration times
- Invalidation of tokens after password change
- Logging and alerting on reset attempts

These mitigations reduce risk without adding unnecessary complexity.

---

## Detection Considerations

Even with prevention controls, detection is important.

Useful detection signals include:

- High volume of reset requests from one IP
- Reset attempts across many accounts
- Repeated token validation failures
- Password resets followed by immediate login from new locations

---

## Assumptions and Scope

- This is a design-level analysis only
- No source code or email templates are reviewed
- MFA and external identity providers are out of scope
- Insider threats are not considered

---

## What This Project Demonstrates

- Understanding of common authentication workflows
- Ability to identify logic-based security flaws
- Practical threat modeling fundamentals
- Clear and concise security documentation

---

## Disclaimer

This project is created for **educational and portfolio purposes only**.
It does not represent a real system or organization.

---

## Author

**Sandaly Singh**  
Security Engineer
