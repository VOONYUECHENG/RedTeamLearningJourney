# Cross-Site Request Forgery (CSRF)

## What is Cross-Site Request Forgery
Cross-Site Request Forgery happens when an attacker tricks an authenticated user's browser into performing unintended actions without the user's consent, such as changing password, deleting files, etc.

## Impact of Cross-Site Request Forgery
-  Unauthorized action performed on behalf of the victim.
-  Data manipulation or deletion.
-  Malware installation and spreading.

## Common Patterns
-  Sensitive action performed via GET and POST requests without protection.
-  Lack of CSRF tokens in state-changing requests.
-  Predictable or reusable anti-forgery tokens.
-  Applications solely relying on cookies for authentication.

## Example Attack Scenario
An attacker discovers a file delete button that doesn't verify CSRF tokens in an application. The attacker creates a malicious link that triggers the file deletion request. When an authenticated user clicks on the link, the browser automatically includes session cookies, causing the file to be deleted without the victim’s intent.

## Remediation
-  Implement CSRF tokens.
-  Implement SameSite cookie attributes.
-  Implement multi-factor authentication when performing state-changing actions (like deleting files, changing password, etc.).
-  Verify Origin and Referer headers. 

## Key Lesson
-  Unlike XSS, which exploits users' trust in the website, CSRF exploits the website's trust in the users.
-  CSRF tokens are the primary defense against CSRF attacks.
-  Cookies are automatically included in cross-site requests.
