# 🔌 API Recon Checklist

> Practical methodology for discovering and testing API endpoints in web applications

---

# 🎯 Objective

Identify hidden API endpoints, parameters, and insecure logic for exploitation.

---

# 🔍 1. Identify API Endpoints

## Common Patterns

```plaintext id="f4h0yx"
/api/
/v1/
/v2/
/rest/
/graphql
```

---

## Sources

* JavaScript files
* Network tab (DevTools)
* Mobile apps
* Burp Suite proxy

---

# 🧠 2. Analyze API Requests

## Focus On

* HTTP methods (GET, POST, PUT, DELETE)
* Request body (JSON, XML)
* Headers (Authorization, tokens)

---

## Example

```http id="9c6z9h"
POST /api/user/update
{
  "user_id": 101,
  "email": "test@mail.com"
}
```

👉 Modify values → check behavior

---

# 🔑 3. Authentication Testing

## Check

* Missing authentication
* Weak tokens
* Reusable tokens

---

## Try

* Remove Authorization header
* Use another user token

---

# 🔓 4. Authorization Testing (IDOR)

## Modify IDs

```json id="hxg9e7"
"user_id": 101 → 102
```

👉 Can you access other users’ data?

---

# ⚡ 5. Parameter Manipulation

## Test

* Add new parameters
* Remove parameters
* Change values

---

## Example

```json id="tjg5bx"
"is_admin": true
"role": "admin"
```

---

# 🧪 6. HTTP Method Testing

Try different methods:

```http id="2h9q6p"
GET → POST → PUT → DELETE
```

👉 Sometimes restricted actions become accessible

---

# 📡 7. Hidden Endpoints Discovery

## Tools

* ffuf
* Burp Intruder

---

## Example

```bash id="5hcd6k"
ffuf -u https://api.target.com/FUZZ -w wordlist.txt
```

---

# 🔍 8. Rate Limiting Check

## Test

* Send multiple requests quickly

👉 If no limit → brute force possible

---

# 🌐 9. CORS Testing

## Add Header

```http id="m1c7q3"
Origin: https://attacker.com
```

👉 Check response headers

---

# 🔁 10. SSRF via APIs

## Look For

```json id="kl3i1x"
"url": "http://example.com"
```

👉 Replace with internal IP

---

# 📂 11. Data Exposure

## Check API Responses

```json id="s6l4g2"
{
  "password": "123456",
  "token": "abc123"
}
```

👉 Sensitive data leak

---

# 🧠 12. GraphQL Specific

## Test

```graphql id="g5s6r8"
{
  __schema {
    types {
      name
    }
  }
}
```

👉 Schema disclosure

---

# 🚨 High-Value Targets

* Authentication APIs
* Payment APIs
* Admin APIs
* Internal APIs

---

# 🧠 Pro Workflow

1. Find endpoints
2. Analyze requests
3. Test auth + authorization
4. Manipulate parameters
5. Look for data leaks

---

# ⚠️ Key Insight

APIs trust structured data → attackers exploit that trust
