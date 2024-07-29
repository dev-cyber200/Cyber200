+++
author = "dev@cyber200"
title = "Top Security Failures"
date = "2024-07-27"
description = ""
tags = [
    "cyber-security",
    "infrastructure-security",
    "security-failures",
]
draft = false
+++

### Top Security Failures

- Exposed Services: Anonymous access to Access Server with FTP Server.
- Unnecessary Accounts, Excessive Permissions: Guest accounts enabled with access to company file servers.
- Denial of Service: Business Application Server is taken down by attackers.
- Unpatched, Outdated Vulnerable Services, Applications: Outdated Desktop computers infected with Ransomware.
- Weak access controls, exposed credentials: The developer places remote access credentials in the code repository.
- No backup or disaster recovery plan: Hardware failure causes the company's data loss.
- Unknown services, applications, and assets running inside the perimeterr: Users running crypto mining software.
- No basic AV, Operating Systems, Firewall Protections: Computer Worm takes over all desktops.

### Nmap Features
- Host Discovery
- Port Discovery
- Version Detection
- OS Detection
- Script with specific features
- Nmap can be used via terminal.
- The official GUI is called Zenmap.
- Most of the security products that perform network scanning and vulnerability scanning are based on NMAP.

#### Nmap Vulnerability Scanning
- You can discover vulnerabilities in hosts using Nmap Scanner.
- Vulnerability discovery should always be made with due care and only under authorization.
- Nmap can discover and exploit vulnerabilities.
- Nmap is not a full-featured vulnerability scanner but is a good place to start.

#### Nmap Vulnerability Discovery
- You can discover vulnerabilities by looking at specific services, versions, or application banners.
- You can also use NSE Scripts. These are special scripts designed to test for specific vulnerabilities.

#### Nmap Script Engine (NSE)
- Allows users to write and share scripts (Written in LUA language)
- These scripts can automate specific tasks, including
    - Specific network discovery
    - Specific services
    - Testing for vulnerabilities of certain exploits
- The following operator -sC applies all default scripts
    - Example: Nmap -sC host or CIDR
- Considered intrusive
- Should not be run without permission
- Nmap NSE Categories: https://nmap.org/nsedoc/categories/

### Identify Exposed Services Best Practices
- Logs and Network monitoring can also indicate abnormal activity to and from the internet.
- Watch for unusual protocols.
- Check cloud storage.
- Restrict Peer to Peer Networking.
- Scan for Malware.
- Prevent Cryptomining.
- SMTP or POP traffic may mean spam is running inside your perimeter.
- Restrict Outbound Inbound Traffic.
- Take advantage of application-aware visibility from UTMs.
- SIEMs have add-ons and applications that help to detect malicious traffic.

#### Unnecessary Accounts
- Windows Guest Accounts may give access to shares, folders, and even files.
- WiFi routers may allow unauthorized access
    - You can actually Google the default passwords of almost every electronic device. Just like Windows,* Ubuntu Guest Accounts will provide a level of access that can be used for exploitation and escalation of privileges.
- A firewall with default credentials can allow attackers to modify security settings
    - If an endpoint is compromised, attackers will probe all these devices and see if they have default credentials.
- Also, Ex-employee accounts left active can potentially be compromised either by external or internal actors.

#### Best Practices
- Enforce SoD, PLoP.
- Avoid giving owner full control permissions.
- Reduced membership of Administrators/Root groups.
- Apply policies that restrict, reduce, disabled unnecessary permissions and privileges.
- Use RBAC to enforce and restrict privileges.


### Denial of Service
Denial of Service is a type of attack where legitimate users are prevented access to a system, application, or host. The use of victim hosts usually amplifies these attacks know as "zombies." These zombies are then directed to attack the target.

#### Types of Denial of Service Attacks
- Volumetric
    - Attack Via Layer 3
    - Pipes are filled with garbage packets.
    - Examples: TCP Flood / UDP Flood
    - Application Based
- Attack via Layer 7
    - Applications are overwhelmed with requests.
    - Examples: GET Flood / Post Flood

#### The following protocols are vulnerable to DDoS
- Echo: port 9
- Daytime: port 13
- Quote of the Day: port 19
- Chargen: port 17
- SNMP: port 169
- DNS: port 53

#### Mitigate DDoS
- Disable internet exposed services that are vulnerable to DDoS.
- If the attack is layer 3 based, you can use ACLs to block malicious traffic.
- If the attack is layer 7 based, you will need to scrub traffic.
- Any attack significant enough will require DDoS protection services.

### Discover Unpatched Services
#### Patching Software Ubuntu

- Find Software that is upgradable with: `sudo apt list --upgradable`
- Find the number of upgradable packages: `sudo cat /var/lib/update-notifier/updates-available`
- Find Security updates: `apt-get -s dist-upgrade |grep "^Inst" |grep -i securi`
- Install them via `apt install update or upgrade`

#### Updating Unpatched Systems Considerations
- Some legacy systems cannot be updated
- Have a plan for patches and out of band patches
- Failing to patch may affect business continuity
- Prioritize sensitive and exposed systems
- Depending on how big your infrastructure is, you may have to accept the risk.

### Identify Weakness in Ciphers

#### Weak Ciphers
- A weak cipher is an encryption algorithm with an insufficient key length.
    - The larger the key, the harder it is to break.
    - The shorter the key, the higher likelihood it can be cracked.
- Always keep in mind support for legacy OSs and Applications.

#### Strong Ciphers

Anything higher than 128 Bit Key is considered a strong cipher algorithm.

FIPS-140-2:
- aes256-ctr
- aes192-ctr
- aes128-ctr

#### indows Servers IIS 10 CIS v1.1.1

Following ciphers must be disabled:

- SSLv2, SSLv3
- TLS1.0, TLS1.1
- DES, RC4, AES 128
- NULL, DES

Following ciphers must be enabled:

- AES-256
- TLS1.2
- HTTP Strict Transport Security (HSTS) Header must be set

#### For IPSec

- Do not use Pre-shared Keys
- Do not use Diffie-Hellman
- Use the strongest encryption algorithm available considering compatibility

#### Strong Ciphers Ubuntu

Enforce Strong Ciphers in Openssh

- aes256-ctr
- aes192-ctr
- aes128-ctr

Enforce Strong Ciphers for Message Authentication CIS 5.2.14 (FIPS-140-2)

- hmac-sha2-256
- hmac-sha2-512

Ensure only strong Key Exchange Algorithms are used CIS 5.2.15 (FIPS-140-2)

- ecdh-sha2-nistp256
- ecdh-sha2-nistp384
- ecdh-sha2-nistp521
- diffie-hellman-group-exchange-sha256
- diffie-hellman-group16-exchange-sha512
- diffie-hellman-group14-exchange-sha256

#### Linux Applications

- Apply highest encryption algorithm along with the highest version of TLS if compatible
- Ensure the password hashing algorithm is SHA-512 CIS Benchmark 5.3.4
- Enable Pluggable Authentication Module (PAM)

#### Pluggable Authentication Module

- PAM: Security mechanism in Linux Operating System allows using different authentication methods beyond simple usernames and passwords.
- Flexible Policies
- Per application policy
- Sets default authentication method
- Single password for multiple authentications
- PAM helps enforce strong ciphers for authentication

#### Enable PAM

- To a pply to an SSHD service that supports it like OpenSSH: `sudo apt install OpenSSH-server`
- Can be configured at: `/etc/pam.d`

#### PAM: Audit and Discover Weak Ciphers

CIS Benchmark 5.3.4

- Ensure the password hashing algorithm is SHA-512
- SHA-512 provides much stronger hashing than MD5, increasing the effort for an attacker to determine the password successfully.

- Audit `grep -E '^\s*password\s+(\S+\s+)+pam_unix\.so\s+(\S+\s+)*sha512\s*(\S+\s*)*(\s+#.*)?$ ' /etc/pam.d/common-password`
- Remediation
    - Edit /etc/pam.d/common-password
    - Include the sha512 option for pam_unix.so
    - password [success=1 default=ignore] pam_unix.so sha512

### Backup

#### Backup 3-2-1 Rule
- 3: 1 Production copy plus 2 additional backup copies.
- 2: Copies should be in 2 different storage types. Example, DISK, NAS, TAPE.
- 1: Store copies offsite to a storage unit, warehouse, third party.

#### Types of Backups
- Full: This the first and full copy of the data.
- Differential: Only copies new files or files that were changed since the last backup.
- Incremental: Copies all files and data that was changed regardless if it was full or differential.

#### Backup Best Practices
- If backing up encrypted data, keys must be backed up and protected as well.
- Full backups take the most time to recover.
- ALWAYS check backup file integrity.
- Backup Data AND System State. Especially servers such as domain controllers or databases.
- You must have a Physical copy saved offsite.
- In some instances, you may want to consider a hard copy backup strategy.
    - Printouts of patient histories
    - Data printouts for reference.

### Disaster Recovery Plan
#### Implement Disaster Recovery
- Hardware & Software Inventory
- Data Sensitivity & Protection
- Access & Identity Management
- Management of Encryption & Credentials
- Backup
- Natural Disaster
- Ransomware
- Terrorism
- Rogue Insider
--------------------
- Once you have created your plans, you must drill your plans. Not practicing renders your plans reduces the likelihood of success.
- Involve all related departments. Each department knows what to prioritize in case of a disaster.
- Protect those plans and save copies offsite as well. You do this, so they don't get destroyed by the actual disaster.
- Adapt plans threatscape.
    - If you are in California, wildfires may be something to consider.
    - If you are in Florida, Hurricanes definitely are a factor.
- Terrorism may have become a less plausible threat, and you might change that scenario and instead plan around power blackouts.
- Constantly updating your plans.

#### Business Continuity Best Practices

- Requires specific procedures per business goals and operations.
- Depends on the Disaster Recovery Plan.
- Balance your recovery dependence.
- Do not rely on one vendor.
- Do not rely on one technology.
- Have a team in place and avoid single points of failure.
- Business Continuity plans must involve all affected business units.

### Vulnerability Management

1. Discover: Work to discover vulnerabilities.
- Software inventory
- Manual checks
- CIS benchmarks
- Vulnerability scans
2. Identify: You must identify these vulnerabilities and discover what is vulnerable.
- A software library
- A webserver software
- An office application
- An outdated/unpatched operating system?
3. Classify: Based on what you find, you must categorize these vulnerabilities.
The best way to do this is to set them as Low, Medium, High, and Critical depending on their CVSS Score and nature.
4. Mitigate: recommend and perform mitigations, and mitigation must be driven by the sensitivity of the vulnerabilities we found.
5. Retest: Once the mitigation or remediation is performed, you will then retest to assure proper mitigation is in place.

#### CVSS Metrics
- Exploitability Metrics:
    - Attack vector
    - Attack Complexity
    - Privilege Required
    - User Interaction
- Base Metric:
    - Impact Metrics
    - Confidentiality Impact
    - Integrity Impact
    - Availability Impact
- Scope:
    - The ability of a vulnerability to affect areas beyond its context.
- Temporal Metric Group:
    - Exploit Code Maturity
    - Remediation Level
    - Report Confidence
- Environment Metric Group:
    - Modified Base Metrics
    - Confidentiality Requirements
    - Integrity Requirement
    - Availability Requirement