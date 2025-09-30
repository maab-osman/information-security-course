# Homework H6 - Going Dark

> **Legal & Ethics Reminder**  
> In Finland, it’s legal to use TOR at the time of writing.  


---

## x) Reading Summaries

### Quintin (2014) – *7 Things You Should Know About Tor*
- Tor still works for anonymity, even against powerful surveillance.
- It’s not just for criminals, its also used by journalists, activists, and everyday people.
- No secret military backdoor, Tor is open-source and audited.
- Running a Tor relay is legal in the U.S., but exit relays may attract attention.
- Tor is easy to use with tools like Tor Browser and Tails OS.
- Speed has improved, but it’s still slower than regular browsing.
- Tor isn’t foolproof, we must follow best practices to stay anonymous.


**Reflection**

- I didn’t realize how many regular people rely on Tor for safety online.
- It’s cool that Tor is open-source as makes it more trustworthy.
- I will be more careful about how I use browsers if I want real privacy.
- It’s reassuring that using Tor isn’t illegal, even if it seems “suspicious.”

Source: Quintin, C. (2014). 7 Things You Should Know About Tor. [online] Electronic Frontier Foundation. Available at: https://www.eff.org/deeplinks/2014/07/7-things-you-should-know-about-tor.

‌
---

### Shavers & Bair (2016) – *Hiding Behind the Keyboard: The Tor Browser*

#### Introduction
- Tor is a modified Firefox browser designed for anonymous internet use.
Its main function is to hide your real IP address, making you very difficult to trace.
It's easy to use, free, and doesn't require technical knowledge to operate.
It's one of the most effective and simple tools for anonymous browsing and communication.

#### History and Intended Use of The Onion Router

- Originally created by the U.S. government in 2002 to protect communications.
- Its legitimate uses include bypassing censorship, whistleblowing, and securing private business chats.
- Like any tool, it can be misused for crime.
- It's now an open-source project, maintained by a global community, not controlled by any single government.  

#### How The Onion Router Works
- Our internet traffic is routed through at least three random volunteer-run relays which are Entry, Middle, and Exit.
- Our data is wrapped in multiple, unbreakable layers of encryption, like an onion.
- Each relay peels off one layer of encryption, only knowing the immediate previous and next relay.
- The Exit relay connects to the final website, not knowing the original source.
- The path changes every 10 minutes for extra security

#### Tracking Criminals Using TOR
- Directly breaking Tor's encryption is nearly impossible for most law enforcement.
- The biggest weakness is the user. Mistakes are the primary way suspects are caught.
- Common investigative tactics include:
    - Exploiting software flaws like the FBI hacking a server to infect visitors' browsers.
    - Social engineering by sending tracking links in emails or documents to get the real IP address.
    - Correlating activity by finding a suspect's identity on the open web.
    - Network monitoring through identifying who on a specific network (like a school or company) was using Tor at the exact time a threat was sent.


**Reflection:**  
- It's impressive how a piece of software can provide such anonymity to anyone.
- The "onion" analogy made the complex cryptographic process easier for me to visualize.
- The system's design is clever because no single relay has the full picture.
- This chapter shows that human error is the biggest vulnerability. It's a classic case of the system being only as strong the person using it.
- I was suprised to learn that most investigations succeed through traditional detective work, not by "breaking" the tech.

Source: Shavers, B. and Bair, J. (2016). Hiding Behind the Keyboard. Syngress.

---

## a) Install TOR Browser and Access .onion Network

## Initial Plan (Failed Trials)

### Trial 1 - Tor Browser
- The teacher provided several pathways: the official Tor Browser download, the torbrowser-launcher, Tails OS, or Whonix.
- I downloaded the Tor Browser Bundle, excited to get started. But when I tried to run it, my screen flashed with an error that would become all too familiar: "requires a CPU with SSE2 support.
<img width="600" height="400" alt="Screenshot 2025-09-30 at 11 29 48 AM" src="https://github.com/user-attachments/assets/6caac762-1e71-4c65-a675-151e8818caa8" />

<br></br>

  - Possible reason for this is that I was running this in a UTM virtual machine on my Mac, and apparently, the emulation didn't include this instruction set.
  -  I tried the 32-bit version next, thinking it might be more compatible. But then I encountered 404 errors, the specific version I needed didn't exist for 32-bit architecture.

    
### Trial 2 - Tor Launcher
- The second availabe option was **torbrowser-launcher**. I ran the commands and this was the result:
<img width="813" height="243" alt="Screenshot 2025-09-30 at 11 47 19 AM" src="https://github.com/user-attachments/assets/f750aee1-4a43-4e6b-bae6-55585375fe89" />
<br></br>

- There were missing dependencies (software-properties-common) and other tools weren't available in default repositories.
- Also Tor Project repository signing issues prevented secure installation.

### Trial 3 - Tails Os
- I also tried Tails operating system that routes everything through Tor. I downloaded the IMG file, expanded it as others had suggested, and configured UTM with precise settings. It booted!

<img width="792" height="514" alt="Screenshot 2025-09-30 at 11 42 02 AM" src="https://github.com/user-attachments/assets/5312295c-6a65-4dcc-99e3-b90b1709cc17" />

<br></br>

- There were hardware emulation problems as there were USB port errors and other hardware compatibility issues in UTM.
- Expanded .img file approach worked but was impractical for daily use since teh performance was very weak.

## Final Plan (Successful!)
### System-level Tor Installation
- As a final approach, I used system-level Tor installation:
  ```bash
  sudo apt install tor
  ```
    
<img width="796" height="369" alt="Screenshot 2025-09-30 at 12 11 18 PM" src="https://github.com/user-attachments/assets/930ffa0c-9b27-4919-acba-55195f59fdce" />
<br></br>

- I configured Firefox manually  by implementing SOCKS5 proxy 127.0.0.1:9050 through the network settings.
- I then verified Tor connectivity through this address check.torproject.org as seen below:
  
<img width="1029" height="305" alt="Screenshot 2025-09-30 at 12 15 54 PM" src="https://github.com/user-attachments/assets/ec30791e-c4ee-4a4c-bf2f-ad84c06ce3c4" />
<br></br>


- At this point I was able to accessed legitimate .onion sites. So I opened a familiar search engine: DuckDuckGo to begin exploring.

<img width="1280" height="628" alt="Screenshot 2025-09-30 at 10 57 54 AM" src="https://github.com/user-attachments/assets/4929cefe-0079-4afc-a4ed-0cb810a01d48" />
<br></br>


- The search results were primarily from the clearnet. I realized that DuckDuckGo, even when accessed via its .onion address, is still a clearnet search engine that indexes the regular web. It does not exclusively search for .onion sites. This meant that I wasn't fully exploring the Tor network as the assignment required.
- This  led me to seek out a search engine that specifically indexes .onion sites like Ahmia, a Finnish project that is designed to search only within the Tor network. 

<img width="1109" height="503" alt="Screenshot 2025-09-30 at 11 11 23 AM" src="https://github.com/user-attachments/assets/ca5519b1-47f6-485a-ab5b-7a76f8d15f74" />
<br></br>


- I began the exploration by typing keywords like "Marketplace".
  
<img width="947" height="306" alt="Screenshot 2025-09-30 at 11 19 45 AM" src="https://github.com/user-attachments/assets/f8bbbb29-b4a3-4ce2-b244-a0ff574b17f8" />

<br></br>


- The marketplaces had surprisingly professional interfaces like the one below:

<img width="1270" height="690" alt="Screenshot 2025-09-30 at 11 18 04 AM" src="https://github.com/user-attachments/assets/9498154a-1205-4677-ab46-3aa6f93170c0" />

<br></br>


- There were many forumns that I able to find that had detailed discussions about privacy and security. Heres an example:

<img width="1283" height="675" alt="Screenshot 2025-09-30 at 11 18 54 AM" src="https://github.com/user-attachments/assets/b0303386-abd1-468c-888a-7bf3ab3afa42" />
  
<br></br>


- And finally, I decided to search for major organizations like the BBC with a proper .onion address. This wasn't some shady underground site, it was legitimate journalism making itself accessible to people in censored countries.
  
<img width="1263" height="614" alt="Screenshot 2025-09-30 at 11 16 48 AM" src="https://github.com/user-attachments/assets/70fc9c1e-1c7f-46e7-9aba-78ed3d9662fe" />
<img width="947" height="306" alt="Screenshot 2025-09-30 at 11 19 45 AM" src="https://github.com/user-attachments/assets/f8bbbb29-b4a3-4ce2-b244-a0ff574b17f8" />








