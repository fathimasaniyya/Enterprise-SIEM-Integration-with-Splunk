# Splunk Universal Forwarder Installation (DPKG Method)

## Overview

This document describes the installation and configuration of the Splunk Universal Forwarder on an Ubuntu target system using the Debian (`.deb`) package. The Universal Forwarder collects system logs and securely forwards them to the Splunk Enterprise server for centralized monitoring and analysis.

---

## Environment

| Item | Value |
|------|------|
| Operating System | Ubuntu Linux |
| Installation Method | DPKG (.deb) |
| Software | Splunk Universal Forwarder |
| Purpose | Forward System Logs to Splunk Enterprise |

---

## Prerequisites

- Ubuntu Linux installed
- Root or sudo privileges
- Splunk Universal Forwarder `.deb` package
- Reachable Splunk Enterprise server
- Network connectivity between Forwarder and Splunk Server

---

## Step 1 — Download the Splunk Universal Forwarder

Download the appropriate `.deb` package from the official Splunk website.

Move the package to your preferred installation directory.

```bash
cd /opt
```

---

## Step 2 — Install Using DPKG

```bash
sudo dpkg -i splunkforwarder-*.deb
```

---

## Step 3 — Start the Universal Forwarder

```bash
sudo /opt/splunkforwarder/bin/splunk start --accept-license
```

Accept the license agreement and create an administrator account when prompted.

---

## Step 4 — Configure the Splunk Server

Connect the Universal Forwarder to the Splunk Enterprise server.

```bash
sudo /opt/splunkforwarder/bin/splunk add forward-server <Splunk_Server_IP>:9997
```

Example

```bash
sudo /opt/splunkforwarder/bin/splunk add forward-server 192.168.1.10:9997
```

---

## Step 5 — Monitor System Logs

Add the system log directory for monitoring.

```bash
sudo /opt/splunkforwarder/bin/splunk add monitor /var/log
```

You can also monitor individual log files.

Example

```bash
sudo /opt/splunkforwarder/bin/splunk add monitor /var/log/auth.log
```

---

## Step 6 — Enable Automatic Startup

```bash
sudo /opt/splunkforwarder/bin/splunk enable boot-start
```

---

## Step 7 — Restart the Universal Forwarder

```bash
sudo /opt/splunkforwarder/bin/splunk restart
```

---

## Step 8 — Verify Status

Check whether the Universal Forwarder is running.

```bash
sudo /opt/splunkforwarder/bin/splunk status
```

Expected Output

```
splunkd is running
```

---

## Verify Connection

List the configured forward server.

```bash
sudo /opt/splunkforwarder/bin/splunk list forward-server
```

Expected status:

```
Active Forwarder
```

---

## Directory Structure

| Directory | Purpose |
|-----------|---------|
| `/opt/splunkforwarder/` | Universal Forwarder Installation |
| `/var/log/` | System Log Files |
| `etc/system/local/` | Local Configuration Files |

---

## Common Commands

```bash
sudo dpkg -i splunkforwarder-*.deb

sudo /opt/splunkforwarder/bin/splunk start --accept-license

sudo /opt/splunkforwarder/bin/splunk add forward-server <Server-IP>:9997

sudo /opt/splunkforwarder/bin/splunk add monitor /var/log

sudo /opt/splunkforwarder/bin/splunk enable boot-start

sudo /opt/splunkforwarder/bin/splunk restart

sudo /opt/splunkforwarder/bin/splunk status

sudo /opt/splunkforwarder/bin/splunk list forward-server
```

---

## Troubleshooting

- Verify that port **9997** is open on the Splunk Enterprise server.
- Ensure the Splunk server is configured to receive forwarded data.
- Confirm network connectivity between the forwarder and the server.
- Restart the Universal Forwarder after making configuration changes.
- Review logs under:

```text
/opt/splunkforwarder/var/log/splunk/
```

---

## Security Notes

- Use secure administrator credentials.
- Limit access to management services.
- Forward only required log sources.
- Keep the Universal Forwarder updated.
- Protect forwarded log traffic using secure network controls.

---
