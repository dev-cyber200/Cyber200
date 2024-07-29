+++
author = "dev@cyber200"
title = "Monitoring and Detection"
date = "2024-07-14"
description = ""
tags = [
    "cyber-security",
    "monitoring",
    "detection",
    "infrastructure-security",
]
draft = false
+++

### Packet Flow via OSI Layers

- The sender uses an FTP client like PuTTY to enter a remote host to connect. This happens at the application level.
- From there, data is translated into the presentation layer using the FTP protocol.
- In the session layer, a network socket is opened at the connecting source to initiate a connection towards the remote host.
- Next, an end-to-end TCP connection with the remote host happens at the transport layer.
- Then, the data gets formatted into IP packets at the network layer.
- The data link transmits data across physical segments.
- Then, the packets go through the physical layer, for example, via a fiber connection.

After the packets flow across the physical layer, they then go through the reformatting of data in the different layers in reverse order until they reach the destination host. In our example, the FTP Server application, which is ultimately the receiver. This process lasts until the sender disconnects, or the server terminates the session.

### Best Practices SIEM
- Do not log everything.
- Focus your monitoring, do not overwhelm yourself with alerts.
- Plan for expansion and manage growth. The licensing cost will increase as you add more log sources.
- Control & Manage access to SIEM.
- Evaluate your data sources and alert effectiveness.