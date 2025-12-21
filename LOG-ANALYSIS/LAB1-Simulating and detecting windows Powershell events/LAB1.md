# lab goal:
        simulating and detecting windows Powershell events
# preparation:
        For this lab, you will need to set up log collection on  Windows:

1.Open Group Policy Editor (gpedit.msc):
i.Navigate to Computer Configuration > Administrative Templates > Windows Components > Windows PowerShell.
<img width="1919" height="1079" alt="Screenshot 2025-12-21 143331" src="https://github.com/user-attachments/assets/cef86754-031d-48bb-9994-f03179f64560" />

ii.Ensure that Module Logging, Script Block Logging, and Script Execution are enabled.
<img width="1919" height="1079" alt="Screenshot 2025-12-21 143715" src="https://github.com/user-attachments/assets/34def886-2345-4fd8-b520-d790056b509b" />

# Executing powershell command and finding this specific event
2.Open Event Viewer:
  Go to Applications and Services Logs → Microsoft → Windows → PowerShell → Operational.
  <img width="1920" height="1032" alt="Screenshot 2025-12-21 144214" src="https://github.com/user-attachments/assets/024bf41a-0d34-4933-bee1-544c3d55ff14" />
3.Open windows powershell and executing the getlocal command:
  <img width="979" height="512" alt="Screenshot 2025-12-21 144802" src="https://github.com/user-attachments/assets/b4f44029-7b62-47c1-8b6d-d0b44faeb021" />
4.Filtering event 4104(using action filter current log) in event Viewer:
<img width="1920" height="1032" alt="Screenshot 2025-12-21 145004" src="https://github.com/user-attachments/assets/ce466750-9916-4d4d-b1ba-9d3e97585a03" />
5.clicking on the secound event in the filtered list and seeing details:
<img width="1920" height="1032" alt="Screenshot 2025-12-21 145248" src="https://github.com/user-attachments/assets/460e479b-df75-48b2-88be-898aa7679c3c" />

# Conclusion:
in order for us to detect windows Powershell events we needed some basic options to be enabled such as:Module logging,Script Block Logging,and Script Execution.
after that we needed to simulate the scenario and test our detection by simulating the powershell event (executing command) and detecting the event(4104) in the Event viewer



