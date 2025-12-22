# What are Windows Security Logs?
Windows Security Logs contain records of security-related events on the system, such as:

1.Successful and Failed Login Attempts: Track users who log in or fail to log in.\
2.Account Lockouts: Occurs when a user exceeds the maximum allowed number of incorrect login attempts.\
3.Audit Policies: Logs related to changes in system audit settings and configurations.\
4.Group Membership Changes: Tracks changes in group memberships and user privileges.\
5.Privilege Escalation: Logs events when a user gains elevated privileges.

These logs are valuable for monitoring security incidents, detecting unauthorized access, and auditing system changes.


# Understanding Event IDs in Security Logs:
Some common Event IDs in Windows Security Logs that you will encounter include:

1.Event ID 4624: Successful Logon.\
2.Event ID 4625: Failed Logon.\
3.Event ID 4740: Account Lockout.\
4.Event ID 4732: A user was added to a security-enabled local group.\
5.Event ID 4672: Special privileges assigned to a new logon (Privilege escalation).


# 🔍 Reference: Windows Logon Types (Event ID 4624/4625)

In Windows Security auditing, the **Logon Type** field within Event IDs 4624 (Success) and 4625 (Failure) is a critical indicator of how a user or process accessed the system. This guide serves as a quick reference for SOC Analysts to identify the method of entry.

##  Core Logon Types (High Priority)

| Type | Name | Description | Analyst Perspective |
| :--- | :--- | :--- | :--- |
| **2** | **Interactive** | Local logon via physical keyboard and monitor. | Normal for workstations; suspicious on servers/domain controllers during off-hours. |
| **3** | **Network** | Connection via network (e.g., shared folders, printers, IIS). | High volume is normal, but this is the primary method for **Lateral Movement**. |
| **10** | **RemoteInteractive** | Connection via **Remote Desktop (RDP)**. | **Highest Risk.** Failures (4625) from unknown IPs often indicate Brute Force or Password Spraying. |

## System & Automation Types

| Type | Name | Description | Analyst Perspective |
| :--- | :--- | :--- | :--- |
| **0** | **System** | Used by the Operating System during startup. | Common at boot time. Not typically an indicator of threat actor activity. |
| **4** | **Batch** | Executed by a scheduled task. | Investigate new Type 4 logons to detect **Persistence** mechanisms left by attackers. |
| **5** | **Service** | Executed by a background system service. | Failures usually indicate a misconfigured service account or expired password. |
| **7** | **Unlock** | User provided credentials to an already-locked workstation. | Failures may indicate an "Insider Threat" attempting to guess a logged-in user's password. |

## Advanced & Special Types

* **Type 8 (NetworkCleartext):** A network login where the password was sent unencrypted. **Note:** This is high risk as credentials can be sniffed in transit.
* **Type 9 (NewCredentials):** Occurs when using `RunAs` with the `/netonly` switch. Often used by admins or attackers to map drives using different credentials.
* **Type 11 (CachedInteractive):** User logged in with saved credentials because the Domain Controller was unreachable (common for remote laptop users).
* **Type 12/13 (Cached Remote/Unlock):** Similar to Type 11 but for RDP or Unlocks in an offline state.

---

> **Note on Missing Types:** > - **Type 1:** Deprecated (used in older Windows NT versions).
> - **Type 6:** Reserved/Deprecated.
> *These will not appear in modern Windows Server or Windows 10/11 logs.*
