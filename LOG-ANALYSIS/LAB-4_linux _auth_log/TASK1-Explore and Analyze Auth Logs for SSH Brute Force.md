# LAB GOAL:
The objective of this lab is to simulate an SSH brute force attack and demonstrate how to detect it using Linux authentication logs.

## Requirements
Attacker Machine: Kali Linux\
Target Machine: Ubuntu Linux Server


## Tools Needed:
hydra (on attacker machine)\
openssh-server (on target machine)\
rsyslog (default logging service)


## Log Files:
/var/log/auth.log – Authentication logs (Ubuntu/Debian)\
/var/log/secure – (CentOS/RHEL)

## What is an SSH Brute Force Attack?
A brute force attack attempts to guess a user’s SSH password by trying many combinations quickly using automated tools like Hydra.

## Why It’s Dangerous
Successful brute force = full shell access\
Attackers can pivot, install malware, or exfiltrate data\
It often goes unnoticed without proper log monitoring


## Attack Patterns Detectable via Auth Logs:
Multiple failed password attempts from one IP\
Repeated login attempts to root/admin accounts\
Success after multiple failures (brute force success)\
Logins from unknown or foreign IPs

# What is Hydra?
Hydra is a fast, open-source password-cracking tool used for brute force attacks on logins.\
It supports 50+ protocols like SSH, FTP, HTTP, SMB, and more.\
Common use: penetration testing and checking for weak passwords in network services.\
Syntax: hydra -L users.txt -P passlist.txt <target_ip> <protocol>\
Use -l/-p for single username/password or -L/-P for files.\
Add -vV for verbose output and -t 4 to set number of threads.

# Step :1 (attack simulation from kali)


