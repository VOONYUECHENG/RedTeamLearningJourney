## How Access Control Vulnerabilities Happen
Access control vulnerabilities occur when an application fails to enforce proper restrictions on what users are allowed to access or perform.

These vulnerabilities commonly arise due to:
- Missing or inconsistent authorization checks
- Trusting user-controlled input (parameters, cookies)
- Client-side enforcement instead of server-side
- Exposure of hidden or unlinked functionality

## Types of Access Control

### Vertical Access Control
- Users gain access to higher-privileged functionality
- Example: normal user accessing admin panel

### Horizontal Access Control
- Users access other users’ data
- Example: changing `user_id=123` → `user_id=124`

### Context-Dependent Access Control
- Access depends on application state
- Example: skipping steps in a workflow

## Common Vulnerable Areas

### URL-Based Access Control
- Sensitive endpoints exposed without checks

### Parameter-Based Access Control (IDOR)
- Direct access to objects using user-controlled input

### Role-Based Access Control
- Roles stored in cookies or request parameters

### HTTP Method-Based Access Control
- Protection applied only to specific methods (GET vs POST)

### Client-Side Access Control
- Restrictions enforced only in frontend

### Multi-Step Processes
- Steps can be skipped or reordered

## Key Lessons
- Access control must always be enforced server-side
- Every request must be validated independently
- Never trust user input for authorization decisions
