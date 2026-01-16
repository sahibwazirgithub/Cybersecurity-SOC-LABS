## LAB GOAL:
1.Learning how to ingest and analyze DNS logs in Splunk.\
2.understanding how to extract useful informatino such as DNS query types,source hosts and common destination ports.\
3.Practice building basic SPL(search processing Language) to investigate DNS activity.

## LAB SETUP:
SPLUNK.\
data source:json formated zeek dns logs.\
log file.(dns_logs.json).

## UPLOAD DNS FILE TO SPLUNK WEB:
1.goto splunk web-->settings>appdata (completed the process such as source type,index etc).
<img width="1920" height="1080" alt="Screenshot 2026-01-16 174356" src="https://github.com/user-attachments/assets/d55689f4-c24e-45a4-ba1d-6aeed27e122b" />

## SPL(Search processing LANGUAGE BASICS):
1.Index="*"\
   filters and outputs all the logs.\
2.filtering by source,host,sourcetype:\
eg.\
source="dns_logs.json"\
sourcetype="_json"\
host="Ubunto-s"\

## INTERESTING FIELDS:
1.query(all about domains such as google.com,yahoo.com etc)\
2.id.orin-h(origin host)\
3.id.resp-h(responder host)\
4.qtype(query type):AAAA,A,PTR,CNAME.

## LAB TASKS:
using spl queries to answer the following questions:

## 1.Identify the most quered domain names:
source="dns_logs.json"\
|stats count by query|sort -count
<img width="1920" height="1080" alt="Screenshot 2026-01-16 183535" src="https://github.com/user-attachments/assets/505c1131-62f0-4951-837c-a210188cfb17" />

## 2.Find the most active user IPs generating DNS traffic:
sourcetype="_json" source="dns_logs.json"|stats count by "id.orig-h"|sort -count
<img width="1920" height="1080" alt="Screenshot 2026-01-16 183927" src="https://github.com/user-attachments/assets/c1d4529e-42c4-4019-810a-def95aaa0d26" />

## 3.Breakdown of DNS query types:
source="dns_logs.json"|stats count by qtype
<img width="1920" height="1080" alt="Screenshot 2026-01-16 184041" src="https://github.com/user-attachments/assets/86c8afe4-f021-4d40-8431-198940611052" />



  
