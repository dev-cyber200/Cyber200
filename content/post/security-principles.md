+++
author = "dev@cyber200"
title = "Security Principles"
date = "2024-06-15"
description = "Offensive techniques often referred to as ethical hacking or penetration testing, involve simulated attacks on systems to identify and address vulnerabilities."
tags = [
    "cyber-security",
    "principles",
]
+++

### CIA Triad
- Confidentiality: Keeping data secret or private.
- Integrity: Ensuring the legitimacy of data so it can be trusted.
- Availability: Ensuring networks, systems, and applications are up and running.

### Authentication Factors:
- Knowledge - Something you know.
- Possession - Something you have.
- Inherence - Something you are.
- Location - Where you are.
- Behavior - Something you do.

### SFA, DFA, and MFA
Single, Dual, and Multi-Factor Authentication are all important forms of authentication you'll encounter. The more types of authentication are required the more secure, and more complicated, your system will become.

### Authorization
Determines what an authenticated user can, and cannot, do.

### Multi-Tenant and Single-Tenant
In a multi-tenant system, data is commingled with other user's data. Meanwhile, in a single-tenant system, your data is in a completely isolated environment.

### Non-Repudiation
Refers to a person's inability to deny something. Basically, someone cannot claim they did not do something. A user cannot pretend they didn't do an action they did.

### Principles of Secure Design
- Principles of Secure Design and Establishing Security Requirements
    - Secure design is a proactive security approach. Secure design is the process of building an application that has been designed with security in mind from the ground up. This is opposed to a more reactive approach of building an application and attempting to secure it after it has been developed.

<br/><br/>
- OWASP Secure Design Principles
    - Minimize Attack Surface
    - Establish Secure Defaults
    - Principle of Least Privilege
    - Defense in Depth
    - Fail Securely
    - Don't Trust Services
    - Separation of Duties
    - Avoid Security by Obscurity
    - Keep Security Simple
    - Fix Security Issues Correctly