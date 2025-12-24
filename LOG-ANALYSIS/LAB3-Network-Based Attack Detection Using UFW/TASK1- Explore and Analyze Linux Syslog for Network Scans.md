# Lab goal:
   The objective of this lab is to simulate a network-based port scan attack and demonstrate how to detect it using ufw.log logs on a Linux system.will learn how to launch the HTTP scan prob from Kali Linux(attacker) machine and detect these scan ataempt on Victim machine using UFW.
   
# Requirments:
we will use docker.
<img width="1920" height="1032" alt="Screenshot 2025-12-25 001819" src="https://github.com/user-attachments/assets/92b3f118-779c-4d70-83fd-99c93849ed60" />

Attacker Machine:: Kali Linux
<img width="979" height="512" alt="Screenshot 2025-12-25 002045" src="https://github.com/user-attachments/assets/68db2029-c289-4ec9-a6a1-d97e5cef2ce6" />

Target Machine: Ubuntu Linux
<img width="979" height="512" alt="Screenshot 2025-12-25 002130" src="https://github.com/user-attachments/assets/48c6aa76-d91b-4d1b-8cbb-179dcf0dd948" />

# Tools Needed:
nmap (on attacker machine)\
ufw or iptables (on target machine)

# Log file :
/var/log/ufw.log

# ip info:
<img width="1920" height="1080" alt="Screenshot 2025-12-25 005037" src="https://github.com/user-attachments/assets/b3d2826d-36b8-4956-b9e8-f3283d456aad" />



# Step#1 (installing and enabling ufw on the ubuntu)
<img width="1920" height="1032" alt="Screenshot 2025-12-25 005722" src="https://github.com/user-attachments/assets/49edaee4-bbe6-4afb-9bb7-f8ffdac7e1eb" />

# enabling ufw and turn on logging:
<img width="1920" height="1080" alt="Screenshot 2025-12-25 011346" src="https://github.com/user-attachments/assets/d0b1607d-5800-40f3-8ab1-c3c302bb2beb" />

2. create firwall rule to drop http traffic from attacker machine:\
 sudo ufw deny from <ip> to any port 80 proto tcp(drop the traffic from specified ip from any port to port 

3. reload firewall for the rule to take effect:
   sudo ufw reload\
<img width="979" height="512" alt="Screenshot 2025-12-25 012326" src="https://github.com/user-attachments/assets/eb27eeed-cce7-4be9-9159-16352a45c059" />


# Step#2 (scanning from attacker machine and detecting from ubuntu):
ON ATTACKER MACHINE:\
nmap -p80 TARGET-IP
<img width="979" height="512" alt="Screenshot 2025-12-25 023608" src="https://github.com/user-attachments/assets/64deced7-4819-437f-bd5b-1b9095d689d6" />



# detecting the HTTP Scanning traffic
tcpdump -n -i eth0 src 172.19.0.2
<img width="979" height="512" alt="Screenshot 2025-12-25 023711" src="https://github.com/user-attachments/assets/ea56c7ac-d19f-4930-9bf2-0c85806fbf2d" />















