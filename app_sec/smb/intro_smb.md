# Introduction to SMB

Author(s): a_person

Last Updated: 07-23-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
- Basic knowledge of Windows  <br />
- Basic knowledge of Networking
- Basic knowledge of the Registry
</details>

## What is it? 
Server Message Block (SMB) is a communication protocol used to share files, printers, serial ports, and miscellaneous communications between nodes on a network. On Microsoft Windows, the SMB implementation consists of two Windows services: ``Server`` and ``Workstation`` (full service names are LanmanServer and LanmanWorkstation). Their full service names also are their names in their respective registry path. It uses NTLM or Kerberos protocols for user authentication. It also provides an authenticated inter-process communication (IPC) mechanism. 

### Why and Where is SMB Used?

The main purpose of SMB is to help computers on a network share resources easily. This connection between a client machine and a server's resources makes it an important protocol in almost every Windows-based environment.

Examples:

*   **Corporate File Sharing:** Accessing a shared network drive on a company file server to open, edit, and save documents.
*   **Domain Administration:** When a computer logs into a Windows domain, it uses SMB to connect to the Domain Controller’s `SYSVOL` and `NETLOGON` shares to download important login scripts and Group Policy security settings.
*   **Shared Network Printing:** Sending a print job from your computer to a central printer that is shared across the office network.

## How does it work?
- The client sends an SMB request to the server to initiate the connection. 
- When the server receives the request, it sends an SMB response back to the client, establishing the communication channel necessary for a two-way conversation. 
- Once it is granted access, the client can access the required resource for reading, writing, executing and so on. 

Since the network server has a resource that it shares with one or more clients, the protocol is also known as a server-client protocol.
The SMB protocol operates on the application layer of the TCP/IP model, but relies on lower network levels for transport. When SMB was using NBT, it relied on ports 137, 138 and 139 for transport. Now, SMB runs directly over TCP/IP and uses port 445. Port 445 supports data encryption and digital signing of SMB packets, providing a more secure means of communication than port 139.

## Important Files and Locations
 - ``HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Shares`` - Stores the definitions and paths of all SMB shares on the system.

 - ``HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters`` - Controls SMB server settings.

 - ``HKLM\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters`` - Controls SMB client settings.

 - ``C:\Windows\System32\srvsvc.dll`` - Core DLL for the SMB server service.

 - ``C:\Windows\System32\srv.sys`` - Kernel driver for SMB server functionality.

 - ``%SystemRoot%\System32\config`` - Location of system registry hives, including those that store SMB configuration.

 - ``%UserProfile%\NTUSER.DAT`` - Contains user-specific registry settings, including recent SMB connections and mount points.

 - ``UNC Paths (\Server\Share)`` - Standard syntax for accessing SMB shares in Windows Explorer or via command line.

 - ``[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\DOS Devices]`` - Maps network drives for all users by assigning a drive letter to a UNC path.

 - ``Administrative shares (C$, ADMIN$, IPC$)`` - Hidden default shares for administrative access, automatically created by Windows.

## References & Further Reading
- https://en.wikipedia.org/wiki/Server_Message_Block
- https://www.techtarget.com/searchnetworking/definition/Server-Message-Block-Protocol
- https://learn.microsoft.com/en-us/windows-server/storage/file-server/file-server-smb-overview
- https://learn.microsoft.com/en-us/previous-versions/windows/desktop/mscs/file-share
