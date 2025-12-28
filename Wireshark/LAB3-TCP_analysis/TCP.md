## LAB GOAL:
The objective of this lab is  analyzing of TCP (Transmission Control Protocol) traffic using Wireshark.

### TCP (Transmission Control Protocol):
TCP is LAYER 4 (Transport) protocol of OSI model.\
It makes sure that the communication is socket to socket(IP+PORT).\
TCP is connection oriented protocols means before transmitting data connection should be established using 3-way handshake.\
TCP is for reliable communication(gaurenteed delivery).

### **Key TCP Fields:**

| Field Name         | Description                                  |
|--------------------|----------------------------------------------|
| **Source Port**     | Sender’s port number                         |
| **Destination Port**| Receiver’s port number                       |
| **Sequence Number** | Number of the first byte in the segment      |
| **Acknowledgment No** | Confirms received data                    |
| **Flags**           | Control bits (SYN, ACK, FIN, RST, PSH, URG) |
| **Window Size**     | Buffer size available                        |
| **Checksum**        | Error-checking field                         |

---

## **Most Common TCP Display Filters**

Use these filters in Wireshark’s **Display Filter** bar:

| Filter                  | Description                              |
|--------------------------|------------------------------------------|
| `tcp`                   | Show all TCP packets                     |
| `tcp.flags.syn == 1`    | Show SYN packets (start of connection)   |
| `tcp.flags.fin == 1`    | Show FIN packets (end of connection)     |
| `tcp.port == 80`        | Show TCP packets on port 80              |
| `ip.addr == 192.168.1.1`| TCP traffic to/from a specific host      |

## Submission
Submit a screenshot showing:
- Show all TCP packets
<img width="1920" height="1080" alt="Screenshot 2025-12-28 190501" src="https://github.com/user-attachments/assets/25ffc6b9-5d5c-4cc8-b2ff-96a05d984fe0" />

-Show SYN packets (start of connection)
<img width="1920" height="1080" alt="Screenshot 2025-12-28 190754" src="https://github.com/user-attachments/assets/139215af-2a01-464e-9a63-3b9b9640d921" />


- Show FIN packets (end of connection)
  <img width="1920" height="1080" alt="Screenshot 2025-12-28 190904" src="https://github.com/user-attachments/assets/40932e46-17ae-4e72-bdb0-82cb3098e27e" />

- TCP traffic to/from a specific host
- <img width="1920" height="1080" alt="Screenshot 2025-12-28 191118" src="https://github.com/user-attachments/assets/d2375a17-7753-4665-8ede-74bff2a1cf6f" />
