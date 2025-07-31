# Introduction to RDP
___
Author(s): a_person

Last Updated: 07-04-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
- Basic knowledge of Windows<br />
- Registry
</details>

## What is RDP?

RDP (Remote Desktop Protocol) is a tool developed by Microsoft that lets you control one computer from another over a network. It is part of Windows Remote Desktop Services (RDS). RDP provides a graphical interface for easy access to the remote Windows desktop. This allows you to work with applications, files, and settings remotely. 

Built into Windows and accessible through the Remote Desktop Connection client (mstsc.exe), RDP sends screen updates, keyboard input, and mouse movements between the client and the remote computer. It can transfer different types of data at the same time. RDP is used for remote work, system management, technical support, and application delivery. It helps users and IT professionals manage computers without needing to be physically present.

## Why and Where is RDP Used?

The main purpose of RDP is to provide control over a remote computer. Unlike Secure Shell(SSH), which is through a command line interface, RDP streams the entire desktop interface. This allows for easy remote management and interaction. 
Examples:

*   **IT Administration:** System administrators use RDP to manage servers located in a data center or cloud environment that's operating system is Windows Server, like Azure or AWS. Other servers, such as those running Linux, are typically managed using SSH.
*   **Remote Work:** An employee working from home can use RDP to connect to their desktop computer at the office. 
*   **Technical Support:** A help desk technician can use RDP to remotely connect to a user's computer to troubleshoot issues, install software, or change settings directly.

## How RDP Works

### The Protocol 

Remote Desktop Protocol (RDP) connects to another computer over a network, usually through TCP port 3389 (default port). It comes preinstalled on Windows, and you can access it through the Remote Desktop Connection app. RDP can manage different types of data separately, such as screen display and keyboard input. It also supports sharing information with multiple users at once.

### Connection Process:

1.  The user launches the Remote Desktop Connection client (`mstsc.exe`) on their Windows device.
2.  The client initiates a TCP connection to the server on port 3389 (by default).
3.  The user authenticates with their Windows username and password.
4.  Client and server negotiate encryption and authentication.
5.  Screen updates are sent to the client, and user inputs are relayed to the server.
6.  The remote desktop session is established, streaming the remote interface to the client while sending input back to the host.



## Important files and locations
 - ``HKCU\Software\Microsoft\Terminal Server Client\Default`` - Stores connection history, credentials, and display settings.
 - ``HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server`` - Controls server-side settings like security, licensing, and session limits.
 - ``C:\Users\[user]\Documents\Default.rdp`` - Stores connection settings like hostname, IP, resolution, and credentials.
 - ``mstsc.exe`` - Remote Desktop Connection client for initiating RDP sessions.
 - ``rdpclip.exe`` - Manages clipboard sharing between local and remote systems.
 - ``tscon.exe`` - Connects to terminal sessions via command line.
 - ``tsdiscon.exe`` - Disconnects terminal sessions via command line.
 - ``termsrv.dll`` - Core RDP server module handling connections.
 - ``wtsapi32.dll`` - Windows Terminal Services API for interacting with RDP services.




___
### References & Further Reading
- https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/023f1e69-cfe8-4ee6-9ee0-7e759fb4e4ee
- https://en.wikipedia.org/wiki/Remote_Desktop_Protocol
- https://learn.microsoft.com/en-us/troubleshoot/windows-server/remote/understanding-remote-desktop-protocol
