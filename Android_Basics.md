# 📱 Complete Android Penetration Testing Guide for Students

## A Hands-on Guide Using AndroGoat — The Vulnerable Android App


# 📖 Table of Contents

1. [Project Overview](#-project-overview)
2. [About AndroGoat](#-about-androgoat)
3. [Android Architecture & Components](#-android-architecture--components)
4. [APK Folder Structure](#-apk-folder-structure)
5. [Understanding the Attack Surface](#-understanding-the-attack-surface)
6. [Lab Environment Setup](#-lab-environment-setup)
   - Hardware & Software Prerequisites
   - Android Emulator Setup
   - Installing AndroGoat
7. [Essential Tools for Android Pentesting](#-essential-tools-for-android-pentesting)
   - static Analysis Tools
   - Dynamic Analysis Tools
   - Network Interception Tools
8. [Android Penetration Testing Methodology](#-android-penetration-testing-methodology)
   - Phase 1: Information Gathering
   - Phase 2: Static Analysis
   - Phase 3: Dynamic Analysis
   - Phase 4: Network Analysis
   - Phase 5: Exploitation & Reporting
9. [OWASP Mobile Top 10 2024 — Complete Breakdown](#-owasp-mobile-top-10-2024--complete-breakdown)
   - M1: Improper Credential Usage
   - M2: Inadequate Supply Chain Security
   - M3: Insecure Authentication/Authorization
   - M4: Insufficient Input/Output Validation
   - M5: Insecure Communication
   - M6: Inadequate Privacy Controls
   - M7: Insufficient Binary Protections
   - M8: Security Misconfiguration
   - M9: Insecure Data Storage
   - M10: Insufficient Cryptography
10. [OWASP Mobile Top 10 2024 × AndroGoat Vulnerability Mapping](#-owasp-mobile-top-10-2024--androgoat-vulnerability-mapping)
    - Complete Vulnerability Mapping Table
    - Step-by-Step Practice Exercises
11. [OWASP MASVS & MASTG — Standards and Testing Guide](#-owasp-masvs--mastg--standards-and-testing-guide)
12. [Complete Toolbox Cheatsheet](#-complete-toolbox-cheatsheet)
    - ADB Commands
    - APK Analysis Commands
    - Frida & Objection Commands
13. [Study Roadmap for Students](#-study-roadmap-for-students)
14. [Additional Resources](#-additional-resources)
15. [Conclusion](#-conclusion)


# 🎯 Project Overview

Welcome to the **Complete Android Penetration Testing Guide**! This guide is specifically designed for **students** and **beginners** who want to learn Android security testing from scratch.

> **Why this guide?** Android powers over 2.5 billion devices worldwide. Understanding how to secure Android applications is a critical skill for any cybersecurity professional. This guide uses **AndroGoat** — an intentionally vulnerable Android app — as your practice ground, providing hands-on experience with real-world security flaws.

**What you will learn:**
- ✅ Android architecture and how apps are built
- ✅ How to set up your own Android pentesting lab
- ✅ Static and dynamic analysis techniques
- ✅ How to identify and exploit OWASP Mobile Top 10 vulnerabilities
- ✅ Using professional pentesting tools (ADB, Frida, Burp Suite, MobSF, etc.)
- ✅ And most importantly — how to **fix** these security issues


# 🐐 About AndroGoat

**AndroGoat** is a purposely developed **open-source vulnerable Android application** built with **Kotlin**. It serves as a learning tool for security professionals and developers to understand, exploit, and defend against vulnerabilities in the Android platform. As one of the first vulnerable apps developed natively in Kotlin, AndroGoat is the perfect solution for anyone looking to master modern Android Application Security Testing.

### Key Characteristics:
- **Language:** Kotlin (modern Android development)
- **Purpose:** Educational security testing
- **License:** Open-source
- **Reference:** Listed in OWASP MASTG (Mobile Application Security Testing Guide) as reference app MASTG-APP-0001

### Complete Vulnerability List (33 Vulnerabilities):

#### 1. Root & Environment Detection (3)
| # | Vulnerability |
|---|---------------|
| 1 | Root Detection |
| 2 | Emulator Detection |
| 3 | Android Debbugable |

#### 2. Insecure Data Storage (7)
| # | Vulnerability |
|---|---------------|
| 4 | Insecure Data Storage – Shared Prefs - 1 |
| 5 | Insecure Data Storage - Shared Prefs - 2 |
| 6 | Insecure Data Storage - SQLite |
| 7 | Insecure Data Storage – Temp Files |
| 8 | Insecure Data Storage – SD Card |
| 9 | Keyboard Cache |
| 10 | Insecure Clipboard Usage |

#### 3. Input Validations (5)
| # | Vulnerability |
|---|---------------|
| 11 | Input Validations – XSS |
| 12 | Input Validations – SQLi |
| 13 | Input Validations – WebView |
| 14 | Input Validations - QR Code |
| 15 | Misconfigured Firebase DB |

#### 4. Unprotected Components (5)
| # | Vulnerability |
|---|---------------|
| 16 | Unprotected Activity |
| 17 | Unprotected Service |
| 18 | Unprotected Broadcast Receivers |
| 19 | Unprotected Content Providers |
| 20 | Custom URL Scheme |

#### 5. Network Security (7)
| # | Vulnerability |
|---|---------------|
| 21 | Network Intercepting – HTTP |
| 22 | Network Intercepting – HTTPS |
| 23 | Network Intercepting – Certificate Pinning - OKHTTP3 |
| 24 | Network Intercepting – Certificate Pinning - Network Security Config |
| 25 | Misconfigured Network_Security_Config.xml |
| 26 | Insecure Logging |
| 27 | Hardcoding Issues - Shopping Cart |

#### 6. Cryptographic & Binary Issues (4)
| # | Vulnerability |
|---|---------------|
| 28 | Broken Cryptography |
| 29 | Binary Patching |
| 30 | Biometric Authentication Issues |

#### 7. Hardcoded Credentials (3)
| # | Vulnerability |
|---|---------------|
| 31 | Hardcoding Issues - AI |
| 32 | Hardcoding Issues - Cloud Service |
| 33 | Android allowBackup |

> 📌 **Pro Tip:** Hyperlink each vulnerability above to its corresponding section in the guide where you learn how to test for it!


# 🏗 Android Architecture & Components

Understanding Android architecture is crucial before diving into pentesting. Let's break it down simply.

## 📱 Android OS Architecture (from bottom to top)

```
┌─────────────────────────────────────────────────────────────┐
│                    SYSTEM APPS                               │  ← Phone, Contacts, Browser, etc.
├─────────────────────────────────────────────────────────────┤
│                    JAVA API FRAMEWORK                        │  ← Content Providers, View System, Location, etc.
├─────────────────────────────────────────────────────────────┤
│              NATIVE LIBRARIES (C/C++)  │   ANDROID RUNTIME  │  ← ART/Dalvik VM, OpenGL, SQLite, etc.
├─────────────────────────────────────────────────────────────┤
│                    HARDWARE ABSTRACTION LAYER (HAL)          │  ← Camera, Bluetooth, Sensors, etc.
├─────────────────────────────────────────────────────────────┤
│                    LINUX KERNEL                               │  ← Device drivers, Power management, etc.
└─────────────────────────────────────────────────────────────┘
```

## 🧩 The Four Core Android Components

Every Android app is built using these four components:

### 1. 🖥️ Activity
- **What it does:** Represents a single screen with a user interface
- **Example:** Login screen, Settings screen, Main dashboard
- **Security Concern:** An exported Activity (accessible by other apps) can be launched maliciously to bypass authorization checks

### 2. ⚙️ Service
- **What it does:** Runs in background to perform long-running operations
- **Example:** Music playback, file download, network sync
- **Security Concern:** Background services may leak sensitive data or perform unauthorized operations if not properly secured

### 3. 📡 Broadcast Receiver
- **What it does:** Responds to broadcast messages from system or other apps
- **Example:** Battery low notification, Wi-Fi connection change, SMS received
- **Security Concern:** Malicious apps can craft and send unauthorized broadcasts to trigger unintended behavior

### 4. 🗄 Content Provider
- **What it does:** Manages shared sets of app data for inter-app communication
- **Example:** Contacts provider, Calendar provider
- **Security Concern:** If misconfigured, other apps can read/modify sensitive data stored by your app

> 🔐 **Security Rule:** Any component marked with `android:exported="true"` can be invoked by other apps. Always protect exported components with proper permissions!


# 📁 APK Folder Structure

An APK (Android Package Kit) is essentially a ZIP archive containing all app files. When you decompile an APK using tools like `apktool`, you'll see:

```
AppName.apk (decompiled)
│
├── AndroidManifest.xml          ← ⭐ MOST IMPORTANT: Permissions, Activities, Services all declared here!
│
├── META-INF/                    ← App signature & certificate information
│   ├── MANIFEST.MF
│   ├── CERT.SF
│   └── CERT.RSA
│
├── lib/                         ← Native libraries (C/C++ code)
│   ├── armeabi-v7a/            ← ARM 32-bit library
│   ├── arm64-v8a/               ← ARM 64-bit library
│   ├── x86/                     ← Intel 32-bit library
│   └── x86_64/                  ← Intel 64-bit library
│
├── assets/                      ← Raw asset files (HTML, JS, images, etc.)
│   └── (no R.java index)
│
├── res/                         ← Application resources
│   ├── drawable/               ← Images
│   ├── layout/                 ← XML layout files
│   ├── values/                 ← Strings, colors, dimensions
│   └── xml/                    ← Network Security Config, etc.
│
├── classes.dex                  ← Dalvik bytecode (the actual app code)
├── classes2.dex                 ← Additional dex files (for multi-dex apps)
│
└── (native-libs)
```

### 🔍 What a Pentester Looks For in Each Folder:

| Folder | What to check |
|--------|---------------|
| **AndroidManifest.xml** | Exported components, permissions, debuggable flag, backup allowance |
| **META-INF/** | Verify app signature integrity |
| **lib/** | Hardcoded secrets in native libraries, vulnerable native code |
| **assets/** | Hardcoded API keys, HTML files with XSS issues |
| **res/xml/** | Network Security Configuration for certificate pinning |
| **classes.dex** | The actual Java/Kotlin code — look for hardcoded passwords, weak crypto |
| **shared_prefs/*** (data/) | Stored user preferences, tokens, credentials |
| **databases/*** (data/) | SQLite databases with user data |


# 🔍 Understanding the Attack Surface

An Android app has multiple entry points that attackers can exploit:

```
┌─────────────────────────────────────────────────────────────────────┐
│                         ATTACK SURFACE                               │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  📥 INPUT CHANNELS:                   🧩 IPC COMPONENTS:             │
│  ├── User input (UI fields)           ├── Exported Activities       │
│  ├── QR code scanning                 ├── Exported Services         │
│  ├── Deep links (URL schemes)         ├── Exported Receivers        │
│  ├── In-app links                     ├── Exported Content Providers│
│  └── File uploads                     └── Custom Intents            │
│                                                                      │
│  🌐 NETWORK CHANNELS:                  🗄 STORAGE CHANNELS:           │
│  ├── HTTP/HTTPS API calls             ├── Shared Preferences        │
│  ├── WebView (JavaScript bridge)      ├── SQLite databases          │
│  ├── Firebase connections             ├── Internal storage          │
│  ├── Certificate pinning              ├── External (SD card)        │
│  └── Custom protocols                 └── Temporary files           │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```


# 🧪 Lab Environment Setup

## Hardware & Software Prerequisites

### Minimum Requirements:
- **Laptop/Desktop:** 8GB+ RAM, 20GB free disk space
- **Operating System:** Windows 10+, macOS, or Linux (Kali Linux recommended)
- **Android Device (optional):** Any Android 6.0+ phone for real-device testing

### Required Software:

| Tool | Purpose | Install Command/Link |
|------|---------|---------------------|
| **Java JDK 8 or 11** | Running Android tools | `sudo apt install openjdk-11-jdk` |
| **Android Studio** | Emulator & SDK tools | [developer.android.com/studio](https://developer.android.com/studio) |
| **ADB (Platform Tools)** | Device communication | Included in Android Studio |
| **Burp Suite Community** | Proxy & interception | [portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload) |
| **Python 3** | Running various tools | `sudo apt install python3` |
| **Node.js & npm** | Some JS-based tools | `sudo apt install nodejs npm` |

## Android Emulator Setup

1. **Install Android Studio** from official website
2. **Open AVD Manager** (Android Virtual Device Manager)
3. **Create Virtual Device:**
   - Choose device: Pixel 4 or Pixel 5 (recommended)
   - Choose system image: Android 9.0 (API 28) or higher
   - Recommended ABI: x86_64 (faster on most computers)
4. **Start the emulator** by clicking ▶️ Play button

> 💡 **Pro Tip:** Root the emulator for better testing! Use Android 6.0 (API 23) images which come pre-rooted. For newer Android versions, consider using **Magisk** for root access.

## Installing AndroGoat

### Method 1: Direct APK Installation
```bash
# Download the APK from GitHub releases
wget https://github.com/satishpatnayak/AndroGoat/releases/download/v1.0/AndroGoat.apk

# Install on device/emulator via ADB
adb install AndroGoat.apk
```

### Method 2: Build from Source
```bash
# Clone repository
git clone https://github.com/satishpatnayak/AndroGoat.git
cd AndroGoat

# Open in Android Studio and build APK
# Then install using adb install
```

### Method 3: Using Releases Page
1. Go to: [github.com/satishpatnayak/AndroGoat/releases](https://github.com/satishpatnayak/AndroGoat/releases)
2. Download the `.apk` file
3. Install:
   ```bash
   adb install AndroGoat.apk
   # If re-installing, use:
   adb install -r AndroGoat.apk
   ```

### Verify Installation:
```bash
# Check if app is installed
adb shell pm list packages | grep androgoat

# Launch AndroGoat
adb shell am start -n com.androgoat/.MainActivity

# Check app data directory
adb shell ls -la /data/data/com.androgoat/
```


# 🛠 Essential Tools for Android Pentesting

## 📊 Static Analysis Tools (Code Review without Running)

| Tool | Description | Command |
|------|-------------|---------|
| **apktool** | Decompile APK to readable format | `apktool d app.apk` |
| **jadx** | Convert DEX to Java source code | `jadx -d output app.apk` |
| **dex2jar** | Convert DEX to JAR for Java decompilers | `d2j-dex2jar app.apk` |
| **JD-GUI** | Java decompiler for viewing JAR sources | `jd-gui app-dex2jar.jar` |
| **MobSF** | Automated security framework (web interface) | `docker run -it opensecurity/mobile-security-framework-mobsf` |

## 🏃 Dynamic Analysis Tools (Testing While App Runs)

| Tool | Description | Install |
|------|-------------|---------|
| **adb** | Android Debug Bridge — communicate with device | Comes with Android SDK |
| **Frida** | Dynamic instrumentation toolkit | `pip install frida-tools` |
| **Objection** | Runtime mobile exploration toolkit | `pip install objection` |
| **drozer** | Android security assessment framework | `pip install drozer` |
| **logcat** | View system logs | `adb logcat` |

## 🌐 Network Interception Tools

| Tool | Description |
|------|-------------|
| **Burp Suite** | Most popular web proxy for intercepting traffic |
| **OWASP ZAP** | Open-source alternative to Burp |
| **mitmproxy** | Lightweight CLI proxy |
| **Charles Proxy** | GUI proxy for macOS/Windows |

## ⚡ Automated Analysis Tools

| Tool | Description | Use Case |
|------|-------------|----------|
| **MobSF** | Mobile Security Framework | Automated static + dynamic analysis |
| **Qark** | Quick Android Review Kit | Find security vulnerabilities |
| **AndroBugs** | Android vulnerability scanner | Fast APK analysis |
| **Quark-Engine** | APK analysis framework | Rule-based threat intelligence |


# 📋 Android Penetration Testing Methodology

A step-by-step methodology for testing Android apps:

## Phase 1: Information Gathering

**Goal:** Understand the app's environment and configurations

```bash
# 1. Get app package name
adb shell pm list packages | grep -i <keyword>
adb shell dumpsys package <package-name> | grep "versionName"

# 2. Check if app is debuggable
aapt dump badging app.apk | grep debuggable

# 3. Get app file path
adb shell pm path <package-name>

# 4. Extract APK from device
adb pull $(adb shell pm path <package-name> | cut -d: -f2) extracted.apk

# 5. Check AndroidManifest.xml
apktool d app.apk
cat app/AndroidManifest.xml
```

**What to look for:**
- `android:debuggable="true"` — Easy debugging and memory inspection
- `android:allowBackup="true"` — Can backup app data via ADB
- Custom permissions and exported components
- Network Security Configuration reference

## Phase 2: Static Analysis

**Goal:** Analyze decompiled code without executing

```bash
# 1. Decompile with jadx (best for Java code)
jadx -d jadx_output app.apk

# 2. Decompile with apktool (best for resources)
apktool d app.apk -o apktool_output

# 3. Search for hardcoded secrets
grep -r "password\|secret\|api_key\|token" jadx_output/
grep -r "[A-Za-z0-9]{32,}" jadx_output/  # Look for long strings (possible API keys)

# 4. Analyze AndroidManifest
cat apktool_output/AndroidManifest.xml | grep -E "exported|permission"

# 5. Check for insecure WebView settings
grep -r "setJavaScriptEnabled" jadx_output/
```

**Tools to use:** jadx GUI for visual browsing, VS Code for text search

## Phase 3: Dynamic Analysis

**Goal:** Test app behavior while running

```bash
# 1. Start app with debugging
adb shell am start -D -n <package-name>/<activity-name>

# 2. Attach debugger (using jdb)
jdb -attach localhost:8700

# 3. Monitor logs
adb logcat | grep -i "<package-name>\|error\|exception"

# 4. Dump app memory (if app is debuggable)
adb shell run-as <package-name> cat /data/data/<package-name>/shared_prefs/
adb shell run-as <package-name> ls -la /data/data/<package-name>/

# 5. Test deep links
adb shell am start -W -a android.intent.action.VIEW -d "your-app-scheme://path" <package-name>
```

**With Frida (for root/non-root devices):**
```bash
# 1. Check Frida compatibility
frida-ps -U

# 2. Explore app with objection
objection -g <package-name> explore

# 3. Common objection commands:
# Inside objection shell:
android hooking list classes
android hooking search methods "password"
android sslpinning disable
env
```

## Phase 4: Network Analysis

**Goal:** Intercept and inspect all network traffic

### Setting Up Burp Suite:

1. **Configure Burp Proxy:** Listen on `127.0.0.1:8080`
2. **Export Burp CA Certificate** (DER format)
3. **Install certificate on Android:**
   ```bash
   # Convert to PEM if needed
   openssl x509 -inform DER -in burp.der -out burp.pem

   # Install certificate (Android 7+ requires root or system CA)
   adb push burp.pem /sdcard/
   # Then install via Settings → Security → Install certificate
   ```

4. **Configure Android proxy:**
   - Settings → Wi-Fi → Modify Network → Advanced
   - Proxy: Manual
   - Host: Your computer's IP address
   - Port: 8080

5. **For SSL Pinning bypass:**
   ```bash
   # Using objection
   objection -g <package-name> explore
   objection> android sslpinning disable

   # Using Frida script
   frida -U -l frida-script.js <package-name>
   ```

## Phase 5: Exploitation & Reporting

**Goal:** Exploit vulnerabilities and document findings

### Example Exploitation Template:

| Severity | Vulnerability | Impact | Proof |
|----------|---------------|--------|-------|
| High | Hardcoded API Key Attacker can access backend services | Found in `Constants.java:45` |
| Medium | Exported Content Provider Data leak to other apps | `AndroidManifest.xml` |
| Low | Debuggable true | Allows memory inspection |

### Reporting Structure:
1. **Executive Summary** — Overview of findings
2. **Methodology** — Tools and techniques used
3. **Detailed Findings** — Each vulnerability with:
   - Description
   - Affected component/file
   - Proof of Concept (screenshots/code snippets)
   - CVSS Score
4. **Remediation Recommendations**
5. **Appendix** — Test logs, commands used


# 📋 OWASP Mobile Top 10 2024 — Complete Breakdown

The **OWASP Mobile Top 10** is the industry standard list of the most critical mobile application security risks. The 2024 update represents a significant evolution from the 2016 version, reflecting modern threat landscapes.

## 📊 Quick Reference Table

| Rank | ID | Risk Category | 2016 Equivalent | Change Type |
|------|----|---------------|-----------------|-------------|
| 1 | M1 | Improper Credential Usage | – | **New** |
| 2 | M2 | Inadequate Supply Chain Security | – | **New** |
| 3 | M3 | Insecure Authentication/Authorization | M4 + M6 | **Merged & Expanded** |
| 4 | M4 | Insufficient Input/Output Validation | – | **New** |
| 5 | M5 | Insecure Communication | M3 | **Persisted** |
| 6 | M6 | Inadequate Privacy Controls | – | **New** |
| 7 | M7 | Insufficient Binary Protections | M7 + M8 + M9 | **Consolidated** |
| 8 | M8 | Security Misconfiguration | – | **New** |
| 9 | M9 | Insecure Data Storage | M2 | **Persisted** |
| 10 | M10 | Insufficient Cryptography | M5 | **Persisted** |

Source: OWASP Mobile Top 10 2024 Final Release

---

## M1: Improper Credential Usage 🔊

### What is it?
The mishandling or misuse of user credentials (passwords, tokens, API keys) that allows attackers to compromise authentication.

### Common Scenarios:
- 🔴 Hardcoding API keys or passwords in source code
- 🔴 Storing user credentials in plaintext
- 🔴 Using weak password policies (no complexity requirements)
- 🔴 Not implementing account lockout after failed attempts

### How to test for M1 in AndroGoat:
```bash
# Look for hardcoded credentials in decompiled code
grep -r "password\|api_key\|secret\|token" jadx_output/

# Check SharedPreferences for stored credentials
adb shell run-as com.androgoat cat /data/data/com.androgoat/shared_prefs/*.xml

# Check SQLite databases
adb shell run-as com.androgoat ls /data/data/com.androgoat/databases/
adb shell run-as com.androgoat sqlite3 /data/data/com.androgoat/databases/*.db ".dump"
```

### Real-world Example in AndroGoat:
Check the **"Hardcoding issues - Shopping Cart"**, **"Hardcoding issues - AI"**, and **"Hardcoding issues - Cloud Service"** vulnerabilities.

### Remediation:
- ✅ Use Android Keystore System or EncryptedSharedPreferences
- ✅ Never hardcode credentials — use environment variables or secure config servers
- ✅ Implement OAuth 2.0 or similar modern authentication
- ✅ Store credentials in server-side sessions only

---

## M2: Inadequate Supply Chain Security 🔊

### What is it?
Risks introduced from third-party libraries, SDKs, dependencies, and development tools used in app development.

### Common Scenarios:
- 🔴 Using outdated libraries with known vulnerabilities
- 🔴 Including unnecessary third-party SDKs
- 🔴 Not verifying the integrity of downloaded dependencies
- 🔴 Using unofficial or modified versions of libraries

### How to test for M2 in AndroGoat:
```bash
# Check for known vulnerable libraries
# Look at build.gradle dependencies first, then:

# Extract dependency list from decompiled code
grep -r "import" jadx_output/ | cut -d' ' -f2 | sort -u

# Check for Firebase misconfiguration
grep -r "firebase\|google-services" jadx_output/
```

### Real-world Example in AndroGoat:
Check the **"Misconfigured Firebase DB"** vulnerability — this demonstrates how a misconfigured third-party backend can expose all user data.

### Remediation:
- ✅ Regularly update dependencies using tools like Dependabot or Snyk
- ✅ Use software composition analysis (SCA) tools
- ✅ Vet third-party SDKs for security and privacy practices
- ✅ Implement dependency verification (checksum verification)

---

## M3: Insecure Authentication/Authorization 🔊

### What is it?
Weaknesses in how the app verifies user identity (authentication) and controls access to resources (authorization).

### Common Scenarios:
- 🔴 No authentication for sensitive functionality
- 🔴 Locally stored authentication decisions (app checks "isLoggedIn" flag)
- 🔴 Weak session management (tokens don't expire)
- 🔴 Insecure biometric implementation (no fallback protection)
- 🔴 Lack of multi-factor authentication (MFA)

### How to test for M3 in AndroGoat:
```bash
# Look for local authentication bypass
grep -r "isLoggedIn\|isAuthenticated\|shared_prefs" jadx_output/

# Check biometric implementation
grep -r "BiometricPrompt\|FingerprintManager" jadx_output/

# Test exported activities that bypass login
adb shell am start -n com.androgoat/.PrivateActivity

# Test custom URL schemes that may bypass auth
adb shell am start -W -a android.intent.action.VIEW -d "androgoat://private-data"
```

### Real-world Example in AndroGoat:
Check **"Unprotected Android Components – Activity"**, **"Biometric Authentication"**, and **"Custom URL Scheme"** vulnerabilities.

### Remediation:
- ✅ Never rely on client-side authentication checks
- ✅ Use server-side session management with short-lived tokens
- ✅ Implement proper biometric authentication with secure fallbacks
- ✅ Enforce MFA for sensitive operations
- ✅ Validate authorization on every request, not just the first

---

## M4: Insufficient Input/Output Validation 🔊

### What is it?
Failure to properly validate, sanitize, or encode data entering or leaving the application, leading to various injection attacks.

### Common Scenarios:
- 🔴 SQL Injection in local databases or through API
- 🔴 Cross-Site Scripting (XSS) in WebViews
- 🔴 Command injection through user input
- 🔴 Path traversal attacks
- 🔴 XML External Entity (XXE) attacks

### How to test for M4 in AndroGoat:
```bash
# Test SQL Injection in app
# Input: ' OR '1'='1
# Input: '; DROP TABLE users; --

# Test XSS in WebView
# Input: <script>alert('XSS')</script>
# Input: <img src=x onerror=alert(1)>

# Check WebView configuration
grep -r "setJavaScriptEnabled\|addJavascriptInterface\|loadUrl" jadx_output/
```

### Real-world Example in AndroGoat:
Check **"Input Validations – XSS"**, **"Input Validations – SQLi"**, **"Input Validations – WebView"**, and **"Input Validations - QR Code"** vulnerabilities.

### Remediation:
- ✅ Use parameterized queries/prepared statements for all database operations
- ✅ Sanitize all user input before displaying in WebViews
- ✅ Implement allowlists for input validation (never blocklists)
- ✅ Disable JavaScript in WebViews unless absolutely necessary
- ✅ Use Content Security Policy (CSP) for WebViews

---

## M5: Insecure Communication 🔊

### What is it?
Failure to properly secure network communication between the mobile app and backend services.

### Common Scenarios:
- 🔴 Using HTTP instead of HTTPS
- 🔴 Not validating SSL/TLS certificates
- 🔴 Weak TLS configurations (TLS 1.0, weak cipher suites)
- 🔴 Not implementing certificate pinning
- 🔴 Sending sensitive data in URL parameters or clear text headers

### How to test for M5 in AndroGoat:
```bash
# Set up Burp Suite as proxy
# First test HTTP traffic (should be visible)
# Then test HTTPS (should be encrypted but visible in Burp if no pinning)

# Test certificate pinning
# Use objection to bypass pinning:
objection -g com.androgoat explore
android sslpinning disable

# Or use Frida:
frida -U -l universal-android-ssl-pinning-bypass.js com.androgoat

# Check Network Security Config
cat apktool_output/res/xml/network_security_config.xml
```

### Real-world Example in AndroGoat:
Check **"Network intercepting – HTTP"**, **"Network intercepting – HTTPS"**, **"Network intercepting – Certificate Pinning - OKHTTP3"**, **"Network intercepting – Certificate Pinning - Network Security Config"**, and **"Misconfigured Network_Security_Config.xml"** vulnerabilities.

### Remediation:
- ✅ Always use HTTPS in production (never HTTP)
- ✅ Implement certificate pinning for critical apps
- ✅ Use Android Network Security Configuration
- ✅ Validate server certificates properly
- ✅ Never disable SSL/TLS validation in production
- ✅ Use modern TLS 1.2/1.3

---

## M6: Inadequate Privacy Controls 🔊

### What is it?
Lack of appropriate controls for handling user data in compliance with privacy regulations (GDPR, CCPA, etc.).

### Common Scenarios:
- 🔴 Collecting more data than necessary (data minimization violation)
- 🔴 No privacy policy or misleading policy
- 🔴 Not obtaining explicit user consent for data collection
- 🔴 Sharing data with third parties without disclosure
- 🔴 No data deletion mechanism (right to be forgotten)

### How to test for M6 in AndroGoat:
```bash
# Check what data is being collected
grep -r "location\|contacts\|camera\|microphone\|SMS\|READ_" AndroidManifest.xml

# Monitor network traffic for data exfiltration
# Look for data being sent to third-party domains

# Check SharedPreferences for consent tracking
adb shell run-as com.androgoat cat /data/data/com.androgoat/shared_prefs/*.xml | grep -i "consent\|allowed\|opted"
```

### Remediation:
- ✅ Implement clear privacy policy within the app
- ✅ Request permissions only when needed with clear explanation
- ✅ Allow users to delete their data
- ✅ Anonymize data where possible
- ✅ Document all third-party data sharing

---

## M7: Insufficient Binary Protections 🔊

### What is it?
Lack of protections that prevent reverse engineering, tampering, and code modification.

### Common Scenarios:
- 🔴 No code obfuscation (easy to reverse engineer)
- 🔴 No root/jailbreak detection
- 🔴 No anti-tampering mechanisms
- 🔴 Debuggable app in production
- 🔴 No integrity checking for APK

### How to test for M7 in AndroGoat:
```bash
# Check if app is debuggable
aapt dump badging AndroGoat.apk | grep debuggable

# Try root detection bypass
# Use Magisk Hide or similar to hide root, see if app detects

# Try to modify and repackage the app
apktool d AndroGoat.apk
# Make small changes (e.g., change a string)
apktool b AndroGoat -o modified.apk
# Try to install modified version
# If app has integrity checks, it will fail

# Test emulator detection
# Run app on emulator vs real device — differences?
```

### Real-world Example in AndroGoat:
Check **"Root Detection"**, **"Emulator Detection"**, **"Android Debbugable"**, and **"Binary Patching"** vulnerabilities.

### Remediation:
- ✅ Use ProGuard/R8 for code obfuscation
- ✅ Implement root/jailbreak detection with proper response
- ✅ Set `android:debuggable="false"` in production
- ✅ Implement integrity checks (though can be bypassed)
- ✅ Consider commercial hardening solutions for high-risk apps

---

## M8: Security Misconfiguration 🔊

### What is it?
Improperly configured security settings in the app, platform, or infrastructure.

### Common Scenarios:
- 🔴 `android:allowBackup="true"` allowing ADB backups
- 🔴 Exported components without proper permission protection
- 🔴 Misconfigured Firebase/GCP/AWS permissions
- 🔴 Debugging features left enabled
- 🔴 Weak password policies
- 🔴 Information leakage in error messages

### How to test for M8 in AndroGoat:
```bash
# Check AndroidManifest.xml for misconfigurations
grep -E "allowBackup|debuggable|exported" AndroidManifest.xml

# Test allowBackup backup
adb backup -f backup.ab com.androgoat
# Extract and analyze backup

# Check Firebase configuration
grep -r "firebase" jadx_output/
# Try to access Firebase URL from browser

# Check for exposed Cloud services
grep -r "cloud\|s3\|bucket\|storage" jadx_output/
```

### Real-world Example in AndroGoat:
Check **"Android allowBackup"**, **"Unprotected Android Components"** (all four types), and **"Misconfigured Firebase DB"** vulnerabilities.

### Remediation:
- ✅ Set `android:allowBackup="false"` for sensitive apps
- ✅ Validate Firebase/Cloud security rules
- ✅ Never export components without necessary permissions
- ✅ Remove all debugging code before release
- ✅ Implement proper error handling (no sensitive data in errors)

---

## M9: Insecure Data Storage 🔊

### What is it?
Storing sensitive data on the device in an unencrypted or insecure manner, exposing it to other apps or attackers.

### Common Scenarios:
- 🔴 Storing passwords/tokens in SharedPreferences in plaintext
- 🔴 Unencrypted SQLite databases
- 🔴 Writing sensitive data to log files
- 🔴 Storing data on external storage (SD card) accessible by other apps
- 🔴 Keyboard caching capturing sensitive input
- 🔴 Clipboard logging

### How to test for M9 in AndroGoat:
```bash
# Check SharedPreferences
adb shell run-as com.androgoat cat /data/data/com.androgoat/shared_prefs/*.xml

# Check SQLite databases
adb shell run-as com.androgoat ls /data/data/com.androgoat/databases/
adb shell run-as com.androgoat sqlite3 /data/data/com.androgoat/databases/*.db ".dump"

# Check files directory
adb shell run-as com.androgoat ls -la /data/data/com.androgoat/files/

# Monitor logs for sensitive information
adb logcat | grep -i "password\|username\|token\|credit\|card\|ssn"

# Check external storage
adb shell ls -la /sdcard/Android/data/com.androgoat/

# Check clipboard
# Try copying sensitive text, check if it remains in clipboard history
```

### Real-world Example in AndroGoat:
Check **"Insecure Data Storage"** vulnerabilities: Shared Prefs (x2), SQLite, Temp Files, SD Card; plus **"Keyboard Cache"**, **"Insecure Logging"**, and **"Insecure Clipboard Usage"**.

### Remediation:
- ✅ Use EncryptedSharedPreferences for sensitive preferences
- ✅ Use SQLCipher for encrypted databases
- ✅ Never log sensitive information (even in debug builds)
- ✅ Use internal storage only for sensitive data
- ✅ Disable keyboard caching for sensitive fields (`android:importantForAutofill="no"`)
- ✅ Clear clipboard after paste when appropriate

---

## M10: Insufficient Cryptography 🔊

### What is it?
Using weak or broken cryptographic algorithms, or implementing cryptography incorrectly.

### Common Scenarios:
- 🔴 Using weak hashing algorithms (MD5, SHA1)
- 🔴 Using broken encryption (DES, RC4)
- 🔴 Hardcoded encryption keys
- 🔴 Using ECB mode for encryption (reveals patterns)
- 🔴 Rolling your own crypto instead of using standard libraries
- 🔴 Not using salting for password hashing

### How to test for M10 in AndroGoat:
```bash
# Look for crypto-related code
grep -r "Cipher\|SecretKey\|KeyGenerator\|MessageDigest" jadx_output/
grep -r "MD5\|SHA1\|DES\|ECB\|RSA\|AES" jadx_output/

# Check for hardcoded keys
grep -r "SecretKeySpec\|IvParameterSpec\|getBytes" jadx_output/

# Look for weak password hashing
grep -r "md5\|sha-1\|MessageDigest" jadx_output/
```

### Real-world Example in AndroGoat:
Check **"Broken Cryptography"** vulnerability.

### Remediation:
- ✅ Use strong, modern algorithms (AES-256-GCM, SHA-256/512, bcrypt, PBKDF2)
- ✅ Never hardcode encryption keys
- ✅ Use secure random number generators (SecureRandom)
- ✅ Use Android Keystore System for key storage
- ✅ Always use authenticated encryption (GCM)
- ✅ Use appropriate password hashing (bcrypt, Argon2)\


# 🔗 OWASP Mobile Top 10 2024 × AndroGoat Vulnerability Mapping

Here's how AndroGoat's 33 vulnerabilities map to the OWASP Mobile Top 10 2024:

| OWASP Risk | Severity | AndroGoat Vulnerabilities |
|------------|----------|---------------------------|
| **M1: Improper Credential Usage** | 🔴 High | • Hardcoding issues - AI<br>• Hardcoding issues - Cloud Service<br>• Hardcoding issues - Shopping Cart |
| **M2: Inadequate Supply Chain Security** | 🟠 Medium-High | • Misconfigured Firebase DB |
| **M3: Insecure Authentication/Authorization** | 🔴 High | • Biometric Authentication<br>• Unprotected Activity<br>• Unprotected Service<br>• Unprotected Broadcast Receivers<br>• Unprotected Content Providers<br>• Custom URL Scheme |
| **M4: Insufficient Input/Output Validation** | 🔴 High | • Input Validations – XSS<br>• Input Validations – SQLi<br>• Input Validations – WebView<br>• Input Validations - QR Code |
| **M5: Insecure Communication** | 🟠 Medium-High | • Network intercepting – HTTP<br>• Network intercepting – HTTPS<br>• Certificate Pinning - OKHTTP3<br>• Certificate Pinning - Network Security Config<br>• Misconfigured Network_Security_Config.xml |
| **M6: Inadequate Privacy Controls** | 🟡 Medium | • Keyboard Cache<br>• Insecure Clipboard Usage |
| **M7: Insufficient Binary Protections** | 🟡 Medium | • Root Detection<br>• Emulator Detection<br>• Android Debbugable<br>• Binary Patching |
| **M8: Security Misconfiguration** | 🟡 Medium | • Android allowBackup<br>• Misconfigured Firebase DB<br>• Unprotected Components (all) |
| **M9: Insecure Data Storage** | 🔴 High | • Insecure Data Storage – Shared Prefs 1 & 2<br>• Insecure Data Storage – SQLite<br>• Insecure Data Storage – Temp Files<br>• Insecure Data Storage – SD Card<br>• Insecure Logging<br>• Keyboard Cache<br>• Insecure Clipboard Usage |
| **M10: Insufficient Cryptography** | 🔴 High | • Broken Cryptography |

## 📝 Step-by-Step Practice Exercises by OWASP Category:

### 🔴 M1 Practice: Hardcoded Credentials

**Task:** Find all hardcoded credentials in AndroGoat.

```bash
# Step 1: Decompile the APK
jadx -d output/ AndroGoat.apk

# Step 2: Search for credentials
grep -r "password\|api_key\|secret\|token\|KEY\|SECRET" output/

# Step 3: Look in specific classes
cat output/sources/com/androgoat/*.java | grep -i "key\|secret"

# Step 4: Check constants files
find output/ -name "*Constants*" -exec cat {} \;
```

**Learning Objective:** Understand why hardcoding secrets in client-side code is dangerous.

---

### 🔴 M3/M4 Practice: Exploiting Unprotected Components

**Task:** Bypass authentication by directly launching a private Activity.

```bash
# Step 1: Check AndroidManifest for exported activities
cat output/AndroidManifest.xml | grep -E "activity.*exported"

# Step 2: Look for activities that might be sensitive
# e.g., PrivateActivity, AdminActivity, SettingsActivity

# Step 3: Launch directly via ADB
adb shell am start -n com.androgoat/.PrivateActivity

# Step 4: Try to launch with custom intents
adb shell am start -n com.androgoat/.AdminActivity --es "key" "value"
```

**Learning Objective:** Learn how exported components create attack vectors and bypass authentication.

---

### 🔴 M4 Practice: SQL Injection

**Task:** Perform SQL injection on AndroGoat's SQLite database.

```bash
# Step 1: Find SQL-related code
grep -r "execSQL\|rawQuery\|compileStatement" output/

# Step 2: Look for search/login features that query database

# Step 3: Test input in the vulnerable part of the app:
# Try input: ' OR '1'='1
# Input: '; DROP TABLE users; --

# Step 4: Check database if injection worked
adb shell run-as com.androgoat sqlite3 /data/data/com.androgoat/databases/*.db "SELECT * FROM users;"
```

**Learning Objective:** Understand that injection vulnerabilities exist not just in web apps but in mobile apps too.

---

### 🟠 M5 Practice: Bypassing SSL Pinning

**Task:** Intercept HTTPS traffic and bypass certificate pinning.

```bash
# Step 1: Run AndroGoat normally, configure Burp proxy → Network calls should fail

# Step 2: Install objection
pip install objection

# Step 3: Run objection with AndroGoat
objection -g com.androgoat explore

# Step 4: Disable SSL pinning from objection shell
android sslpinning disable

# Step 5: Now network calls should work through Burp
# Intercept and analyze/modify traffic
```

**Learning Objective:** Learn why certificate pinning is important and how attackers bypass it.

---

### 🔴 M9 Practice: Extract Data from Storage

**Task:** Extract sensitive data from app's local storage.

```bash
# Step 1: Explore app directory structure
adb shell run-as com.androgoat ls -la /data/data/com.androgoat/

# Step 2: Check SharedPreferences
adb shell run-as com.androgoat cat /data/data/com.androgoat/shared_prefs/*.xml

# Step 3: Check databases
adb shell run-as com.androgoat ls /data/data/com.androgoat/databases/
# If database exists, dump contents:
adb shell run-as com.androgoat sqlite3 /data/data/com.androgoat/databases/*.db ".dump"

# Step 4: Check files directory for temp files
adb shell run-as com.androgoat ls -la /data/data/com.androgoat/files/

# Step 5: When app logs, check logcat
adb logcat | grep -i "androgoat\|password\|token"
```

**Learning Objective:** Understand how insecure data storage exposes user data to other apps and attackers with device access.

---

### 🔴 M10 Practice: Weak Cryptography

**Task:** Identify and break weak cryptographic implementations.

```bash
# Step 1: Find crypto implementation
grep -r "Cipher\|SecretKeySpec\|IvParameterSpec" output/

# Step 2: Identify the algorithm used
# Look for constants like "AES/CBC/PKCS5Padding", "DES", "MD5", "SHA1"

# Step 3: Check for hardcoded keys
grep -r "SecretKeySpec\|KEY\|IV" output/

# Step 4: Try to reverse if key is present in code
# If AES key is hardcoded, you can decrypt stored data easily
```

**Learning Objective:** Learn why proper cryptography with secure key management is essential.


# 📐 OWASP MASVS & MASTG — Standards and Testing Guide

The OWASP MAS (Mobile Application Security) project provides two critical resources for mobile app security:

## MASVS (Mobile Application Security Verification Standard)

The **MASVS** defines security requirements for mobile apps across different verification levels.

### MASVS Verification Levels:

| Level | Name | Description | Use Case |
|-------|------|-------------|----------|
| **L1** | Standard Security | Basic protection against common risks | General-purpose apps |
| **L2** | Defense-in-Depth | Increased resistance against sophisticated attacks | Banking, healthcare, payments |
| **R** | Resilience | Anti-reverse engineering protections | High-risk apps with sensitive IP |
| **P** | Privacy | GDPR/CCPA compliance verification | Apps handling personal data |

### MASVS Control Categories:

| Category | Focus |
|----------|-------|
| **MASVS-STORAGE** | Secure local data storage |
| **MASVS-CRYPTO** | Cryptographic best practices |
| **MASVS-AUTH** | Authentication & session management |
| **MASVS-NETWORK** | Secure network communication |
| **MASVS-PLATFORM** | Platform interaction security |
| **MASVS-CODE** | Code quality & resilience |
| **MASVS-PRIVACY** | Privacy controls |

## MASTG (Mobile Application Security Testing Guide)

The **MASTG** provides detailed test cases and procedures for verifying MASVS requirements. AndroGoat is listed as a reference app (MASTG-APP-0001) in the official MASTG documentation.

### Where to Find:
- **MASVS:** https://mas.owasp.org/MASVS
- **MASTG:** https://mas.owasp.org/MASTG
- **Interactive Playground:** https://mas.owasp.org


# 💻 Complete Toolbox Cheatsheet

## 🔧 ADB (Android Debug Bridge) Commands

### Device Management:
```bash
# List connected devices
adb devices

# Connect to device via TCP/IP
adb connect <device-ip>:5555

# Root the device (if supported)
adb root

# Start a shell on device
adb shell

# Get device info
adb shell getprop ro.product.model
adb shell getprop ro.build.version.release
```

### App Management:
```bash
# Install APK
adb install app.apk

# Re-install (overwrite)
adb install -r app.apk

# Uninstall app
adb uninstall <package-name>

# List all packages
adb shell pm list packages

# List only third-party apps
adb shell pm list packages -3

# Get APK path for a package
adb shell pm path <package-name>

# Extract APK from device
adb pull $(adb shell pm path <package-name> | cut -d: -f2) app.apk

# Clear app data
adb shell pm clear <package-name>

# Force stop app
adb shell am force-stop <package-name>

# Launch app by package name
adb shell monkey -p <package-name> 1

# Launch specific activity
adb shell am start -n <package-name>/<activity-name>
```

### Debugging:
```bash
# View logs with filtering
adb logcat

# Clear logs
adb logcat -c

# Filter by package
adb logcat | grep <package-name>

# Filter by severity (E=error, W=warning, I=info, D=debug)
adb logcat *:E

# Dumpsys commands
adb shell dumpsys package <package-name>   # Package info
adb shell dumpsys battery                  # Battery status
adb shell dumpsys activity activities      # Current activities
adb shell dumpsys meminfo <package-name>   # Memory usage

# Pull file from device
adb pull /remote/path /local/path

# Push file to device
adb push /local/file /remote/path

# Take screenshot
adb shell screencap /sdcard/screenshot.png
adb pull /sdcard/screenshot.png

# Record screen
adb shell screenrecord /sdcard/record.mp4
```

## 📦 APK Analysis Commands

### Using aapt (Android Asset Packaging Tool):
```bash
# Get app basic info
aapt dump badging app.apk

# Get permissions
aapt dump permissions app.apk

# Get XML tree
aapt dump xmltree app.apk AndroidManifest.xml

# Get resources
aapt dump resources app.apk
```

### Using apktool:
```bash
# Decompile APK
apktool d app.apk

# Decompile to specific directory
apktool d app.apk -o output/

# Rebuild APK
apktool b output/ -o modified.apk

# Decompile without decoding resources
apktool d -r app.apk
```

### Using jadx:
```bash
# Decompile to Java source
jadx -d output/ app.apk

# Show progress (GUI mode)
jadx-gui app.apk

# Skip resources
jadx --no-res -d output/ app.apk

# Decompile only specific packages
jadx --include-package com.example app.apk
```

### Using dex2jar:
```bash
# Convert dex to jar
d2j-dex2jar app.apk

# Convert with specific output name
d2j-dex2jar app.apk -o output.jar

# Convert multiple dex files
d2j-dex2jar classes.dex classes2.dex
```

### Using keytool (for signing info):
```bash
# Get certificate information
keytool -printcert -jarfile app.apk

# Get detailed certificate info
keytool -printcert -jarfile app.apk -rfc
```

## 🔓 Frida & Objection Commands

### Frida Setup:
```bash
# Install frida-tools
pip install frida-tools

# Install specific version (match with device)
pip install frida==16.0.0 frida-tools==12.0.0

# Check frida version
frida --version

# List running processes on device
frida-ps -U

# List installed apps on device
frida-ps -Uai

# Kill frida-server on device
adb shell killall frida-server
```

### Objection Setup:
```bash
# Install objection
pip install objection

# Explore app dynamically
objection -g <package-name> explore

# Explore with specific device
objection -d -g <package-name> explore

# Patch APK with frida-gadget
objection patchapk -s app.apk
```

### Objection Commands (Inside explore shell):
```bash
# Environment commands:
env                      # Show runtime environment
ls                       # List directory contents

# Memory exploration:
memory list modules      # List loaded modules
memory list exports      # List exports
memory search "password" # Search memory for string

# Android specific:
android hooking list classes               # List all classes
android hooking list activities            # List activities
android hooking search methods "password"  # Search for methods
android hooking watch class <class>        # Hook entire class
android hooking watch method <method>      # Hook specific method

# SSL Bypass:
android sslpinning disable                 # Disable SSL pinning
android sslpinning list                    # List pinning implementations

# Root detection bypass:
android root disable                       # Bypass root detection

# UI interactions:
android ui touch <x> <y>                   # Simulate touch
android ui screenshot                      # Take screenshot
android ui text "input"                    # Input text

# Device info:
android device info                        # Get device information
android clipboard monitor                  # Monitor clipboard changes
```

### Frida JavaScript Examples:

**Basic hook to bypass SSL Pinning:**
```javascript
Java.perform(function() {
    var X509TrustManager = Java.use('javax.net.ssl.X509TrustManager');
    X509TrustManager.checkServerTrusted.implementation = function(chain, authType) {
        console.log('SSL Pinning Bypassed!');
    };
});
```

**Hook to intercept password field:**
```javascript
Java.perform(function() {
    var EditText = Java.use('android.widget.EditText');
    EditText.getText.implementation = function() {
        var text = this.getText();
        console.log('Password entered: ' + text);
        return text;
    };
});
```


# 🗺 Study Roadmap for Students

## 🟢 Beginner (Weeks 1-2)
- [ ] Understand Android architecture basics
- [ ] Set up Android emulator
- [ ] Install AndroGoat
- [ ] Learn basic ADB commands
- [ ] Extract/decompile APK with apktool
- [ ] Understand APK folder structure
- [ ] Read AndroidManifest.xml and understand permissions

## 🟡 Intermediate (Weeks 3-5)
- [ ] Set up Burp Suite proxy
- [ ] Intercept HTTP/HTTPS traffic from AndroGoat
- [ ] Learn to use jadx for Java source analysis
- [ ] Identify all 4 types of Insecure Data Storage
- [ ] Exploit unprotected components
- [ ] Find hardcoded credentials
- [ ] Perform SQL injection test
- [ ] Understand SSL pinning and bypass with objection

## 🔴 Advanced (Weeks 6-8)
- [ ] Set up Frida and objection
- [ ] Write custom Frida hooks
- [ ] Bypass root detection
- [ ] Bypass emulator detection
- [ ] Modify and repackage APK
- [ ] Perform dynamic binary patching
- [ ] Write penetration testing report

## 🚀 Expert (Weeks 9-12)
- [ ] Complete all 33 vulnerabilities in AndroGoat
- [ ] Write detailed PoC for each vulnerability
- [ ] Practice with additional vulnerable apps (see resources below)
- [ ] Learn Android NDK and native code security
- [ ] Contribute to AndroGoat repo
- [ ] Take eMAPT (Mobile Application Penetration Tester) certification


# 📚 Additional Resources

## Official Documentation:
- **OWASP MASVS:** https://mas.owasp.org/MASVS/
- **OWASP MASTG:** https://mas.owasp.org/MASTG/
- **OWASP Mobile Top 10 2024:** https://owasp.org/www-project-mobile-top-10/
- **Android Developer Security:** https://developer.android.com/topic/security

## Vulnerable Apps to Practice:
| App Name | Language | Difficulty |
|----------|----------|------------|
| **AndroGoat** | Kotlin | Beginner |
| **InsecureBankv2** | Java | Beginner |
| **Damn Vulnerable Android App (DVAA)** | Java | Intermediate |
| **OWASP MSTG Hacking Playground** | Java/Kotlin | Advanced |
| **Android Security Test Suite** | Java | Intermediate |

## Tools Download Links:
- **Android Studio:** https://developer.android.com/studio
- **Burp Suite Community:** https://portswigger.net/burp/communitydownload
- **jadx:** https://github.com/skylot/jadx
- **apktool:** https://github.com/iBotPeaches/Apktool
- **Objection:** https://github.com/sensepost/objection
- **Frida:** https://frida.re/
- **MobSF:** https://github.com/MobSF/Mobile-Security-Framework-MobSF

## YouTube Channels:
- Android Security (Google)
- OWASP Foundation
- The Android Security Podcast
- Mobile Hacking Lab

## Books:
- *Android Security Internals* by Nikolay Elenkov
- *Mobile Application Security Testing Guide (MASTG)* — Free at mas.owasp.org
- *The Mobile Application Hacker's Handbook* by Dominic Chell


# ✅ Conclusion

Congratulations! You now have a **comprehensive guide** to start your journey in Android penetration testing. Remember:

1. **Practice is key** — Theory alone won't make you a good pentester. Use AndroGoat to practice all vulnerabilities.

2. **Follow the methodology** — Don't jump directly to exploitation. Information gathering and analysis save time.

3. **Understand the defenses** — To break something, you need to understand how it works. Also learn how to fix vulnerabilities.

4. **Stay ethical** — Only test applications you own or have explicit permission to test. Use this knowledge to protect, not exploit.

5. **Keep learning** — Mobile security evolves rapidly. Follow OWASP and Android Security updates.

## ⭐ Credits
- **AndroGoat Creator:** Satish Patnayak
- **OWASP Foundation** for the Mobile Top 10 and MASTG/MASTG standards
- **The Entire Android Security Community**

---

**Happy Hacking!** 🐐🔒

> *"The best way to learn security is to break things — your own things, in a controlled environment."*

---

## 🔗 Quick Links:
- [AndroGoat on GitHub](https://github.com/satishpatnayak/AndroGoat)
- [AndroGoat Documentation on Medium](https://medium.com/androgoat)
- [OWASP MASTG Reference for AndroGoat](https://mas.owasp.org/MASTG/apps/android/MASTG-APP-0001/)
