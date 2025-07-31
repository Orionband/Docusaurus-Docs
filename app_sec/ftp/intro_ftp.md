# Introduction to FTP

Author(s): a_person

Last Updated: 07-11-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
- Basic knowledge of Windows  <br />
- Basic knowledge of Networking
</details>

## What is it?
File Transfer Protocol (FTP) is a standard network protocol based on a client-server model. It is used for transferring computer files between a client and a server on a network. Even though it is one of the oldest internet protocols, it is still widely used for web development, large file sharing, and data storage.

SMB (what we talked about in the last 2 articles) and FTP are both network protocols used for transferring files between computers. They have several similarities. They both work over TCP/IP and can be used in client-server setups, where one device hosts the files and another device accesses them. SMB is most commonly used in local area networks (LANs), especially with in Windows environments, where it facilitates file and printer sharing between devices. FTP is better for transferring files over wider networks, such as the internet, and is often used in website management, server-to-server data transfers, and automated file workflows.

The main issue of FTP is its lack of security. Credentials and data are sent in plain text. Because of this, modern secure options like FTPS (FTP over SSL/TLS) and SFTP (SSH File Transfer Protocol) are highly recommended for most situations.

## Why and Where is FTP Used?

The main purpose of FTP is to offer a straightforward way to transfer files between computers, especially over the internet. Unlike SMB, FTP serves as a dedicated tool for one task: uploading and downloading files. This straightforwardness has made it a standard choice for various automated and manual file transfer tasks, especially when systems with different operating systems need to share data.

Examples:

*   **Web Development:** A web developer uses an FTP client (like FileZilla) to upload website files (HTML, images, scripts) from their computer to the web server that hosts the live site.
*   **Automated Data Exchange:** Businesses set up automated scripts to transfer data files, such as daily sales reports or inventory updates, between their servers and those of their partners.
*   **Bulk Data Transfer:** Companies and research institutions use FTP servers to share very large files, like software installers, large datasets, or video archives, that are too big to send via email.

## How does it work?

1. The client starts a connection to the server's command channel, usually on Port 21. The client sends login details (username and password) for the server to confirm.
2. After authentication, the client sends commands (like listing files, changing directories, or requesting a file) to the server through the command channel.
3. When a file transfer or directory listing is needed, a second, temporary data channel opens. The actual file content travels over this channel, which closes when the transfer finishes.

The way the data channel opens determines the mode. In Active mode, the server connects back to the client, but this is often blocked by firewalls. In Passive mode, the client starts the connection to the server. This method is more friendly to firewalls and is the modern standard.

## Important Files and Locations
Note that this is when the FTP Server role is installed in IIS
* **Default FTP Root Directory:** `C:\inetpub\ftproot`
* **IIS Configuration File:** `C:\Windows\System32\inetsrv\config\applicationHost.config`
* **FTP Log Files:** `C:\inetpub\logs\LogFiles\FTPSVC[SiteID]`
* **Built-in Command-Line Client:** `C:\Windows\System32\ftp.exe`

## Microsoft FTP
Windows Server comes with a FTP server as part of IIS. It is not installed by default but can be turned on through "Turn Windows features on or off" or "Add Roles and Features" in Server Manager. 

## Other FTP Servers

* **FileZilla Server:** A widely used free, open-source server that is simple to set up. It supports both FTP and FTPS and has an easy graphical interface for managing users and groups.
* **Wing FTP Server:** A flexible server that supports SFTP, FTPS, and HTTPS. It is known for its web-based administration interface, allowing for remote management from any browser.
* **WinSCP**: Primarily a file transfer client, WinSCP also includes scripting and automation features that can function like a lightweight server solution. It supports SFTP, SCP, and FTP, and is widely used for secure file transfers in scripted or automated workflows.
## References & Further Reading
*   https://learn.microsoft.com/en-us/iis/install/installing-publishing-technologies/installing-and-configuring-ftp-7-on-iis-7
*   https://wiki.filezilla-project.org/Main_Page
*   https://www.cerberusftp.com/
*   https://www.wftpserver.com/
*   https://winscp.net/eng/docs/start
*   https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp
*   https://en.wikipedia.org/wiki/File_Transfer_Protocol
