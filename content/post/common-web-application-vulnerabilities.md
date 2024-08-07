+++
author = "dev@cyber200"
title = "Common Web Application Vulnerabilities"
date = "2024-08-04"
description = ""
tags = [
    "cyber-security",
    "web-app-security",
    "common-web-app-vulnerabilities",
]
draft = false
+++


### Injection Best Practice 
- Use Parameterized Queries - This is the best method in preventing SQL Injection because all variables are limited to the data type. This will prevent malicious code from breaking out of the SQL code and preventing the malicious code from running.
- Sanitize all inputs - I recommend that you always sanitize all inputs before using them. This will prevent malicious code from running not only in SQL Queries but also in other parts of your code.
- For a full list of prevention methods please visit [OWASP Cheatsheet on SQLi Prevention](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html).

### Broken Authentication

Methods to broken authentication:
- Credential Stuffing 
- Brute Force
- Default passwords
- Exposed Session ID in the URL

Best Practice:
- Multi-Factor Authentication
- Captcha
- Failed Login Attempts

### Sensitive Data Exposure
Best Practice:
- Check code using Sensitive Data
- Strong Hashing
- Limit storing sensitive data to only what is needed
- Encrypt all data in transit and at rest

### XML External Entities (XXE)
Best Practice:
- JSON - Try to use less complex data formats such as JSON which don't have DTD
- Disable DTD Processing - Disable both XXE and DTD to prevent RCE in the XML parsers
- Verify XML Data - Always validate your XML data before processing to make sure they don't contain any malicious code.

### Broken Access Control
Best Practice
- Rate Limit Data - by rate-limiting the user access to data on the site, you can slow down their ability to scrape all data from your web application.
- Re-validate on all secure pages - make sure you have proper testing around all secure pages and endpoints to validate access control are working as expected.
- Deny Access for non-public pages by default - you should have general rules that auto deny access to non-public pages and require validation to access these pages.
- Log Access Failures - you should log not only all-access failures but also create automation process that alert you of IP/Users that have a high level of failures.

### Security Misconfiguration
- All environment should be the same - By keeping all of your environments the same you will be able to find any issues before they make it out to production.
- Limit components - You should push to limit the different components used to only what is really needed, then this will reduce your risk and amount of work to make sure everything is updated and working correctly.
- Automate Environment creation and validation - Using automation to create all environments will help reduce user errors and make sure all environments are built exactly the same. Next, you should automate the validation of the environment to help you understand the health and state of your environments.

### Cross-Site Scripting (XSS)
- Reflected - In this type of attack, the payload that the attacker uses becomes part of the request that goes to the web application, and then when the web application processes the request, it will reflect the payload script and execute it on the target local machine.
- Stored - In this type of attack, a payload is sent to the web application where it is saved in the database, and then when it is called from the database, it is executed on the target local machine.
- Document Object Model (DOM) - This type of attack is considered a more advanced type of XSS and is when the vulnerability appears in the Document Object Model (DOM) rather than the HTML page.

The best option to protect your application from XSS is to make sure you sanitize all inputs.

### Insecure Deserialization
### Using Components with Known Vulnerabilities
Best Practice
- Bare Minimum - You should push to limit the different components used to only what is really needed, then this will reduce your risk and amount of work to make sure everything is updated and working correctly.
- Monitor Components Versions - You will want to monitor all resources used, to make sure they are still valid and secure. You can use third-party tools to help automate this.
- Use Trusted Sources - Only download resources from trusted secure sources. By using other sources, you might be creating a backdoor into your system.

### Insufficient Logging and Monitoring
Best Practice
- Centralized Logging - Using a centralized logging system will help reduce the amount of time and effort needed between going thru all servers.
- Automation of log parsing - By automating the log parse, you can reduce the noise from events that need your attention.
- Alerting and fine-tuning of events - Alerting on events is extremely important, but you should also spend some time fine-tuning events to reduce false positive.

### Insecure Design
Best Practice
- Threat Modeling: Regularly conduct threat modeling sessions to identify potential security issues early in the design phase.
- Secure Design Patterns: Use secure design patterns and principles such as least privilege, defense in depth, and fail-safe defaults.
- Security Reviews: Ensure design reviews include security considerations and are conducted by individuals with security expertise.
- Secure Development Lifecycle (SDL): Integrate security into every phase of the development lifecycle, from requirements gathering to design, implementation, and testing.

### Software and Data Integrity Failures
Best Practice
- Digital Signatures: Use digital signatures to verify the integrity and authenticity of software updates and data.
- Code Integrity Checks: Use mechanisms to perform integrity checks on critical code and data.
- Secure CI/CD Pipelines: Implement security controls within your CI/CD pipeline to ensure that only verified code is deployed.
- Dependency Management: Regularly update and manage third-party dependencies, using tools to check for known vulnerabilities.

### Server-Side Request Forgery (SSRF)
Best Practice
- Input Validation: Validate and sanitize all inputs that could be used to generate server-side requests.
- Whitelist Allowable Requests: Implement a whitelist of allowed URLs or domains that the server can access.
- Network Segmentation: Segregate networks to limit access to sensitive internal systems from the web server.
- Metadata Protection: Block access to sensitive metadata endpoints, such as cloud instance metadata services.