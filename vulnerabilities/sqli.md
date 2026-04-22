# SQL Injection (SQLi)

---

## 📌 Description

SQL Injection (SQLi) is a server-side vulnerability that allows an attacker to interfere with the queries that an application makes to its database.

It occurs when user input is directly included in SQL queries without proper validation or sanitization.

---

## ⚙️ How It Works (Technical)

Applications often take user input and insert it into SQL queries.

Example vulnerable query:

```sql
SELECT * FROM users WHERE username = 'admin' AND password = 'password';
```

If input is not sanitized, an attacker can manipulate the query.

---

## 💣 Example Payloads

### Authentication Bypass

```sql
' OR '1'='1
```

Resulting query:

```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
```

👉 This condition is always true → login bypass

---

### Comment Bypass

```sql
' OR 1=1 --
```

The `--` comments out the rest of the query.

---

### Union-Based Injection

```sql
' UNION SELECT null, username, password FROM users --
```

Used to extract data from the database.

---

## 📍 Common Injection Points

* Login forms
* Search fields
* URL parameters
* Cookies
* HTTP headers

---

## 🌍 Real-World Impact

* Unauthorized login (admin access)
* Data leakage (usernames, passwords)
* Database modification or deletion
* Full system compromise

Example:

* SQL injection has been used in major breaches affecting millions of users.

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify input fields

2. Inject:

   ```sql
   '
   ```

   👉 Check for SQL errors

3. Try boolean-based payload:

   ```sql
   ' OR '1'='1
   ```

4. Try error-based testing:

   ```sql
   ' AND 1=CONVERT(int, 'test')
   ```

5. Test for data extraction:

   * UNION-based queries
   * Blind SQLi (true/false responses)

---

## 🛡️ Remediation

* Use parameterized queries (prepared statements)
* Use ORM frameworks
* Validate and sanitize input
* Avoid dynamic SQL queries
* Apply least privilege to database users

---

## 🧠 Key Takeaway

SQL Injection is dangerous because it allows attackers to directly interact with the database, leading to data theft or complete system compromise.
