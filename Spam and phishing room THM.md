objective: in this room we will carry out basic analysis of emails to spot spam and phishing attempts

Task 1:
Our first CTF was to figure what domain an email is associated with which we can easily do by looking at the text following @.

Task 2:
The following task covers the different protocols such as SMTP which sends the email to the email server, POP3 which downloads email to a single device and IMAP which stores emails on the server and lets them be downloaded multiple times as well as synchronization work. The rest of the task is basic trivia in regards to this information.

Task 3:
The following task is about email headers . Email headers contain metadata about the email.
For this task we will open up a VM on THM and carry out email analysis:


![](Images/Pasted%20image%2020261012122706.png)

For now we are opening emails in thunderbird and reviewing their header's
![](ImagesPasted%20image%2020261012123139.png)

A way to view the email told to us in the task which shows more data is to open it in RAW and we can do this by selecting message source option in view
![](Images/Pasted%20image%2020261012123256.png)
The raw view gives us access to much more information such as the ip address of the sender
![](ImagesPasted%20image%2020261012123401.png)Then we are given two simple tasks the first one being to list the subject of the email which you can see in normal view and the second being list the x-originating ip which you can see in RAW form.
Task 4:
The following task is about email bodies which contain the content of the email in either plain text or HTML.
Here we viewed the body in raw format to the message is structured, spot embedded elements, and look for signs of phishing or malicious content.
We are also told about three important headers belonging to attachments:
Content-Type: indicates the file type
Content-Disposition: specifies that the file has an attachment and includes the file name.
Content-Transfer-Encoding: shows the file encoding type

We are now asked to open up email2.txt from the examples folder ![](Images/Pasted%20image%2020261012124718.png)First we are asked about the Content-Type which we can directly see in the screen shot.
Second the name of the attachment which we can also see in the screen shot.
Thirdly we are required to decode the base 64 using either PDF converter or Cyber Chef so i grabbed the entire encoded text and dropped it in pdf converter.
![](Images/Pasted%20image%2020261012125352.png)
The next task goes through the types of phishing emails and a segment on indicators we should look out for however that is ridiculously basic so I do not plan to document that here. Afterwards there is a segment that goes over how suspicious links should be defanged so that they do not work if you accidentally click on them which works by replacing special characters such as @ by alternating ones.
Then we are asked to perform a analysis on email3 similar to the ones we performed before however we are asked to defang the x-originating ip which we did using cyber chef.
![](Images/Pasted%20image%2020261012130338.png)
