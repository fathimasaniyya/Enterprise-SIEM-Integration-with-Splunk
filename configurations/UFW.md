# UFW (Uncomplicated Firewall) Configuration

## Overview

This document describes the installation and configuration of UFW (Uncomplicated Firewall) on the Ubuntu target system. UFW was configured to secure the server by allowing only required services while blocking unauthorized access. It also works alongside Fail2Ban to automatically block malicious IP addresses detected during brute-force attacks.

---

## Environment

| Item | Value |
|------|------|
| Operating System | Ubuntu Linux |
| Firewall | UFW |
| Purpose | Host-Based Firewall |

---

## Prerequisites

- Ubuntu Linux
- Root or sudo privileges
- Internet connectivity
- SSH access

---

## Step 1 — Update the System

```bash
sudo apt update
```

---

## Step 2 — Install UFW

```bash
sudo apt install ufw -y
```

---

## Step 3 — Verify Installation

```bash
sudo ufw version
```

---

## Step 4 — Set Default Policies

Deny all incoming connections by default while allowing outgoing traffic.

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

---

## Step 5 — Allow Required Services

Allow SSH access.

```bash
sudo ufw allow OpenSSH
```

or

```bash
sudo ufw allow 22/tcp
```

If required, allow Splunk Web Interface.

```bash
sudo ufw allow 8000/tcp
```

Allow Splunk Management Port.

```bash
sudo ufw allow 8089/tcp
```

Allow Splunk Receiving Port.

```bash
sudo ufw allow 9997/tcp
```

Allow HTTP for Apache/DVWA.

```bash
sudo ufw allow 80/tcp
```

Allow HTTPS (optional).

```bash
sudo ufw allow 443/tcp
```

---

## Step 6 — Enable UFW

```bash
sudo ufw enable
```

Expected Output

```
Firewall is active and enabled on system startup
```

---

## Step 7 — Verify Firewall Status

```bash
sudo ufw status verbose
```

Example Output

```
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
8000/tcp                   ALLOW       Anywhere
8089/tcp                   ALLOW       Anywhere
9997/tcp                   ALLOW       Anywhere
```

---

## Step 8 — Enable Firewall Logging

```bash
sudo ufw logging on
```

Verify logging status.

```bash
sudo ufw status verbose
```

---

## Step 9 — Reload Configuration

```bash
sudo ufw reload
```

---

## Step 10 — Monitor Firewall Logs

View firewall activity.

```bash
sudo tail -f /var/log/ufw.log
```

---

## Useful Commands

Check status.

```bash
sudo ufw status
```

List numbered rules.

```bash
sudo ufw status numbered
```

Delete a firewall rule.

```bash
sudo ufw delete <rule_number>
```

Disable UFW.

```bash
sudo ufw disable
```

Reset firewall configuration.

```bash
sudo ufw reset
```

---

## Directory

| Directory | Purpose |
|-----------|---------|
| `/var/log/ufw.log` | UFW Firewall Logs |

---

## Common Commands

```bash
sudo apt update

sudo apt install ufw -y

sudo ufw default deny incoming

sudo ufw default allow outgoing

sudo ufw allow OpenSSH

sudo ufw allow 80/tcp

sudo ufw allow 443/tcp

sudo ufw allow 8000/tcp

sudo ufw allow 8089/tcp

sudo ufw allow 9997/tcp

sudo ufw enable

sudo ufw reload

sudo ufw status verbose

sudo tail -f /var/log/ufw.log
```

---

## Troubleshooting

- Ensure SSH is allowed before enabling UFW to avoid losing remote access.
- Verify required application ports are open.
- Check firewall logs for blocked connections.
- Reload UFW after modifying rules.
- Confirm firewall status using `sudo ufw status verbose`.

---

## Security Notes

- Deny all incoming traffic by default.
- Allow only required services.
- Enable logging for monitoring and incident analysis.
- Regularly review firewall rules.
- Integrate UFW with Fail2Ban for automated blocking of malicious IP addresses.

---
