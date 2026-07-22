<h1>Basic Home Lab</h1>

<h2>Purpose</h2>
<p>To  set up a home lab to safely investigate malware and learn new tools and techniques</p>

<h2>Utilities Used</h2>
<p>
   
**Windows 10 Virtual Machine** - the target machine to test malware on. This VM was run using Virtual Box, it provides a sandbox environment to prevent malware from affecting the host machine.
<ul>
   <li>Windows 10 was chosen since it is a popular operating system used by many.</li>
</ul>
   
**Kali Linux Virtual Machine** - the attacking machine which creates the malware. It was also ran using Virtual Box.
<ul>
   <li>Kali Linux was chosen since it comes with the Metasploit Framework preinstalled.</li>
   <li>The Metasploit Framework is a tool used to perform authorised penetration tests to understand and improve system security.</li>
</ul>

**Sysmon** - a Windows tool used to record system activity (such as process creation, network connections and file changes). This is to investigate the activity of the attacking machine on the target machine.

**Splunk** - a SIEM tool used to analyse data and monitor system security. It will recieve the events collected by Sysmon to be indexed and analysed.
<ul>
   <li>Additionally, Splunk also has dashboards and alerts to quickly identify threats.</li>
</ul>
</p>

<h2>Project Walk-Through</h2>

<p align="center">
Step 1: description<br/>
<img src="images\imagestep1.png" height="80%" width="80%" alt="image description"/>
<br />
<br />
Step 2: description<br/>
<img src="images\imagestep2.png" height="80%" width="80%" alt="image description"/>
<br />
<br />
Step 3: description<br/>
<img src="images\imagestep3.png" height="80%" width="80%" alt="image description"/>
<br />
<br />
Step 4: description<br/>
<img src="images\imagestep4.png" height="80%" width="80%" alt="image description"/>
<br />
<br />
Step 5: description<br/>
<img src="images\imagestep5.png" height="80%" width="80%" alt="image description"/>
<br />
<br />
Step 6: description<br/>
<img src="images\imagestep6.png" height="80%" width="80%" alt="image description"/>
<br />
<br />
Step 7: description<br/>
<img src="images\imagestep7.png" height="80%" width="80%" alt="image description"/>
<br />
<br />
Step 8: description<br/>
<img src="images\imagestep8.png" height="80%" width="80%" alt="image description"/>
<br />
</p>

<h2>Findings</h2>
<p>
XXX
</p>

<h2>Conclusion</h2>
<p>
XXX
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
