+++
author = "dev@cyber200"
title = "CVE & Third Party Advisory"
date = "2024-06-30"
description = "Common Vulnerabilities and Exposures or CVE is a dictionary that provides definitions for publicly disclosed cybersecurity vulnerabilities and exposures. The goal of CVE is to make it easier to share data across separate vulnerability capabilities (tools, databases, and services) with these definitions. The National Cybersecurity FFRDC, operated by the Mitre Corporation, maintains the system."
tags = [
    "cyber-security",
    "linux",
]
draft = false
+++

## Operating System Protection Principles
The basis of OS protection is separation of its components into an inner layer, middle layer, and outer layer.

This ensures that there are proper protection mechanisms in place to guarantee that different levels can be protected from one another. Operating systems perform the task of orchestrating the flow of information between the three separated components.

#### Layered Architecture of an Operating system
Events inside an operating system are managed through a set of processes. A process is an instance of a program that has a specific purpose. A software can invoke multiple processes based on the instructions received from the end user. The operating system executes those processes and provides the result to the software or application. Due to the separation model of operating systems, processes are executed in layered rings. Each ring has its own level of permissions and privileges. The central ring has the highest privileges while the outermost ring has the least amount of privilege.

#### Advantage Of Using a Layered Approach
There are two major advantages that the operating system achieves by using this layered approach towards process execution:

- Stability: A process failure in outer rings can be easily recovered without a system crash as only the innermost ring has access to the CPU and memory.
- Defense in Depth: These rings act as layers of defense that the attacker must compromise to gain full access to the system.

#### Difference Between User Mode & Kernel Mode

A process in user mode does not have direct access to hardware, CPU, or memory. User mode does this by creating system calls to the kernel mode, which has complete access to the hardware, CPU & memory.


## CVE & Third Party Advisory

CVE provides a standardized identifier for a given vulnerability or exposure. This helps to quickly and accurately identify a vulnerability, its severity, and the overall impact on the system where it exists.

#### Common vulnerability databases
- ExploitDB: The [Exploit Database](https://www.exploit-db.com/) is a CVE compliant archive of public exploits and corresponding vulnerable software. It was developed for use by penetration testers and vulnerability researchers.

- [National Vulnerability Database](https://nvd.nist.gov/vuln): NVD is a database of standardized vulnerability information based on CVE entries. It uses Open Vulnerability and Assessment Language (OVAL) to describe the security issues in a standard language. The database provides enhanced information like severity scores in CVSS (Common Vulnerability Scoring System) and impact ratings for each CVE identifier.

##### Securing the Boot Loader
- Password Protecting the Boot Loader
Protecting the boot loader is essential in several ways. It restricts access to the system's BIOS (Basic Input Output System) which helps initialize the operating system's kernel.

- BIOS and Boot Loader Security
We can secure the BIOS and the boot loader by password protecting them. This would ensure that the BIOS and the boot loader can be protected from unauthorized users who have physical access to systems. Such unauthorized access can result in the ability to boot up another operating system using removable media or attaining root privileges through single user mode.
    - With password protecting the boot loader, we can:
        - Prevent an attacker from booting into single user mode and becoming the root user of the system.
        - Prevent an attacker from accessing the GRUB console and using the command's interface to change its configuration.
        - Prevent booting of non-secure Operating Systems by enabling dual boot system.

#### Security Baseline
A Security Baseline defines a set of basic or mandatory security objectives which must be uniformly met by all the systems in a large enterprise network. The baseline defines the minimum set of security requirements that should be present. These must be present in every existing system and servers as well as any future systems that would be added in the network. This would ensure that a uniform level of security practices and measures have been followed across all the digital assets within an enterprise.

Security baseline is defined by segregating various system access methods into individual groups. Broadly, these groups would include Access Control, Network Access, Physical security, and Software & Applications. The segregated groups can increase or decrease based on the design of the infrastructure.

Some of the examples of a security baseline would include:

- Installing only applications that are professionally needed and removing all others.
- Restricting access to privileged accounts (e.g. root, sudo, admin) to a small, controlled group of users.
- Restricting access to shared folders.
- Protecting access to the BIOS by a non-default password.
- Ensuring that the only versions which are officially supported by the corresponding operating system or software vendor are installed.

##### Need for Security Baseline
Defining a security baseline for your organization is important because:

- It simplifies the process of implementing security controls uniformly across all endpoints.
- It streamlines the process of implementing security best practices at all levels.
- It reduces the maintenance overhead and the attack surface.

##### Principle Of Least Privilege

Any discussion about security baseline is incomplete without touching upon the Principle of Least Privilege (PoLP). As its name suggests, PoLP is the idea of ensuring that any user, process, or program should only have the bare minimum privileges necessary to perform their daily functions. As simple as it sounds, it can be extremely tricky to implement this as a security baseline principle. It requires a deeper understanding of the system requirements and access levels inside the organization at various levels. The principle of least privilege can also be referred to as the principle of minimal privilege (PoMP) or the principle of least authority (PoLA).

The whole idea of implementing the principle of least privilege is that it reduces the risk of attackers gaining access to critical systems when they compromise a lower privileged account. It ensures that the compromise is limited to a certain area, thus stopping the attackers from laterally moving inside the network.