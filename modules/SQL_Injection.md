# SQL Injection
> SQL injection is a technique that takes advantage of input vulnerabilities to pass malicious SQL commands through a web application for execution by a backend database.


Overview of SQL Injection:
- SQL injection attacks can be performed using various techniques to view, manipulate, insert, and delete data from an application’s database. There are three main types of SQL injection:
  - In-band SQL injection: An attacker uses the same communication channel to perform the attack and retrieve the results
  - Blind/inferential SQL injection: An attacker has no error messages from the system with which to work, but rather simply sends a malicious SQL query to the database
  - Out-of-band SQL injection: An attacker uses different communication channels (such as database email functionality, or file writing and loading functions) to perform the attack and obtain the results


SQL injection can be used to implement the following attacks:
- Authentication bypass: An attacker logs onto an application without providing a valid username and password and gains administrative privileges
- Authorization bypass: An attacker alters authorization information stored in the database by exploiting SQL injection vulnerabilities
- Information disclosure: An attacker obtains sensitive information that is stored in the database
- Compromised data integrity: An attacker defaces a webpage, inserts malicious content into webpages, or alters the contents of a database
- Compromised availability of data: An attacker deletes specific information, the log, or audit information in a database
- Remote code execution: An attacker executes a piece of code remotely that can compromise the host OS


sqlmap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over of database servers. It comes with a powerful detection engine, many niche features, and a broad range of switches—from database fingerprinting and data fetching from the database to accessing the underlying file system and executing commands on the OS via out-of-band connections.

You can use sqlmap to perform SQL injection on a target website using various techniques, including Boolean-based blind, time-based blind, error-based, UNION query-based, stacked queries, and out-of-band SQL injection.


Detect SQL Injection Vulnerabilities using DSSS:
- Damn Small SQLi Scanner (DSSS) is a fully functional SQL injection vulnerability scanner that supports GET and POST parameters. DSSS scans web applications for various SQL injection vulnerabilities.









