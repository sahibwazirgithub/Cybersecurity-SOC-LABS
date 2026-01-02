## LAB GOAL:
   Detect and Respond: Windows Server RDP Brute Force Attack.

----------**LAB Requirments**--------------:

## Machines Required:

## Windows Server 2019 or 2022
RDP enabled\
Event Viewer access
<img width="1920" height="1080" alt="Screenshot 2026-01-03 005747" src="https://github.com/user-attachments/assets/0d6ef938-5314-4864-824b-f5b4caefb5d9" />

## Kali Linux VM
Hydra pre-installed\
Connected to same LAN or Virtual Network
<img width="1920" height="1080" alt="Screenshot 2026-01-03 004834" src="https://github.com/user-attachments/assets/b4006411-07ad-4489-b984-70a312d03d9a" />


## Network:
Ensure both machines are on the same network:(both ip are from same subnet)
Verify RDP (TCP/3389) is open on Windows Server(enabled can be seen in the windows server screenshot shared).


## Preparation Steps
On Windows Server:\
Enable RDP:\
System Properties → Remote → Enable Remote Desktop

Allow RDP in Firewall:\
Windows Defender Firewall → Advanced Settings → Inbound Rules → Remote Desktop (TCP-In) → Enable

## Accessed windows server via RDP:
<img width="1920" height="1080" alt="Screenshot 2026-01-03 011509" src="https://github.com/user-attachments/assets/a6d18f4e-1467-4841-ba5d-25dbbe835a0e" />


## Simulating RDP bruteforce attack:
On Kali Linux: Install Hydra (if not installed):\
sudo apt update && sudo apt install hydra

hydra -l <user> -P <wordlist> rdp://<Windows_Server_IP>
<img width="1911" height="1076" alt="Screenshot 2026-01-03 012252(1)(1)" src="https://github.com/user-attachments/assets/21c5bbc1-b113-4053-8036-656c479f20b7" />

## Visualize the Alert in Event Viewer:
Look for Event ID 4625(filter) in event viewer windows security log:
<img width="1610" height="1036" alt="Screenshot 2026-01-03 013151" src="https://github.com/user-attachments/assets/0eeacb65-abc2-4f51-84db-4e4703885be0" />
## IDENTIFIED ATTACK:
1.many failed logins from ip 192.169.35.129\
2.logon-type:3(modern system does'nt show 11 for rdp now.
<img width="1469" height="957" alt="Screenshot 2026-01-03 014032" src="https://github.com/user-attachments/assets/900d5649-af1f-46c3-93a4-47c7f657a005" />

## Incident Response Steps

## DETECTION:
----Identify Repeated Failed Logons:
Spot Event ID 4625 from same IP\
---Correlate IP Address:
Confirm repeated failures from attacker’s IP.

## Block Attacker IP:
New-NetFirewallRule -DisplayName "Block Attacker" -Direction Inbound -RemoteAddress <Kali_IP> -Action Block
---OR MANUALLY FROM FIREWALL:
_____**SPECIFIED IP**:
<img width="1469" height="957" alt="Screenshot 2026-01-03 015039" src="https://github.com/user-attachments/assets/299f0c2d-3074-40e5-9c4e-341bc2c37b00" />
_____**SPECIFED PORT(3389(RDP))**:
<img width="1469" height="957" alt="Screenshot 2026-01-03 015055" src="https://github.com/user-attachments/assets/1b7e2b75-2539-4396-b2af-7f55d013af41" />

______**CONFIRMING THE FIREWALL IS DROPING PACKETS**:
ENABLE logging drop packets in firewall properties for public,private,domain.\
access pfirewall.log:
<img width="1469" height="957" alt="Screenshot 2026-01-03 020032" src="https://github.com/user-attachments/assets/1f2e1ee0-ddc9-4a39-abfa-b642580bd00f" />



## Collect Evidence:
Export relevant Event Logs

## Report Incident:
Create a brief report with findings and actions taken

## Conclusion:
This lab demonstrated how to:

Simulate an RDP brute-force attack using Hydra\
Detect suspicious logons via Windows Event Viewer\
Respond with basic IR steps without using Sysmon







