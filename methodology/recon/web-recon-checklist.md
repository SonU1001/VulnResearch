# 🌐 Web Recon Checklist

> Practical reconnaissance methodology used in bug bounty and penetration testing

---

# 🎯 Objective

Identify attack surface, hidden assets, and potential entry points.

---

# 🔍 1. Domain & Subdomain Enumeration

## Tools

* subfinder
* amass
* assetfinder

---

## Commands

```bash
subfinder -d target.com
amass enum -d target.com
```

---

## What to Look For

* dev.target.com
* api.target.com
* staging.target.com
* admin.target.com

👉 These are high-value targets

---

# 🌐 2. Live Host Discovery

## Tools

* httpx
* httprobe

```bash
httpx -l domains.txt
```

---

## Goal

Find which subdomains are actually alive

---

# 📂 3. Directory & Endpoint Discovery

## Tools

* ffuf
* dirsearch

```bash
ffuf -u https://target.com/FUZZ -w wordlist.txt
```

---

## Common Paths

* /admin
* /api
* /backup
* /.git
* /.env

---

# 🔗 4. URL & Parameter Discovery

## Tools

* gau
* waybackurls

```bash
gau target.com
```

---

## Look For

* `?id=`
* `?user=`
* `?redirect=`
* `?url=`

👉 These lead to vulnerabilities

---

# 🧠 5. Technology Fingerprinting

## Tools

* whatweb
* wappalyzer

---

## Identify

* Framework (Laravel, Django)
* Server (Apache, Nginx)
* CMS (WordPress)

👉 Helps choose attack methods

---

# 📡 6. API Recon

## Look For

* `/api/`
* `/v1/`
* `/graphql`

---

## Test

* JSON responses
* Hidden endpoints
* Parameter manipulation

---

# 🔐 7. Sensitive File Discovery

## Check for

```plaintext
/.env
/.git
/backup.zip
/config.php
```

---

## Why Important

👉 Can expose:

* API keys
* credentials
* database info

---

# 🧪 8. JavaScript Analysis

## What to Do

* Open JS files
* Search for:

```plaintext
api_key
token
endpoint
secret
```

---

## Tools

* LinkFinder
* JSParser

---

# 🌍 9. Third-Party Services

## Check

* CDN
* external APIs
* integrations

---

## Why

👉 Sometimes weaker than main app

---

# 🚨 10. High-Value Targets Summary

Focus on:

* Admin panels
* APIs
* File uploads
* Authentication endpoints

---

# 🧠 Pro Workflow

1. Collect subdomains
2. Filter live hosts
3. Find endpoints
4. Analyze parameters
5. Start vulnerability testing

---

# ⚠️ Key Insight

Recon is not about tools—it’s about finding **interesting attack surfaces**
