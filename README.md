# 🐟 ShellCamo

**Advanced Command Obfuscation Generator for Red Team & Security Research**

[![Live Tool](https://img.shields.io/badge/Live%20Tool-ShellCamo-00ff88?style=for-the-badge&logo=github-pages)](https://giriaryan694-a11y.github.io/ShellCamo/)
![Stage](https://img.shields.io/badge/stage-Developmental-orange)
![License](https://img.shields.io/badge/license-Educational-blue)
![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20Windows-lightgrey)

> ⚠️ **AUTHORIZED USE ONLY** — This tool is designed exclusively for education, authorized penetration testing, and security research. Unauthorized use is illegal and unethical. Always obtain explicit written permission before generating or executing any payloads.

---

## 🔗 Live Tool

Access ShellCamo directly in your browser — no installation required:

**👉 [https://giriaryan694-a11y.github.io/ShellCamo/](https://giriaryan694-a11y.github.io/ShellCamo/)**

---

## 📖 Overview

ShellCamo is a fully static, client-side web tool that generates **truly hidden** obfuscated command payloads for **Bash**, **PowerShell**, and **cmd.exe**. Unlike basic obfuscators that merely insert quotes or backslashes (leaving the command readable), ShellCamo v4.1 ensures the original command is **never visible** in the generated output.

All payload generation happens entirely in the browser using JavaScript — **no server-side execution, no data transmission, no dependencies**.

### 🎯 Core Principle
Every technique included guarantees that static analysis tools, AV signatures, and log parsers **cannot read the original command** without runtime decoding. Only encoding, transformation, compression, and LOLBin-based techniques are included.

---

## ✨ Features

-   🐧 **Multi-Platform Support** — Generate payloads for Linux/Bash, Windows PowerShell, and cmd.exe
-   🎯 **Platform Selection** — Filter output by target OS (Linux, Windows, or All)
-   📋 **Reliable One-Click Copy** — Event-delegation based clipboard copy with safe base64 encoding (works with all special characters)
-   📊 **Evasion Metrics** — Real-time stats showing technique count, platform coverage, and evasion level rating
-   🎨 **Modern Dark UI** — Cybersecurity-themed responsive design with smooth animations
-   🔒 **100% Client-Side** — Zero network calls; all logic runs locally in the browser
-   ⌨️ **Keyboard Support** — Press `Enter` to generate payloads instantly
-   📱 **Fully Responsive** — Works seamlessly on mobile, tablet, and desktop
-   🏷️ **Technique Labeling** — Each payload is tagged with its category (Encoding, Layered, LOLBin, Encryption, etc.)
-   📝 **Inline Descriptions** — Every payload includes a clear explanation of how it works
-   🚧 **Developmental Stage** — Actively maintained and evolving

---

## 🛡️ Supported Techniques (48 Total)

### 🐧 Bash / Linux (17 Techniques)

| Technique | Category | Description |
| :--- | :--- | :--- |
| Base64 Encoding | Encoding | Standard base64 decode pipe to bash |
| ROT13 Cipher | Encoding | ROT13 shift decoded via `tr` |
| String Reversal | Transform | Reversed string decoded via `rev` |
| Hex Encoding (`$'...'`) | Encoding | ANSI-C hex escape sequences |
| Octal Encoding (`$'...'`) | Encoding | ANSI-C octal escape sequences |
| Double Base64 | Layered | Two layers of base64 encoding |
| Triple Base64 | Layered | Three encoding layers for maximum entropy |
| Here-String + Base64 | Advanced | Bash here-string feeding decoded command |
| Process Substitution | Advanced | Avoids temp files via `<()` |
| XARGS Execution | Advanced | Base64 decoded and piped through xargs |
| Printf Hex Escapes | Encoding | printf with hex escapes piped to bash |
| xxd Reverse Hex | Encoding | Hex string via xxd -r -p |
| Gzip + Base64 | Compression | Command compressed then encoded |
| Variable + Base64 | Advanced | Base64 stored in variable, decoded at runtime |
| Octal echo -e | Encoding | Octal escapes via echo -e |
| Base64 + Reversed | Layered | Base64 of reversed command |
| Hex printf Chain | Encoding | Hex escapes via printf chained to stdin |

### 💙 PowerShell (16 Techniques)

| Technique | Category | Description |
| :--- | :--- | :--- |
| EncodedCommand (`-enc`) | Native | UTF-16LE base64 encoded command |
| Short Flag (`-e`) | Native | Abbreviated `-EncodedCommand` flag |
| Character Array | Encoding | Command as `[char[]]` codes |
| Reversed + Base64 | Layered | Reversed command base64 encoded |
| Environment Variable | Advanced | Encoded payload stored in env var |
| ASCII Cast (`[char]...`) | Encoding | Each char cast to `[char]` then joined |
| Double Base64 | Layered | Two base64 layers with decode chain |
| New-Variable Chain | Advanced | Char codes via New-Variable cmdlet |
| `[ScriptBlock]::Create` | Advanced | Base64 decoded into ScriptBlock |
| .NET Concat + Char Codes | Advanced | .NET concatenation of character codes |
| Base64 + ROT13 | Layered | ROT13 applied then base64 encoded |
| Triple Layer | Polymorphic | Multiple encoding layers combined |
| .NET Convert Base64 | Advanced | Uses .NET Convert class for decode |
| Invoke-Command | Advanced | Invoke-Command with decoded scriptblock |
| XOR Decode | Encryption | Command XOR encoded, decoded via bitwise ops |
| Compressed Stream | Compression | DeflateStream compression + base64 |

### ⬛ cmd.exe (14 Techniques)

| Technique | Category | Description |
| :--- | :--- | :--- |
| certutil -decode | LOLBin | Base64 written to file, decoded with certutil |
| findstr + certutil | LOLBin | findstr filters then certutil decodes |
| mshta VBScript | LOLBin | mshta executes VBScript with encoded command |
| rundll32 JavaScript | LOLBin | rundll32 with javascript: protocol |
| FOR Loop + certutil | LOLBin | FOR /F loop reads decoded certutil output |
| Base64 Variable Expansion | Obfuscation | Base64 split into variables, expanded at exec |
| PowerShell Wrapper | Wrapper | cmd calls PowerShell with -EncodedCommand |
| Delayed Expansion + B64 | Advanced | `/v:on` delayed expansion with base64 |
| Reversed + certutil | Layered | Reversed command stored, certutil decodes |
| Hex + certutil | LOLBin | Hex encoded command decoded via certutil |
| forfiles + B64 | LOLBin | forfiles executes base64 decoded command |
| regsvr32 scrobj.dll | LOLBin | regsvr32 loads scriptlet with encoded command |
| Double B64 + certutil | Layered | Double base64 decoded in two certutil passes |
| bitsadmin download | LOLBin | bitsadmin downloads and executes encoded payload |

---

## 🎯 Use Cases

-   **Red Team Operations** — Test AV/EDR evasion capabilities against signature-based detection
-   **Blue Team Training** — Understand true obfuscation patterns to improve detection rules
-   **Security Education** — Learn how command hiding works across platforms
-   **CTF Competitions** — Rapidly generate hidden payloads for challenges
-   **Detection Engineering** — Build and test YARA/Sigma rules against encoded techniques
-   **Adversary Simulation** — Emulate TTPs mapped to MITRE ATT&CK T1027.010

---

## ⚠️ Legal & Ethical Disclaimer

> **THIS TOOL IS PROVIDED FOR EDUCATIONAL AND AUTHORIZED SECURITY TESTING PURPOSES ONLY.**

-   The obfuscation techniques generated by ShellCamo are **actively used by real threat actors** in the wild.
-   You must have **explicit written authorization** before generating or executing any payload on any system.
-   Unauthorized access to computer systems is a criminal offense under laws including but not limited to the **Computer Fraud and Abuse Act (CFAA)**, **UK Computer Misuse Act**, and equivalent legislation worldwide.
-   The authors and contributors assume **no liability** for misuse of this tool.
-   Always operate within the scope of a **signed Rules of Engagement (RoE)** document.

---

## 🏗️ Technical Details

-   **Architecture:** Single static HTML file with inline CSS and JavaScript
-   **Dependencies:** None — zero external libraries, frameworks, or CDN links
-   **Execution:** 100% client-side; no server, no API calls, no telemetry
-   **Copy Mechanism:** Event delegation + safe base64 data attributes (fixes all special character issues)
-   **Encoding:** Uses native browser APIs (`btoa()`, `atob()`, `TextEncoder`)
-   **PowerShell Base64:** Correctly implements UTF-16LE encoding required by `-EncodedCommand`
-   **Browser Compatibility:** Chrome, Firefox, Edge, Safari (all modern versions)
-   **Stage:** Developmental — actively being improved and expanded

---

## 📜 License

This project is provided for **educational purposes only**. Use responsibly and legally.

---

<div align="center">

**Made By Aryan Giri** | [giriaryan694-a11y](https://github.com/giriaryan694-a11y)

*For education and authorized testing only.*

</div>
