# Recon
## spidering 
### ZAP -- DAD
Kali linux
Traditional and AJAX spider
### SkipFish -- BARRY
command line
Saves as HTML report
#### Both of these do more than just a regular spider it will hint at potential attack vectors
## Web content / server
### above in attack mode
### DIRB --DAD
Scans known configuration URLs
Command line - KALI linux
### Nikto --BARRY
Scans known issues
Attempts to discover webserver / software running
Command Line - KALI Linux

# Vulnerabilities to check
## SQL Injection -- Barry (DAD can jump in)
Are we able to run SQL code in text input fields
## In browser 
DEV tools
Email: '
Password: 123 (does not matter)
Error messages give information
```sql
"SELECT * FROM Users WHERE email = ''' AND password =
```

Try
Email: ```' OR 1=1 --```
Pasword: 123
' ends the first quote
OR adds a condition to test ande means email does not have to match
1=1 is always true
\-- comments out the rest of the line (does not run)

This will scan through the database and select the first record
The first record is often an admin account
#### ZAP (DAD)
Can automate testing all potential SQL attacks
1. Configure ZAP proxy in browser
2. Navigate to the log in page and attempt to login with any credentials
3. In ZAP -> History
4. Find login (POST method)
5. Attack, payload, SQL attack
6. Start fuzzer
#### SQLMap (Barry)
Can be used to dump the entire database
Using search field
Options to evade Web Application Firewall (WAP)
Crack password hashes
Use information gathered from Web content scan and other SQL attacks to narrow

## Credential Stuffing (Barry)
Broken authentication
Login attempts can be automated using BURP suite
1. Proxy / browser
2. Intercept log in request (POST login)
3. Using known email (Find on website)
4. Send to intruder
5. Select password
6. Load word list
7. Start attack
8. Wait
9. Community version is slow
## IDOR (DAD)
Insecure Direct Object Reference
When a web application creates objects for the user such as a shopping cart this needs a URL or other reference
A simple way of doing this is using numbers
E.G. 
cart/1
cart/2
cart/3
However this is obvious to guess if my cart is cart/5
Can I try cart/3, cart/4 etc.
Authentication such as a bearer token
May give acess not only to my cart but to others
##### Tools to exploit this
- Postman
- ZAP
- BURPSuite ?
## XSS (Barry)
Cross site scripting
Browser
Using text fields (such as search)
HTML, iframe, src javascript:
google map embed code is one thing to try

chrisw93@outlook.com