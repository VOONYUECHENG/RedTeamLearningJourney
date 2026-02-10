## How Authentication Vulnerabilities Happen
Authentication vulnerabilities occur when an application fails to properly verify a user’s identity or manage authentication-related logic securely. This often allows attackers to gain unauthorized access to user accounts or sensitive functionality.

In PortSwigger Web Security Academy labs, these vulnerabilities commonly arise due to:
-  Weak credential handling
-  Inconsistent error messages
-  Flawed session or token logic
-  Missing rate limiting or protections against automation

## Common Vulnerable Areas Observed in Labs
### Login Functionality
-  Different error messages for invalid username vs invalid password
-  Missing rate limiting on login attempts
-  Predictable or weak credentials used for testing

### User Enumeration
-  Error messages revealing whether a username exists
-  Response time differences between valid and invalid users
-  Different HTTP status codes or redirects

### Brute-Force Protection
-  No account lockout or request throttling
-  Incomplete protections that can be bypassed using:
  -  IP rotation
  -  Parallel requests
  -  Correct credential ordering

### Multi-Factor Authentication (MFA)
-  MFA codes not tied to a specific session or user
-  Ability to brute-force MFA codes
-  MFA verification step can be skipped or bypassed
-  MFA enforced only after successful login, not consistently

### “Stay Logged In” Cookies
-  Cookies storing sensitive data (e.g. username or token)
-  Predictable or weakly encoded cookie values
-  Tokens not invalidated after logout or password change

### Password Reset Functionality
-  Predictable or reusable reset tokens
-  Tokens not expiring
-  Tokens not bound to a specific user
-  Ability to enumerate valid users through reset responses

### Password Change Functionality
-  Password change does not require current password
-  Password change endpoint trusts client-side values
-  Ability to change another user’s password by modifying parameters

## Key Lessons from Labs
-  Authentication vulnerabilities are often logic flaws, not input-based issues
-  Small differences in application behaviour can leak sensitive information
-  Security controls are often present but inconsistently enforced
-  Defense mechanisms must be applied end-to-end, not partially

## Remediation
-  Use generic error messages for authentication failures
-  Enforce strong rate limiting and account lockout policies
-  Bind authentication tokens to users and sessions
-  Ensure reset and MFA tokens are random, unique, and expire quickly
-  Re-authenticate users for sensitive actions (e.g. password changes)
