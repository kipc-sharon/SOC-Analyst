# The Cyber Kill Chain

** It consists of target identification, decision and order to attack the target, and finally the target destruction.
        The Steps adversaries use to succeed in an attack
            Reconnaissance
            Weaponization
            Delivery
            Exploitation
            Installation
            C2
            Action on Objectives
---
# Topics
# 1. RECONNAISSANCE
Discovering and Gathering information about the target.

**OSINT** -- Framework. 

* OSINT covers so many different types of data, there are many different types of investigations that can be conducted

   Social media, IoT, Dark Web, AI tools..etc.

---

# 2. WEAPONIZATION
    After a successful Recon; Weapon of Destruction -- MALWARE and EXPLOIT = PAYLOAD

        Malware is a program or software that is designed to damage, disrupt, or gain unauthorized access to a computer.

        An exploit is a program or a code that takes advantage of the vulnerability or flaw in the application or system.

        A payload is a malicious code that the attacker runs on the system.
# Macros and VBA
        Macro is simply a small program or set of commands that automate tasks in applications like Microsoft Word, Excel, or PowerPoint.

        VBA is like a lightweight programming language inside Office apps.

        It can:

            Create forms and automate Office features

            Access files on your system

            Run system commands (yes — even CMD or PowerShell!)

A payload has been crafted, now needs to be send to the target machine. Could be a backdoor, a worm, a virus, etc
---
# 3. DELIVERY
Method for transmitting the payload or the malware. Phishing emails, different phishing types, USB, a fakewebsite called watering hole attack. 
---
# 4. EXPLOITATION
* Malware perhaps is now executed in the target system and has now gained access to a target.
* Malicious actor could exploit software, system, or server-based vulnerabilities to escalate the privileges or move laterally through the network.

---

# 5. INSTALLATION
* Reaccess the system(loses the initial access and connection, got detected or system is patched).
**Persistent Backdoor** -- Helps reaccess a previously compromised system, as an attacker.

Ways to create a persistent backdoor

-- **Web shell* -- malicious script written in web development programming languages such as ASP, PHP, or JSP used by an attacker to maintain access to the compromised system. Because of the web shell simplicity and file formatting (.php, .asp, .aspx, .jsp, etc.) can be difficult to detect and might be classified as benign.

-- **Meterpreter* -- Metasploit Framework payload that gives an interactive shell from which an attacker can interact with the victim's machine remotely and execute the malicious code.

-- **Creating or modifying Windows services* -- Adversaries may create or modify Windows services to repeatedly execute malicious payloads as part of persistence. When Windows boots up, it starts programs or applications called services that perform background system functions. Windows service configuration information, including the file path to the service's executable or recovery programs/commands, is stored in the Windows Registry. 
-- **Reg* **A windows utility used at CLI interface to interact with Windows Registry to modify service configurations*-- To query, edit, add, remove information.

-- **Registry Run Keys* -- registry entries in Microsoft Windows that allow programs to automatically execute when a user logs on.

-- *Timestomping* -- File timestamps modification(modify, access, create, time changes)
---
# 6. C2 / C2 Beaconing
-- After persistence, an adversary creates a channel to enable remote control and manipulation of the victim.
**Beaconing* -- The victim communicates back to the attackers C2 server.
-- This way now an attacker can have the victim send credentials, exfiltrate data, lateral movement.
---
# 7. Action on Objectives
-- Adversary can now achieve his intentions/objectives.
        Collect data, priviledge escalate, internal recon, delete traces, lateral move...e.t.c 
       
 **Lab** **Shadow Copy* -- Ms technology an adversary can use to create backup copies, snapshot of computer files or volumes.
---

# KILL CHAIN --
-- These are like the processes an adversary undergoes for their objectives to be accomplished.
-- It involes learning about the victim, identify loopholes in the syste that they can take advantage of to have access ti the system.
-- After identifying a loophole, the attacker goes ahead to create a weapon(malware a.k.a payload) that will be used to exploit they system. A payload will enhance  their manouvering into the system.
-- Delivery phase is the next phase, after having a payload, they need to have it delivered to the victim, could be through a phishing email, a web shell, waterhole attack-fake website, etc.
-- Exploitation -- An attacker goes ahead to exploit the system by trying to escalate privileges, lateral  movement, zero-day, exploit web-serer, or software exploits.
-- After a successful delivery of the payload, an attacker needs to have persistence, in the system, incase of system patches, or detection, or lost initial access, they will need to reaccess the system.(A persistence backdoor)
-- C2 Beaconing -- Remotely controls and manipulate the victim, give command for instance for data exfiltration, still credentials etc.
-- Action on Objectives -- Execute their intentions, launder money, data etc
