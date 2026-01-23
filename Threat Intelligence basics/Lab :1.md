## LAB GOAL:
  The objective of this lab is to learn how to extract Indicators of Compromise (IOCs) from a suspicious email 
  and use threat intelligence tools to investigate their context and maliciousness.
  
## What is Threat Intelligence?
Threat Intelligence (TI) is information about threats, threat actors, and their tactics.\
It helps SOC analysts investigate alerts faster, make informed decisions, and respond to incidents more effectively.

## Types of Threat Intelligence:
Tactical: 
  IOCs like IPs, hashes, domains\
Operational:
  Info about campaigns, malware families\
Strategic:
  Big-picture trends, threat groups, geopolitical context\

## LAB SCENARIO:
 While triaging a phishing alert, We discovered three suspicious indicators:

IP Address: 18.188.148.80\
Domain: aaronthompson.ug\
File Hash(SHA256): d45a079c59c2860f9cf4578a8fc9f5fe8009cff8aaa83c572474d6bfe15ba95b\

## Lab Setup:
Download Email Sample: sample-1.eml\
Tools I Will Use:
VirusTotal\
AbuseIPDB\
URLScan.io\
AlienVault OTX\
ThreatFox\
MXToolbox Header Analyzer

## Tasks
What is the type of the malicious file?\
flv.exe-source-code.7z(it is a 7zip file)

What country is this IP registered in?
US
<img width="1920" height="1080" alt="Screenshot 2026-01-23 171744" src="https://github.com/user-attachments/assets/5b9aba7c-bf83-4bf9-bdb4-95874372aa79" />

What malware name (if any) is associated with this file on VirusTotal?
trojan.badjoke/abobus
<img width="1920" height="1080" alt="Screenshot 2026-01-23 172056" src="https://github.com/user-attachments/assets/197becb1-77b3-406e-98b5-e68afce23027" />
