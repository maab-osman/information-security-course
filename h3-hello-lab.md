# Hello Lab - Week 3
This week, I start building my own hacking lab. The goal is to **learn hacking by hacking**.  
Assignment instruction available at: https://terokarvinen.com/information-security/

---

## Reading tasks Summary

### Karvinen 2021: Install Debian on Virtualbox
- Easy and clear guide to download the Debian ISO.
- Set up the VM with enough RAM and a big virtual disk.
- Add the ISO as a virtual CD and boot the VM.
- Try the live desktop first to test stuff before installing.
- Run the installer, choose English and Finnish settings, and set up user info.
- After installation, log in and update everything using terminal commands.
- To fix the small screen and enable copy and paste, install VirtualBox Guest Additions.

  My thoughts:
  - I had no idea what an ISO was, but it’s just like a digital CD
  - I used the arm64 version since I’m on a Mac with Apple Silicon
  - Gave the VM 4GB RAM and 60GB disk, seemed to run okay.
  - Didn’t hit the black screen bug, but good to know about the xforcevesa trick just in case.
  - UTM was a better option in my case, instead of VirtualBox, as it had some issues there.

  Refrence: Terokarvinen.com. (2024). Install Debian on Virtualbox - Updated 2024. [online] Available at: https://terokarvinen.com/2021/install-debian-on-virtualbox/.
  
---
### Karvinen 2020: Command Line Basics Revisited
- The command line is super old but still super useful.
- pwd, ls, and cd to move around folders.
- nano filename lets you edit files in the terminal.
- mkdir, mv, cp, and rm are for making, moving, copying, and deleting stuff.
- Be careful with rm -r as it deletes everything with no undo!
- SSH lets you connect to other computers remotely.
- scp is for copying files between computers.
- History shows your past commands, and Ctrl + R helps you search them.
- Important folders: /home/, /etc/, /media/, /var/log/.
- sudo gives you admin powers.
- Install software with sudo apt-get install packagename.

  Thoughts:
  - I have some experience with the command line but it was nice to refresh some concepts that I dont use on the daily .
  - Got to learn about the important directories but still don’t fully understand their practicality.

Reference: Terokarvinen.com. (2020). Command Line Basics Revisited. [online] Available at: https://terokarvinen.com/2020/command-line-basics-revisited/ [Accessed 6 Sep. 2025].

---

## a) Can't Fish
Disable networking and show that packets don’t go through.  

- Successfully disabled networking and demonstrated that packets cannot traverse outside the local system.
- I did it by configuring the UTM VM network mode to "Host Only" to restrict external network access (UTM Documentation, 2022) <br><br>
  <img width="630" height="111" alt="Screenshot 2025-09-08 at 9 56 47 PM" src="https://github.com/user-attachments/assets/29c5fbf2-a29c-4308-b401-c8570b73430d" />
  <br><br>
- I used the command below to test connectivity to Cloudflare's DNS server
 
```bash
ping -c 4 1.1.1.1
```

- The result recived was "Network is unreachable", proving zero packet transmission to external networks. <br><br>
  <img width="422" height="89" alt="Screenshot 2025-09-08 at 9 55 07 PM" src="https://github.com/user-attachments/assets/2bd308aa-02c6-4991-9632-170ae3930f00" />

<br><br>Sources used: UTM Documentation. (2022). Network. [online] Available at: https://docs.getutm.app/settings-qemu/devices/network/network/ [Accessed 9 Sep. 2025].


## b) Local Only
-  Successfully performed portscan of localhost using nmap
-  From the previous task, the network remained in "Host Only" mode throughout the scan
-  For this task I had to install nmap using this command

  ```bash
sudo apt install nmap
``` 

- Then I utilized nmap for port scanning in this assignment. I used this command to scan:
  
  ```bash
  sudo nmap -A localhost
    ```

-  I managed to identify open ports and services running on the local system
-  This is the output of the scan
```bash
Other addresses for localhost (not scanned) : ::1
Not shown: 997 closed tcp ports (reset)
PORT STATE SERVICE VERSION
22/tcp open 55h OpenSSH 10.0p2 Debian 7 (protocol 2.0)
80/tcp open http Apache httpd 2.4.65 ((Debian))
http-server-header: Apache/2.4.65 (Debian)
http-title: Apache2 Debian Default Page: It works

631/tcp open ipp     CUPS 2.4
_http-server-header: CUPS/2.4 IPP/2.1
http-robots.txt: 1 disallowed entry

Service Info: OS: Linux; CPE: cpe:/o:linux:linux kernel
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.01
```
 - The majority of ports (997) were closed, indicating a reasonably secure default configuration.
 - PORT STATE SERVICE VERSION is the header for the results each indicating its state (GeeksforGeeks, 2025).
 - The port 22 OpenSSH allows secure remote command-line access to the system (Netcomlearning.com, 2024).

```bash
22/tcp open 55h OpenSSH 10.0p2 Debian 7 (protocol 2.0)

```
 - After research about this specific program, I discovered that it must be protected with a very strong password because hackers love to try to break into it.
   
 ```bash
80/tcp open http Apache httpd 2.4.65 ((Debian))

```
 - Service on Port 80 HTTP is a web server hosting the default "It works!" page. This website host means that my computer can now act as a mini-webserver, but like SSH, it needs to be kept updated to be secure (GeeksforGeeks, 2024).
   
 ```bash
631/tcp open ipp CUPS 2.4

```
   
 - Service on Port 631 open IPP is a printing service called CUPS for managing printers (CBT Nuggets, 2024).
 - I learned that this is a standard helper service on many Linux systems and usually not high risk if connected to a network
   
<br><br> Sources used:
- CBT Nuggets. (2024). What is Port 631? [online] Available at: https://www.cbtnuggets.com/common-ports/what-is-port-631.
- GeeksforGeeks (2025). Nmap Scanning Results. [online] GeeksforGeeks. Available at: https://www.geeksforgeeks.org/ethical-hacking/nmap-scanning-results/ [Accessed 6 Sep. 2025].
- GeeksforGeeks (2024). What is Port 80? [online] GeeksforGeeks. Available at: https://www.geeksforgeeks.org/computer-networks/what-is-port-80/.
- Netcomlearning.com. (2024). What You Need to Know About Port 22 and Secure Shell (SSH). [online] Available at: https://www.netcomlearning.com/blog/what-is-port-22.
‌
 ---
  ## c) Daemon Scan
  
- The Apache web server was already pre-installed and running on the system, so installing it again would not have created a visible difference in the port scan results.
-  Thats why I vsftpd (FTP server) because it was a new service, guaranteeing it would provide a clear comparison for the assignment with previous one.
-  The vsftpd (Very Secure FTP Daemon) package was selected as it is a standard, lightweight FTP server commonly available in Linux repositories (wiki.archlinux.org, n.d.).
-  I installed and launched vsftp using the commands below:
  
  ```bash
sudo apt install vsftpd -y
sudo systemctl start vsftpd
```

-  After disabling the network again, I ran nmap for port scanning similar to the previous task using the command below:
  
  ```bash
sudo nmap -A localhost

```

-  Sample of the scan output:
```bash
Host is up (0.00012s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 996 closed tcp ports (reset)
PORT STATE SERVICE VERSION
21/tcp open  ftp   vsftpd 3.0.5
22/tcp open  ssh   OpenSSH 10.0p2 Debian 7 (protocol 2.0)
80/tcp open  http  Apache httpd 2.4.65 ((Debian))
|_http-server-header: Apache/2.4.65 (Debian)
|_http-title: Apache2 Debian Default Page: It works
631/tcp open ipp CUPS 2.4
|_http-server-header: CUPS/2.4 IPP/2.1
|_http-title: Home -  CUPS 2.4.10
| http-robots.txt: 1 disallowed entry
```
 ### Differences compared to the previous task
 - The new nmap scan reveals port 21 is now open, which was not present in the initial scan.
 - The scan detected the new service: ftp with the specific version vsftpd 3.0.5.
 - Conclusion: Installing a daemon opens new network ports, directly increasing the system's "attack surface" by creating new potential  entry points that must be managed and secured.

<br><br> Sources Used: 
- wiki.archlinux.org. (n.d.). Very Secure FTP Daemon - ArchWiki. [online] Available at: https://wiki.archlinux.org/title/Very_Secure_FTP_Daemon.

   
---

## d) Bandit oh-five
### Level 0
I learned how to connect to a remote server with SSH and read a simple text file using cat.

<img width="526" height="121" alt="Screenshot 2025-09-09 at 12 43 19 AM" src="https://github.com/user-attachments/assets/32ba6c81-4ce2-4219-b787-1fa97c46b9c6" />

### Level 1
I figured out how to open a file with a tricky name "-" by using ./ to tell the command it’s a file, not an option.

<img width="319" height="57" alt="Screenshot 2025-09-09 at 12 43 53 AM" src="https://github.com/user-attachments/assets/7667ce36-30e9-4892-a9c1-48fe9009815f" />

### Level 2
I discovered how to read a filename that contains spaces by wrapping it in quotes or escaping spaces.
    
<img width="469" height="48" alt="Screenshot 2025-09-09 at 12 44 27 AM" src="https://github.com/user-attachments/assets/bf01bf64-cbc2-4e02-b173-0b2b8f46c5ea" />

### Level 3
I explored hidden files inside a folder and used cat to reveal the password.
     
<img width="471" height="146" alt="Screenshot 2025-09-09 at 12 45 01 AM" src="https://github.com/user-attachments/assets/eb21fa21-f85b-49b5-ab5d-7ca78b1ecd4f" />

### Level 4
I practiced identifying the correct file among many by using the file command to check which one was human-readable text.

<img width="674" height="168" alt="Screenshot 2025-09-09 at 12 45 47 AM" src="https://github.com/user-attachments/assets/8a31c411-6b3f-4dad-9093-ce1364644da0" />

<br></br> Final Thoughts:
- At first, I kept messing up with the file names and didn’t understand why the commands weren’t working, but slowly I noticed that small details like spaces, dashes, or hidden dots actually matter a lot in Linux. Each level felt a bit tricky, but once I got the right command it made sense. I still feel like I have to look things up a lot, but now I’m less scared of the command line because I’ve seen how problems can be solved step by step.
- Although I wanted to challenge myself, I had to resort to a walkthrough on levels 3 and 5 since some of the concepts were fairly new to me.
- link: https://mayadevbe.me/posts/overthewire/bandit/overview/


  






