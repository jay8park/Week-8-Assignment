# Week-8-Assignment

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection  
Go to one of the Salesperson's page. Manipulate the URL so that you replace the id with this: ' OR SLEEP(5)=0--'  
It made sense to try doing this on the Salesperson page with a particular employee, because you would be specifically requesting someone at id X. Therefore, I tried replacing the id number with that SQL injection, (which was provided in Hints). This took a while to load and the result of this injection leads the page to be directed to Daron Burke's page (the first guy listed). If I tried this with the Red or Green Target, it would direct me to a page that says "Database query failed". 

Vulnerability #2: Session Hijacking/Fixation  
Essentially, you need to change the session id on one browser to match the session id on another browser. Open up two browsers, and log into one of the browsers (A). Don't log into the other browser (B). Then, get the session id of A, and change the session id of B to the A's. Now, in B, click "Login". You will be able to successfully login without having to input any credentials. 


## Green

Vulnerability #1: Username Enumeration  
User Enumeration is the process of enumerating all possible usernames in an application, server, etc. The strategy is to enter random usernames and see what error-handling message you get. The Username Enumeration vulnerability was found in the Green Tagret because the only in the Green Target Login page, you get an unbolded alert when you enter an invalid username but get a bolded alert when you enter a valid username with wrong password. For the other target, the alerts are all the same.   
<img src="Week 8(1)" width="800">

Vulnerability #2: Cross-Site Scripting  
This vulnerability can be exploited through the "Feedback" section. A user can go to the "Contact" tab and fill out a form in the "Feedback" section with a malivious JavaScript code: <script>alert('Mallory found the XSS!');</script>  
Once you login as admin and check the feedback, a JavaScript alert will pop up. 


## Red

Vulnerability #1: Insecure Direct Object Reference  
The Red Target has an Insecure Direct Object Reference vulnerability because you can see any account. On the salesperson page, you are able to access information about a salesperson that should not be accessible to the public. By changing the id in the URL, you can access salesperson information that you shouldn't be able to access. (Note: try a bunch of id numbers, particularly 10 and 11. Or, you can figure out which one to check but logging in and checking salespersons information).When I tried manipulating the URL, I was redirected to the main "Find a Salesperson" page for the other Targets.  

Vulnerability #2: Cross-Site Request Forgery  
Someone can submit a URL or a dummy page that contains a hidden form in the "Feedback" section by submitting a form. Then, the admin can visit the url from the "Feedback", which will submit a form to the "Edit Section" of the admin page. 
Create a malicious link or form (.html file) that is an auto-submitting form. Then, comment that link in the "Feedback" section in "Contact". Now, as an admin, go to that link. That malicious link would have changed the information of a designated salesperson (e.g. id=3 so Irene Boling).  

## Notes

Describe any challenges encountered while doing the work:  
It took so long to try every possible things for every single target. I wish there were a bit more guidance. Also, had an issue with accessing the admin page. 
