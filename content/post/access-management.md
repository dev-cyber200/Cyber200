+++
author = "dev@cyber200"
title = "Identity Access Management"
date = "2024-07-13"
description = ""
tags = [
    "cyber-security",
    "access-management",
    "infrastructure-security",
]
draft = false
+++

### Firewall Best Practices
- Establish access based on the organization's needs and priorities.
- Determine who can get access.
- From where they can access.
- What services and protocols are needed
    - Example file sharing via SMB or internal company portals via HTTP.
- Do you need VPN access (L2TP, IPSec, PPTP)?
- Enforce services and protocols that are allowed or denied for inbound or outbound traffic
- Application-aware. Take advantage of devices that have application-aware capabilities.

### Clear Text Protocols Rules

- Deny clear text protocols such as FTP, Telnet, and TFTP.
- Do you have internal mail servers?
    - No? then block things like SMTP, POP.
- There might be critical servers that require NO inbound traffic from the internet or specific departments.
- Above all, your rules must cover the basics then apply specific business use-cases.

### Commercial Firewalls Best Practices

Most of the commercial firewall products follow a subscription model.

An annual subscription is required for:

- Receiving updates of the device operating system.
- Getting signature and feature updates.
- Enabling logging to be configured.
    - You must be able to monitor these devices. Therefore, logging must be enabled and configured correctly. You do not want firewalls shutting down or configurations being changed.
- Ensure management interface is only accessible via encrypted protocols (No HTTP or Telnet).
    - Some commercial Firewalls allow HTTP or telnet access for configuration. Make sure this is disabled. Only allow configuration over encryption (TLS, SSL)
        - Ensure password complexity is applied
        - 12 characters
        - 1 number
        - 1 special character
        - 1 Capital letter
        - If you expose your management interface, it will be probed. Make sure your password is complex.
- Ensure lockout settings and failed attempts are set. You cannot set a limit for root or admin as you will lock yourself out.
    - This is actually a technique that attackers will use.
- When possible, enable Multi-Factor Authentication, meaning use more than simply a password.
- Attempt not to expose the management interface to the internet or create Network ACLs only allowing corporate addresses.
- Backup configuration and state, always keep the device up to date, firewalls are targeted by malicious actors.


### Access Control List Best Practices

- Organizational Unit
    - Groups
        - Users
            - Directories and Files
You always want to start from the general to the specific. This is the best way to apply access control lists. If you start from the bottom assigning user-specific permissions, you will create a mess of untraceable permissions and likely break many applications as well.

- Avoid setting permissions for a single user.
- Permissions should be targeted for only the users and groups that need access.
- Avoid setting Everyone/World permissions whenever possible.
- Always consider application access when setting ACLs.
- Stringent permissions can break applications.
- Avoid full control for users unless necessary.
- Shares and directories should be owned by system/root/administrators, not users.
- Remove Anonymous, GUEST, Everyone wherever you find it unless absolutely needed.

### Implementing VLANS and Network Segmentation
#### Benefits of VLANs

- Isolate hosts within that defined VLAN.
- Can improve performance by avoiding network segment collision.
- Hosts can connect with each other even if not connected to the same switches.

#### Best Practices for VLANs

#####  Promiscuous Ports (P-Ports): A ports that can communicate with all other ports on a VLAN.

- Management VLANs should be separated from all others.
- Isolate VLANs used for
    - Guests
    - Visitors
    - Temporary personnel
    - Contractors
- Watch for promiscuous ports, unused interfaces, and disable unneeded protocols.
- Be selective on what VLANs are allowed on the trunk.

#### VLAN Vulnerabilities
- VLAN Hopping Exploits: Jumping to differnt VLANs in an unauthorized manner.
- Switched Spoofing VLAN Attacks: Creates a fake switch and achieves a trunking link between VLANs.

### Network Segmentation Best Practices
- Where applicable, use physical segmentation.
    - The network segmentation concept is similar to VLANs but can be applied by other means.
    - Example: Nuclear power plants cannot have ANYTHING connected to the internet.
- Use firewalls to segment networks.
- You can use Firewalls to segment your network and limit access from other network segments.
- Restrict access via routing and ACLs or VLANs.
- Visualize and map your most valued assets, make it difficult for attackers to get to them.
- A well-segmented network may prevent and contain the damage from compromise.

#### The Top Ten Web Application Vulnerabilities
1. Injection: Unsanitized data against an interpreter as part of a command or query. SQL, NoSQL, LDAP.

2. Broken Authentication: Wrong implementation of authentication functions at the application level. Allows attackers to compromise passwords, keys, tokens.

3. Sensitive Data Exposure: Exposure of PII, financial, or healthcare information.

4. XML External Entities (XXE): Misconfigured XML processors.

5. Broken Access Control: Incorrect limit settings for authenticated users, allows attackers to see other users' accounts or data.

6. Security Misconfiguration: Insecure default configurations.

7. XSS: Application reflects untrusted data in a new web page without validation

8. Insecure Deserialization: Data controlled by a user gets deserialized and potentially allows attackers to manipulate serialized objects to pass malicious code into the application.

9. Using components with known vulnerabilities: Libraries, frameworks, and modules with known vulnerabilities

10. Insufficient logging & Monitoring: Allows attackers to go undetected


### Web Application Firewall

- Serves the same function of a firewall but focused on HTTP traffic, web services.
- Protects against injection attacks (SQL Injection, NoSQL, OS, etc.).
- Blocks known malicious requests and inputs
    - Example: Format strings
- Blocks or protects malicious API requests

#### Open-Source WAFs

ModSecurity by TrustWave is the most popular open-source web application firewall and can be used with Linux based or Windows operating systems. ModSecurity has a plethora of community detection rules. This is definitely, the best choice if you are looking for an entry-level, low-cost implementation of a WAF.

- ModSecurity has rules for attacks such as XSS SQL Injections, General Malicious activity & Common Attacks, and Trojans.
- ModSecurity works with Microsoft IIS Server.


#### Application Program Interface (API)
A web interface that interacts with services and applications. APIs are used for communication and interactions with clients within a framework of detailed specifications.

- APIs reach deep into systems and applications, and they are injection points.
- APIs must be protected and monitored.


### Remote Access Management Best Practices

- Establish an Acceptable Use Policy for remote access.
- Encryption must be enforced in every connection from outside into the perimeter.
- Implement Multi-Factor Authentication (MFA).
- When possible, only allow connections from company provisioned devices.
- If access from BYOD devices must be allowed, enforce management agents before devices are allowed to connect.
- Forbid Shared Access Accounts. Access must be granted on an individual basis.
- Evaluate the risks of remote access architecture you chose.
    - For Example, if you chose a web single sign-on portal, you may need to protect that portal with a WAF.
- Enforce credential management security policies.
- Enforce network management, monitoring, and principles of least privilege and segregation of duty.
- This will allow you to isolate, contain, and deny users that could be compromised.
- Limit length and duration of sessions. Employees will leave sessions open and expose the company.


### Ipv6 Issues
- Network Address Translation (NAT) has slowed the adoption of IPv6.
- Legacy hardware and architecture is still in place that works better with IPv4.

### IPv6 Risks
- Due to address extensions and a large number of addresses, it can be difficult to manage.
- Runs by default, potentially being missed by monitoring devices and logging settings. This provides a potential access path for attackers.
- Network security tools running on IPv4 do not necessarily protect IPv6.
- There are still support issues with ISPs and Vendors. Not all application services and internet providers are fully supporting IPv6.

### Principle of Least Privilege
A user or process is given enough privileges to perform its functions.

### Benefits of Principle of Least Privilege
- Restricts users, processes, or applications to only specific privileges
- Prevents users, processes, and applications from potentially taking over the operating system
- Attack surface is reduced. If a user or applications are compromised, the damage is limited

### Best Practices for PoLP
- Track individual rights
- Monitor escalation of privileges
- Audit account privilege regularly
- Apply to PoLP across users, processes, and applications
- Ultimately, the main goal is to make sure every entity only has enough privileges to do its job

### Segregation of Duties
Segregation of Duties: A check-in place requiring more than one person to complete a task so that no one person is required to do everything.

### Identify Suitable Access Control Models
- Mandatory Access Controls: Access is based on an object and a subject.
When a subject tries to access an object, security attributes determine the level of access.
For example, a user wants to access a file, and this user may have only a specific type of access that they cannot change as this comes from a central authority.
- Discretionary Access Control: Access restrictions based on the identity of subjects or groups to which they belong.
This access model implies permissions can be inherited or passed to an individual user by others.

- Role-Based Access Control: Acces based on specific roles.
    - Can implement MAC or DAC access control models.
    - Recommended for enterprises with 500 users or more.
    - Policy neutral. RBAC is designed around roles and privileges.
    - Three Rules in RBAC
        - First and foremost, a role has to be assigned to a user, and this alone allows him to exercise permissions.
        - Second, authorization for that role has to be active and defined.
        - Third, the exercise of permission is subjected to authorization from the granted role
    - Role Base Access Controls Considerations
        - Permissions can be assigned to many roles and operations.
        - A single operation can be assigned to many permissions.
        - Roles can have many subjects, and a subject can have many roles.
        - Roles can have many permissions.

### Audit Access and Permissions
- ubuntu: https://manpages.ubuntu.com/manpages/xenial/man8/auditd.8.html

### Encryption Inside the Perimeter
- Data at Rest
    - When data is stored
    - Servers, Desktops, Laptops, and even mobiles
- Data at Transit
    - When Data Is Transmitted
    - Email encryption
    - TLS Tunnels to other offices
    - IPSec inside the perimeter
    - VPN
- Data In Use
    - Encrypt data in Memory (Random Access Memory).
    - This type of data has a high payload, and encryption is difficult to achieve.
- Standards
    - When using encryption to meet government standards, you must use only strong ciphers, FIPS-140-1-2.

- IPSec or Internet Protocol Security
    - Encrypts TCP packets end to end
    - Encryption compatible ciphers (AES, 3DES, DES)
    - Authentication Algorithms (HMC-MD5, HMC-SHA1,2)
    - Key Exchange Algorithms (IKE, Diffie Helman KEA)
    - IPSec applies for a host to host and network to network
    - Works at layer 3 in the OSI Model
    - IPSec can be used in Microsoft Windows networks and Linux based networks
    - Digital Certificates can be implemented for authentication
    - IPSec performs mutual party authentication via cryptographic key exchanges

- IPSec Protocols
    - Authentication of Header, Integrity, and Verification of packets
    - Encapsulating Security Protocol (ESP)
    - Encrypts Packet IP Header & Payload
    - Security Association: Protocols involved in the encryption process and key exchange like Internet Key Exchange protocol.

- IPSec Considerations
    - You need infrastructure in place to implement IPSec, and equipment and application compatibility issues may occur.
    - You may not want to encrypt every single network segment but only the most sensitive ones.
    - Things that do not need to be encrypted do not need to go through IPSec.
    - If not managed correctly, keys and digital certificates can be compromised. If your keys are lost or compromised, network traffic will be transparent for attackers.
    - Performance issues may occur due to IPSec processing loads. IPSec is process intensive due to the constant encrypting and decrypting loads.

### Key and Certificate

#### Cryptographic Keys
A string of data used to unlock cryptographic functions.
- Authentication
- Authorization
- Encryption

Keys are fundamental for encryption management.
- You must know where they are, who has them, and when they need to be rotated.
- They must be protected and managed.
- If your keys are compromised, you must revoke your keys and reissue them.

#### Digital Certificates
An electronic document that proves ownership of a public cryptographic key.

- Includes information about the key.
    - Owner
    - A signature that verifies its authenticity.
- A Certificate Authority usually issues Certificates.
- Certificates are used to sign and authenticate encrypted communications.


#### Public Key Infrastructure
Refers to the settings related to software, roles, policy, and hardware needed to create and issue, store and revoke:
- Digital Certificates
- Encryption Keys

#### Public Key Infrastructure Components
- Registration Authority.
    - Verifies requests for issuing a Certificate to an entity.
- Certificate Store.
    - Database that stores digital certificates.
- Certificate Revocation List.
    - List of Digital Certificates that have been revoked and that serves as a reference.
- Certificate Authority.
    - Issues the certificate and the validity.
- Create Policies.
    - Dictates the role's duties of PKI infrastructure.
- Entities Issued Certificates.
    - Signed Documents, Smart Card logons, SSL/TLS Authentication, Encryption of Email communications.

#### Best Practices For Key Management
- Protect your encryption key management system, including physically.
- Access must be audited.
- Keys must be rotated.
- Create an air gap backup.
- Backup your keys somewhere off-site and NOT connected to the internet.
- Encrypt where you store them.
- Create recovery keys in case of system failure or compromise.
    - Optional: Create recovery keys using a third party as custodian.
- Manage issue & revocation.
    - Revoking them early may become a burden and cost money.
    - Work to find the proper length of time for a certificate.
- Be ready to replace or revoke them if needed.
    - Sometimes third parties can be compromised or algorithms are broke
    - Be ready to identify, revoke, and replace them.
- Self-signed will get you going but consider its risks.
    - Self-signed certificates are easy but risky.
    - It is easier to issue your own self-signed certificates than use CA.
    - However, so can malicious actors.
    - It is better than having no certificates at all, but eventually, they will have to be replaced or managed correctly.
- Use a third party. Building a PKI may be too expensive.
- Store them separated from the key. This is a way to avoid a single point of failure.


### Credential Management
Workflows and procedures related to the provisioning, use, and management of credentials within your perimeter, either issued by you or by a third party.

It would be best if you considered the following:

- Credentials that you issue in your company or credentials issued by a third party (i.e., Cloud Provider).
- How you issue or revoke credentials.
- What policies are they subjected to?

A credential is Information that identifies an account and protects it.

#### Credential and Authentication Types
- Physical
    - Paper badge
    - Card with magnetic strips
    - RFID Cards

- Digital Types
    - Mobile IDs
    - Digital Certificates
    - Cryptographic Keys
    - Passwords

- Biometric
    - Retina
    - Fingerprints

- Credential Management
- The main credentials used in enterprises are usernames and passwords.
- Depending on your infrastructure, SSL/TLS Key authentication is also frequently used.
- Employee badges are a type of credential.
- Depending on the number of applications in place, an employee may need to have several credentials.

#### Best Practices: Password Management

According to CIS Benchmarks

- Password Length: 14 Characters or more.
- Password Composition: At least 1 Non-alphabetic character.
- Add a number and uppercase characters.
- Password Expiration: 1-year expiration.
    - I personally recommend 90 days. One year is too long.
- Password Banning: Top 20 more common or bad passwords.
- Session Lock Idle Time: 15 minutes.
- Monitor Failed Logins.
    - Microsoft recommends lockout after 10 failed authentication events.
- Suspend accounts, not in use.
    - Automatically suspend after 4 days of inactivity. This might be a little too much. Make sure you check employee's schedules.
- No password hints should be supplied.

#### Passwords, a Favorite Target for Malicious Actors
- Credential Stuffing
    - Credentials obtained from breaches are probed against multiple sites.
- Phishing
    - Emails, SMS, cloned sites with malicious code capture passwords.
- Keystroke Logging
    - Malware logs keystrokes can capture passwords.
- Local Discovery
    - Passwords on Stickers or spreadsheets with passwords.
- Brute Force
    - Using a dictionary of users and passwords to gain access via multiple tries.


#### Other Credentials Highly Targeted

- Email and passwords are usually the prime identification elements of federated identity.
- Access Keys.Example: Amazon Web Services Access Keys, if compromised, can grant full access to amazon's web service protocol.
- X.509 Certificates: A standard that defines public key certificates used for authentication.
- API Keys: Text strings used for API access.
- SSH Keys: Cryptographic Keys used for SSH access, mainly for servers.
- Consider Single Sign-On Applications, one single portal allows access to multiple applications from a single authentication point.

#### Best Practices: Credential Management

- All credentials have a life cycle and need to have an expiration or renewal date.
- Enforce long, complex password policies.
- Prevent embedding hard coding credentials in code or applications.
- Implement SSO & MFA if possible.

### Auditing Passwords
#### Password Alternatives
- Biometrics
- Fingerprint
- Retina
- Voice

#### Tools for Auditing Passwords
- Linux
    - John The Ripper(opens in a new tab)
    - Hashcat(opens in a new tab)
- Services
    - NCrack(opens in a new tab)
    - THC-Hydra

#### Best Practices: Password Auditing

- Establish a plan to schedule the audit. Every 3 to 6 months should be sound.
- Audit all accounts, including service accounts. Service accounts are also targeted by attacks and can be difficult to catch if compromised.
- Check against well-known password leaked files (i.e., RockYou)
    - There are many popular password files on the internet. The biggest one is RockYou.
    - Create your own with a combination of all these files and make sure your passwords do not match them.
- Create a schema for account naming and creation.
- Specific nomenclature for Servers, Desktops & Mobiles.
- Specific nomenclature for Users vs. Administrators and Service Accounts or Special Groups.
- Have policies and mechanisms ready in case of a breach.
- Use GPOs to enforce password change.
- Have Cloud Platform Mechanisms in place to enforce password change.
- Have a plan to reset and reissue other credentials as well.This may include API Keys, Account Keys, SSH Keys, etc.

### MFA

#### MFA Can Be Defeated
- Brute Force: Some MFA applications may ask the user yes or no when approving access. I saw one case where attackers were targeting students when they knew they were at lunch and could get some of them to click yes after sending them multiple requests to approve.
- Phishing: An attacker may decide to call you directly and ask you to approve a login attempt or tell them the code.
- Man in the middle: This is a technical attack where the attacker gets in the middle via proxy, sniffing, or another transparent tamper method that allows getting the code as the victim is inputting it.
- SIM SWAP: There have been instances where an attacker researches the victim and calls the cellphone carrier company when the victim is traveling or sleeping and has the company authorize a new phone. Swapping the SIM card of the cellphone resets passwords with a new device but the same number and defeats MFA.
- Endpoint or Mobile Compromise: If an attacker compromises the computer or mobile from the victim, it will get and/or execute the MFA factor.


#### Best Practices In Multi-Factor Authentication

- Combine different authentication factors per use case
- Retina scan for security operation center access
- USB Key for changing account information at HR Portal
- Watch lockouts
    - It's important to monitor, as lockouts can defeat MFA's purpose. If there are too many lockouts, productivity will decrease, and users will be discouraged from using it.
- Use apps like Microsoft Authenticator for email and cloud applications
    - SMS (last resort) or Google Authenticator for Single Sign-On portal
- Chose publicly available methods against proprietary
    - Google Authenticator
    - Microsoft Authenticator
    - If you chose a proprietary application, support might be difficult, and not all devices may be supported.
    - Google and Microsoft are widely used and supported applications
- Hardware tokens increase support with potential loss or breakage
- It is a mistake to base your MFA strategy on one single factor. Encryption Algorithms get defeated, and Hardware Token companies get hacked as well. Don't rely on a single extra factor strategy in one single factor.