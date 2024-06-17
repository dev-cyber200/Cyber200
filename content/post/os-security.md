+++
author = "dev@cyber200"
title = "CVE & Third Party Advisory"
date = "2024-06-16"
description = "Common Vulnerabilities and Exposures or CVE is a dictionary that provides definitions for publicly disclosed cybersecurity vulnerabilities and exposures. The goal of CVE is to make it easier to share data across separate vulnerability capabilities (tools, databases, and services) with these definitions. The National Cybersecurity FFRDC, operated by the Mitre Corporation, maintains the system."
tags = [
    "cyber-security",
    "linux",
]
draft = true
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