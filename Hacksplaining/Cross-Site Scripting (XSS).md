# Cross-Site Scripting (XSS)

## What is Cross-Site Scripting
Cross-Site Scripting happens when an application accepts untrusted user input without proper handling, allowing attackers to inject malicious scripts (like JavaScript) that execute in victims' browsers within the context of a trusted website.

## Types of XSS:
-  **Reflected XSS**: The malicious code is reflected off the web server, often from a malicious URL, and execute in the victim's browser.
-  **Stored XSS**: The malicious code is stored permanently on the target server and is served whenever a user access to the compromised page.
-  **DOM-based XSS**: The vulnerability exists in client-side code where JavaScript processes untrusted data from the DOM without proper handling. 

## Impact of Cross-Site Scripting
-  Session hijacking
-  Dos attack
-  Data theft
-  Phishing attack

## Common Patterns
-  User input reflected directly into HTML responses.
-  Stored user-generated content rendered without encoding.
-  Client-side JavaScript modifying the DOM using untrusted data.
-  Lack of output encoding based on context.

## Example Payload
```html
<script>alert(1)</script>
<img src=x onerror=alert(1)>
```
Both of the payloads are harmless and are to confirm an XSS condition.

## Remediation
-  Implement Content Security Policy (CSP).
-  Validate input using allowlists where possible.
-  Apply proper output encoding based on context.
-  Escape Dynamic Content.
-  Avoid inserting untrusted data directly into the DOM.

## Key Lessons
-  Output encoding is the primary defense against XSS.
-  Input validation only is insufficient against XSS.
-  Never trust user input.
