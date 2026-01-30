## GOAL:
Setting up Wazuh EDR.

## Requirements
System 1: Ubuntu 22.04/20.04 (Wazuh Server)\
System 2: Ubuntu 22.04/20.04 (Agent Machine to be monitored)\
Minimum Hardware for Wazuh Server:\
CPU: 4 vCPUs\
RAM: 8GB+\
Storage: 50GB+\
Network Connectivity: Ensure both systems can communicate over the network.\
User Permissions: Root or sudo privileges on both machines.

## Step 1: Install Wazuh Server Using Quick Start:
1.Download and run the Wazuh installation assistant.\
curl -sO https://packages.wazuh.com/4.10/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

2.Accessing Wazuh web interface with https://<WAZUH_DASHBOARD_IP_ADDRESS> and specified credentials:

## Step 2: Onboard an Ubuntu Machine as a Wazuh Agent:
1.Install the Wazuh Agent on the Ubuntu machine to be monitored:
curl -sO https://packages.wazuh.com/4.7/wazuh-agent-linux.sh && sudo bash wazuh-agent-linux.sh

