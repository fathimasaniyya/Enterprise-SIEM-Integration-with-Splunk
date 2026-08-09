# 🛡️ Enterprise SIEM Integration with Splunk

# 📌 Executive Summary

This project demonstrates the implementation of a centralized Security Information and Event Management (SIEM) solution using Splunk Enterprise within a simulated enterprise environment.

The solution collects security logs from multiple sources, correlates security events, detects brute-force attacks, generates real-time alerts, and visualizes security events through custom dashboards. Firewall controls using UFW provide automated protection against malicious SSH login attempts.

The project simulates the responsibilities of a SOC Analyst by monitoring security events, investigating suspicious activities, and improving incident visibility.

---

# 🎯 Objectives

- Deploy Splunk Enterprise
- Configure Splunk Universal Forwarder
- Centralize security log collection
- Monitor authentication events
- Detect brute-force attacks
- Build security dashboards
- Configure real-time alerts
- Block malicious IPs using UFW

---

# 🏗️ Architecture

```
Ubuntu Client
      │
      │ Splunk Universal Forwarder
      ▼
Splunk Enterprise Server
      │
      ├── Authentication Logs
      ├── Apache Logs
      ├── Firewall Logs
      │
      ▼
 Dashboards • Alerts • Reports
      │
      ▼
     UFW 
```

---
# 🖥️ Environment

| Component | Technology |
|------------|------------|
| SIEM | Splunk Enterprise |
| Log Forwarder | Splunk Universal Forwarder |
| Operating System | Ubuntu Linux |
| Firewall | UFW |
| Web Application | DVWA |
| Log Sources | Auth Logs, Apache Logs, Firewall Logs |

---

# 🔍 Security Use Cases

- SSH Brute Force Detection
- Failed Login Monitoring
- Apache Web Login Monitoring
- Firewall Activity Monitoring
- Blocked IP Monitoring
- Security Alert Generation

---

# 📊 Features

- Centralized Log Collection
- Real-Time Monitoring
- Security Dashboards
- Correlation Searches
- Alerting
- Firewall Event Analysis
- Automated SSH Attack Blocking

  ---

# 📂 Log Sources

- `/var/log/auth.log`
- Apache Access Logs
- Apache Error Logs
- UFW Logs

  ---

# 📚 Learning Outcomes

Through this project I learned:

- SIEM architecture
- Enterprise log management
- Event correlation
- Security monitoring
- Incident detection
- Alert creation
- Dashboard development
- Brute-force attack analysis
- Firewall log investigation
- SOC analyst workflow

  ---

# 📄 Disclaimer

This project was developed in a controlled laboratory environment for cybersecurity education, security monitoring practice, and defensive research purposes only.

No unauthorized systems were targeted.
