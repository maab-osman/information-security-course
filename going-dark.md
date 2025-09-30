# Homework H6 - Going Dark

> **Legal & Ethics Reminder**  
> In Finland, it’s legal to use TOR at the time of writing.  
> If you are remotely taking this course from another jurisdiction, laws might differ.  
> Obviously, it’s illegal to do illegal things in TOR, just like it’s illegal to do illegal things anywhere.  
> Only do legal things.  

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

**Steps taken (choose one):**
- Tor Project: [https://www.torproject.org/download/](https://www.torproject.org/download/)  
- Command line:
  ```bash
  sudo apt update
  sudo apt install torbrowser-launcher -y
  torbrowser-launcher
