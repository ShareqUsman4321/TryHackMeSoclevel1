When analyzing a suspicious email our first job will be to analyze the artifacts to judge the email's legitimacy
In the header we should take note of:
1/ Sender email address
2/ Sender IP address
3/  Email Subject line
4/  Recipient email address
5/  Reply to email address
6/  Date and Time

in the body we should take note of:
1/  URL and hyperlinks
2/ Attachment name
3/  Attachment Hash

For mail header analysis we can make use of  MessageHeader to gain information such as IP address, routing path and potential missconfigurations by posting full header into the tool
![](Images/Pasted%20image%2020261106120852.png)

IPinfo can be used the geographical location and associated orginization of an IP address
![](ImagesPasted%20image%2020261106121442.png)
URLScan.io allows analysts to analyze websites without visiting them directly by submitting a URL and simulating a real browser session while recording all activity
![](Images/Pasted%20image%2020261106121827.png)Talos IP and domain reputation center is a threat intelligence tool that allows a analyst to gauge the reputation of a IP or a domain

embedded links are clickable objects

You can safely analyze the destination of a link address using URL extraction tools such as cyber chef which can parse the email for embedded links

Only download attachments in a safe environment such as a lab machine or sandbox. Then you can generate a hash using sha256sum to check its reputation using tools like virus total

ANY.RUN is an interactive malware sandbox that allows users to safely run files and URLS and using it u can interact with the environment, monitor processes, view network activity, and analyze system changes as they happen
![](Images/Pasted%20image%2020261106123031.png)Similarly you can also use Hybrid Analysis and JOESandbox

PhishTool:
A tool that automates much of the work involved in analyzing suspicious emails and combines threat intelligence, OSINT, email metadata, and automated analysis workflows to enable us to quickly identify malicious intent and IOCS.

Now that we have gone through the different tools introduced to us in this room Tryhackme has now presented us with a few simple CTFS where we act as a soc dealing with potential phishing emails to solve so we will bootup the lab and attacker machines

The email we are going to be analyzing is Phish3Case1.eml

![](Images/Pasted%20image%2020261107114008.png)

We are asked to very simple tasks such as analyzing the the email to determine which company is the target of brand impersonation in this case we can see that from the subject line and analyzing the source message to find the originating ip address and the domain referenced in the return field
as well as grabbing the shortened URL from the UPDATE ACCOUNT NOW button by copying the link

In the next series  of tasks we will be analyzing a malicious attachment which was connected to a email regarding payment to Netflix using ANY.RUN

![](Images/Pasted%20image%2020261107114936.png)In this section we first determined how ANY.RUN classifies this file by looking at the top right corner of the analysis from where we also got the name of the attachment as well as the MD5 hash of the attachment which we can use to check the legitimacy of the attachment through something like virus total. We then used to the process tab to locate the URL being used by this attachment and used the connections tab to determine which IP this domain resolves too so that we can block both of them through a firewall and note them down to use in the future as IOCS

excel executable: Uses excel files as a launch pad to trick the system into running unauthorized commands

In the next series of tasks we will be analyzing an excel executable using ANY.RUN



![](Images/Pasted%20image%2020261107122046.png)


First we identified the suspicious process which was EQNEDT32.EXE through the processes tab and then we found its image to determine path and location using the command line associated with the process and found out the CVE associated with the process using the same tab to understand the technique used how to harden our system against it. Next we used the more info button and then selected the http requests tabs inside to find the domain from which the virus was downloaded which can be used as a IOC in the future and can be blocked by our firewall and then used network threats to find the network threat associated with  the attack to see if the IDS fired the same alert on other systems  in the network to find out the total number of infected systems using the SID
