# 🔓 IDOR Checklist

> Practical checklist for identifying Insecure Direct Object Reference (IDOR) vulnerabilities

---

## 🎯 Core Concept

IDOR = Missing authorization check
👉 "Can I access someone else's data by changing an identifier?"

---

## 🔍 Where to Look

* `/api/user?id=`
* `/profile/123`
* `/orders/456`
* `/download?file=`
* `/invoice?id=`

---

## ⚡ Key Parameters to Test

* `id=`
* `user_id=`
* `account_id=`
* `order_id=`
* `file=`

---

## 🧠 Testing Workflow

### 1. Capture Request

Use proxy (Burp Suite)

---

### 2. Identify Object Reference

```http
GET /api/user?id=1001
```

---

### 3. Modify Value

```http
GET /api/user?id=1002
```

👉 Check if response changes

---

## 🔁 Horizontal IDOR

👉 Access another user's data

* Change user IDs
* Change profile IDs

---

## ⬆️ Vertical IDOR

👉 Privilege escalation

* Access admin endpoints
* Modify role IDs

---

## 💣 POST Request Testing

```http
POST /update-email
{
  "user_id": 102
}
```

👉 Change `user_id`

---

## 📂 File-Based IDOR

```http
/download?file=report_123.pdf
```

Try:

```http
/download?file=report_124.pdf
```

---

## 🔢 ID Patterns to Try

* Increment: `1001 → 1002`
* Decrement: `1001 → 1000`
* Random values
* UUID modification

---

## 🧬 API Testing

Check JSON responses:

```json
{
  "user_id": 101,
  "email": "user@example.com"
}
```

👉 Modify and resend

---

## 🔐 Bypass Techniques

* Remove authentication headers
* Change cookies
* Use another user session

---

## 📍 High-Value Targets

* User profiles
* Payment history
* Private messages
* Admin APIs

---

## 🚨 Indicators of Vulnerability

* Data of another user visible
* No error when ID changed
* Response returns valid data

---

## 🧠 Pro Tips

* Always test with **2 accounts**
* Compare responses side-by-side
* Focus on APIs (most vulnerable)

---

## ⚠️ Key Insight

If access is controlled only by ID → likely IDOR
