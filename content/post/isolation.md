
+++
author = "dev@cyber200"
title = "Isolation"
date = "2024-07-04"
description = "Isolation serves as a means for creating an execution environment that is specifically designed for the process. It means that the process running in isolation is in some way separated from the main environment."
tags = [
    "cyber-security",
    "isolation",
    "system-security",
]
draft = false
+++

Through isolation, we aim to achieve a virtual separation between the running system processes and the main operating system. This ensures that a compromise of the system process cannot affect the entire system and should only be limited to the isolated process.

### Implementing Process Isolation through Chroot Jails
A chroot operation changes the apparent root directory for a running process and its children. It allows us to change the root directory to anything other than /. This increases the protection of the system as a process and does not let the user access other critical resources of the system. It locks down the process and the logged-in user sees only the directory that the process is running in. The newly created artificial root directory becomes the chroot jail. Chroot allows an administrator to control access to a service or filesystem while controlling exposure to the underlying server environment.

Note that, for a chroot process to successfully start, the chroot directory must be populated with all required program files, configuration files, device nodes, and shared libraries at their expected locations.

#### Steps for Creating a Jailed Environment
- Define the environment, requirements and build the initial base
- Configure the Jail Options, creating a copy of the service with required dependencies or making configuration changes in the service to restrict accessing locations protected through chroot
- Initialize the Service
- Test restrictions
- Example:
    - Implement the SFTP service inside the chroot jail to ensure that the logged-in user can upload or download files only at specific locations, dir uploads and downloads
        - `useradd -s /bin/false -m -d /home/remoteuser remoteuser`
        - `passwd remoteuser`
        - `sudo chown root: /home/remoteuser`
        - `sudo chmod 755 /home/remoteuser`
        - `sudo mkdir /home/remoteuser/{uploads, downloads}`
        - `sudo chmod 755 /home/remoteuser/{uploads, downloads}`
        - `sudo chown remoteuser /home/remoteuser/{uploads, downloads}`
    - Config Jail options
        - edit `sshd_config`
            - replace line `Subsystem sftp...` with `Subsystem sftp internal-sftp`
            - add below to the end of the file
                - `Match User remoteuser`
                - `ChrootDirectory %h`
                - `ForceCommand internal-sftp`
                - `AllowTcpForwarding no`
                - `X11Forwarding no`
    - Initialize the service: `service ssh restart`
    - Jail Restrictions to a new Group:
        - `groupadd remoteusergroup`
        - `usermod -g remoteusergroup -s /bin/false remoteuser`
        - edit sshd_config
            `Match Group remoteusergroup`
        - restart the service

### Mandatory Access Control(MAC)

 Limit or eliminate the need for a root account, and shift the power from the user accounts to the owner of the system. Implementing a strong MAC policy will prevent an attacker or system exploit from gaining complete access over the system
 - AppArmor
    - install `ngix` start it
    - install `apparmor-utils`
    - create test fiels
        - `cd /`
        - `mkdir -p /data/www/public`
        - `touch /data/www/public/index.html`

        - `makdir -p /data/www/private`
        - `touch data/www/private/index.html`
        - edit `index.html`
    - create an AppArmor profile
        - `cd /etc/apparmor.d/`
        - `aa-autodep ngnix`
        - a new profile under usr.sbin.nginx dir
        - add `/data/www/public/* r` and `deny /data/www/private/* r` to `usr.sbin.ngix`
        - restart Ngnix and AppArmor

### Memory Overflow Attack & Defense

A hardened system with strong restrictions and access control can greatly reduce the overall attack surface and improve the security hygiene of the enterprise. Attackers are constantly looking for new ways to break those controls in order to infiltrate the network. One such way is to attack the common software services or components of the operating system. It is not easy to detect or defend against attacks on trusted services and the operating system.

- Buffer Overflow Attack
- Avoid Buffer overflow:
    - Make Sure You Have Enough Space: Before copying data to a fixed size block, make sure it is large enough to hold the data that you are going to copy.
    - Validating Indices: For your integer variables defined in the code, verify that they are within the proper bounds before you use them as an index to an array.
    - Use Data Structures that Reduce the Risk of Overflows: When possible, use lists in Python without defining the initial size. The interpreter can then handle the length of the list and copy elements accordingly.

### Memory Overflow Protection: ASLR
With ASLR(Address Space Layout Randomization), the entry point of a process is randomized each time it is executed. It is never in a fixed location. This is why it is called Address Space Layout Randomization. With this randomness, exploiting a buffer overflow becomes difficult as it's not easy to guess the location of the return address and overwrite it with the address of shell-code.

#### Implementing ASLR on a Linux

- check if ASLR is enabled: `cat /proc/sys/kernel/randomize_va_space`
    - 0 = Disabled
    - 1 = Conservative Randomization
    - 2 = Full Randomizatio
- enable it `sysctl -a --pattern randomize kernel.randomize_va_space = 2`

#### Limitations of ASLR
- ASLR doesn't mitigate exploits. It only makes it harder for attackers to execute it. It is still the responsibility of the code owners or software developers to mitigate the bugs in their codes which can potentially lead to a buffer overflow.
- Older versions of operating systems do not have in-built support for ASLR leaving those systems vulnerable to buffer overflow attacks.
- Modern exploits can even bypass ASLR by using advanced exploiting techniques. Hence, an in-depth defensive security approach should be practiced.