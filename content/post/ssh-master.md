+++
author = "dev@cyber200"
title = "SSH master"
date = "2024-06-01"
description = "SSH provides a robust and secure method for connecting to remote systems. Its combination of encryption, authentication, and advanced features make it an indispensable tool for system administrators, developers, and anyone who needs secure remote access to servers and other networked devices"
tags = [
    "ssh",
    "dev-kit",
]
categories = [
    "dev-kit",
]
series = [""]
+++

## Overview

SSH (Secure Shell) is a protocol used to securely connect to remote systems over an unsecured network, It was designed to replace earlier insecure protocols such as Telnet, rlogin, and FTP by providing a secure channel over an unsecured network by using a client-server architecture, encryption, and authentication mechanisms.

##### Key Components of SSH
1. SSH Client: The program that initiates the connection to the SSH server. Common SSH clients include OpenSSH, PuTTY, and SecureCRT.
2. SSH Server: The program running on the remote machine that listens for incoming SSH connections. The server component is usually called sshd (SSH Daemon).

## How SSH Works

1. Establishing the Connection
When an SSH client initiates a connection to an SSH server, the following steps occur:

- Connection Establishment:

    - The client connects to the server using TCP on the default port 22 (this can be configured to use a different port).

- Handshake and Key Exchange:

    - The client and server exchange identification data to agree on the SSH protocol version and supported encryption algorithms.
    - They perform a key exchange (commonly using the Diffie-Hellman key exchange algorithm) to securely generate a shared secret key used for encrypting the session.

2. Authentication
After the secure channel is established, the client needs to authenticate itself to the server. SSH supports multiple authentication methods:

- Password Authentication:

    - The client sends a username and password to the server.
    - The server checks the credentials and grants or denies access.

- Public Key Authentication:

    - The client generates a key pair (public and private keys).
    - The public key is added to the server’s ~/.ssh/authorized_keys file.
    - During authentication, the client proves it has the corresponding private key without sending it over the network.
    - The server challenges the client with a message encrypted with the public key. The client must decrypt it with the private key and send back the original message to authenticate.

3. Other Methods:

    - SSH also supports other methods like Kerberos, GSSAPI, and certificate-based authentication.

## Secure Data Transmission
Once authentication is successful, the SSH session begins. All data transmitted between the client and the server is encrypted using the session key established during the handshake.

- Data Encryption:
    - SSH uses symmetric encryption (e.g., AES, ChaCha20) for encrypting the data.
    - This ensures that any data sent over the network is unreadable to anyone who intercepts it.

- Integrity Verification:

    - SSH uses message authentication codes (MACs) to ensure data integrity.
    - This verifies that the data has not been altered during transmission.
- Compression (optional):

    - SSH can optionally compress data before transmitting it to reduce bandwidth usage.

## Advanced Features of SSH
* Port Forwarding:
    * SSH can tunnel other network connections through the secure SSH connection.
    * Local Port Forwarding: Redirects traffic from a local port to a remote address via the SSH server. 
        * It forwards a port from your local machine to a remote server. This can be useful for accessing services on a remote server as if they were running on your local machine.
        * Example Scenario:
        * You want to access a web application running on port 8080 on a remote server (remote.example.com) from your local machine on port 8080.
        ```sh
        ssh -L 8080:localhost:8080 user@remote.example.com
        ```
        * L: Specifies local port forwarding.
        * 8080:localhost:8080: Redirects traffic from localhost:8080 on your local machine to localhost:8080 on the remote server.
        * user@remote.example.com: Your SSH login credentials for the remote server.

    - Remote Port Forwarding: Redirects traffic from a remote port to a local address via the SSH client.
    - Dynamic Port Forwarding: Uses SOCKS proxy to dynamically forward traffic to various destinations.
- X11 Forwarding:

    - SSH can securely forward X11 graphical applications from a remote server to the local client.
- SSH Agent Forwarding:

    - SSH agent stores private keys and can forward authentication requests to avoid repeatedly entering passphrases.
- File Transfers:
    - SCP (Secure Copy Protocol): Transfers files between hosts over an SSH connection.
    - SFTP (SSH File Transfer Protocol): Provides file access, transfer, and management over an SSH connection.