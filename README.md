# 🔍 Nmap Network Scan Task

This repository contains the results and learnings from a basic network reconnaissance task done as part of my Cybersecurity Internship.

---

## 🛠️ Tools Used

- **Nmap** – for port scanning (TCP SYN scan)
- **Kali Linux** – penetration testing OS
- *(Optional)* Wireshark – for packet analysis (not used in this task)

---

## 🎯 Objective

To scan the local network and identify open ports and services running on live hosts, thereby understanding basic network exposure and potential vulnerabilities.

---

## 📡 Scan Details

- **Scan Command Used**:
  ```bash
  sudo nmap -sS 10.0.2.0/24 -oN nmap_scan_results.txt
