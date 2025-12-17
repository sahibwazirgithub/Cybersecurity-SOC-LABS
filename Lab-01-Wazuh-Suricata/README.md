Lab 1: Integrated SIEM/NIDS Defense Wazuh + Suricata.

------Project Overview------
The goal of this lab was to build a functional, end-to-end Security Operations Center (SOC) monitoring environment. By integrating Wazuh (SIEM) and Suricata (NIDS), I achieved real-time alert correlation and network-level threat detection mapped to the MITRE ATT&CK Framework.

--Network Architecture & Schema--
To ensure secure log transport and monitoring, the following environment was established:
Component	        Operating System	        IP Address
Wazuh Manager	    Ubuntu/Wazuh Indexer	    192.168.100.
Suricata Sensor	  Kali Linux	              192.168.100.
Endpoint	        Windows 7 (64-bit)	      192.168.100.
Host PC	          Windows	                  192.168.100.


----Implementation Steps-----

->Phase 1: Agent Setup
Installed and verified Wazuh Agents on both Kali Linux and Windows 7.
Confirmed active communication between agents and the Wazuh Manager dashboard.

->Phase 2: Suricata Installation & Ruleset
Configured Suricata on the Kali Linux machine to act as a network sensor.
Downloaded and installed the Emerging Threats (ET) Ruleset for up-to-date vulnerability detection.
**Key Configuration Changes (suricata.yaml):
    Set af-packet to the correct network interface.
    Defined default-rule-path to /etc/suricata/rules.
    Configured the outputs section to generate eve.json logs for SIEM ingestion.


->Phase 3: Wazuh Integration (The "Bridge")
To allow Wazuh to "see" network threats detected by Suricata, I modified the Wazuh agent configuration on the Kali machine:
File Edited: /var/ossec/etc/ossec.conf
**Configuration Added:
XML
<localfile>
<log_format>json</log_format>
 <location>/var/lib/suricata/eve.json</location>
</localfile>
This tells the Wazuh agent to monitor Suricata’s output and send it to the Manager for analysis.



