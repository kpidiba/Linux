# UFW Basic Usage Guide

**Uncomplicated Firewall (UFW)** is a simple firewall tool used to manage **iptables rules** on Linux systems. It is widely used on **Ubuntu**, **Debian**, and other Linux distributions.

It helps you easily **allow, deny, and manage network ports** to secure your server or local machine.

---

# 1. Installation

Most Linux systems already include UFW. If not, install it.

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install ufw
```

### Verify installation

```bash
ufw --version
```

---

# 2. Check Firewall Status

Before configuring, check whether the firewall is active.

```bash
sudo ufw status
```

Output example:

```bash
Status: inactive
```

---

# 3. Enable or Disable UFW

### Enable firewall

```bash
sudo ufw enable
```

### Disable firewall

```bash
sudo ufw disable
```

---

# 4. Default Firewall Policies

Default policies define how **incoming and outgoing traffic** behave.

### Recommended default settings

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Meaning:

| Policy         | Description                               |
| -------------- | ----------------------------------------- |
| deny incoming  | blocks all external connections           |
| allow outgoing | allows your system to access the internet |

---

# 5. Allow a Port

Allow traffic on a specific port.

### Example: allow port 80 (HTTP)

```bash
sudo ufw allow 80
```

Example: allow port 443 (HTTPS)

```bash
sudo ufw allow 443
```

---

# 6. Allow a Specific Protocol

Ports may use **TCP or UDP**.

### Allow TCP

```bash
sudo ufw allow 22/tcp
```

### Allow UDP

```bash
sudo ufw allow 53/udp
```

---

# 7. Allow a Port Range

Example: allow ports **3000–3010**

```bash
sudo ufw allow 3000:3010/tcp
```

---

# 8. Allow Services by Name

UFW recognizes common services.

Example:

Allow **SSH**

```bash
sudo ufw allow ssh
```

Allow **HTTP**

```bash
sudo ufw allow http
```

---

# 9. Deny a Port

Block traffic to a port.

Example:

```bash
sudo ufw deny 8080
```

---

# 10. Delete a Rule

Remove a rule.

Example

```bash
sudo ufw delete allow 80
```

---

# 11. View Rules

### Show basic rules

```bash
sudo ufw status
```

Example output:

```json
Status: active

To        Action     From
--        ------     ----
22/tcp    ALLOW      Anywhere
80        ALLOW      Anywhere
443       ALLOW      Anywhere
```

---

# 12. Allow Access From Specific IP

Allow SSH from a single IP.

```bash
sudo ufw allow from 192.168.1.100 to any port 22
```

---

# 13. Allow Access to Specific Interface

Example:

```bash
sudo ufw allow in on eth0 to any port 80
```

---

# 14. Logging

Enable firewall logs.

```bash
sudo ufw logging on
```

Log levels:

```json
low
medium
high
full
```

Example:

```bash
sudo ufw logging medium
```

Logs are stored in:

```bash
/var/log/ufw.log
```

---

# 15. Reset Firewall

Reset all rules.

```bash
sudo ufw reset
```

---

# 16. Reload Firewall

Apply new changes.

```bash
sudo ufw reload
```

---

# 17. Common Server Configuration

Example configuration for a **web server**.

Allow:

- SSH

- HTTP

- HTTPS

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing

sudo ufw allow ssh
sudo ufw allow 80
sudo ufw allow 443

sudo ufw enable
```

---

# 18. Check Open Ports

Use tools like:

- `ss`

- `netstat`

- `lsof`

Example:

```bash
ss -tulnp
```

## 19. Best Practices


✔ Always allow **SSH before enabling firewall**  
✔ Use **default deny incoming policy**  
✔ Only open required ports  
✔ Monitor logs regularly

# 20. Useful Commands Summary

| Command               | Description      |
| --------------------- | ---------------- |
| `ufw enable`          | enable firewall  |
| `ufw disable`         | disable firewall |
| `ufw status`          | show rules       |
| `ufw allow 80`        | allow port       |
| `ufw deny 80`         | block port       |
| `ufw delete allow 80` | remove rule      |
| `ufw reset`           | reset firewall   |
