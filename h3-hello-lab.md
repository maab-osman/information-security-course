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
  
