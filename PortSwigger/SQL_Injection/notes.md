## How SQL Injection happens?
SQL injection happens when an application takes untrusted input into queries without sanitization or validation. 
In PortSwigger labs, the vulnerabilities often happen in:
-  URL parameters
-  Login forms
-  Cookies used for tracking or authentication

## Types of SQL Injection
-  **On-band SQL Injection**: On-band SQL injection can be used to retrieve information as the results are shown directly on the application. For example, attackers can use attacks like UNION attacks to retrieve data from other tables. On-band SQL injection is easier to exploit because the error message or results are returned directly in the application response.
-  **Blind SQL Injection**: Blind SQL injection is more difficult and complicated than On-band SQL injection as no data is directly shown on the application. Attackers look for behaviour change in the application and minor details such as difference in response, redirect, or time delays.
-  **Out-of-band SQL Injection**: Out-of-band SQL injection carries the same SQL queries but do it asynchronously, the application's response doesn't depend on the query returning any data, a database error occurring, or on the time taken to execute the query. Therefore, the method to exploit the blind SQL injection vulnerability is by triggering out-of-band network interactions to a system to infer information. This technique is useful when the application is highly restricted and neither data nor errors are returned in responses.

## Remediation
-  Parameterized queries are the most reliable defense and should be used whenever user input is required in database queries.
-  Whitelisting permitted input values or using different logic to deliver the required behavior can also be used to reduce the risk but are insufficient alone.
