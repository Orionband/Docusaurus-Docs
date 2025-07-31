# Hardening FTP

Author(s): a_person

Last Updated: 07-19-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
- Basic knowledge of Windows  
- Registry  
- Group Policy  
- Previous FTP Article  
</details>

## Note
This article will not follow the same format as others because of the many different FTP servers. Therefore, CIS Benchmarks and DoD stigs won’t be the only sources used.

## Microsoft FTP
## Mandate Encrypted Connections
The main vulnerability in standard FTP is that it transmits all data, including credentials, in plain text. Enforcing FTPS (FTP over SSL/TLS) secures the entire session with encryption. This makes it safe from eavesdropping and man-in-the-middle attacks.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP SSL Settings`  
<b>Recommendation:</b> Set the SSL Policy to `Require SSL connections`.

## Disable Anonymous Authentication
Allowing anonymous FTP means anyone can connect without credentials. It must be disabled unless there is a clear and strictly controlled public use case.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP Authentication`  
<b>Recommendation:</b> Select `Anonymous Authentication` and click `Disable` in the Actions pane.

## Implement Logon Attempt Restrictions
To counter automated brute-force password attacks at the application level, IIS has a built-in feature that tracks and blocks malicious IPs. This is an important defense against password guessing aimed at the FTP service.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP Logon Attempt Restrictions`  
<b>Recommendation:</b> Select `Enable logon attempt restrictions` and set a low threshold, such as `Maximum number of failed logon attempts: 5` and `Time period (seconds): 60`.

## Isolate Users to Prevent Directory Traversal
Without user isolation, authenticated users might navigate outside their designated home directory (`../`). This can let a malicious user access files belonging to other users or sensitive system files. User isolation confines each user to their own directory, which basically sandboxes their session.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP User Isolation`  
<b>Recommendation:</b> Select the option `User name directory (disable global virtual directories)`.

## Restrict Access with IP Address and Domain Restrictions
If the FTP server is not meant for public access, limit its exposure to the internet. By using application-level IP restrictions, you can allow only connections from known, trusted locations to attempt authentication.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP IP Address and Domain Restrictions`  
<b>Recommendation:</b> Set the default to `Deny` access and create specific `Allow` rules for trusted IP addresses or ranges.

## Minimize Server Identity and Banner Information
By default, the FTP server banner displays its software name and version. This gives attackers useful information for finding specific exploits. Hiding or generalizing the banner can make it harder for them to gather data.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP Messages`  
<b>Recommendation:</b> Clear the default text in the `Banner Message`, `Welcome`, and `Exit` message fields, or replace them with a general warning that does not identify the software.

## Implement Request Filtering for Files and Commands
This feature gives you control over the FTP protocol to block harmful uploads and commands.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP Request Filtering`  
<b>Recommendation:</b>
<ul>
<li><b>File Name Extensions Tab:</b> Create `Deny` rules for all executable and script file extensions (`.exe`, `.com`, `.bat`, `.cmd`, `.dll`, etc. ) to stop malware uploads.</li>
<li><b>Commands Tab:</b> Review the allowed FTP commands and deny any that are not strictly necessary for your users.</li>
</ul>

## Configure a Limited Passive Mode Port Range for Firewall Compatibility
Passive mode FTP needs a range of ports for data transfers. Leaving this undefined can force you to open thousands of ports in your firewall, which increases the risk. Defining a small, specific port range allows for a precise and secure firewall setup.

<b>Location:</b> `IIS Manager > [Your Server Name] > FTP Firewall Support`  
<b>Recommendation:</b> Enter a limited, custom port range (e.g., `50000-51000`) in the `Data Channel Port Range` field. Then, in the Windows Firewall, create an inbound rule allowing TCP traffic only for that specific range, along with port 21.

## Implement Strict NTFS File System Permissions (Least Privilege)
Proper file system permissions are essential. If an attacker compromises an FTP account, strict NTFS permissions can stop them from accessing unauthorized data or running malware. This is an application of the least privilege principle.

<b>Location:</b> `Windows Explorer > [Right-click FTP root folder] > Properties > Security`  
<b>Recommendation:</b> For each folder, remove the `Everyone` and `Users` groups. Grant permissions only to specific FTP user accounts or groups. For users who only need to download, give them only `Read` and `Read & execute` permissions. For folders meant for uploads, grant `Write` permission but not `Read` or `Execute` to create a secure "drop-box". Avoid granting `Full Control`.

## Enable Comprehensive and Secure Logging
Without detailed logs, it’s hard to investigate a security incident. Logs provide an important record of all connections and file operations.

<b>Location:</b> `IIS Manager > [Your Server] > Sites > [Your FTP Site] > FTP Logging`  
<b>Recommendation:</b> Enable logging with the `W3C` format and select all fields for maximum detail. Store logs on a separate, non-system drive to protect their integrity and prevent the system disk from filling up. Check these logs regularly.

## General Tips for Other FTP Servers

## Prioritize Secure Protocols (FTPS/SFTP) and Disable Plain FTP
The most important hardening step for any FTP server is to disable the standard, unencrypted FTP protocol. An attacker on the network can easily intercept all traffic, including credentials. Using encryption is necessary.

<b>Recommendation:</b> In your FTP server's main configuration, find the protocol settings. Enable FTPS (FTP over SSL/TLS) and/or SFTP (SSH File Transfer Protocol). Disable any options that allow non-encrypted, standard FTP connections.

## Disable Outdated SSL/TLS Protocols and Weak Ciphers
Just enabling encryption is not enough; it must be strong. Older protocols like SSLv3 and TLS 1.0/1.1 have critical flaws (e.g., POODLE, BEAST) that can let attackers decrypt traffic.

<b>Recommendation:</b> In your server's SSL/TLS settings, create a specific list of allowed protocols. Disable SSLv2, SSLv3, TLS 1.0, and TLS 1.1. Allow only TLS 1.2 and TLS 1.3. Also, configure the allowable cipher suite list to exclude known weak ciphers (e.g., those using RC4, 3DES, or any with "NULL" or "ANON").

## Run the FTP Service with a Dedicated, Least-Privilege Account
Third-party FTP servers run as a Windows service. This service should not run using a high-privileged account like `Local System`. If the FTP application has a vulnerability, an attacker could gain the service account's high-level permissions. This control helps limit the damage from any application exploit.

<b>Location:</b> `Services (services.msc) > [Your FTP Service] > Properties > Log On`  
<b>Recommendation:</b> Create a dedicated local user account without interactive logon rights. Grant this account only the specific NTFS permissions it needs to function (e.g., read its own config folder, write to its log folder). Configure the service to log on as this user.

## Use Application-Level IP Access Controls and Anti-Hammering
Most dedicated FTP servers have built-in features to block brute-force attacks and manage access. These should be your main defense against such attacks.

<b>Recommendation:</b>
<ul>
<li><b>IP Access:</b> Find the IP Manager or Access Control settings. Set the default to "Deny" all connections, and then add "Allow" rules only for specific, trusted client IP addresses.</li>
<li><b>Anti-Hammering:</b> Enable auto-banning. Configure it to ban an IP address permanently or temporarily after a small number of failed login attempts (e.g., ban after 5 failures in 1 minute).</li>
</ul>

## Configure Per-User Permissions within the Application
Do not rely only on NTFS permissions. Dedicated FTP servers offer their own per-user permission systems. This allows you to control specific actions like listing directories, creating subdirectories, deleting files, or overwriting files, providing much finer control than NTFS alone.

<b>Recommendation:</b> For every user account created in the FTP server application, review and assign the most limited permissions possible. If a user only needs to upload files, disable their permissions for downloading, deleting, and listing files.

## Keep the FTP Server Application Patched and Updated
Third-party FTP server software, like any application, can have security issues. Developers release patches and updates to fix these problems. Failing to apply these updates leaves your server vulnerable to known and often easily exploitable flaws.

<b>Recommendation:</b> Regularly check the software vendor's website for new versions and security notices. Subscribe to their security updates. Apply patches as soon as they are available, after testing them in a non-production environment.

## Practice

Apeture Science(~5 vulns) and My Little Pony (2 vulns) are images with FTP.
https://images.cypat.guide#gid=0

## References & Further Reading
*   https://learn.microsoft.com/en-us/iis/configuration/system.ftpserver/security/
*   https://wiki.filezilla-project.org/Securing_your_Windows_Service_installation
*   https://filezillapro.com/docs/server/advanced-options/setting-up-connection-security/
*   https://support.cerberusftp.com/hc/en-us/articles/360000499020-Securing-Cerberus-FTP-Server-Best-Practices-for-Enhanced-Security
*   https://www.wftpserver.com/help/ftpserver/index.html?security.htm
*   https://winscp.net/eng/docs/security
