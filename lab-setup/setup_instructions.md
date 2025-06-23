# Lab Setup Instructions

This guide explains how to set up the web vulnerability lab using VirtualBox and DVWA.

---

## 🛠 Requirements
- VirtualBox
- Kali Linux (as attacker VM)
- DVWA (Damn Vulnerable Web App) or BWAPP (target app)
- Host-only Network configuration

---

## 🔧 Steps

### 1. Setup Virtual Machines
- Import Kali Linux into VirtualBox.
- Import DVWA or install a LAMP stack and clone DVWA from GitHub:
```
git clone https://github.com/digininja/DVWA.git /var/www/html/dvwa
```
---

### 2. Configure Host-only Network
- Go to VirtualBox > File > Host Network Manager.
- Create a host-only network (e.g., `vboxnet0`).
- Assign static IPs (e.g., Kali: 192.168.56.105, DVWA: 192.168.56.106)

---

### 3. Start Apache & MySQL on DVWA
```bash
sudo service apache2 start
sudo service mysql start
```
---

### 4. Configure DVWA
Open browser: http://192.168.56.106/dvwa/setup.php
Click Create/Reset Database
Login with:
```
Username: admin
Password: password
```
--- 

### 5. Set Security Level
Navigate to http://192.168.56.106/dvwa/security.php
Set security level to low or medium

---

✅ Lab Ready!
```
You're now ready to test the attacks listed in the /attacks directory.
```
