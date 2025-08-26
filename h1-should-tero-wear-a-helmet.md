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
  - The manifesto emphasizes “values” like collaboration and continuous refinement. How do we ensure these are actually practiced in large teams?
  - Fundamental principles stress alignment with development practices. Could misalignment create a false sense of security even if a threat model exists?
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
  
    
    
- Thoughts and questions:
  - How do we measure the effectiveness of a threat model?
  - Emphasizing data flow diagrams highlights the importance of understanding how information moves, not just where it is stored.

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


## 2. Infosec Scene Podcast

**Darknet Diaries Episode:** *[insert episode]*  
- Key points:
  - 
  - 
- Lessons learned / observations:
  - 
  - 
- Questions / Ideas:
  - 
  - 

---

## a) Security Hygiene

**Basic Security Practices (Everyone should follow):**  
- Strong, unique passwords / password manager  
- Multi-factor authentication  
- Regular software updates  
- Email and phishing awareness  
- Device encryption  
- Backup of critical data  
- Use of VPN on public networks  

**Company / Organizational Security Hygiene:**  
- Network segmentation  
- Security awareness training  
- Incident response plan  
- Regular audits and penetration tests  

---
<br>

## b) Make-Believe Boogie-Man – Threat Model for Imaginary Company

### Company Overview
- **Name:**  
- **Business:**  
- **Customer touchpoints / key assets:**  
- **Diagram of company systems:**  

