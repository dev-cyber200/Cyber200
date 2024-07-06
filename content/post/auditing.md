+++
author = "dev@cyber200"
title = "Auditing"
date = "2024-07-05"
description = "Detect the presence of malware on a system and how we can remediate such infections by using automated scanning tools."
tags = [
    "cyber-security",
    "auditing",
    "system-security",
]
draft = false
+++


Understanding around locating those trails on the affected systems build a complete image of the infection along with a timeline of events.

### System & Service Logging

#### Application & Services Logging
#### Logging Basics in Linux

- Application Logs: These are application-specific logs. For example, logs for an Apache web server.
- Event Logs: These logs are a capture of all the events and system calls occurring in the operating system. In Linux, these logs are captured by syslog.
- Service Logs: These logs can be used to monitor services running on the operating system.
- System Logs: These logs are specific to system issues and related events.

### Logging for Security
- `/var/log/dmesg`: This log file contains kernel ring buffer information. It contains all the logs which are displayed when a system boots up
- `/var/log/auth.log`: This log file contains system authorization information, including user logins and the authentication mechanism that was used. This log file can help us monitoring security events like failed login attempts, brute-force attacks, and other vulnerabilities related to user authorization.
- `/var/log/cron.log`: Malware and spyware programs try to run themselves as cron jobs in order to maintain persistence on the system. A point to note here is that, on Ubuntu Linux, cron logs are written to the syslog file. We can configure it to also write it to cron.log file as a more streamlined way of collecting logs. In short, if the cron.log file doesn't exist then your cron logs are getting written only to syslog.

- Apache & Nginx Web Server Logs
- Package Related Logs, Some of the important log files that capture this information can be:
    - `/var/log/dpkg.log`
    - `/var/log/apt/history.log`
    - `/var/log/yum.log`

### Host-Based Intrusion Detection
It collect, analyze, and correlate logs and alerts if an attack, fraudulent use, or error is detected. HIDS enables you to monitor processes and applications running on devices like servers and workstations. It can correlate system logs and events to alert for changes made to critical settings and system configuration, unauthorized or anomalous activity, unusual user behavior, etc. HIDS technologies are "passive" in nature, meaning their purpose is to identify suspicious activity, not prevent it.

#### HIDS Architecture
It can either monitor a single host or it can be configured to monitor a fleet of devices in the network. In such cases, a log collector agent can push all the logs and events from the devices to a centrally managed HIDS where we can build out our correlations and alerting

Some of the alerting that we can build in a HIDS can include but not limited to:

- Unauthorized Login and Access Attempts
- Gather Events from Other Security Tools like Firewalls, Antivirus Software, and Auditing Tools
- Modification or Access of Critical Files
- Installation of Unwanted or Unauthorized Applications

#### OSSEC
OSSEC is a free, open-source host-based intrusion detection system (HIDS) that has the capability to correlate and process logs from a variety of operating systems and security tools for alerting on possible security incidents. This makes it an ideal choice for an HIDS both to monitor a single or endpoint or a range of devices distributed in a network.

### Advanced Monitoring
#### Building Audit Controls: Moving Beyond Logs
##### Use-Cases
- Monitoring System Calls
Audit controls can be established to monitor and record each system call.

- Monitoring for Changes in Critical Files
This allows us to keep an eye on changes made to critical system files. This can detect any unauthorized access to such critical files.

- Recording and Searching Capability
With all of the auditing information being collected, we need a way to query it for later use. This can help us determine the audit trail of events that occurred in the past.

Such auditing capabilities can give us a way to track security-relevant information on your system! Advanced auditing capabilities can be built two ways:

- Through System Commands
- Through Specialized Tools

#### Process Auditing Through System Commands
Thepstree command can be used to turn the running processes into a tree structure, making it easy to interpret.

#### Process Auditing Through Specialized Tools: Osquery
Installing osquery gives us access to the following components:

- osqueryi: The interactive osquery shell, for performing ad-hoc queries.
- osqueryd: A daemon for scheduling and running queries in the background.
- osqueryctl: A helper script for testing a deployment or configuration of osquery.

#### File Integrity Monitoring
Through FIM, we can monitor for file access, content update, copying and moving actions, as well as files being created on the system.

In order to build a robust FIM service, we need to answer some important questions:

- Which files do we want to monitor from security and compliance purposes?
- How sensitive is the data we want to monitor?
- Which user actions do we want to monitor for?

##### creating FIM through Osquery
- Create the File Integrity Monitoring packs Config File
    - define packs /usr/share/osquery/packs/fim.conf
    - edit fim.conf refer [docs](https://osquery.readthedocs.io/en/stable/deployment/file-integrity-monitoring/#example-fim-config)
- Create/Update the osquery Config File osquery.conf 
    - add "fim": <path-to-fim.conf> to packs

- Restart Osquery and Test the Setup
    - `sudo service osqueryd restart`
    - `osqueryi`
    - `.tables`
    
- Open a new terminal and navigate to the monitored path and create a new file
- query table `file_events` to verify changes

### Malware As An Infection Vector
The usual way malware enters the system is through the internet and email. Malware serves as an entry point for the attacker. It opens up the gate for further infecting the larger network that the user is connected to.
#### Two types of malware attacks
- Targeted
- Generic

#### Malware Scanning
- Signature-based: detection technique involves scanning the entire filesystem against a known list of malware signatures and determining a match. 
    - ClamAV: It uses a scanner service called clamscan to scan the file against its database of rules and signatures. The database needs to be frequently updated using another service called freshclam which pulls the updated signatures from ClamAV's server. It works well for detecting generic malware families. It can also detect targeted malware binaries, but not until it receives the updated definitions from its servers.
- Behavior-based: detection techniques involve looking at certain characteristics of the file, and it doesn't rely on specific signature sets to determine a behavior as malware.
- Advance Malware Detection & Hunting with [YARA](https://virustotal.github.io/yara/)