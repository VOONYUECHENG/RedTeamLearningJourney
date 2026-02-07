# Authentication Vulnerabilities

## What are Authentication Vulnerabilities
Authentication vulnerabilities happen when an application incorrectly implements the mechanisms used to verify the user's identity, allowing attackers to bypass login controls and gain unauthorized access to the user's profile.

## Impact of Authentication Vulnerabilities
-  Account takeover.
-  Leaks of sensitive data.
-  Unintended actions performed.
-  Privilege escalation.
-  Full system takeover if high-privileged account is hijacked.

## Common Patterns
-  Weak or predictable passwords.
-  Lack of account lockout or rate limiting (brute-force enabled)
-  Insecure password storage (e.g. plaintext or weak hashing).
-  Lack of or improperly implemented multi-factor authentication (MFA).

## Example Attack Scenario
An attacker uses a brute-force attack to guess the administrator password on an application that doesn't perform profile lockout or rate limiting, leading to sensitive data leaks and full system compromise.

## Remediation
-  Enforce strong password policies (e.g. minimum length, special characters).
-  Store password hash (with salt/pepper).
-  Use timeout or CAPTCHA to prevent brute-force attacks.
-  Implement third-party authentication from federated identity providers (e.g. login with Google).
-  Implement multi-factor authentication properly.
-  Avoid revealing detailed authentication error messages.
-  Use secure, single-use tokens for password reset via email (when forgot password).
-  Old password needed to change password.

## Key Lessons
-  Implement defense-in-depth to protect authentication.
-  Authentication is the first line of defense.
-  Severity of authentication compromise based on privilege of the account (from data leaks to full system compromise).
