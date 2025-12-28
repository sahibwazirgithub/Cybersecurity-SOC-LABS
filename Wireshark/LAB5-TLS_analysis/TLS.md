## LAB GOAL:
The objective of this lab is to analyze **TLS (Transport Layer Security)** traffic using **Wireshark**.We will explore how TLS secures data over the network, understand handshake messages, and identify metadata like server names and certificate details.


## TLS(transport LAYER security):
It is a cryptographic protocol which secures data over the network.\
The Three main goals of TLS:\
Authentication.(digital certificates)\
confidentiality.(encryption)\
Integrity.(hashing)\
 It runs over **TCP**, commonly on port **443**, and is used in HTTPS, FTPS, SMTPS, etc.

 ### **Key TLS Handshake Messages:**

| Message Type          | Description                                      |
|------------------------|--------------------------------------------------|
| **Client Hello**       | Client initiates secure connection, offers cipher suites |
| **Server Hello**       | Server selects cipher and provides certificate  |
| **Certificate**        | Server provides digital certificate (X.509)     |
| **Key Exchange**       | Client and server exchange keys for session     |
| **Finished**           | Secure session begins                           |

---

##  **Most Common TLS Display Filters**

Use these filters in Wireshark’s **Display Filter** bar:

| Filter                        | Description                              |
|-------------------------------|------------------------------------------|
| `tls`                        | Show all TLS traffic                     |
| `tcp.port == 443`            | TLS over HTTPS                           |
| `tls.handshake.type == 1`    | Client Hello messages                    |
| `tls.handshake.type == 2`    | Server Hello messages                    |
| `tls.record.version == 0x0303`| TLS 1.2 traffic                         |
| `tls.record.version == 0x0304`| TLS 1.3 traffic                         |

---

## 📸 Submission
Submit a screenshot showing:
- Show all TLS traffic
- <img width="1920" height="1080" alt="Screenshot 2025-12-28 201613" src="https://github.com/user-attachments/assets/0d3949e7-8b0d-471a-aad8-26877fc9ec57" />

- Show Client Hello messages
- <img width="1920" height="1080" alt="Screenshot 2025-12-28 201726" src="https://github.com/user-attachments/assets/d0a0a620-4e57-4f5e-bf7a-c73e5624f4ce" />

- Show TLS 1.2 traffic
<img width="1920" height="1080" alt="Screenshot 2025-12-28 201837" src="https://github.com/user-attachments/assets/8ae2a90f-fdbe-435f-8b2e-8047c59a8f9f" />

   





## Conclusion
- TLS secures communication using encryption, making traffic unreadable without keys.
- Wireshark can't decrypt TLS by default but can reveal:
 - Server name (SNI)
 - Certificate chain
 - TLS versions and cipher suites

- Analyzing TLS metadata helps detect:
 - Outdated TLS versions (e.g., TLS 1.0)
 - Suspicious or self-signed certificates
 - Malicious domain encryption abuse
