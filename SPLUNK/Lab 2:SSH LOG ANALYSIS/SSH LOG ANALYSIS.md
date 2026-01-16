## LAB GOAL:
Ingesting and analyzing SSH logs using Splunk.\
Detect failed and successful SSH authentication attempts.\
Identify unusual SSH activity that may indicate brute force or unauthorized access.

## LAB requirments:
Splunk\
Data Source: JSON-formatted Zeek-style SSH logs.\
Log File(ssh-log-file).

NOTE:the log file being used is generated from zeek IDS.
## UPLOADING PROCESS OF ssh_log.json file to Splunk:
<img width="1920" height="1080" alt="Screenshot 2026-01-17 005111" src="https://github.com/user-attachments/assets/96e63fd6-bc1a-48e6-b8db-3bc9cac7c991" />

## Interesting fields in SSH LOG:
1. id.orig_h(the ip address of the device that **started the connection**.\
2. id.resp_h(the ip address of the device that responded to the initial request.\
3. id.resp_p(responeder port which is 22 (ssh)in this case).\
4. event_type(type of event happend eg.successfull SSH login)\
5. auth_attempts(total number of authentication process happend)\
6. auth_sucess(false,true,null).



## Lab Tasks
## 1.List the top 10 endpoints with failed SSH login attempts:
 spl query: source="ssh_log.json" auth_success=false|stats count by "id.orig_h"\
 |sort -count | HEAD 10
 <img width="1920" height="1080" alt="Screenshot 2026-01-17 012433" src="https://github.com/user-attachments/assets/9e2e3586-ca1a-4e28-9b64-898903451d43" />

## 2.Find the number of total SSH connections:
source="ssh_logs.json" |stats count as total_ssh_connections\
NOTE: as (keyword ) will create a new field total_ssh_connections
<img width="1920" height="1080" alt="Screenshot 2026-01-17 013343" src="https://github.com/user-attachments/assets/1192cc77-bab8-4c92-b56d-e5ff10c88f1a" />


## 3.Count all event types (successful, failed, no-auth, multiple-failed) seen in the logs:
 source="ssh_logs.json" |stats count by event_type.
 <img width="1920" height="1080" alt="Screenshot 2026-01-17 013542" src="https://github.com/user-attachments/assets/648627be-2d49-4389-b1b1-82ffd306e09e" />


