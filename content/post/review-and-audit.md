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

8. Tips for Effective Reporting
- Clarity and Conciseness: Write in clear, concise language. Avoid jargon and explain technical terms where necessary.
- Visual Aids: Use tables, charts, and diagrams to illustrate findings and recommendations.
- Actionable Recommendations: Ensure recommendations are specific, actionable, and tailored to the organization’s context.
- Review and Proofread: Review the report for accuracy, completeness, and clarity. Proofread to eliminate errors.










