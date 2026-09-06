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
Evidence: eBook-.mp4
