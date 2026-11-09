# Eng 5.4. Cyber Crisis Management

#### **Task 1 - Introduction**

Crisis Management Team (CMT) whose job is specifically to navigate us through these troubled waters!

#### **Task 2 - What is a Cyber Crisis**

The SOC receives log information that creates events and alerts. In the case that an alert is sufficiently serious, a cyber incident occurs.However, based on the severity of the incident, the blue team decides the best response. In our example, only a level 4 incident would trigger the **Crisis Management Team (CMT)**. As a refresher, these were the four levels:

- **Level 1: SOC Incident** - Small enough that the incident can be taken care of directly by the security operations centre (SOC), such as a user reporting a phishing email
- **Level 2: CERT Incident** - Small enough that a team in the SOC can take care of the incident, such as a single user that has interacted with a phishing email
- **Level 3: CSIRT Incident** - A larger incident that requires not just the SOC team, but also incident managers, such as multiple users that have interacted with a phishing email that contains malware
- **Level 4: CMT Incident** - A critical incident where the CSIRT requires the ability to invoke nuclear actions, such as an incident where ransomware is being deployed and the CSIRT needs to take the environment offline to protect the rest of the estate

So, how does the team actually decide the level of an incident? This is done through an incident severity classification matrix as shown below:

![CMT Severity Scale](https://tryhackme-images.s3.amazonaws.com/user-uploads/6093e17fa004d20049b6933e/room-content/d54b1bd910019fc66fba7413c5b510d7.svg)

Incident severity classification evaluates the breadth of impacted users and critical systems against system recovery difficulty to assign severity levels and trigger appropriate escalation to the Crisis Management Team (CMT) based on organizational matrices and customer impact rules.

**Answer the questions below**

> What would the severity rating of an incident be where multiple users are affected and the impact is medium?
> 

Moderate 

> What would the severity rating of an incident be where multiple users are affected and the impact is low?
> 

Low 

> What would the severity rating of an incident be where an entire business unit is affected and the impact is high?
> 

Critical

#### **Task 3 - The Roles and Responsibilities in a CMT**

**Not all Voices are Equal:** There are several roles and responsibilities that have to be taken care of in the CMT. Normally, not all CMT members are involved from the start. Depending on the crisis, members are added as needed. This is to help ensure that the CMT can respond as rapidly as possible.

**Roles in the CMT:** The table below details some of the roles and responsibilities you can find in a typical CMT:

| **Role/Responsibility** | **Description** |
| --- | --- |
| CMT Chair | The Chair is the person that leads the CMT. Usually, this role is fulfilled by either the CEO or the COO of an organisation. The Chair is responsible for leading the CMT and, as mentioned before, is usually responsible for having the final say in what actions will be implemented during the cyber crisis. |
| Executives | Executives are usually part of the CMT. This includes the CEO, COO, CIO, CTO, CFO, and even the CISO. In cases where not just the CEO is responsible for decision-making, these executives would each be granted a voting right. As executives will ultimately be held accountable for what happened during the incident, they are involved in the CMT to ensure that the damage is kept as small as possible. |
| Communication | An important responsibility in the CMT is communication. This includes communications that are being sent both internally to employees and externally to customers. An important part of any CMT is staying in control of the narrative to help ensure that unnecessary panic is not created. Therefore, communication during the cyber crisis is incredibly vital. |
| Legal | While we would like to believe that the CMT can take any action, it is important to ensure that these actions are actually legal. A very common discussion during certain cyber crisis scenarios is whether a ransom will be paid or whether the team will interact with the threat actors. It is important to note that in certain countries, these actions may not even be legal for the team to do. |
| Operations | One of the CMT member's sole responsibility is to concern themselves with the best possible approach to ensure that the operations of the organisation are affected the least amount possible during the cyber crisis. In certain cases, this role is fulfilled by the COO; however, it can also be fulfilled by an entire team of experts that are looking for ways that business can continue during the crisis. |
| Subject Matter Experts | Most of the members of the CMT are not technical. These are members that are exceptional at business concerns but do not usually concern themselves with the day-to-day complexities of actually running the organisation's systems. During a cyber crisis, subject matter experts (SMEs) play a vital role in providing critical information to the members of the CMT. This information then helps inform the team about the crisis scope and which actions would be the best to perform. During a cyber crisis, this would most likely include the head of the SOC and/or the incident manager of the CSIRT. |
| Scribe | Note-taking is incredibly important during a cyber crisis. It is important to create a full timeline of events as this often has to be disclosed to other third parties, such as the government or regulator. The role of the scribe is therefore important to detail all events and conversations during the CMT session. |

**Answer the questions below**

> Who is responsible for note-taking in the CMT?
> 

Scribe 

> Who is responsible for leading the CMT session?
> 

Chair 

> Who is responsible for ensuring that the actions taken by the CMT do not break the law?
> 

Legal

> Who is responsible for making sure that the stakeholders are informed during the CMT?
> 

Communication 

> Who is responsible for providing more technical information to the CMT to ensure that they can take the appropriate actions?
> 

Subject Matter Experts

#### **Task 4 - The Golden Hour**

**Assembly:** CMT assembly during the Golden Hour utilizes pre-documented call trees, hierarchical role backups, and secure out-of-band communication channels to rapidly convene executive leadership when primary infrastructure may be compromised by a threat actor.

**Information Gathering:** Once the CMT has been established, the very first step is to understand what has happened and what actions should be taken immediately. For a cyber crisis, this is usually done in the form of a CSIRT briefing where the CSIRT provides:

- A summary of the information discovered up to this point
- A summary of the actions that have already been taken by the team and the effect they had on the incident
- Recommendations as to what nuclear actions should be taken immediately by the CMT

**Crisis Triage:** Crisis triage requires the CMT to evaluate CSIRT-proposed response actions against organizational impact, determine mitigation strategies, and expand stakeholder participation while preparing proactive communications.

**Notifications:** Controlling the narrative during major security incidents involves preparing and deploying holding statements internally and externally to reassure stakeholders and maintain trust while the crisis is actively investigated.

**Answer the questions below**

> What is the first step that has to be performed during the CMT golden hour?
> 

Assembly

> In the event of a cyber crisis, who provides the update to the CMT?
> 

CSIRT

#### **Task 5 - The CMT Process**

Once the CMT has been established and the Golden Hour actions have been performed, the CMT starts with a cyclic process to deal with the crisis, as shown below.

![CMT Process](https://tryhackme-images.s3.amazonaws.com/user-uploads/6093e17fa004d20049b6933e/room-content/71572f39d5d25f6a66d26a11cdcd2192.svg)

Maintaining a static Crisis Management Team (CMT) structure during an incident prevents operational fragmentation by relying on dedicated Subject Matter Experts (SMEs) to feed critical intelligence directly into the central decision-making body.

**Information Updates:** Crisis Management Team (CMT) briefing cycles utilize Subject Matter Experts (SMEs) to deliver frequent, translated updates that abstract complex technical metrics into clear business impact assessments.

**Triage:** Continuous crisis triage enables the CMT to dynamically adjust incident severity ratings, onboard new specialized SMEs, and calibrate internal or external communication strategies based on evolving intelligence.

**Action Discussions:** Using the new information provided by the various SMEs, the CMT has to discuss the proposed actions. The goal of these discussions is to understand the impact that these actions would have on the organisation. In this case, we are no longer talking about easy and small actions, such as removing a phishing mail from a user's mailbox. We are talking about large actions such as:

- Restricting remote access to the environment by halting all VPN access
- Performing a domain takeback of the Active Directory domain
- Switching a system over to the disaster recovery environment

These are actions that the CMT can't take lightly, as they would impact the business. The goal of discussions is to better understand that impact and allow the team to determine if there may be any less impactful, but still effective actions that can be taken.

**Action Approvals:** Time-boxed crisis decision-making prevents paralysis during rapidly evolving threats like ransomware propagation, culminating in executive authorization—often led by the CEO—to execute critical remediation steps under strict accountability.

**Documentation and Crisis Closure:** Post-incident documentation compiles scribe notes into a comprehensive crisis record, providing the foundational insights required for executive debriefs, policy refinement, and long-term security maturity enhancements.

**Answer the questions below** 

> What is the term used to describe the process by which the CMT determines the severity of the crisis?
> 

Triage 

> Who is ultimately responsible for ensuring that the CMT takes action?
> 

CMT Chair 

> Who will ultimately be held accountable for the crisis?
> 

CEO

#### **Task 6 - The Importance of SMEs**

**Jack of All Trades:** Crisis Management Team members possess broad organizational scopes rather than specialized technical mastery, requiring them to continuously leverage the specialized knowledge and insights of supporting Subject Matter Experts during a crisis.

**The Masters of One:** This is where subject matter experts come into play. As a security engineer, you may be involved in a CMT if the crisis pertains to your specific division. As the security engineer, you should have an incredible depth of knowledge of your specific system or asset and can therefore provide vital information to the CMT.

The CMT can only take effective actions if the following is true:

- The CMT must have an accurate understanding of the scope of the incident, including what has happened and what the impact is on the business. It will never be possible to understand the full crisis scope as the investigation will still be ongoing, but having an as clear as possible picture is important.
- The CMT has to understand what actions are available for them to take and what the impact vs effectiveness of these actions would be.

SMEs play a critical role in providing this information. As a security engineer, you will understand the system best to know what potential actions can be taken to recover from the crisis. You will know how long backups are kept. You will know whether the environment can switch to DR. You will know what the impact would be if you have to take critical assets in the environment offline.

This information must be clearly communicated to the CMT to ensure they can make an informed decision. Without SMEs, it would be impossible to recover from a crisis.

**Answer the questions below**

> Who is responsible for providing the CMT with technical and in-depth information to allow them to make an informed decision during the crisis?
> 

Subject Matter Experts

#### **Task 7 - The Actions Available to the CMT**

Apart from the technical response the CMT can take to deal with the crisis, there are other actions that the team needs to consider and potentially take. Some actions will help the team control the narrative, while others may be required by law.

**Internal Communication:** Internal crisis communication aligns organization-wide messaging and equips frontline support teams like the help desk with pre-scripted holding statements to handle inquiries and prevent panic during active incidents.

**External Communication:** Managing external crisis communications across media outlets and social platforms requires specialized public relations strategies to maintain public trust and protect brand reputation without inciting unnecessary fear.

**Informing the Regulator:** Regulatory compliance during a security crisis mandates timely breach notifications to industry watchdogs and data protection authorities such as financial regulators and GDPR oversight bodies to satisfy statutory legal obligations.

**Contacting Law Enforcement:** Engaging law enforcement agencies such as the FBI according to predefined playbook procedures assists active investigations and helps preserve the strict chain of custody required for future legal prosecution.

**Exercising CMT:** Now that you understand the CMT process, it is time to use that knowledge to deal with a cyber crisis. Launch the static site and take care of the crisis!

**Answer the questions below**

> What is the value of the flag you receive after successfully dealing with the cyber crisis?
> 

THM{The.Crisis.has.been.managed!}

#### **Task 8 - Conclusion**

In this room, we have learned about how a crisis management team deals with a cyber crisis. To summarise:

- When the severity of an incident becomes sufficiently large, the CSIRT will invoke CMT to help them deal with the crisis.
- The CMT has to make the most of the Golden Hour to ensure that crucial time is not lost to deal with the crisis.
- The CMT follows a process of receiving updates on the crisis scope and discussing the crisis before taking action to help close the crisis.
- Subject Matter Experts play an important role in providing critical information to the CMT to help them better understand the scope of the crisis and take the appropriate actions to deal with it.
