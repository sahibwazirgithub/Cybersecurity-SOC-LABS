## LAB GOAL:
      The objective of this lab is to understand the core steps of incident response by investigating a suspicious bash script execution on a Linux system.

## Scenario: Suspicious Script Found in /tmp
during monitoring system flagged a suspicious file in /tmp. Upon inspection, it's a bash script (payload.sh) that connects to an unknown IP. We are tasked with investigating this incident.

## System Requirements:
Kali Linux\
Terminal access with sudo privileges

# Simulating the attack:
1.creating a script-lab directory and a fakebackup.sh file in that directory
<img width="1376" height="690" alt="Screenshot 2026-01-05 183423" src="https://github.com/user-attachments/assets/f0708f6a-6d2c-4eeb-be4b-75c6f34fc414" />

2.Content of the fakebackup.sh:
 <img width="1377" height="693" alt="Screenshot 2026-01-05 183624" src="https://github.com/user-attachments/assets/328f94b4-0b65-4a98-8b2f-a896e883a65b" />

3.Changing its permissions to executable:
<img width="1920" height="1080" alt="Screenshot 2026-01-05 183748" src="https://github.com/user-attachments/assets/cf284b63-9f3c-4242-b342-c6ea77b4ec58" />

4.executing the fakebackup.sh:
<img width="1920" height="1080" alt="Screenshot 2026-01-05 185807" src="https://github.com/user-attachments/assets/d7e45c45-1405-4583-b301-fa8d04d22e66" />


# Step-by-Step Investigation:
# 1.PREPERATION:
Install curl, lsof, ps, and grep (usually pre-installed).
# 2.DETECTION AND ANALYSIS:
Check running processes:
<img width="1918" height="219" alt="Screenshot 2026-01-05 191816(1)(1)" src="https://github.com/user-attachments/assets/ae36ac44-52d4-4750-8efd-1a64678cd3d9" />


## 3. Containment, Eradication, and Recovery:
Kill any related processes:
<img width="1920" height="1080" alt="Screenshot 2026-01-05 191816" src="https://github.com/user-attachments/assets/0a33268f-4cd8-401c-89b9-c236cb75b1cc" />


Remove the malicious script:
<img width="1920" height="1080" alt="Screenshot 2026-01-05 192028" src="https://github.com/user-attachments/assets/f21fc248-5e8d-48c2-8bc1-8f19afc5d5b1" />


Clear the crontab if persistence was found:

Restart services if needed and log out inactive sessions.

## 4.Post incident activity:
Document:

What triggered the alert?

What was the script doing?

Which user executed it?

Recommendations:

Enable file integrity monitoring (e.g., AIDE).

Restrict /tmp execution using mount options (noexec).

Educate users about unknown script execution.

 


 


