# What is a Network Port Scan?
A port scan is a technique used by attackers to probe a system for open ports and active services. Tools like nmap are commonly used to map a system’s network surface.

# Why It’s Dangerous ?
Port scans are often a precursor to exploitation\
They help attackers identify vulnerable services like open SSH, FTP, or outdated web servers

# What is Nmap?
1.Nmap (Network Mapper) is an open-source network scanning tool.\
2.Used to discover hosts and services on a network.\
3.Helps in identifying open ports, running services, and OS detection.\
4.Commonly used for network inventory and vulnerability scanning.

# Nmap Popular Scan Types:
SYN Scan (-sS): Fast and stealthy port scan.\
TCP Connect Scan (-sT): Full TCP connection, less stealthy.\
UDP Scan (-sU): Scans UDP ports for services.\
Ping Scan (-sn): Checks which hosts are up, no port scan.

# What is UFW?


UFW stands for Uncomplicated Firewall, a frontend for iptables.\
Simplifies firewall management for Linux users.\
Used to allow, deny, and manage traffic rules easily.\
Logs are stored in: /var/log/ufw.log.\
Rule file: /etc/ufw/before.rules\
To check ufw status: ufw status\
To check the rule number: ufw status numbered\

# UFW Rule Syntax:

Basic allow rule: ufw allow\
Deny a port: ufw deny\
Allow by service: ufw allow (e.g., ufw allow ssh)\
Allow by IP: ufw allow from\
Allow specific port from IP: ufw allow from to any port\
Delete rule: ufw delete allow\
