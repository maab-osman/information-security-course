# Hello Lab - Week 3
This week, I start building my own hacking lab. The goal is to **learn hacking by hacking**.  

---

## Reading tasks Summary

### Karvinen 2021: Install Debian on Virtualbox - Updated 2024
- Easy and clear guide to download the Debian ISO.
- Install VirtualBox and create a new virtual machine.
- Use “Expert Mode” and skip “Unattended Install”.
- Set up the VM with enough RAM and a big virtual disk.
- Add the ISO as a virtual CD and boot the VM.
- Try the live desktop first to test stuff before installing.
- Run the installer, choose English and Finnish settings, and set up user info.
- After install, log in and update everything using terminal commands.
- Install a firewall and reboot.
- To fix small screen and enable copy paste, install VirtualBox Guest Additions.

  My thoughts:
  - I had no idea what an ISO was, but it’s just like a digital CD
  - I used the arm64 version since I’m on a Mac with Apple Silicon
  - Gave the VM 4GB RAM and 60GB disk, seemed to run okay.
  - Didn’t hit the black screen bug, but good to know about the xforcevesa trick just in case.
  - UTM was a better option in my case instead of VirtualBox as it had some issues there.
  
  
### Karvinen 2020: Command Line Basics Revisited
- The command line is super old but still super useful.
- pwd, ls, and cd to move around folders.
- nano filename lets you edit files in the terminal.
- mkdir, mv, cp, and rm are for making, moving, copying, and deleting stuff.
- Be careful with rm -r as it deletes everything with no undo!
- ssh lets you connect to other computers remotely.
- scp is for copying files between computers.
- Use man or --help to learn what a command does.
- history shows your past commands, and ctrl + R helps you search them.
- Important folders: /home/, /etc/, /media/, /var/log/.
- sudo gives you admin powers.
- Install software with sudo apt-get install packagename.
- Remove stuff with sudo apt-get purge packagename.
- You can play a game called Nethack in the terminal.

  Thoughts:
  - I have some experience with the command line but it was nice to referesh some concepts that I dont use on the daily .
  - Got to learn about the about the important directories but still don’t fully understand their practicality.

---

## a) Can't Fish
Disable networking and show that packets don’t go through.  

- Successfully disabled networking and demonstrated that packets cannot traverse outside the local system.
- I did it by configuring UTM VM network mode to "Host Only" to restrict external network access
  <img width="630" height="111" alt="Screenshot 2025-09-08 at 9 56 47 PM" src="https://github.com/user-attachments/assets/29c5fbf2-a29c-4308-b401-c8570b73430d" />
- I used the commmand down below to test connectivity to Cloudfare's DNS server
 
```bash
ping -c 4 1.1.1.1
```

- The result recived was "Network is unreachable", proving zero packet transmission to external networks.
  <img width="422" height="89" alt="Screenshot 2025-09-08 at 9 55 07 PM" src="https://github.com/user-attachments/assets/2bd308aa-02c6-4991-9632-170ae3930f00" />

## b) Local Only
-  Successfully performed portscan of localhost using nmap
-  From the previous task, the network remained in "Host Only" mode throughout the scan
-  For this task I had to install nmap using this command

  ```bash
sudo apt install nmap
```

-  Then I utilized nmap for port scanning in this assignment. I used this command to scan:
  
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
 - PORT STATE SERVICE VERSION is the header for the results each indicating its state.
 - The port 22 OpenSSH allows secure remote command-line access to the system.
   
```bash
22/tcp open 55h OpenSSH 10.0p2 Debian 7 (protocol 2.0)

```
 - After research about this specific program, I discovered That it must be protected with a very strong password because hackers love to try and break into it.
   
 ```bash
80/tcp open http Apache httpd 2.4.65 ((Debian))

```
 - Service on Port 80 HTTP is a web server hosting the default "It works!" page. This website host means that my computer can now act as a mini-webserver, but like SSH, it needs to be kept updated to be secure.
   
 ```bash
631/tcp open ipp CUPS 2.4

```
   
 - Service on Port 631 open IPP is a printing service called CUPS for managing printers.
 - I learned that this is a standard helper service on many Linux systems and usually not high risk if connected to a network.

  ## b) Daemon Scan
  
- The Apache web server was already pre-installed and running on the system, so installing it again would not have created a visible difference in the port scan results.
-  Thats why I vsftpd (FTP server) because it was a new service, guaranteeing it would provide a clear comparison for the assignment with previous one.
-  The vsftpd (Very Secure FTP Daemon) package was selected as it is a standard, lightweight FTP server commonly available in Linux repositories
-  I installed and launched vsftp using the commands below:
  
  ```bash
sudo apt install vsftpd -y
sudo systemctl start vsftpd
```

-  After disabling the network again, I ran nmpap for port scaning similar to the previous task using the command below:
  
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




