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

## FTPS vs SFTP
It's important to note that while both offer secure transfers, FTPS is FTP secured by SSL/TLS. SFTP, however, is a different protocol built on top of SSH, using a single connection for both commands and data.

## Important Files and Locations
Note that this is when the FTP Server role is installed in IIS
* `C:\inetpub\ftproot` - Default location for hosted FTP content. Can be changed per site in IIS Manager.
* `C:\Windows\System32\inetsrv\config\applicationHost.config` - Stores all IIS site and FTP configuration settings.
* `C:\inetpub\logs\LogFiles\FTPSVC[SiteID]` - Contains FTP connection and transfer logs; [SiteID] matches the site’s numeric ID in IIS.
* `C:\Windows\System32\ftp.exe` - Basic FTP client for command-line transfers and testing.

## Microsoft FTP
Windows Server comes with a FTP server as part of IIS. It is not installed by default but can be turned on through "Turn Windows features on or off" or "Add Roles and Features" in Server Manager. 

## Other FTP Servers

* **FileZilla Server:** A widely used free, open-source server that is simple to set up. It supports both FTP and FTPS and has an easy graphical interface for managing users and groups.
* **Wing FTP Server:** A flexible server that supports SFTP, FTPS, and HTTPS. It is known for its web-based administration interface, allowing for remote management from any browser.

## Common FTP Clients
*   **FileZilla Client:** A free, open-source, cross-platform client with a graphical user interface, supporting FTP, FTPS, and SFTP.
*   **WinSCP:** (Windows only) A free graphical SFTP, SCP, S3, FTP, and WebDAV client. Known for its strong integration with Windows and scripting capabilities.


## References & Further Reading
*   https://learn.microsoft.com/en-us/iis/install/installing-publishing-technologies/installing-and-configuring-ftp-7-on-iis-7
*   https://wiki.filezilla-project.org/Main_Page
*   https://www.cerberusftp.com/
*   https://www.wftpserver.com/
*   https://winscp.net/eng/docs/start
*   https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp
*   https://en.wikipedia.org/wiki/File_Transfer_Protocol

## Practice

Apeture Science(~5 vulns) and My Little Pony (2 vulns) are images with FTP.
https://images.cypat.guide#gid=0

## Vulenrability Research
*   https://learn.microsoft.com/en-us/iis/configuration/system.ftpserver/security/
*   https://wiki.filezilla-project.org/Securing_your_Windows_Service_installation
*   https://filezillapro.com/docs/server/advanced-options/setting-up-connection-security/
*	https://support.cerberusftp.com/hc/en-us/articles/360000499020-Securing-Cerberus-FTP-Server-Best-Practices-for-Enhanced-Security
*   https://www.wftpserver.com/help/ftpserver/index.html?security.htm
*   https://winscp.net/eng/docs/security
