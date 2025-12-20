# lab goal:
        simulating and detecting windows Powershell events
# preparation:
        For this lab, you will need to set up log collection on  Windows:

1.Open Group Policy Editor (gpedit.msc):
i.Navigate to Computer Configuration > Administrative Templates > Windows Components > Windows PowerShell.
ii.Ensure that Module Logging, Script Block Logging, and Script Execution are enabled.

2.Open Event Viewer:
  Go to Applications and Services Logs → Microsoft → Windows → PowerShell → Operational.
