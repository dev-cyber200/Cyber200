+++
author = "dev@cyber200"
title = "Discovery Methodlogies"
date = "2024-08-05"
description = ""
tags = [
    "cyber-security",
    "web-app-security",
    "discovery-methodlogies",
]
draft = false
+++

### Static Application Security Testing (SAST)
Static Application Security Testing (SAST) is a tool used to analyze application source code or compiled code to help identify possible security vulnerabilities. This tools is able to find potential vulnerabilities through scanning for known issues within the tech stack. This tool is able to walk through the application workflows and look for possible ways to exploit the application using injection and other attack vectors.

### What a SAST is not?
SAST is not a replacement for manual testing, because they are trying to interpret the application workflows, it is easy for these tools to get lost in applications that have complex workflows. The SAST is also only scanning the static code and can not discover environment level vulnerabilities. Also, these tools are looking for known vulnerabilities and design patterns. As applications become more complex, it becomes harder for these tools to properly asset an application.

### Why Use a SAST?
Even though there are some shortcomings of a SAST, they can easily scan large code repositories and help Security experts focus their attention on areas that have more complexity in them. They are also helpful in the software development life cycle (SDLC), as they can be introduced in the development process to perform commitment level scanning. This will help give developers a faster feedback loop to help find immediate security issues and move the security awareness level high up the SDLC, which makes fixing these issues less expensive.

### Bandit
A open source tool that was designed to find security issues within Python code. https://github.com/PyCQA/bandit


[OWASP source code Analysis](https://owasp.org/www-community/Source_Code_Analysis_Tools)

### Read a Static Scan Report
### Set the OWASP for Each Vulnerability
- OWASP: NEEDMOREINFO
- OWASP: A9

### Prioritize the Vulnerabilities
#### Calculate Severity using Risk Rating
- Risk = Likelihood * Impact(Business Impact(BI))
- [Risk = ((Discovery + Exploitable + Awareness + Detection)/4) * BusinessImpact](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology)
- Discovery is how easy it is for a group of attackers to discover the vulnerability
- Exploitable is how easy it is for a group of attackers to actually exploit the vulnerability
- Awareness has to do with how well known is this vulnerability to the type of attackers that will attack this type of system
- Detection has to do with our ability to actually detect if this attack is or was executed


### Prioritize Vulnerabilities

OWASP Risk Rating template in [google sheet](https://docs.google.com/spreadsheets/d/1-Zz7V09Bxd6bd1IkZXOXvKschh8fx69rF64Jk-Nc-Fk/edit?gid=0#gid=0)


### How to Recommend High-Level Best Practices
A narrative on what the issue is and a high level best practice approach on fixing the issue. This information should be enough to help the developer better understand the issue and lead them on their way to fixing it using standard industry best practices.

- [https://owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/)

- comparing TOP10 from past years

### Make and Write a Recommendation
- Provide a link to the OWASP-10 type of ulnerability and provide Best Practices you may have discovered


### Limitations
When using SAST it's essential to remember the limitation of this tool. SAST tool can only look for known issues and configurations within the codebase it was designed for, so it won't find issues that are not known or private. This tool is excellent at scanning large codebases, but it may not correctly handle all the workflows for complex systems. Finally, this tool is most effective when appropriately trained for your application.

### Further reading
- https://owasp.org/www-community/OWASP_Risk_Rating_Methodology
- https://www.kitploit.com/2019/05/bandit-tool-designed-to-find-common.html
- https://www.kitploit.com/2019/05/bandit-tool-designed-to-find-common.html