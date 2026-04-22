# Insecure Direct Object Reference (IDOR)

---

## 📌 Description

IDOR is a type of access control vulnerability where an application exposes internal object references (such as user IDs) without proper authorization checks.

This allows attackers to access or modify data belonging to other users.

---

## ⚙️ How It Works (Technical)

Applications often use identifiers to access resources.

Example:

```url id="b9n4dp"
https://example.com/api/user?id=123
```

If the application does not verify whether the logged-in user owns this ID, an attacker can modify it:

```url id="1gn0r6"
https://example.com/api/user?id=124
```

👉 Access another user's data

---

## 💣 Example Scenarios

### Accessing Other User Profiles

```url id="5b1k3h"
https://example.com/profile/1001
```

Change to:

```url id="q4y9g2"
https://example.com/profile/1002
```

---

### Modifying Data

```http id="6p6uqm"
POST /api/update-email
{
  "user_id": 102,
  "email": "attacker@email.com"
}
```

👉 If no authorization check → attacker updates another account

---

## 📍 Common Places to Find

* User profile endpoints
* API requests with IDs
* File downloads
* Order or transaction history

---

## 🌍 Real-World Impact

* Unauthorized data access
* Account takeover
* Privacy violations
* Data modification or deletion

---

## 🔎 Detection Methodology (Pentester Approach)

1. Log in as a normal user
2. Intercept requests (using proxy)
3. Identify object references:

   * `id=`
   * `user_id=`
   * `account=`
4. Modify the value
5. Observe response:

   * Does it return another user's data?

---

## 🛡️ Remediation

* Implement proper access control checks
* Verify ownership of every request
* Use indirect references (UUIDs)
* Avoid exposing predictable IDs

---

## 🧠 Key Takeaway

IDOR occurs when applications trust user input for accessing resources without verifying authorization.
