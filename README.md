# 🔐 IDS & IPS Lab using Snort (Kali Linux & Ubuntu)

## 📌 Project Overview

This project demonstrates a working Intrusion Detection System (IDS) using Snort in a virtual lab environment.

* Kali Linux is used as the attacker
* Ubuntu is used as the victim machine
* Snort detects malicious traffic such as ping and scanning

---

## 🎯 Objectives

* Understand IDS concepts
* Configure Snort IDS
* Simulate attacks using Kali Linux
* Detect attacks in real-time

---

## 🖥️ Lab Setup

### 🔹 Attacker Machine (Kali Linux)

* IP: 192.168.1.10
* Tools: Nmap, Ping

### 🔹 Victim Machine (Ubuntu)

* IP: 192.168.1.20
* Tool: Snort IDS

---

## ⚙️ Installation

```bash
sudo apt update
sudo apt install snort -y
```

---

## 🔧 Configuration

Edit Snort configuration:

```bash
sudo nano /etc/snort/snort.conf
```

Set:

```
ipvar HOME_NET 192.168.1.0/24
```

---

## 🚨 Rules Configuration

Edit:

```bash
sudo nano /etc/snort/rules/local.rules
```

Add:

```
alert icmp any any -> any any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
alert tcp any any -> any 22 (msg:"SSH Attack Detected"; sid:1000002; rev:1;)
alert tcp any any -> any any (msg:"Nmap Scan Detected"; flags:S; sid:1000003; rev:1;)
```

---

## ▶️ Run Snort

```bash
sudo snort -A console -c /etc/snort/snort.conf -i enp0s3
```

---

## 💣 Attack Simulation

### 🔹 Ping Attack

```bash
ping 192.168.1.20
```

### 🔹 Nmap Scan

```bash
nmap -sS 192.168.1.20
```

---

## 🔍 Results

Snort successfully detects:

* ICMP Ping attacks
* SSH brute force attempts
* Network scans

---

## 📂 Project Structure

```
IDS-IPS-Snort-Lab/
│
├── README.md
├── configs/
├── scripts/
├── screenshots/
└── report/
```

---

## 📸 Screenshots

Add:

* Ping attack
* Snort alert
* Nmap scan
* Snort running

---

## ⚠️ Disclaimer

This project is for educational purposes only.

---

## 👨‍💻 Author

Tariq Ahmad
https://www.linkedin.com/in/tariq-ahmad1122
