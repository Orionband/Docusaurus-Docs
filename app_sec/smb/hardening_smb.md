# Hardening SMB Server
___
Author(s): a_person

Last Updated: 07-06-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
- Basic knowledge of Windows  <br />
- Basic knowledge of Networking <br />
- Registry<br />
- Group Policy<br />
- Previous SMB Article<br />
</details>

## Overview
This article will contain hardening recommended by CIS and the DoD. They will be represented as * and + respectively. Each hardening object will be followed by a reason/rationale as well as the GP location

## Hardening

### Ensure 'Access this computer from the network' is set to 'Administrators, Authenticated Users, ENTERPRISE DOMAIN CONTROLLERS'. *+
Users who can connect from their computer to the network can access resources on target computers for which they have permission. For example, the Access this computer from the network user right is required for users to connect to shared printers and folders. If this user right is assigned to the Everyone group, then anyone will be able to read the files in those shared folders. However, this situation is unlikely for new installations of Windows Server 2003 with Service Pack 1 (SP1), because the default share and NTFS permissions in Windows Server 2003 do not include the Everyone group. This vulnerability may have a higher level of risk for computers that you upgrade from Windows NT 4.0 or Windows 2000, because the default permissions for these operating systems are not as restrictive as the default permissions in Windows Server 2003.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Access this computer from the network`
<br />
### Ensure 'Deny access to this computer from the network' to include 'Guests, Local account and member of Administrators group'. *+
Users who can log on to the computer over the network can enumerate lists of account names, group names, and shared resources. Users with permission to access shared folders and files can connect over the network and possibly view or modify data.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Deny access to this computer from the network`
<br />
### Ensure 'Microsoft network client: Digitally sign communications (always)' is set to 'Enabled'. *+
Session hijacking uses tools that allow attackers who have access to the same network as the client or server to interrupt, end, or steal a session in progress. Attackers can potentially intercept and modify unsigned SMB packets and then modify the traffic and forward it so that the server might perform undesirable actions. Alternatively, the attacker could pose as the server or client after legitimate authentication and gain unauthorized access to data. SMB is the resource sharing protocol that is supported by many Windows operating systems. It is the basis of NetBIOS and many other protocols. SMB signatures authenticate both users and the servers that host the data. If either side fails the authentication process, data transmission will not take place.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network client: Digitally sign communications (always)`
### Ensure 'Microsoft network client: Digitally sign communications (if server agrees)' is set to 'Enabled'. *+
Session hijacking uses tools that allow attackers who have access to the same network as the client or server to interrupt, end, or steal a session in progress. Attackers can potentially intercept and modify unsigned SMB packets and then modify the traffic and forward it so that the server might perform undesirable actions. Alternatively, the attacker could pose as the server or client after legitimate authentication and gain unauthorized access to data. SMB is the resource sharing protocol that is supported by many Windows operating systems. It is the basis of NetBIOS and many other protocols. SMB signatures authenticate both users and the servers that host the data. If either side fails the authentication process, data transmission will not take place.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network client: Digitally sign communications (if server agrees)`
### Ensure 'Microsoft network client: Send unencrypted password to third-party SMB servers' is set to 'Disabled'. *+
If you enable this policy setting, the server can transmit passwords in plaintext across the network to other computers that offer SMB services, which is a significant security risk. These other computers may not use any of the SMB security mechanisms that are included with Windows Server 2003.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network client: Send unencrypted password to third-party SMB servers`
### Ensure 'Microsoft network server: Amount of idle time required before suspending session' is set to '15 or fewer minute(s)'. *
Each SMB session consumes server resources, and numerous null sessions will slow the server or possibly cause it to fail. An attacker could repeatedly establish SMB sessions until the server's SMB services become slow or unresponsive.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Amount of idle time required before suspending session`
### Ensure 'Microsoft network server: Digitally sign communications (always)' is set to 'Enabled'. *+
Session hijacking uses tools that allow attackers who have access to the same network as the client or server to interrupt, end, or steal a session in progress. Attackers can potentially intercept and modify unsigned SMB packets and then modify the traffic and forward it so that the server might perform undesirable actions. Alternatively, the attacker could pose as the server or client after legitimate authentication and gain unauthorized access to data. SMB is the resource sharing protocol that is supported by many Windows operating systems. It is the basis of NetBIOS and many other protocols. SMB signatures authenticate both users and the servers that host the data. If either side fails the authentication process, data transmission will not take place.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Digitally sign communications (always)`
### Ensure 'Microsoft network server: Digitally sign communications (if client agrees)' is set to 'Enabled'. *+
Session hijacking uses tools that allow attackers who have access to the same network as the client or server to interrupt, end, or steal a session in progress. Attackers can potentially intercept and modify unsigned SMB packets and then modify the traffic and forward it so that the server might perform undesirable actions. Alternatively, the attacker could pose as the server or client after legitimate authentication and gain unauthorized access to data. SMB is the resource sharing protocol that is supported by many Windows operating systems. It is the basis of NetBIOS and many other protocols. SMB signatures authenticate both users and the servers that host the data. If either side fails the authentication process, data transmission will not take place.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Digitally sign communications (if client agrees)`
### Ensure 'Microsoft network server: Disconnect clients when logon hours expire' is set to 'Enabled'. *
If your organization configures logon hours for users, then it makes sense to enable this policy setting. Otherwise, users who should not have access to network resources outside of their logon hours may actually be able to continue to use those resources with sessions that were established during allowed hours.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Disconnect clients when logon hours expire`
### Ensure 'Microsoft network server: Server SPN target name validation level' is set to 'Accept if provided by client' or higher. *
The identity of a computer can be spoofed to gain unauthorized access to network resources.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Microsoft network server: Server SPN target name validation level`
### Ensure 'Network access: Allow anonymous SID/Name translation' is set to 'Disabled'. *+
If this policy setting is enabled, a user with local access could use the well-known Administrator's SID to learn the real name of the built-in Administrator account, even if it has been renamed. That person could then use the account name to initiate a password guessing attack.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Allow anonymous SID/Name translation`
### Ensure 'Network access: Do not allow anonymous enumeration of SAM accounts and shares' is set to 'Enabled'. *+
An unauthorized user could anonymously list account names and shared resources and use the information to attempt to guess passwords or perform social engineering attacks. (Social engineering attacks try to deceive users in some way to obtain passwords or some form of security information.)
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Do not allow anonymous enumeration of SAM accounts and shares`
### Ensure 'Network access: Restrict anonymous access to Named Pipes and Shares' is set to 'Enabled'. *+
Null sessions are a weakness that can be exploited through shares (including the default shares) on computers in your environment.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network access: Restrict anonymous access to Named Pipes and Shares`
### Ensure 'Network security: Do not store LAN Manager hash value on next password change' is set to 'Enabled'. *+
The SAM file can be targeted by attackers who seek access to username and password hashes. Such attacks use special tools to crack passwords, which can then be used to impersonate users and gain access to resources on your network. These types of attacks will not be prevented if you enable this policy setting, but it will be much more difficult for these types of attacks to succeed.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: Do not store LAN Manager hash value on next password change`
### Ensure 'Network security: LAN Manager authentication level' is set to 'Send NTLMv2 response only. Refuse LM & NTLM'. *+
Windows 2000 and Windows XP clients were configured by default to send LM and NTLM authentication responses (Windows 95-based and Windows 98-based clients only send LM). The default settings in OSes predating Windows Vista / Windows Server 2008 (non-R2) allowed all clients to authenticate with servers and use their resources. However, this meant that LM responses - the weakest form of authentication response - were sent over the network, and it was potentially possible for attackers to sniff that traffic to more easily reproduce the user's password. The Windows 95, Windows 98, and Windows NT operating systems cannot use the Kerberos version 5 protocol for authentication. For this reason, in a Windows Server 2003 domain, these computers authenticate by default with both the LM and NTLM protocols for network authentication. You can enforce a more secure authentication protocol for Windows 95, Windows 98, and Windows NT by using NTLMv2. For the logon process, NTLMv2 uses a secure channel to protect the authentication process. Even if you use NTLMv2 for older clients and servers, Windows-based clients and servers that are members of the domain will use the Kerberos authentication protocol to authenticate with Windows Server 2003 or newer Domain Controllers. For these reasons, it is strongly preferred to restrict the use of LM & NTLM (non-v2) as much as possible.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\Security Options\Network security: LAN Manager authentication level`
### Ensure 'Audit Detailed File Share' is set to include 'Failure'. *+
Auditing the Failures will log which unauthorized users attempted (and failed) to get access to a file or folder on a network share on this computer, which could possibly be an indication of malicious intent.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Advanced Audit Policy Configuration\Audit Policies\Object Access\Audit Detailed File Share`
### Ensure 'Audit File Share' is set to 'Success and Failure'. *+
In an enterprise managed environment, workstations should have limited file sharing activity, as file servers would normally handle the overall burden of file sharing activities. Any unusual file sharing activity on workstations may therefore be useful in an investigation of potentially malicious activity.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Advanced Audit Policy Configuration\Audit Policies\Object Access\Audit File Share`
### Ensure 'Configure SMB v1 client driver' is set to 'Enabled: Disable driver (recommended)'. *+
Since September 2016, Microsoft has strongly encouraged that SMBv1 be disabled and no longer used on modern networks, as it is a 30 year old design that is much more vulnerable to attacks then much newer designs such as SMBv2 and SMBv3. More information on this can be found at the following links: Stop using SMB1 | Storage at Microsoft Disable SMB v1 in Managed Environments with Group Policy – "Stay Safe" Cyber Security Blog Disabling SMBv1 through Group Policy – Microsoft Security Guidance blog
<br />
GP: `Computer Configuration\Policies\Administrative Templates\MS Security Guide\Configure SMB v1 client driver`
### Ensure 'Configure SMB v1 server' is set to 'Disabled'. *+
Since September 2016, Microsoft has strongly encouraged that SMBv1 be disabled and no longer used on modern networks, as it is a 30 year old design that is much more vulnerable to attacks then much newer designs such as SMBv2 and SMBv3. More information on this can be found at the following links: Stop using SMB1 | Storage at Microsoft Disable SMB v1 in Managed Environments with Group Policy – "Stay Safe" Cyber Security Blog Disabling SMBv1 through Group Policy – Microsoft Security Guidance blog
<br />
GP: `Computer Configuration\Policies\Administrative Templates\MS Security Guide\Configure SMB v1 server`
### Ensure 'MSS: (NoNameReleaseOnDemand) Allow the computer to ignore NetBIOS name release requests except from WINS servers' is set to 'Enabled'. *+
The NetBT protocol is designed not to use authentication, and is therefore vulnerable to spoofing. Spoofing makes a transmission appear to come from a user other than the user who performed the action. A malicious user could exploit the unauthenticated nature of the protocol to send a name-conflict datagram to a target computer, which would cause the computer to relinquish its name and not respond to queries. An attacker could send a request over the network and query a computer to release its NetBIOS name. As with any change that could affect applications, it is recommended that you test this change in a non-production environment before you change the production environment. The result of such an attack could be to cause intermittent connectivity issues on the target computer, or even to prevent the use of Network Neighborhood, domain logons, the NET SEND command, or additional NetBIOS name resolution.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\MSS (Legacy)\MSS: (NoNameReleaseOnDemand) Allow the computer to ignore NetBIOS name release requests except from WINS servers`
### Ensure 'Audit client does not support encryption' is set to 'Enabled'. *
Organizations should be aware of all unencrypted SMB traffic in their environment. Older SMB protocols that do not use encryption can make an environment susceptible to many types of attacks, including SMB interception attacks.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Server\Audit client does not support encryption`
### Ensure 'Audit client does not support signing' is set to 'Enabled'. *
Organizations should be aware of all unsigned SMB traffic in their environment. Older SMB protocols that do not use signing can make an environment susceptible to many types of attacks, including SMB interception attacks.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Server\Audit client does not support signing`
### Ensure 'Audit insecure guest logon' is set to 'Enabled'. *
Insecure guest logons can be used by file servers to allow unauthenticated access to shared folders.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Server\Audit insecure guest logon`
### Ensure 'Enable remote mailslots' is set to 'Disabled'. *
Remote mailslots is a legacy protocol that uses SMBv1 to function. This protocol is linked to known vulnerabilities, such as denial of service, buffer overflow, and remote code execution attacks.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Server\Enable remote mailslots`
### Ensure 'Mandate the minimum version of SMB' is set to 'Enabled: 3.1.1'. *
The newer, more modern version of SMB (v3) is supported and available on all currently supported Microsoft Windows OSes. SMBv1 is no longer enabled by default due to its security risks, and although SMBv2 is more robust than v1, it does not support encryption like its successor.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Server\Mandate the minimum version of SMB`
### Ensure 'Set authentication rate limiter delay (milliseconds)' is set to 'Enabled: 2000' or more. *
Authentication rate limiter considerably reduces the risk of brute force attacks by implementing a 2-second delay (default) between each failed NTLM or PKU2U-based authentication attempt. According to Microsoft, if an attacker sends 300 brute force attempts per second from a client for 5 minutes which equals 90,000 passwords, the same number of attempts would now take 50 hours or more.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Server\Set authentication rate limiter delay (milliseconds)`
### Ensure 'Audit server does not support encryption' is set to 'Enabled'. *
Organizations should be aware of all unencrypted SMB traffic in their environment. Older SMB protocols that do not use encryption can make an environment susceptible to many types of attacks, including SMB interception attacks.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Workstation\Audit server does not support encryption`
### Ensure 'Audit server does not support signing' is set to 'Enabled'. *
Organizations should be aware of all unsigned SMB traffic in their environment. Older SMB protocols that do not use signing can make an environment susceptible to many types of attacks, including SMB interception attacks.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Workstation\Audit server does not support signing`
### Ensure 'Enable insecure guest logons' is set to 'Disabled'. *+
Insecure guest logons are used by file servers to allow unauthenticated access to shared folders.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Workstation\Enable insecure guest logons`
### Ensure 'Require Encryption' is set to 'Enabled'. *
The newer, more modern version of SMB (v3) is supported and available on all currently supported Microsoft Windows OSes. SMBv1 is no longer enabled by default due to its security risks, and although SMBv2 is more robust than v1, it does not support encryption like its successor.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Lanman Workstation\Require Encryption`
### Ensure 'Hardened UNC Paths' is set to 'Enabled, with "Require Mutual Authentication", "Require Integrity", and “Require Privacy” set for all NETLOGON and SYSVOL shares'. *+
In February 2015, Microsoft released a new control mechanism to mitigate a security risk in Group Policy as part of the MS15-011 / MSKB 3000483 security update. This mechanism requires both the installation of the new security update and also the deployment of specific group policy settings to all computers on the domain from Windows Vista / Server 2008 (non-R2) or newer (the associated security patch to enable this feature was not released for Server 2003). A new group policy template (NetworkProvider.admx/adml) was also provided with the security update. Once the new GPO template is in place, the following are the minimum requirements to remediate the Group Policy security risk: \\*\NETLOGON RequireMutualAuthentication=1, RequireIntegrity=1, RequirePrivacy=1 \\*\SYSVOL RequireMutualAuthentication=1, RequireIntegrity=1, RequirePrivacy=1 Note: A reboot may be required after the setting is applied to a client machine to access the above paths. Additional guidance on the deployment of this security setting is available from the Microsoft Premier Field Engineering (PFE) Platforms TechNet Blog here: Guidance on Deployment of MS15-011 and MS15-014.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Network\Network Provider\Hardened UNC Paths`
### Ensure nonsystem-created file shares limit access to groups that require it. +
Shares on a system provide network access. To prevent exposing sensitive information, where shares are necessary, permissions must be reconfigured to give the minimum access to accounts that require it.
<br />
Navigate to System Tools >> Shared Folders >> Shares.
<br />
Right-click any nonsystem-created shares.
<br />
Select "Properties".
<br />
Select the "Share Permissions" tab.
<br />
If the file shares have not been configured to restrict permissions to the specific groups or accounts that require access, this is a finding.
<br />
Select the "Security" tab.
<br />
If the permissions have not been configured to restrict permissions to the specific groups or accounts that require access, this is a finding.
### Ensure the Server Message Block (SMB) v1 protocol is not installed. +
SMBv1 is a legacy protocol that uses the MD5 algorithm as part of SMB. MD5 is known to be vulnerable to a number of attacks such as collision and preimage attacks and is not FIPS compliant.
<br />
<br />
Powershell:
<br />
**Uninstall-WindowsFeature -Name FS-SMB1 -Restart**

## Practice
DPRK(3 vulns), Mushroom Kingdom(3 vulns), PPTH(3 vulns), and Among the Reindeer(2 vulns) are some images with SMB.
https://images.cypat.guide#gid=0

___
### References & Further Reading
- https://stigviewer.com/stigs/microsoft_windows_server_2022
- https://workbench.cisecurity.org/benchmarks/21344




