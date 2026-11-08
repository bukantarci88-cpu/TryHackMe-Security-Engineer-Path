# Eng 4.6. Weaponizing Vulnerabilities

#### **Task 1 - Introduction**

Weaponizing a vulnerability refers to the process of taking a known vulnerability in a software or system and creating an exploit for it, which can then be used to gain unauthorized access or perform other malicious actions.

Threat actors weaponize individual or chained system vulnerabilities across physical hardware, virtualized platforms, and cloud environments to gain unauthorized or elevated access, while repositories like the National Vulnerability Database (NVD) track this accelerating volume of discovered security flaws.

#### **Task 2 - What is an Exploit?**

Software exploits are malicious code payloads delivered via diverse vectors such as messages, email attachments, or embedded files that, upon execution, grant attackers remote or local system control, cause operational disruption, or enable unauthorized data exfiltration.

Exploits function as specialized technical methods categorized into local privilege escalation or network-based remote execution—often developed and financed by nation-states, criminal syndicates, or specialized brokers on dark web markets—to serve as vehicles for achieving broader operational objectives.

**Answer the questions below**

> What is the term for an exploit that is used to gain control of a system remotely?
> 

remote exploit

#### **Task 3 - Vulnerability Lifecycle**

The Department of Defense Vulnerability Disclosure Program (VDP) leverages the five-stage Lifecycle of a Vulnerability Framework—comprising Discovery, Coordination, Mitigation, Management, and Lessons Learned—to systematically triage, validate, and remediate security vulnerabilities reported by external researchers.

![Different stages of the lifecycle of a vulnerability](https://tryhackme-images.s3.amazonaws.com/user-uploads/62a7685ca6e7ce005d3f3afe/room-content/010b30ab11a3760f6a43d52cb2782c46.png)

- **Product Launched:** A vendor in the public market launches an information technology product (hardware or software).
- **Vulnerability Discovery (Public or Private):** Researchers working independently or sponsored by private/public organizations for various interests discover vulnerabilities in the product. A 0-day vulnerability is one that has yet to be made public after being found. In any other case, when a vulnerability is found, it is made available to the general public via the internet or other special sources. Before the vulnerability is publicly disclosed online, the manufacturer typically has already developed a patch or update for the product at this stage.
- **Development of a Proof of Concept (PoC) or Exploit:** A PoC proving the exploitability of the newly discovered vulnerability is prepared in-house by the vendor or received from bug bounty hunters/independent researchers. It is crucial at this stage to keep the vulnerability disclosure discrete as the PoC is typically the first stage in developing an exploit, and bad actors can use it in the wild.
- **Patch Development or Update:** The product manufacturer creates a patch or update to prevent the known vulnerability from being exploited by adversaries.
- **Patch Release:** The product manufacturer releases the patch for the vulnerability so the customers can apply it to the product in their environment.
- **Patch Install:** The customer or end-users update or patch their systems, so the known vulnerability cannot be used against it.

**Answer the questions below**

> A vulnerability not patched by the vendor and unknown to most people is called a?
> 

0-day 

> What is a commonly used term for a demonstration that proves the exploitability of a newly discovered vulnerability?
> 

Proof of concept

> What does a product manufacturer typically release to prevent a known vulnerability from being exploited by adversaries?
> 

patch

#### **Task 4 - Opportunity for Weaponizing Vulnerabilities**

Vulnerability weaponization is a complex, time-intensive process requiring deep technical expertise to develop or procure custom exploits from underground markets, operating within specific temporal opportunity windows before patches are deployed.

![flow chart of the opportunity period for weaponizing a vulnerability](https://tryhackme-images.s3.amazonaws.com/user-uploads/62a7685ca6e7ce005d3f3afe/room-content/e0bed60e9d9bd82ec747e4fac57d2c30.png)

Zero-day vulnerabilities afford extended exploitation windows ranging from days to years before detection, whereas n-day vulnerabilities face a high-risk window immediately following patch release when adversaries reverse-engineer updates to create rapid exploits prior to enterprise patching.

**Answer the questions below**

> Can it take days, months, or even years to develop a 0-day exploit?
> 

yea

> An exploit developed once the vendor has released the patch is called?
> 

n-day

#### **Task 5 - Exploit Chaining**

Chaining exploits in tandem, also known as "**exploit chaining**" or "**multi-stage exploitation**", is a technique hackers use to string together multiple exploits for vulnerabilities to gain complete control of a target system. The desired goal is to develop a complete **Remote Code Execution (RCE) chain**, allowing the attacker to execute arbitrary code on the target system with the highest privileges.

- **Reconnaissance:** The attacker will gather information about the target system and its vulnerabilities. This can be done through various methods, such as network scanning, port scanning, and vulnerability scanning.
    
    ![Chaining exploits lifecycle](https://tryhackme-images.s3.amazonaws.com/user-uploads/62a7685ca6e7ce005d3f3afe/room-content/6db928385248e0724b3f785390be98fc.png)
    
- **Initial Exploit:** The attacker will use the information gathered during the reconnaissance phase to identify an initial vulnerability that can be exploited, which could be known and that has not been patched. The attacker will use an exploit that takes advantage of this vulnerability to gain access to the target system.
- **Privilege Escalation:** This will allow them to access sensitive information, such as login credentials and system files, and execute code with higher privileges.
- **Persistence:** The attacker will use other exploits to establish persistence on the target system, allowing them to maintain access even if the initial exploit is discovered and patched.
- **Lateral Movement:** The attacker will then use additional exploits to move laterally through the target system's network and compromise other systems. This will allow them to gain access to additional sensitive information and resources.
- **RCE**: Once the attacker has established persistence and moved laterally through the network, they will use the final exploit in the chain to gain RCE. This may include using malware to gain control of the target system or a privilege escalation exploit to gain access to the target system's kernel.

**Answer the questions below**

> What is the technique called to string together multiple exploits?
> 

Exploit chaining

> After initial access to the system, the process for gaining higher access within the system is called?
> 

Privilege escalation

> The step in which the adversary tries to maintain long time access to the system is called?
> 

persistence

#### **Task 6 - Chaining Multiple Vulnerabilities - A Case Study**

To demonstrate the process for **"exploit chaining in tandem to develop a complete RCE Remote Code Execution (RCE) chain"**, let's examine a real-world situation. The exercise focuses more on how to chain vulnerabilities than **how to exploit a vulnerability**.

**How to Chain Multiple Exploits:** Using a case study, let's dig deeper into various phases of exploit chaining. The installation procedure and the fundamental commands are not covered as the goal of this study is to chain exploits for developing a complete RCE chain.

![Login form for the web application](https://tryhackme-images.s3.amazonaws.com/user-uploads/62a7685ca6e7ce005d3f3afe/room-content/c10ae7f395dcc50b72d71ca5a2e7adb9.png)

**Answer the questions below**

> What is the response when we enter email [test@chatai.com](mailto:test@chatai.com)' as user email and password 123 in the login form?
> 

undefined

<img width="512" height="583" alt="image" src="https://github.com/user-attachments/assets/d86aa3af-1e20-4ba3-b30c-8791cff61540" />


> Execute the command whoami, what is the output you receive?
> 

nt authority\system

<img width="528" height="305" alt="image 1" src="https://github.com/user-attachments/assets/cfcf0fe4-ea7c-4d55-be7d-b8b55c32411d" />


> Have you noticed the file flag.txt in the web root directory? What is the flag value?
> 

THM{010101_PAWNED}

<img width="658" height="341" alt="image 2" src="https://github.com/user-attachments/assets/68f24edd-4ca9-4661-ae2e-caaf334b7a78" />

<img width="456" height="65" alt="image 3" src="https://github.com/user-attachments/assets/75abacbb-58e9-4941-a676-8f2cda027c3e" />


> How many files are available in the C:\xampp\htdocs\img folder?
> 

2

<img width="633" height="266" alt="image 4" src="https://github.com/user-attachments/assets/deada942-3944-43b0-800b-abd867113998" />


#### **Task 7 - Automating Common Tasks**

Several ways to automate these tasks include scripts, scheduling tools, and platforms that offer security orchestration, automation, and response (SOAR) capabilities.

- **Scripts**: Scripting languages such as Python, PowerShell, and Bash enable security professionals and system administrators to automate repetitive operational tasks, continuous vulnerability scans, log analysis, and complex incident response workflows.
- **Scheduling Tools**: Task schedulers such as cron jobs and Windows Task Scheduler automate routine security operations by executing scripts and vulnerability scanners at predefined intervals to continuously detect network vulnerabilities, generate severity reports, and streamline remediation workflows.
- **SOAR Platforms**: Security Orchestration, Automation, and Response (SOAR) platforms such as Shuffle and Splunk provide a centralized management framework that unifies diverse security tools including firewalls, IDS, and SIEMs to automate complex incident response playbooks, threat hunting workflows, and case management tasks.

When automating tasks and security checks, it is important to consider the following best practices:

- Test your scripts and automation tools in a controlled environment before deploying them in production.
- Ensure that your scripts and automation tools are well-documented and easy to understand.
- Use logging and monitoring to keep track of the tasks that have been automated.
- Review your automation and security checks regularly to ensure they are still practical and relevant.
- Keep your scripts and automation tools updated and patched to address any security vulnerabilities.

In summary, automating common tasks and security checks can help organizations streamline operations and improve their overall security posture. When implementing automation, it is important to consider best practices such as testing, documentation, logging and monitoring, regular review, and security updates.

**Answer the questions below**

> As a security engineer, is it important to ensure that automated scripts being executed are acquired from legitimate sources?
> 

yea

#### **Task 8 - Conclusion**

Learned about the lifecycle of a vulnerability, how exploits are developed, and how to chain multiple vulnerabilities to get complete control of a system. Moreover, we have also briefly discussed how we could automate routine tasks to assist a security engineer.

In summary, creating exploits based on existing vulnerabilities is a complex process involving discovering vulnerabilities, research, exploit development, testing, and deployment. However, vulnerabilities and exploits must be dealt with using extreme care, and all testing should be carried out in an isolated environment to avoid infecting one's own system.
