# OWASP-Juice-Shop-Penetration-Testing
Web Application Penetration Testing using Burp Suite on OWASP Juice Shop

## Step-by-Step Procedure

### Step 1 – Open Kali Linux

Start VMware Workstation and launch the Kali Linux virtual machine.

---

### Step 2 – Launch Burp Suite

Open Terminal and run:

```bash
burpsuite
```

Burp Suite Community Edition opens.

---

### Step 3 – Create Temporary Project

Select Temporary Project → Next → Use Burp Defaults → Start Burp.

---

### Step 4 – Verify Proxy Listener

Go to **Proxy → Proxy Settings** and verify listener is active on:

`127.0.0.1:8080`

---

### Step 5 – Enable Intercept

Go to **Proxy → Intercept** and ensure:

**Intercept is ON**

---

### Step 6 – Configure Browser Proxy

In Firefox settings, set:

* HTTP Proxy: 127.0.0.1
* Port: 8080
* Enable “Also use this proxy for HTTPS”

---

### Step 7 – Open OWASP Juice Shop

Open:

`http://localhost:3000`

The application loads successfully.

---

### Step 8 – Verify Request Capture

Go to **Proxy → HTTP History** and verify requests are being captured.

---

### Step 9 – Open Login Page

Click **Account → Login**

This page is used for testing login vulnerabilities.

---

### Step 10 – Capture Login Request

Enter test credentials and click Login.

Burp captures the request.

Right-click and select:

**Send to Repeater**

---

### Step 11 – Perform SQL Injection Testing

Modify the request using:

`GET /search?q=' OR 1=1--`

Click **Send**.

The server response confirms SQL Injection testing.

---

### Step 12 – Perform XSS Testing

Modify the request using:

`GET /search?q=<script>alert(1)</script>`

Click **Send**.

The response confirms reflected XSS testing.

---

### Step 13 – Check Security Misconfiguration

Review HTTP response headers and error messages.

Observed improper error handling and exposed server responses.

This indicates security misconfiguration.

---

### Step 14 – Analyze Responses

Use **HTTP History** and **Repeater** to study:

* Status codes
* Error messages
* Input validation issues
* Server behavior

This helps confirm vulnerabilities.

---

### Step 15 – Document Findings

Record:

* Vulnerability name
* Payload used
* Response received
* Risk level
* Suggested remediation

Screenshots were captured as proof of testing.

---

## Conclusion

The project successfully demonstrated web application penetration testing on OWASP Juice Shop using Burp Suite by identifying vulnerabilities such as SQL Injection, XSS, and Security Misconfiguration based on the OWASP Top 10 framework.

