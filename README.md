# Basic Home Lab (w/ Sysmon, Splunk)

## Table of Contents
- [Purpose](#purpose)
- [Utilities Used](#utilities-used)
- [Project Walkthrough](#project-walkthrough)
- [Findings](#findings)
- [Conclusion](#conclusion)

## Purpose
To set up a home lab and use it to safely create and investigate a basic malware and learn how to use the Splunk SIEM tool.

## Utilities Used
   
**Windows 10 Virtual Machine** - the target machine to test malware on. This VM was run using Virtual Box, it provides a sandbox environment to prevent malware from affecting the host machine.
- Windows 10 was chosen since it is a popular operating system used by many.
   
**Kali Linux Virtual Machine** - the attacking machine which creates the malware. It was also ran using Virtual Box.
- Kali Linux was chosen since it comes with the Metasploit Framework preinstalled.
- The Metasploit Framework is a tool used to perform authorised penetration tests to understand and improve system security.

**Sysmon** - a Windows tool used to record system activity. This is to investigate the activity of the attacking machine on the target machine.

**Splunk** - a SIEM tool used to analyse data and monitor system security. It will recieve the events collected by Sysmon to be indexed and analysed.
- Additionally, Splunk also has dashboards and alerts to quickly identify threats.

## Project Walkthrough

<p align="center">Step 1: Windows 10 VM setup</p>
<p align="center"> <img src="images/imagestep1.png" height="80%" width="80%"/> </p>

<p align="center">Step 2: Kali VM setup</p>
<p align="center"> <img src="images/imagestep2.png" height="80%" width="80%"/> </p>

<p align="center">Step 3: connect to the internet through NAT (reduce the risk of malware)</p>
<p align="center"> <img src="images/imagestep3.png" height="80%" width="80%"/> </p>
<p align="center">*NAT allows a VM to access the internet by sharing the host computer's network connection while keeping the VM hidden from the external network</p>

<p align="center">Step 4: Install Sysmon</p>
<p align="center"> <img src="images/imagestep4.png" height="80%" width="80%"/> </p>

<p align="center">Step 5: Restart Sysmon64 in Services to ensure it is working</p>
<p align="center"> <img src="images/imagestep5.png" height="80%" width="80%"/> </p>

<p align="center">Step 6: Install Splunk</p>
<p align="center"> <img src="images/imagestep6.png" height="80%" width="80%"/> </p>

<p align="center">Step 7: Create an account and log into it</p>
<p align="center"> <img src="images/imagestep7.png" height="80%" width="80%"/> </p>

<p align="center">Step 8: Head to Search & Reporting to test out Splunk's functionality</p>
<p align="center"> <img src="images/imagestep8.png" height="80%" width="80%"/> </p>

<p align="center">Step 9: Create an endpoint index in C:\Program Files\Splunk\etc\system\local\inputs.conf</p>
<p align="center"> <img src="images/imagestep9.png" height="80%" width="80%"/> </p>

<p align="center">Step 10: Create an endpoint index on Splunk</p>
<p align="center"> <img src="images/imagestep10.png" height="80%" width="80%"/> </p>

<p align="center">Step 11: Install the Splunk Add-On for Sysmon</p>
<p align="center"> <img src="images/imagestep11.png" height="80%" width="80%"/> </p>

<p align="center">Step 12: Change the Network Adapter from NAT to Internal Network (reduce the risk of malware entering the host machine)</p>
<p align="center"> <img src="images/imagestep12.png" height="80%" width="80%"/> </p>
<p align="center">*Internal Network allows VMs to communicate with each other on a private virtual network (a 'fake internet') but prevents access to the host machine and the internet</p>

<p align="center">Step 13: Change to Internal Network for both Virtual Machines</p>
<p align="center"> <img src="images/imagestep13.png" height="80%" width="80%"/> </p>

<p align="center">Step 14: Statically assign an IP for the Windows 10 VM</p>
<p align="center"> <img src="images/imagestep14.png" height="80%" width="80%"/> </p>

<p align="center">Step 15: Check if the IP is assigned in Windows Command Prompt with ipconfig</p>
<p align="center"> <img src="images/imagestep15.png" height="80%" width="80%"/> </p>

<p align="center">Step 16: Statically assign an IP for the Kali Linux VM</p>
<p align="center"> <img src="images/imagestep16.png" height="80%" width="80%"/> </p>

<p align="center">Step 17: Check if the IP is assigned in Linux terminal with ifconfig</p>
<p align="center"> <img src="images/imagestep17.png" height="80%" width="80%"/> </p>

<p align="center">Step 18: Ping the Windows IP in the Kali VM to check the connectivity</p>
<p align="center"> <img src="images/imagestep18.png" height="80%" width="80%"/> </p>

<p align="center">Step 19: Ping the Kali IP in the Windows VM to check the connectivity</p>
<p align="center"> <img src="images/imagestep19.png" height="80%" width="80%"/> </p>

<p align="center">Step 20: Use nmap to scan and identify any open ports</p>
<p align="center"> <img src="images/imagestep20.png" height="80%" width="80%"/> </p>

<p align="center">Step 21: Choose a payload within msfvenom</p>
<p align="center"> <img src="images/imagestep21.png" height="80%" width="80%"/> </p>

<p align="center">Step 22: Build the malware with the chosen payload. check if the file exist with 'ls', and its type with 'file'</p>
<p align="center"> <img src="images/imagestep22.png" height="80%" width="80%"/> </p>

<p align="center">Step 23: Open metasploit with msfconsole</p>
<p align="center"> <img src="images/imagestep23.png" height="80%" width="80%"/> </p>

<p align="center">Step 24: Open a handler to listen in on the port recieving the malware</p>
<p align="center"> <img src="images/imagestep24.png" height="80%" width="80%"/> </p>

<p align="center">Step 25: Change the payload option to that of the msfvenom</p>
<p align="center"> <img src="images/imagestep25.png" height="80%" width="80%"/> </p>

<p align="center">Step 26: Set the lhost to the attacker's IP</p>
<p align="center"> <img src="images/imagestep26.png" height="80%" width="80%"/> </p>

<p align="center">Step 27: Start the handler and wait for the target to execute the malware</p>
<p align="center"> <img src="images/imagestep27.png" height="80%" width="80%"/> </p>

<p align="center">Step 28: Start a HTTP web server using Python on port 9999 so that the target can download the malware</p>
<p align="center"> <img src="images/imagestep28.png" height="80%" width="80%"/> </p>

<p align="center">Step 29: Disable Windows Defender on the Windows VM</p>
<p align="center"> <img src="images/imagestep29.png" height="80%" width="80%"/> </p>

<p align="center">Step 30: Visit the HTTP web server on the Windows VM and download the malware</p>
<p align="center"> <img src="images/imagestep30.png" height="80%" width="80%"/> </p>

<p align="center">Step 31: Open a Command Prompt on Windows with Administer privileges and check the active connections with 'netstat -anob'</p>
<p align="center"> <img src="images/imagestep31.png" height="80%" width="80%"/> </p>

<p align="center">Step 32: Check for an established connection from the Kali (attacking) machine on the Windows VM</p>
<p align="center"> <img src="images/imagestep32.png" height="80%" width="80%"/> </p>

<p align="center">Step 33: Sorting the PID on Window's Task Manager will show that the malware is running</p>
<p align="center"> <img src="images/imagestep33.png" height="80%" width="80%"/> </p>

<p align="center">Step 34: Since the malware has been executed on the target machine, the handler on the Kali VM will show a connection</p>
<p align="center"> <img src="images/imagestep34.png" height="80%" width="80%"/> </p>

<p align="center">Step 35: A connection can also be seen with the incomming HTTP requests on the web server</p>
<p align="center"> <img src="images/imagestep35.png" height="80%" width="80%"/> </p>

<p align="center">Step 36: Generate telemetry on the target machine: "shell"</p>
<p align="center"> <img src="images/imagestep36.png" height="80%" width="80%"/> </p>

<p align="center">Step 37: Generate telemetry on the target machine: "net user"</p>
<p align="center"> <img src="images/imagestep37.png" height="80%" width="80%"/> </p>

<p align="center">Step 38: Generate telemetry on the target machine: "net localgroup"</p>
<p align="center"> <img src="images/imagestep38.png" height="80%" width="80%"/> </p>

<p align="center">Step 39: Generate telemetry on the target machine: "ipconfig"</p>
<p align="center"> <img src="images/imagestep39.png" height="80%" width="80%"/> </p>

<p align="center">Step 40: Query the attacking IP on Splunk</p>
<p align="center"> <img src="images/imagestep40.png" height="80%" width="80%"/> </p>

<p align="center">Step 41: Select any value in EventCode and click it</p>
<p align="center"> <img src="images/imagestep41.png" height="80%" width="80%"/> </p>

<p align="center">Step 42: Copy and add its process_guid to the query</p>
<p align="center"> <img src="images/imagestep42.png" height="80%" width="80%"/> </p>

<p align="center">Step 43: Filter the results with 'table' for simpler results. Notice that in the CommandLine column, every activity performed by the attacker can be seen</p>
<p align="center"> <img src="images/imagestep43.png" height="80%" width="80%"/> </p>

*This project was inspired by MyDFIR's Youtube series on building a Basic Home Lab

## Findings
A home lab provides a sandbox enviroment that is able to safely test malware without risking severe damage to the host machine. This is because virtual machines can be easily reverted to a previous state or be deleted without losing important documents if things ever go wrong.
- Additionally, this project also shows that by changing Network Adapter to NAT (Network Address Translation), or better, Internal Network, the virtual machine significanly reduces the risk of affecting the host machine, making it ideal for learning and practising cybersecurity skills.

As a bonus:
1. This home lab project also shows the usefulness of SIEM tools, in this case, Splunk. Splunk helped with collecting, indexing and analysing logs which makes it much easier to detect suspicious behavior on a system. Or, when malicious activity is found, Splunk is helpful in investigating activities of the attacker.
   - by installing a Sysmon (System Monitor) add-on, Splunk gains much more useful fields and logs. The detailed security events Sysmon records can even allow Splunk to analyse an attacker's activity step-by-step.

2. Using Metasploit in this project shows one of many possibilities of what attackers can do or learn about a target system when a malicious file is downloaded. For example, process creations, as done so in this project, file changes and network connection, which can be read about in the options menu. This helps with building an understanding of the techniques attackers use, and hence, better defence.

## Conclusion
Building a home lab improved my understanding of how malware can be created, how a target system could be affected by malware and how SIEM tools can help detect threats, and hence, allow for a more effective response to threats.
