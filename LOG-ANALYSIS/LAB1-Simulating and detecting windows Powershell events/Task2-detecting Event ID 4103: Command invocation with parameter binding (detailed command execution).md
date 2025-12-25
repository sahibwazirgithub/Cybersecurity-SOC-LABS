# Lab goal:
 Detecting Command invocation with parameter binding from event viewer.

# Requirements:
System: Windows 10/11 or Windows Server 2019/2022\
Tools:
Windows Event Viewer (pre-installed)\
PowerShell (Pre-installed on Windows)\
Administrative Privileges (required for enabling logs)

# Preparation:
Before proceeding, make sure PowerShell script block logging is enabled on your system:

1.Press Win + R, type gpedit.msc, and press Enter to open the Group Policy Editor.\
2.Navigate to: Computer Configuration > Administrative Templates > Windows Components > Windows PowerShell\
3.Turn on Module Logging, Script Block Logging, and Script Execution.\
4.Apply the settings and close the Group Policy Editor.
<img width="1920" height="1040" alt="Screenshot 2025-12-25 175009" src="https://github.com/user-attachments/assets/50156b00-dd6b-457e-86ce-01c280196505" />

# Key PowerShell Log to Monitor:
 Event ID 4103: Command invocation with parameter binding (detailed command execution)

# Step 1:(executing the command which will generate log entry):
Run the following PowerShell command to generate a log entry:\
Start-Process "notepad.exe" -ArgumentList "C:\Windows\System32\drivers\etc\hosts"\

About the  command:
1.Starts a new process using the Start-Process cmdlet.\
2.Specifies "notepad.exe" as the program to launch.\
3.Passes "C:\Windows\System32\drivers\etc\hosts" as an argument to Notepad.\
4.As a result, Notepad opens the hosts file directly.
<img width="1920" height="1040" alt="Screenshot 2025-12-25 175253" src="https://github.com/user-attachments/assets/49b36238-490b-490f-a102-fb547a2c5336" />

# Step 2:(detecting the event 4103 in the event viewer):
goto:Applications and Services Logs → Microsoft → Windows → PowerShell → Operational\
filter 4103 event.\
find info like: \
PowerShell command that was executed\
User who ran the command\
Timestamp of the execution\
<img width="1920" height="1040" alt="Screenshot 2025-12-25 175930" src="https://github.com/user-attachments/assets/e53bc573-7d2e-4147-9ee0-7ec14b316ac3" />

 

 

