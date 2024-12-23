```markdown
# Cyber Operation Automation Script

## Overview
This script, `cyber_operation_script.sh`, is designed to automate defensive actions against identified cyber threats. It blocks malicious IPs, domains, and limits brute-force attempts, providing logging and monitoring capabilities for further analysis.

---

## Features
- 🛡️ **Malicious IP Blocking**: Blocks known attacker-controlled IPs (e.g., `5.252.178.193` and `94.131.101.186`).
- 🌐 **Domain Blocking**: Prevents communication with identified malicious domains (e.g., `mainsercheronlinehostingbot.com`).
- 🚦 **Rate Limiting**: Applies rate limits on ports `80` and `443` to mitigate brute-force attempts.
- 📊 **Traffic Logging**: Captures suspicious traffic in `/var/log/suspicious_traffic.log`.
- 🖥️ **System Monitoring**: Logs abnormal CPU or memory usage for malware detection.
- 📝 **Comprehensive Report**: Generates a defense report summarizing blocked activities.

---

## Prerequisites
- **Operating System**: Kali Linux or any Linux-based distribution.
- **Dependencies**:
  - `iptables` for network rules.
  - `tcpdump` for logging network traffic.
  - `awk` for resource monitoring.

---

## How to Use

### 1. Setup
Grant execution permissions:
```bash
chmod +x cyber_operation_script.sh
```

### 2. Run the Script
Execute with elevated permissions:
```bash
sudo ./cyber_operation_script.sh
```

### 3. Verify Functionality
- Check iptables rules:
  ```bash
  sudo iptables -L -v -n
  ```
- Monitor logs for blocked traffic:
  ```bash
  tail -f /var/log/suspicious_traffic.log
  ```

---

## Sample Outputs

### 1. **Iptables Rules**
The script applies the following rules:
- Blocking IPs: `5.252.178.193`, `94.131.101.186`
- Rate-limiting ports `80` and `443`.

**Command**:
```bash
sudo iptables -L -v -n
```
**Output**:
```
Chain INPUT (policy ACCEPT)
pkts bytes target     prot opt in     out     source               destination
  10   600 DROP       all  --  *      *       5.252.178.193        0.0.0.0/0
   5   300 DROP       all  --  *      *       94.131.101.186       0.0.0.0/0
```

---

### 2. **Ping and Curl Tests**
- **Ping Test**:
  ```bash
  ping 5.252.178.193
  ```
  **Output**:
  ```
  PING 5.252.178.193 (5.252.178.193) 56(84) bytes of data.
  Request timed out.
  ```

- **Curl Test**:
  ```bash
  curl http://5.252.178.193
  ```
  **Output**:
  ```
  curl: (7) Failed to connect to 5.252.178.193 port 80: Connection refused
  ```

---

### 3. **Traffic Logs**
Traffic from malicious IPs is logged in `/var/log/suspicious_traffic.log`.

**Command**:
```bash
tail -f /var/log/suspicious_traffic.log
```
**Output**:
```
[DATE TIME] IP 5.252.178.193 blocked by iptables.
```

---

### 4. **Resource Monitoring**
Logs abnormal CPU or memory usage in `/var/log/resource_monitor.log`.

**Command**:
```bash
tail -f /var/log/resource_monitor.log
```
**Output**:
```
[DATE TIME] High CPU usage detected for process ID 1234.
```

---

## Documentation

### Purpose and Functionality
- Automates network defenses by blocking malicious entities and limiting brute-force attempts.
- Provides real-time logging and monitoring for detailed analysis.

### Instructions for Running
1. Ensure the script has execute permissions: `chmod +x cyber_operation_script.sh`
2. Run with:
   ```bash
   sudo ./cyber_operation_script.sh
   ```

### Dependencies
- **iptables**: For applying firewall rules.
- **tcpdump**: For logging traffic.
- **awk**: For analyzing CPU and memory usage.

---

## Sample Screenshots

### Combined Logs (Figure 6A, 6B, 6C)
- **Traffic Logs**: Logs all suspicious traffic from blocked IPs.
- **Blocked Payloads**: Reassembled TCP streams for POST requests.
- **Resource Monitoring**: Abnormal system usage logs.

**Screenshot Placeholder**:
![image](https://github.com/user-attachments/assets/116e4b01-11fe-4613-97b9-ecb3e0421f0e)
![image](https://github.com/user-attachments/assets/0ed6ca18-ff88-462a-b30b-98f0aae8967f)
![image](https://github.com/user-attachments/assets/50599004-c09c-49cf-b4e3-914eac6769a3)


---

## Contribution
Author: **Muhammad Zubair**  
Contact: *mz23acr@herts.ac.uk*

---
