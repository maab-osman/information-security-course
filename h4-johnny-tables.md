## H4: Johnny Tables

### A01 - Broken Access Control
- Users can do things they’re not supposed to, like seeing or changing other people’s data.
- Common problems:
  - Changing URLs or data to access someone else’s account.
  - Acting like an admin without permission.
  - APIs are missing proper access checks.
  - Misconfigured settings like CORS or cookies.
- It matters because it can lead to data leaks, unauthorized actions, or full system compromise.
- There are multiple prevention methods mentioned, like:
    - Always deny access by default unless allowed.
    - Reuse access control logic across the app.
    - Log and monitor failed access attempts.

  Thoughts: I was surprised to learn that simple URL changes can expose sensitive data easily.
  

### A05 - Security Misconfiguration
- The app or system is not set up securely, so it might have weak settings or default passwords still active.
- Common problems:
  - Leaving sample apps or default accounts on live servers.
  - Showing detailed error messages to users.
  - Using outdated software or not applying security patches.
- It matters because hackers can easily find and exploit these weak spots to steal data or take control of systems.
- To prevent we must:
  - Use a secure setup process that’s the same for all environments.
  - Remove anything unnecessary.
  - Regularly update and review configurations and permissions.
  - Automate security checks and use security headers.
    
Thoughts: Is it more a lack of awareness or just pressure to ship fast that leads to these misconfigurations?
  
### A06 - Vulnerable and Outdated Components
- In short terms, Your app uses old or unsafe parts that hackers can exploit.
- There is risk if:
  - You don’t know what versions of software you’re using.
  - You don’t update your software regularly.
  - You use components that are no longer supported.

- Preventions include:
  - Keeping a list of all the software parts you use.
  - Removing anything we don’t need.
  - Using tools to check for known security issues.
  - Only downloading components from trusted sources.

  Thoughts: It’s easy to forget how much modern apps rely on third-party stuff. But if even one of those pieces is outdated, it’s like leaving the back door open. Makes me think twice about skipping those update reminders.


### A03 - Injection
- Attackers trick the app into running harmful commands by inserting malicious input.
- The common types include:
  - SQL injection
  - OS command injection
  - NoSQL injection
  - Object Relational Mapping (ORM).

- The preventions mentioned:
- Use safe APIs or parameterized queries.
- Validate and sanitize all user input.
- Avoid building queries by combining strings and user data.

Thoughts: Injection vulnerabilities highlight the critical importance of separating data from code execution. 

### Munroe - xkcd 327: "Exploits of a Mom"
The comic shows a mom naming her child
" Robert'); DROP TABLE Students;-- "
I recognized this SQL query but on second thought, I realized that it is  malicious input that is used to trick a system into deleting a whole database table.
- The teacher on the call later emphasized that the data had been lost because of her son (The injection).
- The mother replies, saying that they should have "sanitized" their database inputs, referring to the practice of validating and cleaning user input to prevent injection attacks.

**References**
- Munroe, R. (n.d.). Exploits of a Mom. [online] xkcd. Available at: https://xkcd.com/327/.
- OWASP (2021). A01:2021 – Broken Access Control. [online] owasp.org. Available at: https://owasp.org/Top10/A01_2021-Broken_Access_Control/.
- OWASP (2021). A05 Security Misconfiguration - OWASP Top 10:2021. [online] owasp.org. Available at: https://owasp.org/Top10/A05_2021-Security_Misconfiguration/.
- OWASP (2021). A06 Vulnerable and Outdated Components - OWASP Top 10:2021. [online] owasp.org. Available at: https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/.
- OWASP (2021). A03 Injection - OWASP Top 10:2021. [online] owasp.org. Available at: https://owasp.org/Top10/A03_2021-Injection/.

‌
---

## a) Goat - Install WebGoat 2023.4
Using my UTM virtual machine, I was able to install successfully following the guide given by the teacher. Terokarvinen.com. (2023)
- The same commands on the guide were used, except I faced an issue trying to download Java.
- After trying to configure the issue, I ran this command since I was not sure if it belonged to my previously installed files.
```bash
apt search openjdk
```
- This solved the issue since I figured out access to a different version of Java, "openjdk-21-jre", then proceeded to download it.
- Finally, I was able to launch WebGoat using the commands mentioned in the guide. The picture below was taken from the terminal, indicating a successful launch.
  
<img width="629" height="125" alt="Screenshot 2025-09-15 at 10 10 05 PM" src="https://github.com/user-attachments/assets/e1d2f1e8-462b-476b-b7a8-5807f58c069a"/>
<br></br>

- Following the guide, I changed the port and was able to open the URL on my browser as seen below.

<img width="346" height="217" alt="Screenshot 2025-09-15 at 10 15 07 PM" src="https://github.com/user-attachments/assets/7ac07a0c-e3fd-4287-8d4c-8547fbabd573" />
<br></br>

Reference: Terokarvinen.com. (2023). Try Web Hacking on New Webgoat 2023.4. [online] Available at: https://terokarvinen.com/2023/webgoat-2023-4-ethical-web-hacking/.

---

## b) F12 - WebGoat 2023.4: *General: Developer tools*
This challenge was included at the end of the developer tools lesson.
  1. Firstly, I read and reviewed the chapters in the lesson to understand the content.
  2. Starting the task, I opened the developer's tool on the browser by pressing F12.
  3. Then I located the networks tab and clicked on the "Go!" button as instructed.
  5. Then I received a POST method as a response, which contained more detailed information.
     
     <img width="601" height="413" alt="Screenshot 2025-09-15 at 10 30 46 PM" src="https://github.com/user-attachments/assets/ac62f892-c53f-485b-aee5-e1bc2bc34dca" />
<br></br>

  6. Initially, it took a while to locate the number from the default "Headers" tab, realizing it may be under a different tab.

  7. Then, finally, the networkNum could be accessed through the "Request" tab easily.
<br></br>

<img width="512" height="181" alt="Screenshot 2025-09-15 at 10 35 36 PM" src="https://github.com/user-attachments/assets/5c2f0172-ae36-4346-910d-c85ddc09960f" />

<br></br>

Learnings: This exercise taught me that critical data, such as networkNum, is often hidden in the "Request" payload rather than in headers, reinforcing the importance of thoroughly inspecting all tabs in Developer Tools during security assessments.

---

## c) Update OS & Applications
I have updated all operating systems by running the following commands:

```bash
sudo apt update

sudo apt full-upgrade -y

sudo reboot
```

Reference: Bill Sky - The Computer Guy! (2024). Linux 04: How to update and install applications on Linux. [online] YouTube. Available at: https://www.youtube.com/watch?v=GmqhbsaGk3I [Accessed 14 Sep. 2025].

---
## d) Sequel - SQLZoo tasks

### 0 SELECT basics
1. I used the `WHERE` clause with a string match to retrieve the population of Germany, reinforcing how single quotes denote string values in SQL.
2. I employed the `IN` operator to filter results for multiple countries, learning how to efficiently check against a list of values.
3. I utilized the `BETWEEN` operator to find countries with areas within a specified range, understanding how inclusive range checks work in SQL.
     
### 2 SELECT from World
- Subtask 1: I executed a basic `SELECT` query to retrieve all countries' names, continents, and populations, gaining an overview of the dataset's structure and content.
- Subtask 2: I applied the `WHERE` clause with a population filter `>= 200000000` to list only large countries, practicing numerical comparisons in SQL.

**Reference:** sqlzoo.net. (n.d.). SQLZOO. [online] Available at: https://sqlzoo.net/wiki/SQL_Tutorial.

---
## e) PortSwigger Labs - SQL injection in WHERE clause.


The vulnerability was in the pets **category** filter where user-supplied input was concatenated directly into a SQL `WHERE` clause without sanitization or prepared statements. By manipulating the category parameter, an attacker could change the logic of the query so that it returned all products including unreleased ones. This is a good demonstration of a broken access-control issue.


### How I found the vulnerability
- Noted the category parameter in the URL (`?category=Pets`) was reflected in page content.  
- Injected a syntax-breaking character and observed a SQL error in the response, which indicated that user input reached the database query unsanitized.  
- The error and subsequent behavioral changes confirmed the injection point.

### Anatomy of the exploit
**Payload entry point**  
- The `category` parameter in the HTTP GET request is inserted directly into the `WHERE` clause on the server side. No input sanitization or parameterization was applied.

**Payload purpose**  
- The attack aims to alter the `WHERE` clause from a restrictive filter into an always true condition, and to neutralize any subsequent filtering. Conceptually, this is done by:
  1. Terminating the original string or expression.
  2. Injecting a boolean condition that is always true (so the `WHERE` matches every row).
  3. Commenting out the rest of the original query so protective filters are ignored.

**Why it worked**  
- The server-side code constructs the query via string concatenation: `SELECT * FROM products WHERE category = '" + userInput + "' AND released = 1`.
- My input `Pets' OR 1=1--` transformed this into `SELECT * FROM products WHERE category = 'Pets' OR 1=1--' AND released = 1`. The `OR 1=1` makes the entire `WHERE` condition true for every row, and the `--` comments out the `AND released=1` filter, removing the access control.
<img width="696" height="298" alt="Screenshot 2025-09-16 at 9 48 37 AM" src="https://github.com/user-attachments/assets/9a3f892b-fc79-47fc-a1fe-3765e709b244" />
<br></br>

**Defensive measures & mitigations for this scenario (Martinez, 2024)**:

- Use parameterized queries, as this is the most effective defense. It separates SQL code from data, preventing the interpreter from executing injected commands.

- Implement strict allow-list validation for inputs like category names. For example, only allow letters.

- The database user account used by the application should have minimal permissions.
  
**Reflection:** This lab underscored how a simple lack of input sanitization in a single parameter can completely break an application's security model. It highlights that security is not a feature but a fundamental requirement that must be integrated into the code's foundation, not added on later.

References: 
- Martinez, J. (2024). How to Prevent SQL Injection Attacks: 6 Proven Methods. [online] Strongdm.com. Available at: https://www.strongdm.com/blog/how-to-prevent-sql-injection-attacks.
- portswigger.net. (n.d.). Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data | Web Security Academy. [online] Available at: https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data.

‌

‌



