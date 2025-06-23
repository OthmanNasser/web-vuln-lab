# Reflected XSS

## 🎯 Objective

Test if the web application is vulnerable to **Reflected Cross-Site Scripting (XSS)** by injecting JavaScript payloads into user input and observing if they are reflected in the page.

---

## 📌 Target Info

- **Target IP**: 192.168.56.105  
- **Service**: HTTP (Port 80)  
- **App Used**: DVWA (XSS - Reflected Module)  
- **Tools**: Browser, Burp Suite (optional)

---

## 🧭 Steps

### 🔹 Step 1: Access the Vulnerable Page

Go to:

```http
http://192.168.56.105/dvwa/vulnerabilities/xss_r/
```

Use low security level in DVWA to begin.


### 🔹 Step 2: Inject Script in Input Field
Use this payload:
```
<script>alert('XSS')</script>
```
If an alert box pops up, the input is reflected without sanitization.

### 🔹 Step 3: Test URL Manipulation
Send the following in the URL query:
```
http://192.168.56.105/dvwa/vulnerabilities/xss_r/?name=<script>alert('XSS')</script>
```
Observe if the JavaScript executes on page load.

📝 Notes
Reflected XSS occurs when data is immediately returned by the server in the response.

Try different payloads such as:
```
"><script>alert(1)</script>
```
Use Burp Suite’s repeater to test quickly with different inputs.

✅ Conclusion
```
The application reflects user input without sanitization, making it vulnerable to Reflected XSS.
Successful exploitation can lead to cookie theft, session hijacking, or redirecting users to malicious sites.
```
