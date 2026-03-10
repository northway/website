---
icon: lucide/timer

tags:
  - linux
  - systemd
  - timer
---

# Systemd Timer

Timer unit configuration

A [systemd timer](https://man7.org/linux/man-pages/man5/systemd.timer.5.html) requires two unit files: a `.service` file that defines what to run, and a `.timer` file that defines when to run it.

Let's create the two files:

* `/etc/systemd/system/afraid-freedns-v4.timer`

```bash
[Unit]
Description=Run the Afraid FreeDNS IPv4 update in every 5 minutes

[Timer]
OnCalendar=*-*-* *:00,05,10,15,20,25,30,35,40,45,50,55:00
Unit=afraid-freedns-v4.service

[Install]
WantedBy=timers.target
```

* `/etc/systemd/system/afraid-freedns-v4.service`

```bash
[Unit]
Description=Afraid FreeDNS IPv4 update
After=network.target

[Service]
Type=oneshot
ExecStart=/usr/bin/curl -s https://sync.afraid.org/u/TOKEN/

[Install]
WantedBy=multi-user.target
```

Reload the systemctl deamon and enable the timer.

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now afraid-freedns-v4.timer

# Check timer status and next trigger time
systemctl status afraid-freedns-v4.timer

# List all active timers
systemctl list-timers
```
