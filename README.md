# Insecure-Direct-Object-Refereces-IDOR-
<br>
What are insecure direct object references (IDOR)?<br>
<br>
Insecure direct object references (IDOR) are a type of access control vulnerability that arises when an application uses user-supplied input to access objects 
directly. The term IDOR was popularized by its appearance in the OWASP 2007 Top Ten. However, it is just one example of many access control implementation mistakes 
that can lead to access controls being circumvented. IDOR vulnerabilities are most commonly associated with horizontal privilege escalation, but they can also arise in 
relation to vertical privilege escalation.
<br>
IDOR examples<br>
There are many examples of access control vulnerabilities where user-controlled parameter values are used to access resources or functions directly.<br>
<br>
IDOR vulnerability with direct reference to database objects<br>
Consider a website that uses the following URL to access the customer account page, by retrieving information from the back-end database:<br>
<br>
https://insecure-website.com/customer_account?customer_number=132355
<br>
<br>
Here, the customer number is used directly as a record index in queries that are performed on the back-end database. If no other controls are in place, an attacker can 
simply modify the customer_number value, bypassing access controls to view the records of other customers. This is an example of an IDOR vulnerability leading to 
horizontal privilege escalation.<br>
<br>
An attacker might be able to perform horizontal and vertical privilege escalation by altering the user to one with additional privileges while bypassing access 
controls. Other possibilities include exploiting password leakage or modifying parameters once the attacker has landed in the user's accounts page, for example.<br>
<br>
IDOR vulnerability with direct reference to static files<br>
IDOR vulnerabilities often arise when sensitive resources are located in static files on the server-side filesystem. For example, a website might save chat message transcripts to disk using an incrementing filename, and allow users to retrieve these by visiting a URL like the following:<br>
<br>
https://insecure-website.com/static/12144.txt<br>
<br>
In this situation, an attacker can simply modify the filename to retrieve a transcript created by another user and potentially obtain user credentials and other sensitive data.<br>
<br>
This is a test lab in portswigger:<br>
<br>
https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references<br>
