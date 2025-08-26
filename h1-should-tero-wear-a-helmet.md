# Should Tero Wear a Helmet?
*Information Security Course Homework*  
**Source:** [Karvinen 2024: Information Security Course](https://terokarvinen.com/information-security/)

---

## 1. Threat Modeling Articles & Videos

**Braiterman et al 2020: Threat Modeling Manifesto**  
- Key points:
  - Threat modelling can be defined as  analyzing representations of a system to highlight concerns about security and privacy characteristics.
  - Need: It allows us to pinpoint design and implementation issues that require mitigation throughout a system's lifecycle.
  - The output of a threat model is known as threats.
  - Threats inform decisions that you might make.
  - Threat modelling is catered to everyone, especially those who are concerned for their privacy and security.
  - The Manifesto is highlighted under 2 guidelines: Values and Principles.

    a. Value is something that has relative worth or importance
    - Some values include:
      
      - People and collaboration
      - Doing Threat modelling
      -  Continuous refinement
        
    b. Principles describe the fundamental truths of threat modelling. There are 3 types:
    
      1. Fundamental: truths that enable successful threat modelling
         - The best use of TM is to improve the security and privacy of a system through early and frequent analysis.
         - The outcomes of TM are meaningful when they are of value to stakeholders.
         - TM must align with an organization's development practices and follow design changes and iterations.
           
      2. Patterns that are highly recommended
         - Systemic Approach: use of structure during process/
         - Informed creativity: include both craft and science
         - Varied Viewpoints: prioritize diverse ideas.
           
      4. anti-patterns that are avoided.
         - Hero Threat Modeler: TM is not exclusive.
         - Admiration for the problem: prioritize finding practical and relevant solutions.
         - Tendency to overfocus: Always remember the big picture.
         
- ### Thoughts and questions:
  - Creativity and systemic approaches must coexist, as too much focus on one may compromise the other.
  -  Communicating threat model outcomes in a way that stakeholders find meaningful is as important as identifying threats themselves.
  - Informed creativity is recommended as a pattern. How do we measure or evaluate creativity in threat modeling without compromising rigor?
  - Varied viewpoints are highlighted as essential. Which stakeholders are often overlooked, and how can their perspectives be integrated?
  - Applying these principles in fast-paced environments can be challenging but necessary to keep systems secure.
  ---
 
**Shostack 2022: World's Shortest Threat Modeling Course (12 parts)**  
- Key points:
  - We threat model to anticipate problems when they're inexpensive to deal with, before the start of any project.
  - It is easier to make changes early on, as TM is a set of methods that allows us to think of security to ensure the security of the project.
    
  - The 4-question framework of TM includes:
    1. What are we working on?
       -Whiteboards, Value of collaboration (Creating simultaneously), could be much wider.
      - Collaborating to help us answer this question is essential.
      - Sketching is a way to create inputs and list down issues that could help us answer the next question in the framework.
      - Records help us learn new things about the system we are working on and help us fill necessary details.
      - Data Flow diagrams are important as threats tend to follow data. They are also simple and easy to use to help us understand what we are working on.
      - Flow diagrams include 5 symbols:
          1. External entities: outside our control (sharp pointy corners)
          2. Processes: Any running code under our control 
          3. Data Flows: The element to connect entities and processes.
          4. Data Stores: where data is stored (drunms)
          5. Trust boundaries: where we show that different elements are operated by different entities and control is enforced. <br><br>

 
   
             
        <img width="600" height="300" alt="Screenshot 2025-08-26 at 1 51 19 PM" src="https://github.com/user-attachments/assets/8c809dd3-03cf-4b44-9165-db5f2d137e4e" />

    2. What could possibly go wrong?
       - The heart of TM
       - STRIDE or Kill Chain frameworks can help us answer these questions.
       - Structures can be helpful as well.
       - The STRIDE structure stands for: Spoofing, Tampering, Repudiation, Information Disclosure, Denial Disclosure and Elevation of Privileges. Each of these are problems that occurs in ALL FORMS OF systems like software, IoT, or mobiles.
       - STRIDE is a fundamental way to improve our TM and get better answers for our questions by ensuring that we have at least one threat of each component.
         
    3. What could we do about it?
       -There are many variations, and one constant is "we are going to track our work".
       - Each problems need something to be done about it.
       - The key is not to ignore these issues and treat them as development items.
       - Risk management is applied to a subset of the threats under TM to help us control the impact and make a decision.
       - TM precedes risk management and informs it.
         
    5. Did we do a good job?
       - Would you recommend this project to your friend/colleague? If not, TM has not been applied efficiently.
       - The model must be reviewed by all stakeholders at this stage.
  
    
    
- ### Thoughts and questions:
  - How do we measure the effectiveness of a threat model?
  - Emphasizing data flow diagrams highlights the importance of understanding how information moves, not just where it is stored.

     ---

**OWASP Cheat Sheets Series Team 2021: Threat Modeling Cheat Sheet**  
- Key points:
  - The article mentions key points mentioned earlier, but goes into depth on the advantages and challenges of threat modelling.
    
  - The Advantages of TM include:
      - Identifying risks early on: TM focuses on identifying potential security issues during the early design phase.
      - Increased Security Awareness: Result of the increased creative and critical thinking among participants that challenges them to "think like an attacker"
      - Improved Visibility of Target of Evaluation: Result of the deep understanding of a system being evaluated.
  -  TM can be challenging for development teams for several reasons that include:
      - Lack of knowledge and experience in the field of security is hindering the process of modelling. This may result in overlooked issues. 
      - Complex and time-consuming due to its systematic approach. This may lead to frustration and discouragement.
      - Communication and collaboration between different teams. This may misdirect the project or leave it incomplete.

  - The challenges mentioned above can be addressed through:
    - Inviting Security experts and teams to TM sessions, which can significantly improve the process.
    - Invest in regular IT security training for development teams.
    - Implement processes and tools that simplify and automate threat modelling.
    - Promote a culture of security within an organization.
    - Regular review sessions and cross-team workshops.
    - 
- ### Thoughts and questions:
  - Early identification of risks is only useful if organizations actually act on the findings. 
  - The suggestion to promote a security culture stands out, since it shifts TM from being a one-time exercise to becoming part of everyday development.  
  - Are automated TM tools reliable enough to reduce workload, or do they risk missing threats?
   ---


## 2. Infosec Scene Podcast

**Darknet Diaries Episode:** *Episode 25: Alberto*  

- Alberto, a 41-year-old Uruguayan. A skilled and well-credentialed InfoSec professional (former Interpol specialist) detected and responsibly reported a critical vulnerability  on a medical provider's website, but two years later, he was framed as the perpetrator of a ransomware attack.

- On the Saturday morning of 2015, his girlfriend wanted to log into the medical institute to access her health record. When he poked around the website, and was able to log in as the admin easily. He had access to every single information on their system. This was a severe vulnerability.
  
- He immediately sent an email to the Uruguayan CERT, and they resolved it.
  
- In Feb 2017, someone hacked the same server. Alberto was one main suspects. The interpol visited his home, where Alberto told them everything and how exactly he found the issue 2 years ago. The police were suspicious of him and decided to hold him in jail.
  
- During the home search, the police found hacking tools, crypto wallets, security equipment, and paraphernalia like a rubber ducky and an Anonymous mask in his home. Rather than recognizing them as standard InfoSec tools or educational props, they used this as confirmation of guilt.
  
- The police also found 30 credit cards and 13,000 Euros in cash, which increased their suspicion, but Alberto claimed he needed them for crypto trading.

- High psychological pressure and threats toward his family pushed Alberto into a false confession.
  
- They powered on devices instead of creating forensically sound disk images and left a large portion of Alberto’s devices and data unexamined, jeopardizing evidence integrity.

- The incident devastated his girlfriend’s mental health, resulted in the loss of their relationship, and inflicted trauma that lasted well beyond the incident.
  
- This was the first time a hacker had gone to prison in Uruguay, so it was a big deal.  The police may have hyped up the story too, thinking it was a great achievement for them to have captured a dangerous hacker.

- Once in prison, Alberto was showered with admiration by other inmates, earning status as “the hacker,” very different from how law enforcement treated him.

- After spending nine months in prison, Alberto was set free. To Alberto, the investigation went wrong in a million ways.  The police weren’t knowledgeable enough on how to handle this case, and didn’t take all the evidence, and they handled the evidence poorly.

Security Community vs. Legal Perception
The episode poses a key question: why do security professionals embrace hacker culture? The answer lies in that very closeness to their adversaries—it’s a practical necessity for defending networks effectively.
  
- ### Lessons learned:
  - Even when vulnerabilities are reported responsibly, organizations may not act, leaving both systems and the ethical hacker exposed.
  - This case highlights the risk of bias: investigators saw Alberto’s hacker tools as incriminating instead of professional.
  - The stigma around “hackers” damages the trust needed between security professionals and law enforcement.
  - Security is not just technical; it deeply affects people’s lives, relationships, and reputations.
    
- Questions:
  - Could mandatory security training for investigators prevent these kinds of miscarriages of justice?
  - How can organizations create safer channels for responsible disclosure so ethical hackers don’t risk becoming suspects?
    
---

## a) Security Hygiene


**Basic Security Practices (NordVPN, 2024):**  
- Strong, unique passwords/password manager  
- Multi-factor authentication  
- Regular software updates  
- Email and phishing awareness  
- Device encryption  
- Backup of critical data  
- Use of VPN on public networks  

**Company Security Hygiene (ACSM_Accro, 2024) :**  
- Network segmentation
- Automating software patching
- Setting up data backups
- Security awareness training  
- Incident response plan  
- Regular audits and penetration tests  

---
<br>

## b) Make-Believe Boogie-Man – Threat Model for Imaginary Company

### Company Overview
- **Name: GlowWell**  
- **Business: A tech company that delivers personalized skincare and wellness products through a subscription model**  

### (1) What are we working on?
  - The key assets and their priority:
      - Skin and health data (High): sensitive information regulated under GDPR
      - Payment info (High): financial risk
      - Customer profiles (Medium): Personalized, no sensitive info.
      - Product inventory (Low): only operational risk.
      - Recommendation chatbot (Medium):

    **Diagram of company systems:**  

    <img width="750" height="537" alt="Screenshot 2025-08-26 at 4 45 02 PM" src="https://github.com/user-attachments/assets/20386f60-3915-4fd0-a40a-11a4269ceb8f" />


    **Customer Touchpoints:** 
    - Website and App
    - Email
    - AI chatbot
    - Delivery Tracking
 

### (2) What Can Go Wrong?
- Threat modeling techniques used (Poston, 2021):
   - STRIDE
   - CIA
   - MITRE ATT&K
  
  **Threats modelling table example:**  

  <img width="756" height="351" alt="Screenshot 2025-08-26 at 5 03 52 PM" src="https://github.com/user-attachments/assets/a60fbcc4-5eef-4d6a-b3f1-8fdac9c37537" />

 
  **Threat Actors (Catalan, 2024):**
  - Cybercriminals
  - Competitors
  - Insiders (people with access to customer data)

   **Known TTPs: (www.pentestpeople.com, n.d.)**
  - Malware attacks: malicious software that gains access to personal information.
  - SQL Injection Attacks: used to delete, change, or even control data or an entire database.
  - Phishing: to steal login or payment info
  - Insider misuse: abusing access rights
  - Denial of Service (DoS): prevents users from accessing the site.

  **Risk Prioritization:**
  1. Data breach
      - Probability: Medium
      - Impact: Very High
  2. Payment Fraud
      - Probability: Medium
      - Impact: Very High
  3. AI manipulation
      - Probability: Low
      - Impact: Medium

  **Business Continuity (coder, 2024):**
  - Must maintain app uptime and data integrity.
  - Conduct a Risk and Impact Assessment
  - Develop a detailed plan for essential operations.
  - Encourage a Security Awareness Culture among employees.

 

### (3) What Are We Going to Do About It?
- Mitigation strategies and META (Khurana and Kaul, 2019) :  
  - implement MFA AND login alerts to avoid account takeovers: Mitigate
  - Input validation and model monitoring to avoid chatbot manipulation: Mitigate
  - Encryption and access control to control data breaches: Mitigate
  - Use Stripe/PayPal (third-party services) to combat fraud: Transfer
  - Role-based access to eliminate insider misuse: Mitigate
    

### (4) Did We Do a Good Enough Job?
- Continuous evaluation:
    - Security audits: Regularly assessing an organization's security controls to ensure compliance with standards and policies.
    - Penetration tests: Simulating a cyberattack to find and exploit vulnerabilities in systems and applications.
    - Threat modelling: Identifying and analyzing potential threats to a system (Shostack, n.d.)
    - Monitoring:  Continuously collecting and analyzing data from IT systems to detect and respond to security incidents in real time. (Hpe.com, 2022)
- Process improvement notes:
    - Security is ongoing.
    - Threat model evolves with new features, threat intelligence, and customer feedback.

---

## Sources / References
- Coder, seo (2024). Seven Best Practices for Business Continuity | BCG. [online] Bcg1. Available at: https://www.businesscontingencygroup.com/post/7-best-practices-for-an-effective-business-continuity-plan [Accessed 26 Aug. 2025].
- Hpe.com. (2022). What is Security Monitoring? | Glossary. [online] Available at: https://www.hpe.com/emea_europe/en/what-is/security-monitoring.html.
- Terokarvinen.com. (2025). Information Security - 2025 early autumn - ICI002AS2AE-3007. [online] Available at: https://terokarvinen.com/information-security/.
- www.threatmodelingmanifesto.org. (n.d.). Threat Modeling Manifesto. [online] Available at: https://www.threatmodelingmanifesto.org/.
- Shostack. (n.d.). World’s Shortest Threat Modeling Course. [online] Available at: http://www.youtube.com/playlist?list=PLCVhBqLDKoOOZqKt74QI4pbDUnXSQo0nf [Accessed 26 Aug. 2025].
- OWASP (2024). Threat Modeling. [online] cheatsheetseries.owasp.org. Available at: https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html. 
- darknetdiaries.com. (2018). Alberto – Darknet Diaries. [online] Available at: https://darknetdiaries.com/episode/25/.
- NordVPN. (2024). Personal cybersecurity: 23 tips and best practices. [online] Available at: https://nordvpn.com/blog/personal-cybersecurity/.
- ACSM_Accro (2024). How Businesses Can Achieve Effective Cyber Hygiene. [online] Australian Cyber Security Magazine. Available at: https://australiancybersecuritymagazine.com.au/how-businesses-can-achieve-effective-cyber-hygiene/.
- Poston, H. (2021). Top threat modeling frameworks: STRIDE, OWASP Top 10, MITRE ATT&CK framework and more | Infosec. [online] www.infosecinstitute.com. Available at: https://www.infosecinstitute.com/resources/management-compliance-auditing/top-threat-modeling-frameworks-stride-owasp-top-10-mitre-attck-framework/.
- Catalan, C. (2024). A Comprehensive Guide to 7 Types of Threat Actors. [online] Teramind Blog | Content For Business. Available at: https://www.teramind.co/blog/types-of-threat-actors/.
- www.pentestpeople.com. (n.d.). The Top 5 Cyber Threats Facing Businesses Today. [online] Available at: https://www.pentestpeople.com/blog-posts/the-top-5-cyber-threats-facing-businesses-today.
- Khurana, R. and Kaul, D. (2019). Dynamic Cybersecurity Strategies for AI-Enhanced eCommerce: A Federated Learning Approach to Data Privacy. [online] Available at: https://www.researchgate.net/publication/386347451_Dynamic_Cybersecurity_Strategies_for_AI-Enhanced_eCommerce_A_Federated_Learning_Approach_to_Data_Privacy.

‌

‌

‌

‌

‌

‌

‌
- Other sources used:  

      
