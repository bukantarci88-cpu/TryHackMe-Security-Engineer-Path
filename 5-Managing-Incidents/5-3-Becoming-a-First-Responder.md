# Eng 5.3. Becoming a First Responder

#### **Task 1 - Introduction**

Cross-functional incident response occurs when domain experts and non-Blue Team system owners are called upon during security incidents to provide system context, technical assistance, and forensic validation for systems under their operational management.

#### **Task 2 - Preservation of Evidence**

**Volatility of Evidence**

The biggest mistake that is performed during incidents is shutting the host down. This is wrong for the following two main reasons:

- A significant amount of important evidence is found in volatile spaces, meaning it is lost as soon as the device loses power
- It immediately alerts the threat actor that we might be on to them, meaning they might start a more disruptive attack

Evidence preservation during incident response requires prioritizing the collection of transient system data based on the IETF order of volatility before executing disruptive containment measures like network disconnection to prevent the destruction of volatile forensic artifacts.

**1. Registers and Cache:** CPU registers and cache represent the most volatile tier of system data, changing in split seconds and requiring immediate capture when feasible to preserve critical runtime execution context for advanced malware analysis.

**2. Routing Table, ARP Cache, Process Table, Kernel Statistics and Memory:** Capturing intermediate volatile evidence including active RAM, running process tables, routing tables, and ARP caches is essential for mapping ephemeral network communications, active process behavior, and staged malware payloads before system power loss or time-to-live expiration destroys the forensic record.

**3. Temporary File Systems:** It is common for applications to create and use temporary files on hosts. For example, on a web server, active sessions are usually stored in temporary files. While these files are often preserved longer on the host, we do not want to take any chances in losing these files that may be important for the investigation.

**4. Disk:** Preserving disk snapshots secures non-volatile file system data and local logs for legal proceedings, enabling analysts to detect threat actor tampering by comparing local artifacts against remotely stored telemetry.

**5. Remote Logging and Monitoring:** Preserving remote log archives as far back as possible during an active investigation ensures analysts can determine the full historical scope of an incident despite limited remote retention policies.

**6. Physical Configuration and Network Topology:** Documenting and preserving network topology and physical host configurations such as subnet membershipsclarifies the lateral scope of an incident and identifies adjacent systems requiring forensic scrutiny.

**7. Archival Media:** Utilizing non-volatile backups as historical baselines allows incident responders to determine how far back a security compromise penetrated by comparing current disk artifacts against trusted historical states.

**The Other Two Big DON'Ts**

We have already talked about the first big don't, which is to not turn off the device; however, there are two other big don'ts according to the IETF:

- **Don't trust the programs on the system.** This means that you should not use the actual software on the host to perform your evidence collection. The simple reason for this is that the threat actor may have altered these programs and that by using these programs, you are tainting the evidence that you are trying to capture.
- **Don't run programs that modify the access times of files.** When a file was accessed is evidence itself. If you perform a simple Copy + Paste, you will taint this evidence. This is why special software or hardware is used when evidence is captured to ensure that the evidence is captured as is and not tainted.

**Chain of Custody:** Chain of custody is a rigorous documentation and tracking process that establishes the legal admissibility and uncompromised integrity of digital evidence by proving it has not been tampered with throughout its lifecycle and that forensic analysis is conducted solely on verified bit-stream copies.

**Answer the questions below**

> What priority order for preservation (number only) is given for the Disk?
> 

4

> What priority order for preservation (number only) is given for Archival Media?
> 

7

> What priority order for preservation (number only) is given for the Register and Cache?
> 

1 

> What is the term used to describe ensuring that evidence can be used in legal proceedings?
> 

Chain of Custody

#### **Task 3 - Alerting the Relevant Stakeholders**

**Incident Playbooks:** Incident response playbooks provide standardized, pre-defined procedures that ensure repeatable, thorough execution across various threat scenarios such as phishing or credential compromise while seamlessly integrating cross-functional workflows.

**Call Trees:** Call trees establish structured communication and hierarchical escalation paths that define precisely who must be notified during an incident and when to escalate issues to specialized response teams like the Blue Team based on severity.

**The Responsibility of the First Responder:** Security engineers act as organizational first responders by ensuring their respective divisions are operationally prepared for security incidents through clear escalation pathways, accessible reporting tools, and established safety protocols.

**Answer the questions below**

> What is the term that describes a defined process that the blue team follows during an incident?
> 

Playbook 

> What is the term that describes the structure used to inform all the relevant parties about the incident?
> 

Call Tree

#### **Task 4 - Isolation of the Incident**

**The Importance of Containment:** Incident containment is the vital initial phase of the NIST response lifecycle that halts the spread of a security breach and prevents threat actor re-entry, serving as an absolute prerequisite before executing eradication and recovery.

**Containment Methods:** As discussed before, the best containment method is not to switch off the host, as this will destroy evidence and potentially alert the threat actor. However, there are other means of isolation that can be performed:

- Network  Segmentation - The host is isolated from the network perspective by being placed into a different network segment. This isolation aims to ensure that the infection cannot spread to other hosts on the network. Effective [network security](https://tryhackme.com/room/intronetworksecurity) is very important!
- Physical Isolation - The host is collected and fully isolated from the network and users. For example, a user's workstation is confiscated. This isolation aims to ensure that no further actions can be performed on the host and evidence is preserved.
- Virtual Isolation - The host is restricted from communicating through the use of software. For example, the EDR can be used to jail the host, meaning it is only allowed to communicate with specific entities on the network and perform certain actions. The goal of this isolation is similar to confiscating the host, but can be performed remotely. Furthermore, in some cases, if the EDR is compromised, this may not work.

**Sending Threat Actors Back to the Dial-Up Days:** Tactical rate limiting via endpoint detection and response (EDR) tools allows blue teams to secretly degrade attacker command-and-control communication speeds, buying critical time for deep forensic investigation without tipping off the adversary. 

**The Responsibility of the First Responder:** As mentioned before, as the security engineer, you may not be responsible for isolating the incident. However, you will be relied upon as a subject matter expert to help the team understand what containment methods may be possible and to also understand what the impact would be of implementing these containment methods.

**Answer the questions below**

> What containment method can be performed remotely using the EDR?
> 

Virtual Isolation 

> What containment method requires the blue team to collect the infected host?
> 

Physical Isolation 

> What containment method aims to ensure that the infected host cannot communicate with other hosts?
> 

Network Segmentation

#### **Task 5 - Business Continuity Plan**

**Invoking BCP:** Invoking the Business Continuity Plan (BCP) during high-severity incidents only after successful containment grants temporary emergency authorization to bypass standard operational processes and change-management controls, enabling rapid recovery back to Business as Usual (BAU) under strict senior management oversight.

**BCP vs DRP:** A BCP is very similar to a Disaster Recovery Plan (DRP). However, the DRP will mainly focus on the technical recovery of our division. A BCP is more encompassing and covers elements such as communication to internal and external stakeholders. A DRP is usually included in the BCP to help with the technical recovery.

**Creating a BCP:** As a security engineer, you may be responsible for creating a BCP. The following steps can be followed to create an effective BCP:

1. **Perform a Business Impact Analysis** You have to plan for the worst-case scenario. By performing an analysis, you can determine what could happen in the event of an incident and how it would impact not only your organisation, but also your customers. The analysis is usually performed using a combination of qualitative and quantitative measures.
2. **Define the Potential Recovery Actions** - Based on the scenarios of the first step, you can determine what potential recovery actions would be possible. For example, in case one of the production servers become unresponsive or has to be isolated, you could potentially switch to your disaster recovery server. Documenting these recovery actions will allow the team to recover faster during an actual incident.
3. **Plan the BCP Team Structure** - When the BCP is invoked, there are certain responsibilities that have to be fulfilled, such as documenting actions and alerting stakeholders. These responsibilities should be planned and documented together with the details of the individuals that would perform them.
4. **Test the BCP Plan** - In order to ensure that your BCP works as expected, you have to train your team on using it and then test it using a tabletop exercise.

**BCP Metrics:** As mentioned, the Business Impact Analysis assessment will use quantitative measures. These allow the team to determine how long it would take to implement the recovery actions of the BCP and whether these timelines are acceptable, below are some of the most common metrics used.

- **Recovery Point Objective** - The amount of data we are willing to accept can be lost. For example, if we say we are willing to lose an hour of data but no more, then our backups have to run every single hour.
- **Recovery Time Objective** - The amount of time required to recover the hardware of our system
- **Work Recovery Time** -The amount of time required to recover the software and data of our system
- **Maximum Tolerable Downtime** -The maximum amount of downtime that we are willing to accept. We have to ensure that our RTO and WRT combined do not exceed this threshold
- **Mean Time Between Failures** - How long our system will operate between incidents on average
- **Mean Time To Repair** - How long it will take to recover our system on average

**Answer the questions below**

> What does BCP stand for?
> 

Business Continuity Plan 

> What does DRP stand for?
> 

Disaster Recovery Plan 

> What BCP metric is used to describe the amount of time required to recover the hardware of our system?
> 

Recovery Time Objective 

> What BCP metric is used to describe the average amount of time required to recover our system?
> 

Mean Time to Repair

#### **Task 6 - Documentation of Actions**

**The Importance of Documentation:** Comprehensive documentation during BCP activation is essential to record emergency operational changes that bypass standard change management controls, ensuring a verifiable audit trail for retracing steps and facilitating a seamless handover to incident response teams.

**Documentation Templates:** In order to assist with the documentation process, it is usually recommended that the BCP document also contain a documentation template that can be used. We do not want to waste time creating this during the incident, so preparing this template is important. The template should allow for the following information to be provided:

- Time at which the action was requested. Times should ideally be provided in a standard format such as UTC to ensure that times can be matched to other sources
- Description of the update or action that was performed
- Reasoning for performing the action
- Individual approving the action being performed
- Individual responsible for performing the action
- Time at which the action was performed
- Description of changes observed after the action was performed

**Lessons Learned:** Documentation is not only important to perform a successful handover, but also provides us with the ability to review the incident and actions taken at a later date. It is through this review process that we can investigate what went wrong and what can be done to ensure that it is prevented in the future. This process helps us reduce the number of incidents that we have.

**Answer the questions below**

> What time format should be used in our incident notes to ensure that all times match?
> 

UTC

#### **Task 7 - Handing Over**

**Answer the questions below**

> What is the value of the flag you receive after responding to the incident?
> 

THM{I.am.ready.to.become.a.first.responder}

<img width="637" height="352" alt="image" src="https://github.com/user-attachments/assets/46802649-2264-47f9-9947-2856cf7fdbb8" />


#### **Task 8 - Conclusion**

To summarise:

- Make sure that you preserve evidence and understand that some evidence may be more volatile.
- Make sure that you understand how you should raise the alarm that an incident has occurred, whether through a ticket submission or a call tree.
- Isolation is key to ensuring that the scope of the incident can be contained. However, there are many different methods that can be used for isolation.
- BCP can be used to ensure that rapid changes can be made to help address the incident, but documentation is incredibly important to be able to retrace actions and get the environment back to business as usual as fast as possible.
