## LAB GOAL:
The objective of this lab is to investigate and respond to a malicious cron job used by an attacker to maintain persistence on a Linux system.I will simulate the attack, detect the malicious
scheduled task, analyze the script, and remove the threat — applying the full incident response lifecycle.

## WHAT IS CRON JOB:
A cron job is a sheduled task that runs automatically at defined intervals on Unix/Linux systems.
----**key features**----
.runs commands automatically(every minute,daily,weekly)\
.useful for backups,updates,monitering scripts,etc\
.work in background via the cron service.
---**format of cron entry**-----
```
*  *  *  *  *  command-to-run
│  │  │  │  │
│  │  │  │  └─ Day of the week (0-7, Sun = 0 or 7)
│  │  │  └──── Month (1 - 12)
│  │  └─────── Day of month (1 - 31)
│  └────────── Hour (0 - 23)
└───────────── Minute (0 - 59)
```

Attaker often use cron to re-execute payloads,reconnect-and-control servers or mantain access.

## LAB SCENARIO:
    A malicious cron job is running every minute.\
an attacker has added a cron job that silently runs a malicious script from /tmp every minute.our job is to detect and understand its behaviour and remove it safely.

## LAB SETUP:
KALI.
Terminal with sudo access.

------**Simulate the Incident**--------
1. Create a fake "malicious" script:
```bash
echo -e '#!/bin/bash\necho "Ping from attacker server" >> /tmp/.cron.log' > /tmp/malicious.sh
chmod +x /tmp/malicious.sh
```
2. Add a cron job for the current user:
```
echo "* * * * * /tmp/malicious.sh" >> /var/spool/cron/root

## Step-by-Step Investigation:
## Preperation:
- Make sure cron is installed and running:
```
sudo systemctl status cron
```
- Enable logging (cron logs are usually in /var/log/syslog or /var/log/cron).

#
