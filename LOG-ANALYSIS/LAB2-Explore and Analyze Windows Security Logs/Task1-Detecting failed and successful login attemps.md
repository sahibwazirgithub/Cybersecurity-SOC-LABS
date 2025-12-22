# Our machine:installed on vmware(virtual machine)
System: Windows Server 2022
<img width="1920" height="1040" alt="Screenshot 2025-12-22 220705" src="https://github.com/user-attachments/assets/efdbb3d6-9831-4adb-9272-bbdc6d895334" />

# Lab Goal:
  simulating failed login attempt and detecting it through event viewer in our Windows Server 2022


# Step#1(simulating failed login attempt):
1.create a test user "dummy1" on our windows server.
<img width="1920" height="1040" alt="Screenshot 2025-12-22 221336" src="https://github.com/user-attachments/assets/749e59ba-64c8-4457-ab15-a5313d8812bd" />

2.we will simulate failed login attempt using powershell command(specifying wrong password) on our windows server:\
COMMAND:net use \\127.0.0.1\IPC$ /user:dummy1 wrong123(trying severel failed login attempts by executing this command multiple times with slight  passwords  variation)
<img width="1920" height="1040" alt="Screenshot 2025-12-22 221625" src="https://github.com/user-attachments/assets/9f43c2b6-a48f-48e1-ad0e-7e7f264a5765" />

## Step 2: Detect the Log in Windows Event Viewer:
1.In the Event Viewer, navigate to:\
Windows Logs → Security\
2.After the failed login, go back to Event Viewer.\
3.Filter the Security Logs for Event ID 4625 (Failed Logon).
<img width="1920" height="1040" alt="Screenshot 2025-12-22 222001" src="https://github.com/user-attachments/assets/a732373a-5709-42b0-bd0f-79e91a9d02f1" />

4.Look for entries that correspond to the failed login attempt.
<img width="1920" height="1040" alt="Screenshot 2025-12-22 222244" src="https://github.com/user-attachments/assets/09e96086-0d61-4f98-ac6f-384fb25ad405" />






