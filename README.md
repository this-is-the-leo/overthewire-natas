markdown
# Natas Writeup

[![OverTheWire](https://img.shields.io/badge/OverTheWire-Natas-3fb950)](https://overthewire.org/wargames/natas/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![HTML](https://img.shields.io/badge/HTML-5-orange)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS](https://img.shields.io/badge/CSS-3-blue)](https://developer.mozilla.org/en-US/docs/Web/CSS)

> A comprehensive, educational walkthrough of the Natas wargame from OverTheWire.

---

## 📖 Table of Contents

- [About This Project](#about-this-project)
- [Project Goals](#project-goals)
- [Structure](#structure)
- [Levels Overview](#levels-overview)
- [Technologies Covered](#technologies-covered)
- [Tools Used](#tools-used)
- [Project Structure](#project-structure)
- [Key Security Lessons](#key-security-lessons)
- [Quick Reference](#quick-reference)
- [Installation & Usage](#installation--usage)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## About This Project

This repository contains detailed writeups for the **Natas** wargame from [OverTheWire](https://overthewire.org/wargames/natas/), covering levels 0 through 35. Natas is a web security wargame that teaches the fundamentals of web application vulnerabilities through hands-on, practical challenges.

Each level is documented with a focus on understanding the underlying vulnerability, the exploitation process, and the defensive measures required to prevent it in real-world applications.

### Why Natas?

Natas is one of the best wargames for learning web security because:
- It starts with basic concepts and progressively increases in difficulty
- Each level introduces a new vulnerability or technique
- It requires minimal setup — only a browser and basic tools
- It covers both client-side and server-side vulnerabilities

---

## Project Goals

This project was created with the following objectives:

| Goal | Description |
|------|-------------|
| **Educational** | Provide clear, step-by-step explanations of each vulnerability |
| **Technical** | Include practical commands, code examples, and exploitation techniques |
| **Defensive** | Explain how to prevent each vulnerability in real-world applications |
| **Bilingual** | Available in both English and Persian (Farsi) |
| **Professional** | Demonstrate technical and analytical skills through high-quality documentation |
| **Accessible** | Designed for beginners while remaining valuable for experienced developers |

---

## Structure

Each level writeup follows a consistent structure to ensure clarity and ease of learning:
┌─────────────────────────────────────────────────────────────┐
│ Level X → Natas X+1 │
├─────────────────────────────────────────────────────────────┤
│ Challenge Overview → What the level presents │
│ Key Concepts → Security topics involved │
│ Initial Analysis → Approach to understanding │
│ Solution Walkthrough → Step-by-step resolution │
│ Commands and Code → Practical implementation │
│ Why It Works → Technical explanation │
│ Defensive Measures → How to prevent it │
│ Key Takeaways → Summary of insights │
└─────────────────────────────────────────────────────────────┘

text

---

## Levels Overview

| Range | Levels | Topics |
|-------|--------|--------|
| **00–05** | 6 | **Web Fundamentals** — View Source, JS Bypass, Directory Listing, robots.txt, Referer, Cookies |
| **06–10** | 5 | **Server-Side Vulnerabilities** — PHP Include, Path Traversal, Encoding, Command Injection |
| **11–15** | 5 | **Cryptography & File Upload** — XOR, File Upload, SQL Injection, Blind SQL |
| **16–20** | 5 | **Blind Injection & Session Attacks** — Blind Command Injection, Time-Based SQL, Session ID |
| **21–25** | 5 | **Advanced Injection & Type Juggling** — Session Injection, Header Injection, LFI |
| **26–30** | 5 | **Object Injection & Advanced SQL** — PHP Object Injection, UNION SQL, Stacked Queries |
| **31–35** | 5 | **File Upload & XXE** — Image Verification, XML External Entity |

### Difficulty Distribution
📊 35 Levels Total
├── 🟢 Easy : 12 levels (00–05, 06–10)
├── 🟡 Medium : 2 levels (04, 05)
└── 🔴 Hard : 21 levels (06–35)

text

---

## Technologies Covered

| Category | Technologies |
|----------|--------------|
| **Frontend** | HTML, CSS, JavaScript, Browser DevTools |
| **Backend** | PHP (Include, Session, Serialization, Type Juggling) |
| **Database** | SQL (Injection, Blind SQL, UNION, Stacked Queries) |
| **System** | Command Injection, Shell Metacharacters |
| **Data Formats** | XML (XXE), JSON, Base64, Hex Encoding |
| **Network** | HTTP Headers (Referer, Location, Cookies) |
| **Security** | Authentication Bypass, Session Management, File Upload Security |

---

## Tools Used

| Tool | Purpose |
|------|---------|
| **Browser DevTools** | Source inspection, cookie editing, network analysis |
| **curl** | HTTP requests with custom headers, automation |
| **Burp Suite** | Intercepting and modifying requests, Intruder for brute force |
| **Python** | Automation for blind injection, brute force, data extraction |
| **Netcat / nc** | Listening for out-of-band XXE exfiltration |
| **xxd / base64** | Command-line encoding/decoding |

---

## Project Structure
natas-writeup/
│
├── README.md # Project documentation
├── LICENSE # MIT License
│
├── index.html # English home page (Levels 00–35)
├── fa/
│ └── index.html # Persian home page
│
├── levels/ # English level writeups
│ ├── level-0.html
│ ├── level-1.html
│ ├── ...
│ └── level-35.html
│
└── fa/ # Persian level writeups
└── levels/
├── level-0.html
├── level-1.html
├── ...
└── level-35.html

text

---

## Key Security Lessons

Throughout this writeup series, the following security principles are emphasized:

### 1. Never Trust Client-Side Data
Everything sent to the browser — HTML comments, JavaScript, cookies — is fully inspectable and modifiable by the user.

### 2. Implement Server-Side Validation
Authentication, authorization, and input validation must always be performed on the server, never solely on the client.

### 3. Secure Configuration Is Critical
- Disable directory listing on web servers
- Don't use `robots.txt` to hide sensitive paths
- Store sensitive files outside the web root

### 4. Avoid Security by Obscurity
Hiding something does not make it secure. Attackers will find it.

### 5. Use Cryptographic Signing
Protect cookies and client-side state with cryptographic signatures to prevent tampering.

### 6. Use Prepared Statements
Parameterized queries are the most effective defense against SQL injection. No other defense is as reliable.

### 7. Disable External Entities in XML Parsers
XXE attacks can read local files and perform SSRF. Always disable external entity resolution.

### 8. Never Deserialize Untrusted Data
PHP object injection can lead to remote code execution. Use JSON instead of `serialize()`/`unserialize()`.

### 9. Validate File Uploads Thoroughly
Check file type, content, size, and store uploaded files outside the web root. Re-encode images to remove embedded code.

### 10. Use Strong Session Management
Session IDs must be cryptographically random with high entropy. Never use sequential or predictable IDs.

---

## Quick Reference

| Level | Vulnerability | Difficulty |
|-------|---------------|------------|
| 00 | HTML Comment | 🟢 Easy |
| 01 | JavaScript Bypass | 🟢 Easy |
| 02 | Directory Listing | 🟢 Easy |
| 03 | robots.txt Info Disclosure | 🟢 Easy |
| 04 | Referer Spoofing | 🟡 Medium |
| 05 | Cookie Manipulation | 🟡 Medium |
| 06 | PHP Include | 🔴 Hard |
| 07 | Path Traversal | 🔴 Hard |
| 08 | Encoding Bypass | 🔴 Hard |
| 09 | Command Injection | 🔴 Hard |
| 10 | Command Injection (Filter) | 🔴 Hard |
| 11 | XOR Encryption | 🔴 Hard |
| 12 | File Upload (Client-Side) | 🔴 Hard |
| 13 | File Upload (Server-Side) | 🔴 Hard |
| 14 | SQL Injection | 🔴 Hard |
| 15 | Blind SQL (Boolean-Based) | 🔴 Hard |
| 16 | Blind Command Injection | 🔴 Hard |
| 17 | Blind SQL (Time-Based) | 🔴 Hard |
| 18 | Session ID Prediction | 🔴 Hard |
| 19 | Session ID Encoding | 🔴 Hard |
| 20 | Session Data Injection | 🔴 Hard |
| 21 | Cross-Site Session | 🔴 Hard |
| 22 | Header Injection | 🔴 Hard |
| 23 | PHP Type Juggling | 🔴 Hard |
| 24 | PHP Type Juggling (Advanced) | 🔴 Hard |
| 25 | LFI — Log Poisoning | 🔴 Hard |
| 26 | PHP Object Injection | 🔴 Hard |
| 27 | SQL Injection (UNION) | 🔴 Hard |
| 28 | SQL Injection (Stacked) | 🔴 Hard |
| 29 | Command Injection (Advanced) | 🔴 Hard |
| 30 | SQL Injection (Filter Bypass) | 🔴 Hard |
| 31 | File Upload (Image Verification) | 🔴 Hard |
| 32 | XXE — External Entity | 🔴 Hard |
| 33 | XXE — File Inclusion | 🔴 Hard |
| 34 | XXE — DTD-Based | 🔴 Hard |
| 35 | XXE — OOB Exfiltration | 🔴 Hard |

---

## Installation & Usage

### Option 1: View Online
Visit the GitHub Pages URL to view the writeup in your browser.

### Option 2: Clone Locally

```bash
git clone https://github.com/this-is-the-leo/natas-writeup.git
cd natas-writeup
Then open index.html in your browser to start exploring.

Option 3: Serve with Python
bash
python3 -m http.server 8000
Then navigate to http://localhost:8000 in your browser.

📝 Contributing
Contributions are welcome! If you find any issues or have suggestions for improvements:

Fork the repository

Create a new branch

Make your changes

Submit a pull request

📄 License
This project is for educational purposes only. Use responsibly and only on systems you have permission to test.

MIT License — see the LICENSE file for details.

text
MIT License

Copyright (c) 2025 Leo (Ilya Farahani)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
🙏 Acknowledgments
OverTheWire — For creating the Natas wargame and providing an incredible platform for learning

OWASP — For web security education resources and the OWASP Top 10

PortSwigger — For Burp Suite and excellent web security content

The Security Community — For continuous knowledge sharing and collaboration

👨‍💻 Author
Leo (Ilya Farahani)

🌐 GitHub: github.com/this-is-the-leo

🔗 LinkedIn: linkedin.com/in/ilya-farahani

💬 Telegram: t.me/Here_is_leo

📧 Email: ilyafarahani9@gmail.com

Feel free to reach out for questions, collaboration, or feedback!

🌟 Star the Project
If you found this writeup helpful, please consider starring the repository on GitHub!

https://img.shields.io/github/stars/this-is-the-leo/natas-writeup.svg?style=social

Happy Hacking! 🚀

"Security is not a product, but a process." — Bruce Schneier