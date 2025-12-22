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


Code,Name,Commonality
0,System,"Used by the OS itself at startup. You'll see this often, but it's rarely an ""attack."""
1,(None),Missing / Deprecated.
2,Interactive,Standard local keyboard login.
3,Network,Accessing files/printers over the network.
4,Batch Job,"Scheduled tasks (e.g., automated backups)."
5,Service,A system service starting up.
6,(None),Missing / Reserved.
7,Unlock,Entering a password to a screen that was already locked.
8,NetworkCleartext,Unencrypted network login (High Risk!).
9,NewCredentials,Using the RunAs command.
10,RemoteInteractive,RDP (Remote Desktop).
11,CachedInteractive,Logging in while offline (laptops).
