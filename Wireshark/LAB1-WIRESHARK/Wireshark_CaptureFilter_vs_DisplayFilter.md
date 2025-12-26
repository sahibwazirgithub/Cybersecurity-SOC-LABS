## CAPTURE FILTER VS DISPLAY FILTER

# Capture filter:
capture filter is basically used to capturing packets by reducing the ammount of packets or filtering specific type of traffic to capture in the first place.\
It makes the analysis very focused.\
captures the packet live(while filtering)
<img width="1920" height="1080" alt="Screenshot 2025-12-26 174251" src="https://github.com/user-attachments/assets/076c010e-7775-49e4-a6bb-d37c7bd30d4a" />

## EXAMPLE:
---want to capture data packets only related to host address 192.168.100.6 using interface eth0---------
<img width="1920" height="1080" alt="Screenshot 2025-12-26 175020" src="https://github.com/user-attachments/assets/6bf2daba-4716-4fe5-b0d8-b84c585d1924" />

---result----
we can see that each packet includes ip 192.168.100.6 either src or destination\
<img width="1920" height="1080" alt="Screenshot 2025-12-26 175214" src="https://github.com/user-attachments/assets/15d9d5d1-5cd0-40dc-a832-b355fa5c3d36" />


# Display filter:
This filter can be used for analysis of packets without interferring in the original capture data.\
Applied on the already captured packets (meaning we just want to look the area of our interest).
<img width="1920" height="1080" alt="Screenshot 2025-12-26 175615" src="https://github.com/user-attachments/assets/f7f3a573-7be1-4daf-a358-a133e9a5c575" />


