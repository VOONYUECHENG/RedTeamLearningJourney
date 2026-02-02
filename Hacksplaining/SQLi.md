# SQL Injection

## What is SQL Injection
SQL Injection occurs when user-supplied input is not properly validated or sanitized and is directly concatenated into an SQL query, allowing an attacker to manipulate the query’s logic.

## Impact of SQL Injection
-  Access to confidential data. (e.g. credentials, credit card information, etc.)
-  Modification of database data. (INSERT INTO, UPDATE)
-  Bypass authentication.
-  DoS attack. (Overloading the database)

## Common Patterns
-  Input directly concatenated into queries.
-  Error message revealing information and behaviour of database.
-  Blind injection using Boolean-based or Time-based SQLi.
-  Applications assume user input will always be validated and well-formed.

## Example Payload
```sql
'--
' OR 1=1--
' UNION SELECT
```

## Remediation
-  Prepared Statements (Parameterized Queries)
-  Input Validation (Allowlists where possible)
-  Implement Least Privilege Principle
-  Disable Detailed Database Error Message in Production
-  Escaping User Input (e.g. Use “ \ ” on special characters like “ ’ ”) (Note: Use prepared statements if possible)

## Key Lessons
-  Never trust user inputs, sanitize them before using them as parameters.
-  Use prepared statement when user input is needed in queries.
