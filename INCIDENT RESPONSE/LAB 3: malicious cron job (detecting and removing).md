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

echo "* * * * * /tmp/malicious.sh" >> /var/spool/cron/root
<img width="1920" height="1080" alt="Screenshot 2026-01-14 194414" src="https://github.com/user-attachments/assets/9bd8f4c9-70b4-4a29-84e9-38425bf2601b" />
<img width="1920" height="1080" alt="Screenshot 2026-01-15 185036" src="https://github.com/user-attachments/assets/e64bab34-ce0c-4e6b-824b-09c49e7f7a27" />


## Step-by-Step Investigation:
## Preperation:
- Make sure cron is installed and running:

sudo systemctl status cron

- Enable logging (cron logs are usually in /var/log/syslog or /var/log/cron).

## Detection and analysis:
1.Check for suspicious cron entries:
crontab -l\
2.Search cron directories for unauthorized jobs:
grep -r "/tmp/" /etc/cron* /var/spool/cron/crontabs\
3.Review logs to confirm execution:
cat /tmp/.cron.log
4.Analyze the script:
cat /tmp/malicious.sh
<img width="1920" height="1080" alt="Screenshot 2026-01-15 185147" src="https://github.com/user-attachments/assets/ec0ce55b-e72a-4ac1-a999-c6d8e560eab5" />
<img width="1920" height="1080" alt="Screenshot 2026-01-15 192156" src="https://github.com/user-attachments/assets/1fbdc583-ecab-4130-b83e-b8271635da39" />


## conatainment,eradication and recovery:
1.Remove the malicious cron job:
crontab -l | grep -v "malicious.sh" | crontab -
2.Delete the script and its output:
rm -f /tmp/malicious.sh /tmp/.cron.log
3.Restart the cron service:
sudo systemctl restart cron
<img width="1920" height="1080" alt="Screenshot 2026-01-15 191059" src="https://github.com/user-attachments/assets/7b8056b6-f755-4e20-b4a1-366aade21c5a" />

### Step 4. Post-Incident Activity
- Document the following:
 - When the cron job was added
 - What the script was doing
 - Any signs of lateral movement or download activity

- Recommendations:
 - Restrict cron job access to authorized users only
 - Enable cron integrity checks
 - Set up alerts for new cron entries (using auditd or inotify)


