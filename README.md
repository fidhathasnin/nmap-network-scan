# 🔍 Nmap Network Scanning Task

## 📝 Task Overview
Performed a basic network scanning task using **Nmap** on a local network (`10.0.2.0/24`) to identify:
- ✅ Live hosts
- ✅ Open ports
- ✅ Running services  
Optional packet analysis using **Wireshark**.

---

## 💻 Commands Used

### 1. SYN Scan for Local Network
```bash
sudo nmap -sS 10.0.2.0/24
```
# 🔍 Nmap Network Scan Task

## 🔎 Observations

### Live Hosts Found:
- 10.0.2.2  
- 10.0.2.3  
- 10.0.2.15  

### Open Ports & Services:
#### 10.0.2.2:
- 135 (msrpc)
- 445 (microsoft-ds)
- 903 (iss-console-mgr)
- 5357 (wsdapi)

#### 10.0.2.3:
- 53 (domain)

#### 10.0.2.15:
- 80 (http)

---

## 🧠 Common Services on Open Ports

| Port | Service         | Notes                                                              |
|------|------------------|--------------------------------------------------------------------|
| 135  | msrpc            | Windows RPC – vulnerable to RPC DCOM exploits.                    |
| 445  | microsoft-ds     | SMB – known for EternalBlue & SMBv1 vulnerabilities.              |
| 903  | iss-console-mgr  | Used by VMware – disable if unused.                               |
| 5357 | wsdapi           | Web Services for Devices – potential information leak.            |
| 53   | domain           | DNS – verify it’s not open to recursion.                          |
| 80   | http             | Web server – check for outdated software or misconfigurations.    |

---

## ⚠️ Risk Summary

- **SMB (445)** and **RPC (135)** may pose serious external exposure risks.
- **HTTP (80)** on 10.0.2.15 should be tested for:
  - Directory listing
  - Outdated CMS
  - Open admin panels
- **DNS (53)** could be vulnerable to:
  - DNS poisoning
  - Amplification attacks

---

## 💾 Output File

Nmap scan result was saved to:

```bash
sudo nmap -sS 10.0.2.0/24 -oN scan_results.txt
```
## ⚠️ Risk Summary

- **SMB (445)** and **RPC (135)** can be high-risk if exposed externally — vulnerable to attacks like EternalBlue or DCOM exploits.
- The **HTTP (80)** service on 10.0.2.15 should be assessed for:
  - Directory listing
  - Unpatched web software (e.g., outdated CMS)
  - Exposed admin interfaces
- **DNS (53)** might allow:
  - Recursive queries
  - DNS amplification or cache poisoning attacks
