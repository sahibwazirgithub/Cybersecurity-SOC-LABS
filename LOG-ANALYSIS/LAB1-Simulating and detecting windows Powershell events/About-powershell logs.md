# What are Windows PowerShell Logs?
PowerShell logs contain information about PowerShell script executions, including details about the commands that were run, the processes that invoked them, and the user who executed them. These logs can be used to detect potential misuse of PowerShell, including post-exploitation techniques often used by attackers.

# Key PowerShell Logs to Monitor:
Event ID 4104: Script block logging, capturing the PowerShell commands executed.\
Event ID 4103: Command invocation with parameter binding (detailed command execution).\
Event ID 4698: PowerShell Module Logging for the execution of specific modules.\
Event ID 4101: Execution of PowerShell commands through command-line arguments.


# Why Is This Important for Blue Teams?
This log can be used to detect malicious PowerShell usage, such as:

1.LOLBAS (Living Off The Land Binaries) like using Start-Process or Invoke-WebRequest\
2.Loading payloads or obfuscated PowerShell commands\
3.Persistence via PowerShell commands in startup or tasks\
Example of LOLBAS Tools These are legitimate Windows tools that attackers often abuse for stealthy malicious actions.

# 🛠️ Windows Living Off the Land Binaries (LOLBins)

| 🛠️ Tool | 📌 Path | 🚩 Abuse Technique |
| :--- | :--- | :--- |
| **powershell.exe** | `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` | Execute payloads, download malware, bypass AV |
| **certutil.exe** | `C:\Windows\System32\certutil.exe` | Download files using: `certutil -urlcache -f` |
| **mshta.exe** | `C:\Windows\System32\mshta.exe` | Execute malicious HTML apps or remote scripts |
| **regsvr32.exe** | `C:\Windows\System32\regsvr32.exe` | Load and execute remote/local DLLs |
| **rundll32.exe** | `C:\Windows\System32\rundll32.exe` | Execute DLLs or scripts to evade detection |
| **wmic.exe** | `C:\Windows\System32\wbem\wmic.exe` | Execute commands, gather system info |
| **bitsadmin.exe** | `C:\Windows\System32\bitsadmin.exe` | Download/upload files silently |
| **msbuild.exe** | `C:\Windows\Microsoft.NET\Framework\v4.0.30319\msbuild.exe` | Execute malicious C# code in project files |
| **installutil.exe** | `C:\Windows\Microsoft.NET\Framework\v4.0.30319\installutil.exe` | Run code during .NET assembly install |
| **schtasks.exe** | `C:\Windows\System32\schtasks.exe` | Create scheduled tasks for persistence |
