# Homework: Kill Chain  

### Hutchins et al. 2011: *Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains*  
- **Abstract**  
  - Older security methods, like antivirus software, only focus on fixing weaknesses after a hacker has gotten in.
  -  With progress in time, we saw the emergence of Advanced Persistent Threat (APT) that represents highly trained and  well-resourced adversaries that steal information over a longer period of time.
  -  Unlike others, they are too sophisticated for the old security tools to stop.
  -  Intelligence-driven defense is a proposed solution introduced to combat them using an intelligence-based security model. This solution includes:
      - Creating an intelligence feedback loop to gain more information about the adversary.
      - Using a kill chain model to deconstruct an intrusion.
      - Predicting their actions based on gathered data.
      - Connecting smaller attacks to understand the bigger picture of their so-called "campaigns"
  - The main idea from the abstract conveys that instead of just trying to fix weaknesses, we can actively track and disrupt the specific hacker.
  - This model addresses the threat component of risk, not just the vulnerability component. It allows us to disrupt the attacker's process proactively.
  - There are also strategic advantages like:
      - Reduces the adversary's chance of success systematically.
      - Reduces resources and investments spent due to the data collected.
      - Creating helpful metrics for evaluating the performance and its effectiveness.
    
- **3.2 Intrusion Kill Chain**  
  - The intrusion kill chain is a model that simply breaks a cyberattack into a sequence of seven required phases.
  - It is adapted from military targeting doctrine.
  - The key principle here is that a "chain" is a process in which each phase is linked. Meaning, disrupting a single link will make the whole attack fail.
  - The seven phases of intrusion include:
    1. Reconnaissance: Attacker searches and chooses a target.
    2. Weaponization: The attacker couples malicious code with an exploit into a deliverable payload
    3. Delivery: The weaponized payload is transmitted to the target.
    4. Exploitation: The malicious code is triggered on the victim's system.
    5. Installation: The attack installs malware on the system to maintain access.
    6. Command & Control: A connection has been established between the target's system and the attacker, allowing them to gain remote control.
    7. Actions on Objectives: The attacker accomplishes their goal, whether it be by stealing data, destruction or or using the system to move laterally to other parts of the network.

**My Questions and thoughts:**  
- Speaking practically, how does the intelligence feedback loop realistically work? Like, how does a normal company set it up?
- How much monitoring is required to gain "information superiority" as mentioned in the text? Where do we draw the line between monitoring and surveillance?
- Since this paper was written back in 2011, is the kill chain still relevant today? Do all attacks follow the seven steps in order?
- In the kill chain, which phase is the easiest for defenders to break?
- After reading about the kill, I'm curious to see a real-world scenario of how it can be executed.

**Reference:**  
- Hutchins, E., Cloppert, M. and Amin, R. (2011). Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains. [online] Available at: https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf.

---

## Task a) Tactics, Tools, and Procedures  

### MITRE ATT&CK Matrix for Enterprise (General FAQ)  
- **Definition of Tactic:**  
  - Tactic is described as the "why" of an ATT&K technique or sub-technique. It is the reason for acting.
  - *Example:* A good example can be the lateral movement. The adversary's goal here is to move through someone's network to reach a specific target system.
 
    
- **Definition of Technique and Subtechnique:**  
  - Technique is described as the "how", the method used by adversaries to achieve a goal.
  - *Example Technique:* Phishing (T1566) is a technique used to achieve initial access.
  - Subtechnique is described as a more specific description of the malicious behavior. It provides more detail about "how" the technique is executed.
  - *Example Subtechnique:* Spearphishing Attachment (T1566.001) is a good example as it is a specific type of phishing.
    

- **Definition of Procedure:**  
  - Procedure is the specific implementation of a particular adversary or tool used to perform a technique or subtechnique.
  - *Example:* An adversary uses a specific PowerShell command to download their payload. That exact command is the procedure.

**My Questions and thoughts:**  
- The framework is extensive. What methodologies are used to prioritize which techniques to defend against first?
- How can we use ATT&CK to measure the effectiveness of our defense? Can we "score" ourselves on how many techniques we can detect or mitigate?
- How is the ATT&CK matrix kept current? What is the process for adding a new technique or sub-technique based on a newly observed adversary procedure?

**Reference:**  
- Mitre.org. (2015). FAQ | MITRE ATT&CK®. [online] Available at: https://attack.mitre.org/resources/faq/#general-faq [Accessed 1 Sep. 2025].
- MITRE (2025). MITRE ATT&CK. [online] Mitre.org. Available at: https://attack.mitre.org/.

‌
---


## Task c) (Voluntary Bonus) Attack Story  

- **Initial Access**: An attacker sends a Spearphishing Attachment (T1566.001) to an employee. The email has a fake invoice attached. 
- **Execution**: The employee opens the attachment, which is a malicious Word document. This runs a script, using User Execution (T1204) to launch the malware. 
- **Persistence**: The malware creates a new scheduled task on the computer (T1053.005). This task is set to run the malware every day, ensuring the attacker stays in the system. 
- **Defense Evasion**: The malware disguises itself as a legitimate Windows process, a technique called Masquerading (T1036). This helps it avoid detection by simple antivirus software.
- **Exfiltration**: Finally, the malware collects important files and secretly sends them out to a server controlled by the attacker (T1567).

**Defensive Actions:**  
- Teach employees how to spot phishing emails.
- Use security tools to block malicious emails before they reach the inbox.
- Keep software updated to fix vulnerabilities and malware exploits.
- Use advanced security software that can detect suspicious behaviors.
- Watch for unusual outbound traffic to unknown websites.

---



## References
- MITRE (2025). MITRE ATT&CK. [online] Mitre.org. Available at: https://attack.mitre.org/.
- Darktrace.com. (2017). Darktrace. [online] Available at: https://www.darktrace.com/cyber-ai-glossary/cyber-kill-chain.
- Trellix.com. (2025). Available at: https://www.trellix.com/security-awareness/threat-intelligence/what-is-mitre-attack-framework/.
- Securonix. (n.d.). Threat Chains: Combating Today’s Multi-Tier Threat Landscape. [online] Available at: https://www.securonix.com/blog/threat-chains-combating-todays-multi-tier-threat-landscape/.

‌

‌

