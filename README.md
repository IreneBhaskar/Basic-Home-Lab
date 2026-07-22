# Basic Home Lab (w/ Sysmon, Splunk)

## Table of Contents
- [Purpose](#purpose)
- [Utilities Used](#utilities-used)
- [Project Walkthrough](#project-walkthrough)
- [Findings](#findings)
- [Conclusion](#conclusion)

## Purpose
To  set up a home lab to safely investigate malware and learn new tools and techniques

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

<p align="center"> Step 1: description </p>
<p align="center"> <img src="images\imagestep1.png" height="80%" width="80%"/> </p>

<p align="center"> Step 2: description</p>
<p align="center"> <img src="images\imagestep2.png" height="80%" width="80%"/> </p>

## Findings
XXX

## Conclusion
XXX
