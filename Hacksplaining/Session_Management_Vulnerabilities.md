# Session Management Vulnerabilities

## What are Session Management Vulnerabilities
Session management vulnerabilities occur when an application fails to securely create, manage or invalidate session identifiers, allowing attackers to hijack or manipulate sessions.

## Impact of Session Management Vulnerabilities
-  Session hijacking.
-  Impersonate authenticated users.
-  Unauthorized access to sensitive data.
-  Authentication bypass.
-  Privilege escalation.

## Common Patterns
-  Weak or predictable session IDs.
-  Excessive session lifetime without expiration or rotation.
-  Passing session ID in via URL or request parameters (GET/POST).
-  Session not invalidated after logout or password change.
-  Lack of Secure, HttpOnly, and SameSite cookie attributes.

## Example Attack Scenario
**Session Hijacking**: The attacker intercepts or guesses the victim's session ID due to weak session handling. Using the session ID, the attacker gains access to authenticated session without knowing the exact credentials.

**Session Fixation**: The attacker exploits an application which doesn't regenerate session IDs after logging in. The attacker creates a phishing link that requires a user to log in with the attacker's session ID, then the attacker uses the authenticated session to perform unintended actions without knowing the credentials.

## Remediation
-  Generate long, random and unpredictable session IDs.
-  Store and pass session IDs in cookies.
-  Regenerate session IDs after authentication.
-  Set Secure, HttpOnly, and SameSite attributes on cookies.
-  Implement timeout and replace expired session IDs.
-  Require new session ID from suspicious referrer.

## Key Lessons
-  Session IDs are equivalent to authentication credentials.
-  Poor session handling can bypass strong authentication.
