## LAB GOAL:
The objective of this lab is to analyze HTTP (Hypertext Transfer Protocol) packets using Wireshark. We will explore HTTP request/response headers, understand how web communication works.

## HTTP(hypertext transfer protocol):
Application Layer Protocol.\
It serves as the foundation for data communication on the World Wide Web,allowing browser to request information like a webpage from a server.\
It typically runs over TCP port 80.

### **Key HTTP Fields:**

| Field Name         | Description                              |
|--------------------|------------------------------------------|
| **Request Method** | GET, POST, HEAD, etc.                    |
| **Host**           | The website being accessed               |
| **User-Agent**     | Information about the client/browser     |
| **URI**            | Resource path on the server              |
| **Status Code**    | Server's response status (e.g., 200 OK)  |
| **Content-Type**   | MIME type of the response (e.g., text/html) |
| **Cookie/Header**  | Session or tracking information          |

---

##  **Most Common HTTP Display Filters**

Use these filters in Wireshark’s **Display Filter** bar:

| Filter                    | Description                              |
|---------------------------|------------------------------------------|
| `http`                   | Show all HTTP traffic                    |
| `tcp.port == 80`         | HTTP traffic by default port             |
| `http.request.method == "GET"` | Show all GET requests             |
| `http.request.uri`       | View requested resources                 |
| `http.set_cookie`        | Show cookies in HTTP responses           |
| `ip.addr == 192.168.1.10`| HTTP traffic to/from specific host       |

---

## Conclusion
- HTTP traffic is readable and easy to analyze in Wireshark.
- Analyzing HTTP helps detect:
 - Sensitive data exposure in URLs or headers
 - Malware beaconing to C2 servers
 - Suspicious file downloads or unauthorized access

##  Submission
 screenshot showing:
- Show all HTTP traffic
  <img width="1920" height="1080" alt="Screenshot 2025-12-28 194403" src="https://github.com/user-attachments/assets/97882e4c-f543-47bd-86c5-156aea1ae8e7" />

- Show all GET requests
  <img width="1920" height="1080" alt="Screenshot 2025-12-28 194547" src="https://github.com/user-attachments/assets/06a4a696-d9ad-4a8f-844f-082f41ed544b" />

- View requested resources
- <img width="1920" height="1080" alt="Screenshot 2025-12-28 194741" src="https://github.com/user-attachments/assets/73ae92e4-c7f0-48bd-b618-93ac99f2bd51" />






