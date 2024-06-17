+++
author = "dev@cyber200"
title = "Review and Audit"
date = "2024-06-16"
description = "Offensive techniques often referred to as ethical hacking or penetration testing, involve simulated attacks on systems to identify and address vulnerabilities."
tags = [
    "cyber-security",
    "audit",
]
+++


## Infrastructure and Control Audits
- Controls: The measures an organization takes to reduce risk.
- Preventive: Security measures to stop an event from occurring. They can be:
    - Physical
    - Technical
    - Procedural
    - Detective
    - Security measures to detect or alert on an event or incident

- Corrective: Security measures are taken to repair damage.

- Audit: An official examination or review.

- Information Systems Security Audit: Systematic assessment of an organization's security operations.

- Control Frameworks - Frameworks provide a structure that can be used to manage security controls.

- Control Audits - Performed by a 3rd party to test the efficacy of your controls.

- Infrastructure Audits - Performed internally to assess our information systems.


## Design, Architecture, and Code Reviews
- Design - Assess a proposed design and highlight areas to consider when building out the system.
    - What type of data we will be processing and storing.
    - Is it new?
    - Is it a protected type?
    - Where will the system be hosted? On-prem or public cloud?
    - Any new ‘risky’ processes or features?
    - New encryption or authorization?
    - New user functionality?
- Architecture - Assess a proposed (or in some cases already built) architecture.
    - Tell me about how you’re encrypting __________.
    - Algorithm
    - How is data stored?
    - How is it encrypted?
    - How is it accessed?
    - Dig into APIs.
- Code - Aims to identify security issues in the source code.
    - How are you sanitizing output and verifying input?
    - What third-party libraries are you using?
    - Are there any hard-coded secrets?

## Industry Standards and Best Practices
- Frameworks
    - Independent Parties
        - Center for Internet Security: [CIS Critical Security Controls](https://www.cisecurity.org/controls)
        - International Organization for Standardization (ISO): [ISO 27001](https://www.iso.org/standard/27001)
        - PCI Security Standards Council: [PCI DSS](https://www.pcisecuritystandards.org/)
    - Government Organizations
        - [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework/csf-11-archive)
        - Healthcare Insurance Portability and Accountability Act (HIPAA)

## Writing Reports and Recommendations

1. Executive Summary
- Purpose: Provide a high-level overview of the audit, highlighting key findings and recommendations for senior management.
- Content
    - Objective: State the purpose of the security audit.
    - Scope: Describe the scope of the audit, including systems, applications, and networks assessed.
    - Methodology: Briefly explain the methodologies used, such as penetration testing, vulnerability scanning, or configuration reviews.
    - Key Findings: Summarize the most critical findings.
    - Recommendations: Highlight the most important recommendations.
    - Conclusion: Provide a brief conclusion on the overall security posture.


2. Introduction
- Purpose: Set the context for the audit, providing detailed background information.
- Content
    - Background: Explain why the audit was conducted.
    - Audit Scope: Define the boundaries of the audit, including systems and processes reviewed.
    - Objectives: State the specific goals of the audit.
    - Standards and Frameworks: Mention any security standards or frameworks used as benchmarks, such as NIST, ISO/IEC 27001, or OWASP.
##### Example
- Testing and vulnerability rankings are based on NIST 800-30 threat rankings methodology. The following section outlines the NIST-based scoring methodology applied to the assessment findings:



3. Methodology
- Purpose: Detail the methods and tools used during the audit to provide transparency and reproducibility.

- Content
    - Approach: Describe the overall approach, such as black-box testing, white-box testing, or gray-box testing.
    - Tools: List the tools used for various tests, like Nmap, Nessus, Metasploit, Burp Suite, etc.
    - Procedures: Explain the procedures followed, including reconnaissance, vulnerability scanning, exploitation, and post-exploitation.

4. Findings
- Purpose: Present detailed findings from the audit, categorized by severity and impact.
- Content
    - Summary Table: Include a table summarizing findings with categories like vulnerability, risk level, affected systems, and recommended actions.
    - Detailed Findings: For each finding, provide:
    - Title: Clear and concise title.
    - Description: Detailed description of the issue.
    - Impact: Potential impact if the vulnerability is exploited.
    - Evidence: Screenshots, logs, or code snippets supporting the finding.
    - Risk Level: Assessment of the risk level (e.g., critical, high, medium, low).
    
##### Example
Finding ID|	Title	|Risk Level	|Affected Systems|	Recommended Action
---|---|---|---|---
F-001|	SQL Injection|	High|	Web Application|	Input validation and parameterized queries
F-002	|Weak Password Policy|	Medium|	All User Accounts|	Implement strong password policies and enforce MFA

5. Recommendations
- Purpose: Provide actionable steps to mitigate identified risks and enhance security.

- Content
    - Prioritized Actions: List recommendations in order of priority.
    - Detailed Steps: Provide detailed, actionable steps for each recommendation.
    - Resources: Include links to relevant resources, guidelines, or tools to assist in implementation.

6. Conclusion
- Purpose: Summarize the audit findings and the overall security posture of the organization.
- Content
    - Overall Assessment: Provide an overall assessment of the organization's security.
    - Improvements: Highlight areas of improvement since the last audit, if applicable.
    - Next Steps: Suggest next steps, including follow-up audits or continuous monitoring.

7. Appendices
- Purpose: Include additional information and supporting documents.
- Content
    - Glossary: Define technical terms and acronyms used in the report.
    - References: List references to standards, frameworks, and tools mentioned in the report.
    - Detailed Logs: Provide detailed logs, scan results, and raw data as necessary.


##### Example-1 structure of a security audit reports
```markdown
# Security Audit Report

## 1. Executive Summary
- Objective
    - The objective of this security audit was to evaluate the current security posture of ABC Corporation’s IT infrastructure, identify vulnerabilities, and provide actionable recommendations to enhance security.
- Scope
    - The audit covered:
        - Internal network and servers
        - Web applications
        - Endpoint devices
        - Security policies and procedures
- Methodology
    - The audit utilized:
        - Network and vulnerability scanning tools (Nmap, Nessus)
        - Penetration testing tools (Metasploit, Burp Suite)
        - Configuration reviews
        - Staff interviews
- Key Findings
    - High-risk SQL injection vulnerability in the customer portal
    - Outdated software with known vulnerabilities
    - Weak password policies across user accounts
    - Lack of multi-factor authentication (MFA) for critical systems
- Recommendations
    - Implement input validation and parameterized queries to prevent SQL injection
    - Update and patch all software to the latest versions
    - Enforce strong password policies and MFA
    - Conduct regular security training for staff
- Conclusion
    - ABC Corporation has several critical vulnerabilities that need immediate attention. By addressing these issues and implementing the provided recommendations, the organization can significantly improve its security posture.

## 2. Introduction
- Background: ABC Corporation requested a comprehensive security audit to assess its current security measures and identify potential vulnerabilities. The audit was conducted over a two-week period.
- Audit Scope
    - The audit included:
        - Network infrastructure (routers, switches, firewalls)
        - Servers (web, database, file servers)
        - Web applications (customer portal, internal tools)
        - Endpoint devices (desktops, laptops, mobile devices)
        - Security policies and procedures
- Objectives
    - Identify and assess vulnerabilities
    - Evaluate security configurations and practices
    - Provide actionable recommendations
- Standards and Frameworks
    - OWASP Top Ten
    - NIST Cybersecurity Framework
    - ISO/IEC 27001

## 3. Methodology
- Approach: The audit used a combination of black-box and white-box testing methods to simulate external and internal threats.
- Tools
    - Nmap: Network discovery and port scanning
    - Nessus: Vulnerability scanning
    - Metasploit: Exploitation framework
    - Burp Suite: Web application security testing
    - Wireshark: Network protocol analysis
- Procedures
    - Reconnaissance: Gathering information about the network and systems
    - Scanning: Identifying open ports, services, and vulnerabilities
    - Exploitation: Attempting to exploit identified vulnerabilities
    - Post-Exploitation: Assessing the potential impact and extracting data
    - Reporting: Documenting findings and recommendations

## 4. Findings
- Summary Table
- Detailed Findings
    - F-001: SQL Injection
        - Description: The customer portal is vulnerable to SQL injection, allowing attackers to manipulate database queries.
        - Impact: Potential unauthorized access to sensitive customer data.
        - Evidence: Exploitation via ' OR '1'='1 payload.
        - Risk Level: High
        - Recommended Action: Implement input validation and use parameterized queries.

## 5. Recommendations
- Prioritized Actions
- Detailed Steps
- Resources
- Example:
    - Implementing Multi-Factor Authentication
    - Steps:
        - Implement MFA for all critical systems and user accounts.
        - Use MFA solutions that support various authentication methods (e.g., SMS, authenticator apps, hardware tokens).
        - Regularly review and update MFA configurations.
        - Reference: NIST SP 800-63B Authentication Guidelines

## 6. Conclusion
- Overall Assessment: ABC Corporation has several critical vulnerabilities that need immediate attention. Addressing these issues will significantly enhance the organization’s security posture.
- Improvements
    - Implementing the recommended actions will reduce the risk of unauthorized access and data breaches.
    - Regular security training and awareness programs will help maintain a strong security culture.
- Next Steps
    - Address high-priority vulnerabilities immediately.
    - Schedule follow-up audits to ensure remediation efforts are effective.
    - Implement continuous monitoring to detect and respond to new threats promptly.

## 7. Appendices
- Glossary
- References
- Detailed Logs
```


##### Example-2 structure of a security audit reports
```markdown
# Security Audit Report 

## 1. Methodology
- Testing and vulnerability rankings are based on NIST 800-30 threat rankings methodology. 

### Threat Likelihood
- High: A threat actor is highly likely to create an event
- Moderate: A threat actor is likely to create an event
- Low: A threat actor is unlikely to create an event

### Threat Impact
- Critical: The event would have a catastrophically negative impact on the organization.
- High: The event would have a severe negative impact on the organization.
- Moderate: The event would have a negative impact on the organization.
- Low: The event would have a limited negative impact on the organization.
- Informational: The event would have a negligible impact on the organization.

### Level of Risk: Likelihood x Impact
- Critical: The event would have multiple severe or catastrophic negative effects on the organization.
- High: The event would have a catastrophic negative effect on the organization.
- Moderate: The event would have a negative effect on the organization.
- Low: The event would have a limited negative impact on the organization
- Informational: The event would have a negligible impact on the organization.

## Scope
- The assessment was performed with the following targets in scope:
    - http://www.my-application.com:8080
    - https://www.st-my-application.com
    - https://www.prod1.my-application.com

## Executive Summary
The assessment team conducted a penetration test for “Your Company” from October 10 – October 15, 2020. This test was designed to provide “Your Company” with an assessment of your web application from the perspective of a malicious external 3rd party.

## Synopsis
The assessment team discovered several vulnerabilities including cross-site scripting, SQL injection, and denial of service.

## Finding and Recommendations
- UNAUTHENTICATED SQL INJECTION – CRITICAL
- Cross-Site Scripting: A SQL injection attack consists of the insertion or “injection” of a SQL query via the input data from the client to the application. A successful SQL injection exploit can read sensitive data from the database, modify database data (Insert/Update/Delete), execute administration operations on the database (such as shutdown the DBMS), recover the content of a given file present on the DBMS file system and in some cases issue commands to the operating system. SQL injection attacks are a type of injection attack, in which SQL commands are injected into data-plane input in order to effect the execution of predefined SQL commands. Source: (opens in a new tab)OWASP: SQL Injection(opens in a new tab)

- Details
    - The assessment team identified a SQL Injection attack on the login page of your application. The team was able to successfully exploit this vulnerability to bypass authentication and access restricted pages.
    - This was discovered on:
        - https://www.my-application.com

- Recommendations:To address the SQL injections issues, the assessment team recommends:
    - Using parameterized queries when executing SQL with user input
    - Only allow expected inputs
```

8. Tips for Effective Reporting
- Clarity and Conciseness: Write in clear, concise language. Avoid jargon and explain technical terms where necessary.
- Visual Aids: Use tables, charts, and diagrams to illustrate findings and recommendations.
- Actionable Recommendations: Ensure recommendations are specific, actionable, and tailored to the organization’s context.
- Review and Proofread: Review the report for accuracy, completeness, and clarity. Proofread to eliminate errors.
