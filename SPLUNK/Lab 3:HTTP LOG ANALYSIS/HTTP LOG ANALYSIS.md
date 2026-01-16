## LAB GOAL:
Detecting client errors, server errors, and suspicious web activity.\
Identifying large file transfers and suspicious URI access attempts.

## LAB requirments:
SPLUNK\
Data Source: JSON-formatted Zeek-style HTTP logs.\
http_log.json (log file).

## Sucessfully uploaded http log file):
<img width="1920" height="1080" alt="Screenshot 2026-01-17 014831" src="https://github.com/user-attachments/assets/086900ad-ecf5-4d70-8acb-6f98a00ccb74" />

## Interesting fields:
1.method(GET,POST,PUT,DELETE,OPTIONS,CONNECT)\
2.status_code(200(OK),500 etc),\
3.resp_body_len.\
4.uri(path),\
5.user_agent.


## Tasks:
## 1.Find the top 10 endpoints generating web traffic:
spl query:\
source="http_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" sourcetype="_json" \
|stats count by "id.orig_h"|sort - count |head 10
<img width="1920" height="1080" alt="Screenshot 2026-01-17 015602" src="https://github.com/user-attachments/assets/dc1d51bd-d094-45b8-879b-10f649450667" />

## 2.Count the number of server errors (5xx(CODE) observed:
spl query:\
source="http_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" event_type="Server Error" |stats count as server_errors
<img width="1920" height="1080" alt="Screenshot 2026-01-17 020022" src="https://github.com/user-attachments/assets/c0e85a32-91a3-493e-b09f-af359eb62620" />

## 3. Identify User-Agents associated with possible scripted attacks:
as we know user_agents shouldn't include "sqlmap/1.5.1", "curl/7.68.0", "python-requests/2.25.1", "botnet-checker/1.0"\
spl query:\
source="http_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" user_agent IN("sqlmap/1.5.1", "curl/7.68.0", "python-requests/2.25.1", "botnet-checker/1.0")\
|stats count by user_agent
<img width="1920" height="1080" alt="Screenshot 2026-01-17 022419" src="https://github.com/user-attachments/assets/4c084c4d-cec4-4a8c-97b0-4111c2f8d7c0" />

## 4.Find large file transfers (greater than 500 KB):
source="http_logs.json" host="sahibnoor-VMware-Virtual-Platform" index="lab" resp_body_len > 500000 | table ts "id.orig_h" uri resp_body_len event_type|sort -resp_body_len
<img width="1920" height="1080" alt="Screenshot 2026-01-17 022918" src="https://github.com/user-attachments/assets/a87beb55-633e-4c82-9541-28b5ead347e6" />






