# 🔴 Reflected Cross-Site Scripting (XSS)

<p align="center">
  <img src="https://img.shields.io/badge/Vulnerability-Reflected%20XSS-red?style=for-the-badge">
  <img src="https://img.shields.io/badge/Severity-Medium-orange?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Pending%20Validation-orange?style=for-the-badge">
</p>

---

## 🐞 Vulnerability Overview

> [!WARNING]
> A potential **Reflected Cross-Site Scripting (XSS)** vulnerability was
> observed during testing of `https://www.sierrawireless.com`.

The search functionality on the affected page reflects **user-controlled input**
into the application's response without adequate output encoding.

During testing, a crafted XSS payload supplied through the search functionality
resulted in JavaScript execution within the context of the affected origin.

**Affected page:**

`https://www.sierrawireless.com/resources/ebook/`

---

## 🎯 Affected Functionality

| Field | Details |
|---|---|
| **Target** | `www.sierrawireless.com` |
| **Affected Page** | `/resources/ebook/` |
| **Vulnerability** | Reflected Cross-Site Scripting (XSS) |
| **Attack Vector** | Search functionality |
| **Browser Tested** | Google Chrome |
| **Platform** | HackerOne |
| **Report State** | Preliminary Review Passed |
| **Validation** | Pending Program Reproduction |
| **Status** | 🟠 Pending Validation |

---

## 📋 Report Status

> [!NOTE]
> The HackerOne report has passed **preliminary review**.
>
> This does **not** confirm that the vulnerability has been validated.
> The report is currently pending reproduction and further assessment by the
> program team.

---

## 💥 Proof of Concept

### Payload

```html
<img src=x onerror=alert(1)>
```

### 🔬 Observed Behavior

The supplied input was reflected in the application's response, and the
JavaScript payload executed successfully in the testing environment.

An `alert(1)` dialog was observed during testing.

> [!IMPORTANT]
> Successful JavaScript execution was observed during testing, but the issue
> has not yet been confirmed by the HackerOne program.
> 
> Final validation and reproduction by the program team are still pending.

### 🧪 Steps To Reproduce

#### 01 — Navigate to the affected page
Open:
  ```https://www.sierrawireless.com/resources/ebook/```
  
#### 02 — Locate the search functionality
Locate the search box on the page.

#### 03 — Enter the payload
Enter the following payload into the search field:
  ```<img src=x onerror=alert(1)>```

#### 04 — Submit the search
Submit the search request.

#### 05 — Observe the behavior
Observe that the supplied input is reflected in the response and the
JavaScript payload executes.
  An `alert(1)` dialog is displayed.

#### 06 — Verification
The behavior was reproduced during testing using Google Chrome and observed
through the browser's Developer Tools.

### 🎥 Video PoC
A screen recording demonstrating the observed behavior is included with this
PoC.

Evidence: `XSS/Reflected/Task-01-www.semtech.com/eBook - Semtech (formerly Sierra Wireless) - Google Chrome 2026-09-03 19-02-00.mp4`

> [!NOTE]
> The video is a screen recording without audio and is provided solely as
> visual evidence of the observed behavior.

### 💥 Impact

If confirmed as a reflected XSS vulnerability, an attacker could potentially
craft malicious input or a URL containing JavaScript and attempt to persuade a
victim to interact with the affected functionality.

Successful exploitation could allow attacker-controlled JavaScript to execute
within the security context of the affected origin.

Depending on the application's functionality, victim privileges, and applicable
security controls, potential consequences may include:

* Manipulation of page content
* Performing actions available to the victim
* Accessing information exposed to scripts running within the affected origin
* Executing attacker-controlled JavaScript in the victim's browser

### 🛡️ Recommended Remediation

The application should properly handle user-controlled input before reflecting
it into HTML responses.

Recommended measures include:

* Apply context-appropriate output encoding.
* Avoid inserting untrusted input directly into HTML.
* Properly sanitize user-controlled HTML where HTML input is legitimately
required.
* Implement a strong Content Security Policy (CSP) as an additional
defense-in-depth measure.
* Review other functionality using the same input-handling mechanism for
similar reflection issues.

### 👤 Author

Roshan Jeffrin R

Security Researcher • Bug Hunter

> ⚠️ Disclosure Notice
>
> This PoC is published for educational and security research purposes.
> Vulnerability testing should only be performed against systems where you
> have explicit authorization.
