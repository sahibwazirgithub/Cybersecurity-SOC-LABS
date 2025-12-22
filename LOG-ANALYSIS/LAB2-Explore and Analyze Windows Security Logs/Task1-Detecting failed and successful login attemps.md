# Our machine:
System: Windows Server 2022

# Lab Goal:
  simulating failed and successful login attempt and detecting it through event viewer in our Windows Server 2022


# Step#1(simulating failed and successful login attempt at the same time):
1.create a test user "dummy1" on our windows server.

2.we will simulate login attempt using powershell command on our windows server:\
COMMAND:net use \\127.0.0.1\IPC$ /user:haxuser1 WrongPassword

