+++
author = "dev@cyber200"
title = "Authentication"
date = "2024-06-30"
description = "Authentication is a critical piece in the security puzzle. Though it may sound like an easy service to setup and build, it is actually quite complex and also opens up doors for additional security challenges."
tags = [
    "cyber-security",
    "authentication",
    "system-security",
]
draft = false
+++


### Unix Password Management Tools
Third-party password management tools come into the picture. They make it easy to:

- Manage passwords across multiple services.
- Store passwords securely.
- Configure password restriction policies.

### Defining Password Best Policies
Some Examples of Password Best Policies
- Minimum of 8 characters in the password string. It should contain characters from the four primary categories: uppercase letters, lowercase letters, numbers, and characters.
- Should not be a common string like your name, city of birth, or date of birth which can all be easily guessed by attackers.
- It should be different from your previously used passwords on the same service.
- There should be a password rotation policy which should either automatically expire the password after certain days or remind the user to change the password once the threshold is reached.

### Remote Access Management

#### Risks Associated With SSH Service
- One of the biggest risks associated with SSH is that of stolen credentials. If attackers can gain access to the credentials of a system administrator (through phishing or social engineering attacks), they can become virtually invisible in the network. Due to the strong security measures implemented by SSH, their activities will be invisible to most network security solutions deployed in the organization.

- Another risk associated with SSH is its ability to execute system commands. SSH not only helps securely transfer files over the internet, it also helps execute system commands and helps you move from one machine within the network to another. This allows the attackers to laterally move into the network while remaining completely undetected by simply using the available tools on the system. This requires no specialized malware or spyware to perform these activities. This is referred to as living off the land, a technique used by advanced attackers to silently move inside the compromised network by using system tools.

- Attackers inside the network can also abuse the SSH protocol to exfiltrate data. Most organizations permit outbound SSH access through their firewall which makes it easy for attackers already inside the network to establish a reverse-tunnel and exfiltrate the data out. A point to note here is that the attackers also do not need any special tooling in this case. SSH is set up on almost all Linux servers or, at least, it is incredibly easy to set up without alerting the intrusion detection and protection services.

- The SSH service is often running on heavily insecure devices in a network like a jump host or a CCTV camera. These insecure devices are a prime target of attackers as it gives them an easy way into the corporate network. Usually, these devices are configured with default credentials by external vendors and contractors which leaves the gates open for exploitation of the wider network.

#### A typical attack on an SSH server
- Attackers use automated scripts and bots to scan the internet and identify IP addresses that have port 22 open.
- Once the IP address is located, the bot attempts to brute force the combination of multiple usernames and passwords which are commonly used.
- If successful, the username-password combination is reported back to the attacker which they can use to make unauthorized access to the system.


#### Configuring SSH to Improve Security
- One of the essential steps for securing an SSH server is to disable root login. sudo can be used as a mode for users if they require higher permissions to execute a task.
- Define a list of permitted users. By doing this, you ensure that any other user is not able to log into the server even if it belongs to the same access group as other users in the list.
- Changing the default port of the SSH service. This can help deflect automated bots and scanners who are looking for open port 22 randomly on the internet to brute force login credentials.
- Configuring SSH keys for login instead of passwords can make it even more difficult for attackers to brute force login credentials. You can disable password-based access and instead generate public keys on the client machines and add them to the server.
- Using multi-factor authentication (MFA) can be another way of further securing the client-server authentication. This may require using additional tools and libraries but they can be easily integrated with the ssh server to validate the end-users through MFA.

### Encryption

#### Securing Data at Rest
Data at rest encryption ensures that files are always stored on disk in an encrypted form. The files only become available to the operating system and applications in a readable form while the system is running and unlocked by a trusted user. Encrypting data at rest is vital for regulatory compliance to ensure that sensitive data saved on disks is not readable by any user or application without a valid key.

#### Implementing Encryption

##### Directory Level Encryption (DLE)
As the name suggests, directory Level encryption applies to directories as a container. Access to files inside the directory would require the use of encryption keys. This approach can also be used to segregate data of identical sensitivity but requires multiple encryption keys for different directories based on content type or access groups.

##### File Level Encryption (FLE)
This is the lowest level of abstraction where individual files are encrypted instead of the entire disk or directory. This is again done to protect data of varying sensitivity on the same system.


##### Full Disk Encryption (FDE)
Full disk encryption works by encrypting a system's entire hard drive. This not only includes the data stored on it, but also the operating system files. An encryption key or passphrase is used during system boot which begins the decryption process.