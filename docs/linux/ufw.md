---
icon: lucide/brick-wall-shield

tags:
  - linux
  - firewall
  - ufw
---

# UFW

UFW - Uncomplicated Firewall

The default firewall configuration tool for Ubuntu is ufw. Developed to ease iptables firewall configuration, ufw provides a user friendly way to create an IPv4 or IPv6 host-based firewall. By default UFW is disabled.

<https://help.ubuntu.com/community/UFW>

## Status

```bash
sudo ufw status verbose
```

```bash
sudo ufw status numbered
```

## Enable / Disable

```bash
sudo ufw enable
```

```bash
sudo ufw disable
```

## Default rules

Deny all incoming:

```bash
sudo ufw default deny incoming
```

Allow all outgoing:

```bash
sudo ufw default allow outgoing
```

## Allow

Allow CDIR, target port and protocoll.

```shell
sudo ufw allow from 192.168.0.0/24 to any port 22 proto tcp
```

```bash
sudo ufw allow from 1.1.1.1/32 to any port 22 proto tcp comment 'Example jumphost'
```

Allow for inet interface.

```bash
sudo ufw allow in on eth1 to any port 3306
```

Allow port ranges.

```bash
sudo ufw allow proto tcp from any to any port 8080:8090
```

Comments:

```bash
sudo ufw allow proto tcp from any to any port 80,443 comment 'web apps'
```

Insert before a numbered rule:

```bash
sudo ufw insert 2 allow to any port 2222 proto tcp comment 'sometext'

sudo ufw insert 11 allow from 111.111.111.111/32 to any port 22 proto tcp comment 'Example jumphost'
```

## Services

### Add 

```bash
sudo ufw allow http
```

### Deny

```bash
sudo ufw deny ssh
```

### Remove

```bash
sudo ufw delete allow http
```
