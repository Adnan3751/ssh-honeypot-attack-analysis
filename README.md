
# SSH Honeypot Attack Analysis

## 📌 Overview
This project demonstrates the deployment of an SSH honeypot using **Cowrie** to capture and analyze real-world attack traffic. The goal is to understand attacker behavior, brute-force attempts, post-compromise activity, and apply SOC-style log analysis techniques.

---

## 🛠️ Technologies Used
- Linux (Ubuntu / Kali)
- Cowrie SSH Honeypot
- Python 3
- iptables
- GeoIP Database
- JSON Log Analysis

---

## 🏗️ Architecture
Internet Attack Traffic
        ↓
    SSH Honeypot (Cowrie)
        ↓
     Cowrie JSON Logs
        ↓
   Python Log Parser
        ↓
 Attacker Behaviour Analysis
 
**Deployment Summary**

Deployed Cowrie SSH honeypot on a Linux virtual machine

Redirected live SSH traffic (port 22) using iptables

Enabled JSON logging for session, login, and command activity

Collected logs for offline security analysis

**🔍 Analysis Performed**

Identified SSH brute-force login attempts

Extracted attacker IP addresses and attempted usernames

Analyzed attacker commands executed after successful login

Observed reconnaissance and malware download behavior

Performed GeoIP-based country attribution of attackers

**Sample Python Log Parsing**
import json

with open("cowrie.json", "r") as f:
    for line in f:
        log = json.loads(line)
        print(log.get("src_ip"), log.get("eventid"))
        
**Security Use Cases**
SSH brute-force attack detection

Threat intelligence gathering

SOC log analysis and investigation

Understanding attacker tactics and behavior

**📌 Key Learnings**

Real-world attackers follow predictable brute-force patterns

Centralized logging is critical for incident response

Honeypots provide valuable insight into attacker behavior

**⚠️ Disclaimer**

This project is for educational and research purposes only. No production systems were harmed.



