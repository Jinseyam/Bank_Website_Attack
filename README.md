# Bank_Website_Attack
Utilizing SQL injection, XSS, and CSRF attacks on a simulated bank’s login page to gain access to victim bank accounts.

The below describes the defenses put up by the website and is associated with an exploit that was able to bypass these defenses.
## SQL Injection
The first goal is to demonstrate SQL injection attacks that log you in as the victim user without knowing their password.
### sql_0.txt
In this part, inputs are not sanitized. You must craft username and password inputs that cause the SQL query to succeed for the victim’s account without knowing the real password.
### sql_1.txt
One of the developers has attempted to fix the vulnerability by escaping single quotes (') in the username and password by doubling them. Your job is to bypass this defense and log in as the victim.

## XSS Attack
The dashboard page after login allows searching for transactions. However, the user input to search is repeated without proper sanitization. By exploiting this, you can embed scripts in the search query that execute in the victim’s browser. The ultimate goal is to steal the victim’s account number and balance and send it to the attack server.
### xss_0.txt
In this version, no defenses are applied. Your input is reflected directly without any sanitization.
### xss_1.txt
One of the developers implemented a defense that removes the word “script” (case-insensitive). 
### xss_2.txt
Another developer thinks their defense is pretty solid since they remove all occurrences of script, img, body, style, meta, embed, and object.
### xss_3.txt
The developer decided to strip out the punctuation that is at the root of the issue
### xss_4.txt
The developer tried to strengthen their filtering by combining both methods. They remove all occurrences of several tags and also strip out certain punctuation characters

## CSRF Attack
Write CSRF attacks against SunnyBank’s money transfer functionality, which allows users to transfer money to other users’ accounts.
The goal is to craft an HTML file that either automatically triggers a transfer from the victim’s account to the attacker's account when opened by the victim
### csrf_0.html
No defenses against CSRF attacks are implemented. Create an HTML file such that when a user is logged in and opens it in their browser, money is sent to the attacker’s account. 
### csrf_1.html
The developers have implemented a secure version of the transfer functionality. This version attempts to protect against CSRF attacks by requiring a token. Specifically, the site sets a cookie named csrf_token to a random 16-byte value, and the legitimate transfer form includes this token as a hidden form field. The server will verify that both the form field and the cookie match. If they do not match, the transfer is rejected.
