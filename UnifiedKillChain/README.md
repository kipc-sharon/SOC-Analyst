# Unified Kill Chain(UKC)

---
For this lab, the objective is to understand an attacker's “Kill Chain” so that defensive measures can be put in place to either pre-emptively protect a system or disrupt an attacker's attempt.

**Kill Chain* -- An attacker stages/methodology/path to an attack.

# TOPICS
# 1. THREAT MODELLING
-- Mapping an organizations IT assets(Systems and Applications that need to be secured.)
-- Assess vulnerabilities and weaknesses in the applications and system
-- Action Plan -- what is to be done on the system, applications and vulnerabilities to ensure a secure system
-- Policies -- Are the future preventions.

**Frameworks that guide UKC Threat Modelling**

# STRIDE
# DREAD
# CVSS

# 2. UKC
We explore different Cybersec Kill Chain Frameworks
**Mitre&Attack*
**LockHeed Martins*
**UKC* -- Pauls Pols'

**UKC**
--Has 18 stages, complements the rest of the frameworks
    **Reconnaissance*
    **Weaponization*
    **Delivery*
    **Social Engineering*
    **Exploitation*
    **Persistence*
    **Defense Evasion*
    **Command & Control*
    **Pivoting*
    **Discovery*
    **Privielege Escalation*
    **Execution*
    **Credential Access*
    **Lateral Movement*
    **Collection*
    **Exfiltration*
    **Impact*
    **Objectives*
---

From the topic below, I understood it as the UKC categorizing, into 3 phases, **IN, THROUGH, OUT***
# Phase: In(Initial Foothold)
-- An attacker will employ numerous tactics to investigate the system for potential vulnerabilities that can be exploited to gain a foothold in the system like learning of the applications and services that are running.

**Reconnaissance (MITRE Tactic TA0043)**
    -- According to UKC, in this phase the attacker gathers information relating to their target. This can be achieved through means of passive and active reconnaissance. They include discovering what systems and applications/services are running, understand the targets network topology.
**Weaponization** -- 
    -- UKC describes the adversary setting up the necessary infrastructure to perform the attack. For example, this could be setting up a command and control server, or a system capable of catching reverse shells and delivering payloads to the system.
**Social Engineering**
    -- UKC describes this phase as adversary employs techniques that involves manipulating employees to perfomr actions that will aid/escalate their access to the system, involves impersonating a website, a user eg pose as head of IT department,
**Exploitation**
    --  UKC defines "Exploitation" as abuse of vulnerabilities to perform code execution. For example:Uploading and executing a reverse shell to a web application.
**Persistence**
    -- UKC describes the techniques an adversary uses to maintain access to a system they have gained an initial foothold on. For example:Creating a service on the target system that will allow the attacker to regain access, persistence backdoor such as a reverse shell will execute when a system administrator logs in(*Registry Run Keys)
**Defense Evasion**
    -- These addresses the different techniques an attack uses to evade defense measures put in place in the system/network. Firewalls(Network&Web), AV, IDS. This helps during an attack analysis for an org to kwno their position of their infrastructure llopholes.
**C2**
    -- Stage of the UKC to establish communications between the adversary and target system.
**Pivoting**
    -- A technique an adversary uses to reach other systems within a network that are not otherwise accessible (for example, they are not exposed to the internet). There are often many systems in a network that are not directly reachable and often contain valuable data or have weaker security. 
---
# Phase: Through (Network Propagation)
An attacker would seek to gain additional access and privileges to systems and data to fulfil their goals. The attacker would set up a base on one of the systems to act as their pivot point and use it to gather information about the internal network.

**Pivoting**
-- Once the attacker has access to the system, they would use it as their staging site and a tunnel between their command operations and the victim’s network. The system would also be used as the distribution point for all malware and backdoors at later stages.
**Discovery**
-- The adversary would uncover information about the system and the network it is connected to. Within this stage, the knowledge base would be built from the active user accounts, the permissions granted, applications and software in use, web browser activity, files, directories and network shares, and system configurations.
**PA**
-- An adversary would try to gain more prominent permissions within the pivot system. They would leverage the information on the accounts present with vulnerabilities and misconfigurations found to elevate their access to one of the following superior levels like Root,Local Administrator,user account with Admin-like access, user account with specific access or functions.
**Execution**
-- The atacker deploy their malicious code using the pivot system as their host. Remote trojans, C2 scripts, malicious links and scheduled tasks are deployed and created to facilitate a recurring presence on the system and uphold their persistence.
**Credential Access** 
-- The adversary would attempt to steal account names and passwords through various methods, including keylogging and credential dumping. This makes them harder to detect during their attack as they would be using legitimate credentials.
**Lateral Movement**
-- With the credentials and elevated privileges, the adversary would seek to move through the network and jump onto other targeted systems to achieve their primary objective. The stealthier the technique used, the better.
---
# Phase: Out (Action on Objectives)
This phase wraps up the journey of an adversary’s attack on an environment, where they have critical asset access and can fulfil their attack goals. These goals are usually geared toward compromising the confidentiality, integrity and availability (CIA) triad.

**Collection**
-- After all the hunting for access and assets, the adversary will be seeking to gather all the valuable data of interest. This, in turn, compromises the confidentiality of the data and would lead to the next attack stage – Exfiltration. The main target sources include drives, browsers, audio, video and email.
**Exfiltration (MITRE Tactic TA0010)**
--To elevate their compromise, the adversary would seek to steal data, which would be packaged using encryption measures and compression to avoid any detection. The C2 channel and tunnel deployed in the earlier phases will come in handy during this process.
**Impact (MITRE Tactic TA0040)**
-- If the adversary seeks to compromise the integrity and availability of the data assets, they would manipulate, interrupt or destroy these assets. The goal would be to disrupt business and operational processes and may involve removing account access, disk wipes, and data encryption such as ransomware, defacement and denial of service (DoS) attacks.
**Objectives**
-- With all the power and access to the systems and network, the adversary would seek to achieve their strategic goal for the attack.

For example, if the attack was financially motivated, they may seek to encrypt files and systems with ransomware and ask for payment to release the data. In other instances, the attacker may seek to damage the reputation of the business, and they would release private and confidential information to the public.

**Conclusion**
The module teaches on threat intelligence,a critical component of cybersecurity that enables organizatons with actionable insights to proactively guide their defence mechanism against cyber threats.
To achieve this, we have to be familiar with the different cyber kill chain frameworks, which are the methods an attacker uses to achieve their objectives.

UKC(Paul Pols')is a framework that complements other kill chain frameworks such as Mitre&Attack, Lockheed Martins. It has 18 phases, unlike one with 7 phases.