# Command Injection

## What is Command Injection
Command Injection happens when an application accepts untrusted input and passes it directly to a system shell or operating system command without proper validation and sanitization, allowing an attacker to execute arbitrary system commands.

## Impact of Command Injection
-  DoS attack.
-  Unauthorized execution of system commands.
-  Unauthorized access to sensitive files and information.
-  Privilege escalation.
-  Full system compromise.

## Common Patterns
-  User input concatenated directly into system commands.
-  Use of dangerous commands (like system(), exec(), Runtime.exec()).
-  System assumes user input is validated and well-formed.

## Example Payload
```bash
; ls
&& whoami
| id
```
These payloads are used to confirm command injection condition.

## Remediation
-  Input validation & sanitization using strict allowlists.
-  Implement least privilege principles.
-  Escape command arguments.
-  Disable unnecessary system components.
-  Use parameterized APIs.

## Key Lessons
-  Never trust user input.
-  Eliminating shell execution is the primary method to prevent command injection attacks.
