## LAB GOAL:
upload and search Zeek connection logs in Splunk.\
Finding top clients, top servers, and most common services.\
Identifying large traffic and long connections.

## LAB SETUP:
SPLUNK.\
Data Source: JSON-formatted Zeek-style connection logs.\
zeek_conn_logs.json (LOG FILE TO BE UPLOADED TO SPLUNK.

## LOG FILE UPDOAD:
<img width="1920" height="1080" alt="Screenshot 2026-01-17 222211" src="https://github.com/user-attachments/assets/2311207c-dcdf-444b-94c3-6840f8a547f0" />

## Interesting Fields:
1.service(used services eg:SMTP,DNS,HTTP,FTP and more).
2.id.host_h(originator host)\
3.id.resp_h(responder host).


## LAB TASKS:
## 1.Find the Top 10 Client IPs (id.orig_h):
spl query:\
source="zeek_conn_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" sourcetype="_json" | stats count by "id.orig_h" |sort - count | head 10
<img width="1920" height="1080" alt="Screenshot 2026-01-17 222818" src="https://github.com/user-attachments/assets/bb5b4848-c4ef-48af-b130-ebc095c06f37" />


## 2.List Most Common Services:
spl query:\
source="zeek_conn_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" sourcetype="_json" |stats count by service |sort - count
<img width="1920" height="1080" alt="Screenshot 2026-01-17 223057" src="https://github.com/user-attachments/assets/3ca0e321-192d-42ec-a6e7-44457a3c70de" />

## 3.Find Connections with Duration > 1 Second:
spl query:\
source="zeek_conn_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" sourcetype="_json" duration>1 | table ts "id.orig_h" "id.resp_h" service duration | sort - duration
<img width="1920" height="1080" alt="Screenshot 2026-01-17 223637" src="https://github.com/user-attachments/assets/afd0c33b-df78-4976-bc48-7e1ab1a7e91d" />

## 4. Identify the Most Accessed Internal Servers:
source="zeek_conn_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" sourcetype="_json" |stats count by "id.resp_h"|sort - count |head 10
<img width="1920" height="1080" alt="Screenshot 2026-01-17 223917" src="https://github.com/user-attachments/assets/97667755-fcfc-4071-8744-655af6eb163c" />

