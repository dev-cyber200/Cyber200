+++
author = "dev@cyber200"
title = "Infrastructure Security Assessment"
date = "2024-07-07"
description = "Infrastructure Security Assessment is all about the visibility of all the devices inside your perimeter."
tags = [
    "cyber-security",
    "security-assessment",
    "infrastructure-security",
]
draft = false
+++


### Key Questions
- What is the importance of knowing what assets we have in our infrastructure?
- What system and third-party software are running in our assets?
- How do we manage updates and security patching?

### Approach Infrastructure Security.

- Identify the importance of Asset Management
- Mitigate the risks of Shadow IT
- Mitigate the risks of BYOD
- Perform Security Patching and Software Updates
- Identify CIS Benchmarks(Industry security configuration best practices), Mitre CVE, Mitre ATT&CK(ATT&CK: Matrix of attack Tactics Technic and Procedures)
- Audit Physical & Software Assets

### Infrastructure Security Goals
- Achieve visibility of all devices inside your perimeter, enabling the defender to mitigate risks.
- Identifying devices allows us to perform management, patching, and updates on discovered assets.
- Be aware of IoTs,

### The Risk from IoTs
- IoT devices are hard to manage but easy to deploy.
- Low-Quality Manufacturing & Software is vulnerable from the factory.
- IoTs are very difficult to manage and update once deployed. For example, if you decide to place a camera on a far corner of your warehouse, these devices are usually forgotten, but they stay there, vulnerable and exposed.
- Low in cost, but they can become very costly if exposed. These devices create an extended surface of attack.

### Assets and Permanence
Assets can be:
- Permanent: They are likely to stay for a very long time. Examples of this are Servers, Desktops, Network Switches, Firewalls, WiFi Access Points
- Temporary: They may stay for some time but not too long. E.g., phones that employees bring and connect into the perimeter WiFi, contractor workstations that are removed once their work is finished, laptops issued to contractors which are returned when work is completed
- Transient: These are assets that are there for a specific amount of time. E.g., a vendor comes and joins your network for support or updates; a visitor connects to a company's guest WiFi, a customer comes for a meeting and connects to your conference room network drop

### Possible Shadow IT Scenarios
- Accounting adds a switch to their department, bypassing the company's network access controls.
- John brings his own printer, increasing the risk of exposure of sensitive information or even stolen printouts.
- Jeff brings a portable WiFi access point. Now unregistered devices can access the corporate network.
- Tom joins WiFi with a rooted and backdoor phone. A rooted or jailbroken phone with unauthorized application stores can have backdoors. Now you have a phone that could be open to remote access by unknown actors.
- Danielle installs an unsupported cloud backup client. Now you have company data being stored in an unknown, unauthorized location.


### Mitigate Risks of Shadow IT
- Inventory all assets
- Create access controls
- Inventory all software, applications, and licenses
- Implement security controls for users and remote access management
- Train users in Acceptable Use of corporate devices and networks
- Perform periodic network scans to discover new hosts (LAN/WIFI)

### Mitigate Risks of BYOD

- Supported devices must be monitored and protected (Example: Google Work Profile/ VMWare AirWatch). Both are agents that allow the management of devices and enforce the company's controls and security policies.
- Ensure these devices are up to date by requiring BYOD devices to be set to update automatically.
You must provide applicable protections such as endpoint or antivirus for laptops, make sure software is licensed and operating systems and applications are up to date, and have security updates as well.
- Prevent exfiltration
    - Protect Intellectual Property
    - Implement data loss prevention procedures, harden and protect your most sensitive data
    - Track data access

#### BYOD Policies
- You must first craft a policy then enforce it. This policy must establish things like the brand of laptops, the hardware specs, the operating system software, and applications that must be running.
- Protection and controls
- A policy acknowledged by the user of what is acceptable and what is not. For example, you cannot browse adult sites.
- Use Remote management as a way to access these devices remotely by authorized personnel.
- A mechanism to isolate and remotely wipe the device; if it becomes infected, unusual activity is detected, or it is lost. For example, an employee from the sales department with customer sensitive data has resigned, and it is suspected they are going to work for a competitor.
- Protect employee privacy. Whatever access is achieved in BYOD, you must respect and protect private and sensitive information. The privacy of employee pictures, text messages, and private life outside of work needs to be maintained.

### System and Third-Party Software Updates
- Establish procedures for software updates for all operating systems and inventoried applications.
- Manage licenses and support contracts with vendors. This includes:
    - Special licenses
    - Support contracts for End Of Life Operating System
    - Advanced release of updates
- Third-Party Updates Pro Tips
    - Must be supported by contracts and tracked.
    - Licensing and support contracts apply. You will have to call the third-party vendor about these.
    Vendors have their own schedules of releasing updates, and you have to keep track of it.
    - Third-Party software vulnerabilities can bypass your OS Defenses. A clear example of this is Java. This leaves your systems open to severe attacks. Keep track of the highly vulnerable software you have to use.
    - In some instances, you may have to accept risk.

### Software Inventory and Version Tracking
Software Inventory: The act of registering ALL the applications running in your perimeter hosts.

Software Packages: Software versions in use must be identified and added to your inventory tracking.
#### Out of Band Patches (OOBP)
Out of Band Patches: Emergency software releases that are done outside of the normal schedules of releasing software and security updates and patches are referred to as out of band patches.

- Extraordinarily dangerous and high-risk vulnerabilities affecting operating systems or applications.
- It May not be released during the ordinary schedules, although it may coincide with them.
- You must be on the lookout for these.

### Golden Image
A representation of your organization approved, supported, and managed including operating systems, applications, or any other software that is deployed within your perimeter.
- It only contain approved and licensed products, for example, Microsoft Outlook 2013 or Adobe Acrobat 10.
- They must represent your security posture.
- Must include all of the AV, Endpoint, Firewall, Security products applied to your machines. For example, a specific version of Carbon Black Endpoint.
- It represents the company's infrastructure by segment (Business Units, IT, Security, Development).
- Must be equal for everyone in their segment—only one image per department, desktop, or server.

### Identify Industry Frameworks for Vulnerability Reference
- CIS Benchmarks for Ubuntu 18.04
- Windows 10 ENT

- [Mitre Common Vulnerabilities & Exposures](https://cve.mitre.org/): An industry database of vulnerabilities and exposures.
- [Mitre Adversarial Tactics, Techniques & Common Knowledge](https://attack.mitre.org/): Known as Mitre ATT&CK a matrix of tactics, techniques & Procedures observed in malicious actors campaigns.
    - Tactics: A established behavior of an actor.
        - Credential Access: malicious actors access a password.
    - Techniques: The specific execution of that behavior.
        - Brute Force SSH password: malicious actor uses thc hydra to brute-force ssh password.
    - Procedures: How to perform the execution.
        - Emotet a crimeware has been observed using a hardcoded list of passwords to brute force user accounts.
- [Center for Internet Security Benchmarks](https://www.cisecurity.org/cis-benchmarks): An organization that publishes best practices in security configuration and hardening of systems.
- [OWASP TOP 10](https://owasp.org/www-project-top-ten/): An open-source web applications security project. Top Ten Web vulnerabilities.

#### Matrix of TTPs
- Enterprise
    ###### techniques categories
    - Initial Access: entry vectors to gain a foothold in newly compromised systems.
    - Execution: perform actions on compromised systems.
    - Persistence: maintain access in compromised systems.
    - Privilege Escalation: assume higher rights within compromised systems.
    - Defense Evasion: bypass controls inside the victim system.
    - Credential Access: obtain credentials from compromised systems.
    - Discovery: find new possible targets and data within compromised systems.
    - Lateral Movementt: move around compromised systems.
    - Collection: gather information elements from compromised systems.
    - Exfiltration: take data out of the targeted victim.
    - Impact: how it affects victim organization/environment.
- Mobile
- Cloud pre-att&ck

#### Center for Internet Security
- Baseline: What is needed to be in place for security systems.
- Configure: How to apply it.
- Security: Check if control is in place or not.
CIS Level 1: Basic security requirements needed for a specific system.

CIS Level 2: Suggested security settings for greater security. (May result in loss of functionality).

#### Open Web Application Security Project (OWASP)

##### 2021 Top 10 Web Application Security Risks
- Broken Access Control
- Cryptographic Failures
- Injection
- Insecure Design
- Security Misconfiguration
- Vulnerable and Outdated Components
- Identification and Authentication Failures
- Software and Data Integrity Failures
- Security Logging and Monitoring Failures
- Server-Side Request Forgery (SSRF)

### The flow of Infrastructure Security Assessment
- Discover
    - Use network tools to discover network assets
    - Perform software inventory
    - Register status of OS, updates, patches, security & third parties
- Check
    - Perform network vulnerability scans (OpenVas, Nmap)
    - Consult CIS Benchmarks, Mitre CVE/ATT&CK, OWASP
- Apply
    - Software updates and patches
    - Security updates
    - Harden configuration
    - Recommend/apply mitigation, decommission, or replacement of affected assets

### Responsible Disclosure
The disclosure of know vulnerabilities and mitigations (if they have been found) after a 90 day period.
#### Address uncertainty by keeping yourself up to date
- Vulnerability Frameworks & Scanners. Helpful, but it does not represent the entire universe of threats and vulnerabilities.
- Community Bulletins and Associations. Often reveal new exploits in the wild.
- Industry Associations & Vertical Information Sharing Analysis Centers. Provide insightful information.
- Security Research Community. Always a top source for vulnerabilities and attacks.


### Reading
- [BYOD](https://www.techtarget.com/whatis/definition/BYOD-bring-your-own-device). This article gives an industry perspective on BYOD.
- [MITRE ATT&CK](https://attack.mitre.org/) Here you can read more about Mitre ATT&CK Matrix and its categories.
- [Lockheed Martin Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html) Please read this page about the different phases and definitions of the Cyber Kill Chain by Lockheed Martin.
- [OODA Loop](https://en.wikipedia.org/wiki/OODA_loop). This link will help you become familiar with a term used frequently in Cyber Security, the OODA loop.
- [Fighting Lateral Movement and Shadow IT with Machine Learning](https://www.youtube.com/watch?v=MePKGuKrUvY)