## LAB GOAL:
The objective of this lab is to  understand and analyze ICMP (Internet Control Message Protocol) packets using Wireshark.

## ICMP(Internet control message protocol):
A core protocol of Internet protocol suit.\
Operates at the network layer (layer 3) of the OSI model.\
The most common ICMP messages include Echo Request (Type 8) and Echo Reply (Type 0).

### **Key ICMP Fields:**

| Field Name       | Description                          |
|------------------|--------------------------------------|
| **Type**         | Defines the ICMP message type        |
| **Code**         | Provides further detail for the type |
| **Checksum**     | Error-checking for header            |
| **Identifier**   | Helps match requests and replies     |
| **Sequence No.** | Sequence of the request/reply        |
| **Data**         | Optional payload                     |

---

## Purpose:
ICMP is for control and diagnostic functions,not data transmission.\
It helps in sending error messages and operational information related to Ip processing.\
Essential for maintaing a healthy and manageble network.

## ICMP message types"
Echo request/Echo reply(type:8 and 0).\
Distination Unreachable(type 3).\
Time exceeded(type 11)(used by traceroute).\
redirect(type 5).\
Parameter problem(type 12).\etc

## ICMP use cases:
Traceroute.\
error reporting.\
toplology discovery.etc

## Analyzing ICMP Packets using wireshark:
filtering icmp packets using by specifying type field 8(echo request)
## icmp.type==8(echo request)
<img width="1920" height="1080" alt="Screenshot 2025-12-27 200218" src="https://github.com/user-attachments/assets/3a9ebfd3-35e8-45b4-88a5-59ec4f43298d" />

## icmp.type==0(echo reply)
<img width="1920" height="1080" alt="Screenshot 2025-12-27 200515" src="https://github.com/user-attachments/assets/94a079af-4968-4c72-bba2-f719a565fd0b" />

## icmp.type==3(destination unreachable)
<img width="1920" height="1080" alt="Screenshot 2025-12-27 200743" src="https://github.com/user-attachments/assets/0d29c1ec-8a05-4ad1-be95-a8fe7c17c610" />

Note:code = (port unreachable) issue is with port.\

## icmp(for filtering all of the icmp packets)

## Conclusion:
ICMP is a fundamental protocol for network troubleshooting.\
Wireshark helps visualize ICMP packet flow and structure.\
Understanding ICMP helps detect network scanning, ping sweeps, and unreachable hosts.
















