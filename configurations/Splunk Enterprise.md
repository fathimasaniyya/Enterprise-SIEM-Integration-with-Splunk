# Splunk Enterprise Installation (DPKG Method)

## Overview

This document explains how Splunk Enterprise was installed on the SIEM server using the Debian (.deb) package.

---

## Environment

| Item | Value |
|------|------|
| OS | Ubuntu Linux |
| Installation Method | DPKG |
| Software | Splunk Enterprise |

---

## Prerequisites

- Ubuntu installed
- Root/Sudo access
- Splunk Enterprise .deb package downloaded

---

## Step 1 — Download Splunk

Move the downloaded package into the desired directory.

Example:

```bash
cd /opt
```

---

## Step 2 — Install Using DPKG

```bash
sudo dpkg -i splunk-*.deb
```

---

## Step 3 — Start Splunk

```bash
sudo /opt/splunk/bin/splunk start --accept-license
```

Accept the license and create an administrator account.

---

## Step 4 — Enable Auto Start

```bash
sudo /opt/splunk/bin/splunk enable boot-start
```

---

## Step 5 — Verify Service

```bash
sudo /opt/splunk/bin/splunk status
```

Expected:

```
splunkd is running
```

---

## Step 6 — Access Web Interface

```
http://SERVER-IP:8000
```

Login using the administrator credentials created during installation.

---

## Important Ports

| Port | Purpose |
|------|----------|
|8000|Web Interface|
|8089|Management|
|9997|Receiving Forwarders|

---

## Commands Used

```bash
sudo dpkg -i splunk-*.deb
sudo /opt/splunk/bin/splunk start --accept-license
sudo /opt/splunk/bin/splunk enable boot-start
sudo /opt/splunk/bin/splunk status
```

---

## Troubleshooting

- Check service status
- Verify port 8000
- Ensure firewall allows access
- Restart Splunk if required

---

## Security Notes

- Use strong administrator credentials.
- Restrict management port access.
- Keep Splunk updated.
  
---
