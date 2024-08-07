+++
author = "dev@cyber200"
title = "Web Penetration Test"
date = "2024-08-05"
description = ""
tags = [
    "cyber-security",
    "web-app-security",
    "web-penetration-test",
]
draft = true
+++


### SQL Injection Best Practice
- Using Parameterized Queries
- Sanitize all inputs

### Cross-Site Scripting

### Brute Force Login
Questions to answer:
- What web method is it using, POST/GET?
- What URL is it using?
- What form elements are needed?
- Can we tell if the login attempt passed or failed?

### Salt vs Pepper
- Pepper is a static text that is used to harden password and help to make it more difficult to crack. When using pepper it is recommended that you use a string that is over 100 chars long and contains a random combination of the following Upper Case, Lower Case, Numbers, and Special Characters. It is also recommended that you don't store the pepper inside the database or in code, but rather inside an environment variable or secret vault.

- Salt is a unique text that is generated per password and should never repeat and is saved in the database alongside the hash password.

### How to crack hashes
- Brute force
- Wordlist
- Rainbow tables
- Lookups