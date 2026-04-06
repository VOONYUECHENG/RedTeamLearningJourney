## Attack Scenarios

### 1. Horizontal Access Control (IDOR)

Request:
GET /account?user_id=123

Attack:
Change parameter:
GET /account?user_id=124

Result:
Access another user’s account data

---

### 2. Vertical Privilege Escalation

Request:
GET /admin

Attack:
Directly access endpoint without UI navigation

OR

Modify request:
POST /admin/deleteUser

Result:
Perform admin-only actions as normal user

---

### 3. Role Manipulation via Cookie

Cookie:
role=user

Attack:
Change to:
role=admin

Result:
Gain access to admin functionality

---

### 4. HTTP Method Bypass

Blocked request:
GET /admin → 403 Forbidden

Attack:
POST /admin

Result:
Access granted due to missing method validation

---

### 5. Hidden Endpoint Discovery

Attack:
Check:
- /robots.txt
- JavaScript files
- Burp proxy history

Discover:
GET /admin-panel

Result:
Access unlinked admin functionality

---

### 6. Multi-Step Workflow Bypass

Normal flow:
1. Add item
2. Confirm purchase
3. Payment

Attack:
Skip step 2:
POST /payment

Result:
Complete action without required validation

---

### 7. Parameter-Based Privilege Escalation

Request:
POST /updateRole
role=user

Attack:
role=admin

Result:
Privilege escalation if not validated server-side
