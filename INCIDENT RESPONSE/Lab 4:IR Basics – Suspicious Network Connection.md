### LAB GOAL:
Investigate and respond to a suspicious outbound network connection from a Linux machine. This simulates beaconing behavior or data exfiltration.\ 
Will learn to inspect open connections, trace source processes, and mitigate threats.

## Why It Matters
Attackers often use hidden outbound connections to communicate with command-and-control (C2) servers. Detecting and cutting off these connections is essential for SOC and IR teams.

## ⚠️ Scenario: Unexpected Outbound Connection Detected:
A Linux system shows an active connection to an unknown IP 45.13.220.98:443, not related to any known services.

## Lab Setup
System Requirements\
Ubuntu/Kali Linux system\
Internet access\
Tools: curl, netstat or ss, lsof

### **Simulate Suspicious Connection**

nohup bash -c 'while true; do curl http://45.13.220.98/ping >/dev/null 2>&1; sleep 30; done' &
<img width="1919" height="680" alt="Screenshot 2026-01-15 194710" src="https://github.com/user-attachments/assets/d71efa38-3d0d-44bd-b58f-09aa775b5e68" />



🧪Step-by-Step Investigation
### Step 1: Detect Active Network Connections

netstat -plant
# or
ss -plant

Look for a suspicious IP such as 45.13.220.98:443.

Here 
-p	Show the PID and program name of the connection
-l	Show only listening sockets
-a	Show all connections and listening ports
-n	Show numeric addresses (don’t resolve hostnames or port names)
-t	Show only TCP connections
<img width="1914" height="1077" alt="Screenshot 2026-01-15 195044" src="https://github.com/user-attachments/assets/e40764bf-3d8b-4b38-b5a1-6f78d853787d" />


### Step 2: Identify the Responsible Process
Get the PID from netstat or ss output

Investigate:
ps aux | grep 45.13.220.98
<img width="1920" height="1080" alt="Screenshot 2026-01-15 195246" src="https://github.com/user-attachments/assets/ef97aecc-4f14-4811-9ab3-4790a1353bcd" />



### Step 3: Containment & Eradication
- Kill the process:


kill <PID>
# or
pkill curl
<img width="1920" height="1080" alt="Screenshot 2026-01-15 195601" src="https://github.com/user-attachments/assets/3f2c8e6a-ea09-4c44-b685-ee45bccac7c6" />

- Block the IP using UFW:


ufw deny out to 45.13.220.98
<img width="1920" height="1080" alt="Screenshot 2026-01-15 200003" src="https://github.com/user-attachments/assets/e000c1e2-0da6-4e1d-9e2c-c623ef1ff00f" />

### Step 4: Post-Incident Activity
Document:
- What process initiated the connection?
- Remote IP and port?
- Binary path used?

Recommendations:
- Implement egress filtering
- Deploy IDS/IPS solutions
- Monitor outbound connections and unusual traffic
