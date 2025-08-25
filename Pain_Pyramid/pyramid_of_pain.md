# Pyramid Of Pain
-- Learn what is the Pyramid of Pain and how to utilize this model to determine the level of difficulty it will cause for an adversary to change the indicators associated with them, and their campaign.

-- Improves the effectiveness of Cyber Threat Intelligence(CTI)

# Topics1.

# 1. HASH VALUES

--------

 Hash >>
 Hash Algorithm
HASH types:
MD5 128-bit
SHA-1 -- 160bit hash vale.//;;
SHA-2 --256bit SHA 256

-- Security professionals usually use the hash values to gain insight into a specific malware sample, a malicious or a suspicious file, and as a way to uniquely identify and reference the malicious artifact.

-- security researchers would provide the hashes related to the malicious or suspicious files used at the end of the report

**Tools** VirusTotal, MetaDefender Cloud-OPSWAT.
        Get-FileHash -- computes hash value of a file using a specified hashing algorithm.
           *Syntax*
           Get-FileHash
                [-Path] <String[]>
                [[-Algorithm] <String>]
                [<CommonParameters>]
        **Command** : **Get-FileHash /etc/apt/sources.list | Format-List*
        Demo
**Lab**
Challenge when a value/data gets altered, it changes the hash value(Malware variations and instances)

Using the command below in windows ps to get a hash of a file
# Open PowerShell and run
Get-FileHash C:\path\to\suspicious.exe -Algorithm SHA256 -- Get HASH VALUE
NOTE: Sligh change in the file changesthe hash values.

LAB:
From a report and a given has value, we get a file name

---
# 2. IP ADDRESS
IP -- used to identify any device connected to a network. These devices range from desktops, to servers and even CCTV cameras.

Defense mechanisms here involves blocking, dropping, deleting inbound requests from IP addresses.

**Pitfal* -- **Proxies** can be used to hibernate attackers IP.

-- Fast Flux is a DNS technique used by botnets to hide phishing, web proxying, malware delivery, and malware communication activities behind compromised hosts acting as proxies. The purpose of using the Fast Flux network is to make the communication between malware and its command and control server (C&C) challenging to be discovered by security professionals. 

**LAB** 
Go through a report, there are different IOC listed and associated logs;The report the logs on file activities, network, processes, behaviors, DNS requests, connections etc. 


Specificaly look for an IP address for a malicious process(PID) and the domain name associated with the PID.

Learny/// 
Correlating PID in a file event, and it making connections/communication over a network. 
Here an exe file, associated with an IP and a domain name.

----

# 3. DOMAIN NAMES

**DNS** -- Translates domain names/urls to IP addresses.

-- Domain Names can be a little more of a pain for the attacker to change as they would most likely need to purchase the domain, register it and modify DNS records. Unfortunately for defenders, many DNS providers have loose standards and provide APIs to make it even easier for the attacker to change the domain.

-- Attackers look for a shortcut to hava a domain name.
    The long way involves  buying a domain from a registrar, give out detals, set up DNS records, pay, this methods will leave paper trail, its time consuming,.
        So, he just spins up a new IP address on a VPS.(DNS Providers are sleeping on the job)
        Attackers thus can instantly switch domains when one gets blocked (domain fluxing).

        Use DNS APIs to rotate C2 servers or phishing sites dynamically.

**LAB** 
An attacker generate domain name that wouldvlook very legitimate, or cop on a legit domain name.

**Tools** -- Punycode -- Punycode is a way of converting words that cannot be written in ASCII, into a Unicode ASCII encoding."
    Domain names/urls for instance  URL adıdas.de  which has the Punycode of  http://xn--addas-o4a.de/
        Attackers usually hide the malicious domains under URL shorteners.   A URL Shortener is a tool that creates a short and unique URL that will redirect to the specific website specified during the initial step of setting up the URL Shortener link. The attackers normally use the following URL-shortening services to generate malicious links: bit.ly, goo.gl, tiny.pl etc
 
**PUNYCODE ATTACK* --  type of attack uses Unicode characters in the domain name to imitate the a known domain.

.py that converts ASCII to Unicod to pyunicode.

---

# Host Artifcts

-- Traces or observables that an attacker leaves in the system. A.k.a Forensic evidences such as registry values, suspicious process execution, IOCs, attack patterns.



**LAB**
Follow through a malicious process activity from the alert logs report.

We look for an IP address for a process named regidle.exe that makes a POST request to a US based IP on port 8080. Filtered through the report for he process name and port and found it. Then proceed to looking for its location, boom found exact IP.

-- Next Question: actor drops a malicious executable (EXE). What is the name of this executable
    -- steps to tracing the excutable.

-- A Virustotal report that shows how many vendors determine this host to be malicious

**RegIdle.dll -- a windows core dll. Trusted and signed by Microsoft in System32.

    -- Used by windows system to perform background optimization on system registry during idle time.

    -- Attackers can hijack, drop a fake regidle.dll in a location where a privileged process loads it.
    
    -- Can be side-loaded -- abuse a legitimate binary (regsvr32, installers, or services) that loads RegIdle.dll insecurely.
    
    -- Masquerade -- a malware called RegIdle.dll to hide in plain sight.

The lab is abit confusing.
---


# 4. Network Artifacts

-- Are traces, evidence, or digital "footprints" left behind by network activity.

**User Agent String -- HTTP Headers a client sends to a webserver to identify itself. The header has information like an application, operating system, version, vendor etc**> Requests could be from a webbrowser, a curl request, a python request library.

**C2 Information**

**URI Patterns from a HTTP POST requests**


 Tools to Collect & Analyze Network Artifacts

    Collection: tcpdump, Wireshark, Tshark, Zeek, Suricata, Sysmon (Windows event logs), Firewalls

    Analysis: Wireshark, Moloch/Arkime, ELK Stack, Splunk, Security Onion

    Correlation: Threat intel feeds (domain/IP reputation), MITRE ATT&CK mapping
 
    **Examples**
        DNS Artifact: Victim queries login-secure-office365[.]com

        Traffic Artifact: HTTPS connection to attacker IP on port 443

        Log Artifact: Firewall shows unusual outbound connection from internal user

        Authentication Artifact: Failed login attempts from unusual IP

**LAB** 
In the lab, we go through Wireshark PCAP file with POST requests containing  malicious strings. TShark has been used to filter out, extract from HTTP Requests(POST), the host and the user-agent strings.

-- After extraction, we decode the string from BUGBYTE.ME website and find the name of the browser for this request from th user-agent string filtered out.

  **Command:*  -- **tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap **

  # 5. Tools
  **Fuzzy Hashing/Contect Triggered Piecewise Hashes** SSDeep -- A method used to determine similarities between files, binaries etc.
  
  # 6. TTP:
  -- TTPs stands for Tactics, Techniques & Procedures. This includes the whole MITRE ATT&CK Matrix, which means all the steps taken by an adversary to achieve his goal, starting from phishing attempts to persistence and data exfiltration. 

Pyramid of Pain