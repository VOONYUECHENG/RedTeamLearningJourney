## How Authentication Vulnerabilities Happen
Authentication vulnerabilities occur when an application fails to properly verify a user’s identity or securely manage authentication logic. This often allows attackers to gain unauthorized access to user accounts or sensitive data.

In PortSwigger Web Security Academy labs, these vulnerabilities commonly arise due to:
-  Weak credential handling.
-  Inconsistent or detailed error messages.
-  Flawed session or token logic.
-  Weakly implemented multi-factor authentication (MFA).
-  Missing rate limiting or protections against brute-force attacks.

## Common Vulnerable Areas Observed in Labs
### Login Functionality
-  Different error messages for invalid username and invalid password.
-  Missing rate limiting on login attempts.
-  Predictable or weak credentials used.

### User Enumeration
-  Error messages revealing whether a username exists.
-  Response time differences between valid and invalid users.
-  Different HTTP status codes or redirects.

### Brute-Force Protection
-  No account lockout or request throttling after a certain amount of tries.
-  Only valid username gets account lockout.
-  Incomplete protections that can be bypassed using:

  1.  IP rotation.
  2.  Parallel requests.
  3.  Correct credential ordering.

### Multi-Factor Authentication (MFA)
-  MFA codes not tied to a specific session or user.
-  Easily brute-forced MFA codes.
-  MFA verification step can be skipped or bypassed.
-  MFA enforced only after successful login and is not verified properly.
-  Logging in with own credentials and MFA code, then replacing session cookies with the victim’s cookies.

### “Stay Logged In” Cookies
-  Cookies storing sensitive data (e.g. username or token).
-  Predictable or weakly encoded cookie values.
-  Tokens not invalidated after logout or password change.
-  Brute-forcing persistent login tokens is not rate-limited or blocked.

### Password Reset Functionality
-  Predictable or reusable reset tokens.
-  Tokens not expiring.
-  Tokens not bound to a specific user.
-  Ability to enumerate valid users through reset responses.
-  Sending plaintext passwords via email, exposing credentials to interception (e.g. Man-in-the-Middle attacks).
-  Password reset URLs contain parameters that expose usernames and can be modified to target other users.

### Password Change Functionality
-  Password change does not require current password.
-  Password change endpoint trusts client-side values.
-  Ability to change another user’s password by modifying parameters.
-  Different behaviour from different input (attackers can brute-force old password by checking behaviour):

  1.  Wrong old password, same for new password and new password confirmation.
  2.  Wrong old password, different for new password and new password confirmation.
  3.  Correct old password, different for new password and new password confirmation.

## Key Lessons from Labs
-  Authentication vulnerabilities are often logic flaws, not input-based issues.
-  Small differences in application behaviour can leak critical sensitive information.
-  Security controls are often present but inconsistently enforced.
-  Defense mechanisms must be applied end-to-end, not partially.

## Remediation
-  Use generic error messages for authentication failures and indistinguishable response time.
-  Enforce strong rate limiting and account lockout policies.
-  Bind authentication tokens to users and sessions.
-  Ensure reset and MFA tokens are random, unique, and expire quickly.
-  Re-authenticate users for sensitive actions (e.g. password changes).
-  Enforce strong password policies.
-  Enforce HTTPS and ensure authentication data is only transmitted over encrypted connections.
-  Test authentication logic not only on the main login page but also on supporting functionality such as password reset and account recovery.
