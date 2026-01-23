## LAB GOAL:
The goal  is to analyze an email sample using manual investigation techniques.\
Will learn how to review email headers, validate the sender's identity, check domain/IP reputation, and extract indicators of compromise (IOCs).

## LAB SETUP:
1.sample email for this scenario(.eml)\
TOOLS RECOMMENDED:
MX Toolbox Email Header Analyzer\
EML Analyzer\
IP reputation check (e.g., VirusTotal, AbuseIPDB, Cisco Talos)\
Whois lookup (e.g., whois.domaintools.com)\
URL and Domain analysis (e.g., urlscan.io, VirusTotal)

## SCENARIO:
I received an email from BANCO DO BRADESCO LIVELO claiming that my card has 92,990 points expiring today, sent from banco.bradesco@atendimento.com.br.

## Questions:
## USING EML ANALYZER BY UPLOADING THE SUSPICIOUS .eml file :
 <img width="1920" height="1080" alt="Screenshot 2026-01-23 164924" src="https://github.com/user-attachments/assets/11075331-c1ae-4c42-a67e-b0d607eb1dd2" />

1.What is the **full email address of the sender**?\
 banco.bradesco@atendimento.com.br\
2.What **domain is used** to send this email? (Check Return-Path or From)\
 @atendimento.com.br
3.What is the **sender’s IP address** from the header?
 137.184.34.4\
4.Is the sender IP blacklisted? (Check using AbuseIPDB or VirusTotal – Answer Yes/No)\
<img width="1920" height="1080" alt="Screenshot 2026-01-23 165041" src="https://github.com/user-attachments/assets/14448b6e-ea68-4cfd-9be7-34431bbbc8f5" />
5.What is the **result of SPF(sender policy framework) authentication**? (Pass / Fail / Neutral)\
 spf=temperror (sender IP is 137.184.34.4) smtp.mailfrom=ubuntu-s-1vcpu-1gb-35gb-intel-sfo3-06; dkim=none (message not signed) header.d=none;dmarc=temperror action=none header.from=atendimento.com.br;compauth=fail reason=001\
 (can be found by EML analyzer)
6.What is one **suspicious URL or link** found in the email body?
<img width="1920" height="1080" alt="Screenshot 2026-01-23 165415" src="https://github.com/user-attachments/assets/4a4440c2-6e01-4cae-a8d8-798453bfbd76" />
<img width="1920" height="1080" alt="Screenshot 2026-01-23 165608" src="https://github.com/user-attachments/assets/46973644-479c-4ecd-acb7-6628c297afee" />

