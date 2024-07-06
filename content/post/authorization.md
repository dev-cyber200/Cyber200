+++
author = "dev@cyber200"
title = "Authorization"
date = "2024-07-04"
description = "Through authorization, we aim to achieve access level control to data and services on the system. What this means is that an authenticated user may or may not be authorized to access all the files or services on the server."
tags = [
    "cyber-security",
    "authorization",
    "system-security",
]
draft = false
+++

### Linux Groups
### Linux Users
Linux being a multi-user system, it can be used to create users in order to define the access levels and permission boundaries. There can be two types of users: system users and regular users.

System users are able to run non-interactive or background processes on a system with lesser privileges. These users are created without the home directory and are mostly used to control installed softwares.

Regular users are the user accounts who can perform logging in through the linux UI and have a home directory associated with the account. They have full access to their home directory and may or may not have access outside it. To view the currently logged in user, we can use the whoami command while, to list all users associated with the system, we can peek into the /etc/passwd file discussed in the previous lesson.

In addition to the two user types, there is the superuser, or root user, that has the ability to override any file ownership and permission restrictions. This is the highest access level of the system and this user can make any modifications to the filesystem or processes.


### Access Control
#### Controlling & Defining Permissions
It allows a normal system user to run programs with the security privileges of another user of higher privilege. By default, that user can be the root or superuser user on the system. The command will prompt for your password and will verify if you are a permitted user for this command. If the normal system user is an allowed user in a file called /etc/sudoers, they can execute the command at the higher privilege. 

#### Best practices 
##### Regularly Monitoring for User Accounts and Access Levels
Creating user accounts for various tasks is easy but often those accounts are not deleted once they are no longer needed. It is essential to build automated monitoring of such accounts to ensure that they don't become a point of failure in case of a cyber attack.


##### Controlling Accounts Through Password Rotation
This technique also helps to remove stale accounts if no one updates their password after a certain number of days.

##### Implementing the Principle of Least Privilege
This goes back to our first lesson where we talked about the benefit of only providing the amount of access to a user which is required for day to day work.

##### Eliminating Shared Account Usage
Sharing of account credentials is a bad practice, especially when there is no control over who uses the credentials.

##### Controlling Account and Group Access

##### Manage and Record Privileged Activity
Keeping a trail of all the privileged activities on the system not only helps with creating detection techniques, it also helps identify the type of usage in case of a security incident. It helps connect the dots in order to figure out the infection chain.

```bash
# Deny app-admin user from using 
# the su command
vi /etc/sudoers
app-admin ALL=(ALL:ALL) ALL,\
!/bin/su
```

### Ownership & Permissions
- Changing File Permissions: `chmod u<g|o>+rw test.sh`

- Changing File Ownership: `chown`

### Unauthorized Processes

#### Limiting Network Exposure by Eliminating Unnecessary Services
When we run certain services that require network access, like SSH, these services bind themselves to specific ports and listen for connection. There are two important points to note here:

- The running process
- The socket connection launched by the service.

#### Determining Open Ports on the System and the Process Associated with Them
- `netstat -a` fro performing socket-level diagnosis on the system
- Examine each and every port to determine if there are any ports that stand out or which are not the standard port numbers.
- Identify which process has bound to the particular socket and the user-level access of the process. 
    - `netstat -antp`
    - `ps -p <pid>`
- Try and determine the files associated with that process to understand if it was a malware or spyware file which was executed on the system

### Authorization with NAC
Network access control can also prevent unauthorized access to data both internally as well as externally. Insider threats are a real problem that every organization has to deal with

#### Limiting Unauthorized Systems from Remote Connection
#### Utilizing iptable Rules for Restricting Access
- Work with filter table, NAT table, mangle table and the raw table to define rules
- `sudo iptables -A INPUT -p tcp --dport 22 -j DROP`
- `sudo iptables -A INPUT -s 192.168.56.101 -j ACCEPT`
- `iptables -A INPUT -i eth1 -p tcp --dport 31337 -j DROP`

### Threats Due to External Devices
External devices can be used as a potential attack mechanism on highly critical systems like industrial control systems, nuclear power plants, military servers, etc. In order to gain some form of access to those systems and networks, attackers may use a malicious insider to connect an infected device to the systems so that they can infect the system with backdoors and spyware. Such tools can then open up sockets and connections with which the attackers can use to infiltrate the network. These types of attacks are usually carried out on industrial grade systems that do not have any inbound connectivity from the internet.

#### Best practices  to prevent from such attacks
- Disabling External Ports: USB and CD/DVD ports
- Disabling Auto-Run and Auto-Play Features: Operating systems implement a means to automatically execute the content inside an external storage media as soon as it is plugged into the system. Attackers exploit this method to execute their payloads as soon as the external device is connected to the system.
- Antivirus Scanning of External Devices: A lot of times, it is not feasible to disable external ports on the system. In those cases, we can deploy Antivirus scanning programs that can be configured to automatically scan the external devices for the presence of malware and spyware as soon as they are connected to the system.
- Protecting Bluetooth Connectivity: A security exposure can occur if your critical servers have Bluetooth enabled. It opens up a potential door for attacks in multiple ways. Make sure that, if the service is required, it should be set in non-discoverable mode or completely disabled if it is not required.
