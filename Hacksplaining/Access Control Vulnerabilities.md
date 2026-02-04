# Access Control Vulnerabilities

## What are Access Control Vulnerabilities
Access control vulnerabilities occur when an application fails to define and enforce what authenticated or unauthenticated users are allowed to do, allowing attackers to perform actions or gain access to resources beyond intended permissions.

## Impact of Access Control Vulnerabilities
-  Unauthorized access to sensitive data.
-  Horizontal privilege escalation (access to other users' data).
-  Vertical privilege escalation (gain admin-level access).
-  Data deletion or modification.
-  Full system compromise.

## Common Patterns
-  Missing authorization checks on sensitive endpoints.
-  Insecure Direct Object Reference (IDOR).
-  Parameter manipulation.
-  Client-side enforcement of access control.
-  Predictable resource identifiers (e.g. user IDs).

## Example Attack Scenario
**IDOR**: An attacker notices that a user profile is accessed using a URL parameter such as /profile?id=1000. By changing the ID value, the attacker is able to access other users’ profiles without authorization.

**Privilege Escalation**: An attacker realizes changing parameters like admin=false to admin=true can allow access to admin controls.

## Remediation
-  Centralize access control.
-  Test access control critically.
-  Verify user permission on every sensitive request.
-  Implement least privilege principles.
-  Enforce access control on server-side.

## Key Lessons
-  Authentication does not imply authorization.
-  Access control must be enforced server-side.
-  Broken access control is one of the most common and critical web vulnerabilities.
