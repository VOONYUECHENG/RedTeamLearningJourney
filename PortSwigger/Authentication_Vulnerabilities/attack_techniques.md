## Authentication Attack Techniques
This document summarizes common authentication attack techniques identified through hands-on PortSwigger Web Security Academy labs. The focus is on exploitation methods rather than theoretical explanations.

### User Enumeration Techniques
-  Observe different error messages for:
    1.  Invalid usernames.
    2.  Invalid passwords.
-  Compare response behaviours:
    1.  Response time differences.
    2.  Redirect differences.
    3.  HTTP status code variations.
    4.  Error message differences.

### Brute-Force Attack Techniques
#### Login Brute-Force
-  Attempt multiple passwords against a known username.
-  Exploit missing rate limiting or account lockout.
-  Use:
    1.  Credential stuffing.
    2.  Password spraying.

#### Brute-Force Protection Bypass
-  Rotate IP addresses to avoid IP-based rate limiting.
-  Send parallel requests to bypass sequential protections.
-  Abuse logic where:
    1.  Only valid usernames trigger account lockout.
    2.  Lockout counters reset after successful login attempts.
    3.  Account stuffing (distributing login attempts across multiple accounts to avoid IP or account-based lockout).

### Multi-Factor Authentication (MFA) Bypass Techniques
-  Brute-force MFA codes when:
    1.  No rate limiting is applied.
    2.  Codes are short or predictable.
    3.  MFA codes do not expire.
-  Bypass MFA by:
    1.  Skipping verification steps.
    2.  Accessing protected endpoints directly (changing URL redirects).
-  Session manipulation:
    1.  Log in using own credentials and valid MFA code.
    2.  Replace session cookies with the victim’s cookies after MFA validation.
-  Exploit MFA logic not bound to:
    1.  Specific user.
    2.  Specific session.
    3.  Single authentication attempt.

### “Stay Logged In” / Remember Me Cookie Attacks
-  Decode or tamper with persistent login cookies.
-  Brute-force predictable token values.
-  Replay stolen cookies if:
    1.  Tokens do not expire.
    2.  Tokens are not invalidated after logout or password change.
-  Abuse missing rate limiting on cookie validation endpoints.

### Password Reset Exploitation Techniques
-  Enumerate users via password reset responses.
-  Modify password reset URLs to target other users.
-  Reuse password reset tokens if:
    1.  Tokens do not expire.
    2.  Tokens are not bound to a specific user.
-  Intercept credentials when passwords are transmitted in plaintext via email.
-  Perform token guessing or brute-forcing when protections are weak.

### Password Change Exploitation Techniques
-  Change passwords without providing the current password.
-  Modify request parameters to target other users.
-  Abuse behavioural differences to brute-force old passwords:
    1.  Wrong old password + matching new passwords.
    2.  Wrong old password + mismatched new passwords.
    3.  Correct old password + mismatched new passwords.
-  Exploit client-side validation that is not enforced server-side.

## Key Takeaways
-  Authentication attacks rely heavily on logic flaws.
-  Small behavioural differences are often enough to exploit systems.
-  Partial or inconsistent protections are common and exploitable.
-  All authentication-related functionality should be tested, not just login pages.
