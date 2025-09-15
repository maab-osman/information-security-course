#### Johnny Tables
> **Important:** keep all activities safe, legal and ethical. Do **not** test vulnerabilities against machines you do not own or are not explicitly authorised to test.  
> You are only allowed to begin hands-on tasks after accepting the course rules in Moodle.

---

## x) Read & Summarize (brief bullets + one comment or question each)

### OWASP Top 10 (2021)
#### A01:2021 - Broken Access Control
- Users can do things they’re not supposed to, like seeing or changing other people’s data.
- Common problems:
  - Changing URLs or data to access someone else’s account.
  - Acting like an admin without permission.
  - APIs missing proper access checks.
  - Misconfigured settings like CORS or cookies.
- It matters because it can lead to data leaks, unauthorized actions, or full system compromise.
- There are multiple prevention methods mentioned like:
    - Always deny access by default unless allowed.
    - Reuse access control logic across the app.
    - Log and monitor failed access attempts.

  Thoughts: I was suprised to learn that simple URL changes can expose sensitive data easily.
  

#### A05:2021 — Security Misconfiguration
- The app or system is not set up securely so it might have weak settings or default passwords still active.
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
  - 
Thoughts: Is it more a lack of awareness or just pressure to ship fast that leads to these misconfigurations?
  
#### A06:2021 — Vulnerable and Outdated Components
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

  Thoughts: it’s easy to forget how much modern apps rely on third-party stuff. But if even one of those pieces is outdated, it’s like leaving the back door open. Makes me think twice about skipping those update reminders.


#### A03:2021 - Injection
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

### Munroe — xkcd 327: "Exploits of a Mom"
The comic shows a mom naming her child
" Robert'); DROP TABLE Students;-- "
I recognized this sql query but on a second thought I realized that it is  malicious input is used to trick a system into deleting a whole database table.
- The teacher on the call later emphasies that the data has been lost because of her son (The injection).
- The mother replies saying that they should have "sanitized" their database inputs reffering to he practice of validating and cleaning user input to prevent injection attacks.

**References**
- Munroe, R. (n.d.). Exploits of a Mom. [online] xkcd. Available at: https://xkcd.com/327/.
- OWASP (2021). A01:2021 – Broken Access Control. [online] owasp.org. Available at: https://owasp.org/Top10/A01_2021-Broken_Access_Control/.
- OWASP (2021). A05 Security Misconfiguration - OWASP Top 10:2021. [online] owasp.org. Available at: https://owasp.org/Top10/A05_2021-Security_Misconfiguration/.
- OWASP (2021). A06 Vulnerable and Outdated Components - OWASP Top 10:2021. [online] owasp.org. Available at: https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/.
- OWASP (2021). A03 Injection - OWASP Top 10:2021. [online] owasp.org. Available at: https://owasp.org/Top10/A03_2021-Injection/.

‌
---

## a) Goat — Install WebGoat 2023.4
- Using my UTM virtual machine I was capable of installing successfully following the guide givent by the teacher. Terokarvinen.com. (2023)
- The same commands on the guide were used except I faced an issue trying to download java.
- After trying to cofigure the issue, I ran this command since I was not sure if it belonged to my previously installed files.
- apt search openjdk
- This solved the issue since I figured O access to a different version of java, "openjdk-21-jre".
  
<img width="629" height="125" alt="Screenshot 2025-09-15 at 10 10 05 PM" src="https://github.com/user-attachments/assets/e1d2f1e8-462b-476b-b7a8-5807f58c069a"/>
<br></br>

- After downloading I was capable of launching webgoat and opening the url on my browser.

<img width="346" height="217" alt="Screenshot 2025-09-15 at 10 15 07 PM" src="https://github.com/user-attachments/assets/7ac07a0c-e3fd-4287-8d4c-8547fbabd573" />



---


## b) F12 — WebGoat 2023.4: *General: Developer tools*
This challenge was included at the end of the developer tools lesson.
  1. I first opened the developers tool on the browser by pressin f12.
  2. Then I located the networks tab and clocked on the "Go!" button as instructed.
  3. Then I recieved a POST method as a response which contained more detailed information.
     
     <img width="601" height="413" alt="Screenshot 2025-09-15 at 10 30 46 PM" src="https://github.com/user-attachments/assets/ac62f892-c53f-485b-aee5-e1bc2bc34dca" />
<br></br>

  4. Then finally the networkNum could be accessed through the "Request" tab easily.
<br></br>

<img width="512" height="181" alt="Screenshot 2025-09-15 at 10 35 36 PM" src="https://github.com/user-attachments/assets/5c2f0172-ae36-4346-910d-c85ddc09960f" />

---

## c) Not Outdated — Update OS & Applications (Linux)
I have updated all operating system by running the following commands:

```bash
sudo apt update

sudo apt full-upgrade -y

sudo reboot
```



---
## d) Sequel — SQLZoo tasks

- 0 SELECT basics — notes & answers
  1. I used the WHERE clause with a string match to retrieve the population of Germany, reinforcing how single quotes denote string values in SQL.
  2. I employed the IN operator to filter results for multiple countries, learning how to efficiently check against a list of values.
  3. I utilized the BETWEEN operator to find countries with areas within a specified range, understanding how inclusive range checks work in SQL.
     
- 2 SELECT from World — subtasks 1 & 2
  - Subtask 1: I executed a basic SELECT query to retrieve all countries' names, continents, and populations, gaining an overview of the dataset's structure and content.
  - Subtask 2: I applied the WHERE clause with a population filter (>= 200000000) to list only large countries, practicing numerical comparisons in SQL.

**Reference:** SQLZoo — https://sqlzoo.net/



