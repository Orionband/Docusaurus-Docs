# Hardening RDP

---

Author(s): a_person

Last Updated: 07-04-2025

Recommended Prerequisites (click to expand)

- Basic knowledge of Windows <br />
- Registry<br />
- Group Policy<br />
- Previous RDP Article<br />

## Overview

This article will contain hardening recommended by CIS and the DoD. They will be represented as \* and + respectively. Each hardening object will be followed by a reason/rationale as well as the GP location

## Hardening

### Ensure 'Allow log on through Remote Desktop Services' is set to 'Administrators, Remote Desktop Users'\*+

Any account with the Allow log on through Remote Desktop Services user right can
log on to the remote console of the computer. If you do not restrict this user right to
legitimate users who need to log on to the console of the computer, unauthorized users
could download and run malicious software to elevate their privileges.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local
Policies\User Rights Assignment\Allow log on through Remote Desktop Services`

### Ensure 'Deny log on through Remote Desktop Services' to include 'Guests, Local account' and must prevent access from highly privileged domain accounts and local accounts on domain systems and unauthenticated access on all systems.\*+

Any account with the right to log on through Remote Desktop Services could be used to
log on to the remote console of the computer. If this user right is not restricted to
legitimate users who need to log on to the console of the computer, unauthorized users
might download and run malicious software that elevates their privileges.
<br />
GP: `Computer Configuration\Policies\Windows Settings\Security Settings\Local
Policies\User Rights Assignment\Deny log on through Remote Desktop Services`

### Ensure 'Disable Cloud Clipboard integration for server-to-client data transfer' is set to 'Enabled'\*

In high security environments, clipboard data should stay local to the system and not
synced to the cloud as it may contain sensitive information that should be contained
locally.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Connection Client\Disable
Cloud Clipboard integration for server-to-client data transfer`

### Ensure 'Do not allow passwords to be saved' is set to 'Enabled'\*+

An attacker with physical access to the computer may be able to break the protection
guarding saved passwords. An attacker who compromises a user's account and
connects to their computer could use saved passwords to gain access to additional
hosts.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Connection Client\Do not
allow passwords to be saved`

### Ensure 'Allow UI Automation redirection' is set to 'Disabled'\*

In a more security-sensitive environment, it is desirable to reduce the possible attack
surface. The need for UI Automation redirection within a Remote Desktop session is
rare, and not supported at this time, but it makes sense to reduce the number of
unexpected avenues for malicious activity to occur.
<br />
GP: `Computer Configuration\Administrative Templates\Windows Components\Remote
Desktop Services\Remote Desktop Session Host\Device and Resource
Redirection\Allow UI Automation redirection`

### Ensure 'Do not allow COM port redirection' is set to 'Enabled'\*

In a more security-sensitive environment, it is desirable to reduce the possible attack
surface. The need for COM port redirection within a Remote Desktop session is very
rare, so makes sense to reduce the number of unexpected avenues for data exfiltration
and/or malicious code transfer.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Device and
Resource Redirection\Do not allow COM port redirection`

### Ensure 'Do not allow drive redirection' is set to 'Enabled'\*+

Data could be forwarded from the user's Remote Desktop Services session to the user's
local computer without any direct user interaction. Malicious software already present
on a compromised server would have direct and stealthy disk access to the user's local
computer during the Remote Desktop session.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Device and
Resource Redirection\Do not allow drive redirection`

### Ensure 'Do not allow location redirection' is set to 'Enabled'\*

In a more security-sensitive environment, it is desirable to reduce the possible attack
surface. The need for location data redirection within a Remote Desktop session is rare,
so it makes sense to reduce the number of unexpected avenues for malicious activity to
occur.
<br />
GP: `Computer Configuration\Administrative Templates\Windows Components\Remote
Desktop Services\Remote Desktop Session Host\Device and Resource
Redirection\Do not allow location redirection`

### Ensure 'Do not allow LPT port redirection' is set to 'Enabled'\*

In a more security-sensitive environment, it is desirable to reduce the possible attack
surface. The need for LPT port redirection within a Remote Desktop session is very
rare, so makes sense to reduce the number of unexpected avenues for data exfiltration
and/or malicious code transfer.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Device and
Resource Redirection\Do not allow LPT port redirection`

### Ensure 'Do not allow supported Plug and Play device redirection' is set to 'Enabled'\*

In a more security-sensitive environment, it is desirable to reduce the possible attack
surface. The need for Plug and Play device redirection within a Remote Desktop
session is very rare, so makes sense to reduce the number of unexpected avenues for
data exfiltration and/or malicious code transfer.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Device and
Resource Redirection\Do not allow supported Plug and Play device redirection`

### Ensure 'Do not allow WebAuthn redirection' is set to 'Enabled'\*

In a more security-sensitive environment, it is desirable to reduce the possible attack
surface. To reduce this, resources inside the Remote Desktop session should not be
allowed to use the local authenticator.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Device and
Resource Redirection\Do not allow WebAuthn redirection`

### Ensure 'Restrict clipboard transfer from server to client' is set to 'Enabled: Disable clipboard transfers from server to client'\*

In a more security-sensitive environment, it is desirable to reduce the possible attack
surface. The need for the clipboard to transfer data from a Remote Desktop session to a
client is rare, so it makes sense to reduce the number of unexpected avenues for
malicious activity to occur.
<br />
GP: `Computer Configuration\Administrative Templates\Windows Components\Remote
Desktop Services\Remote Desktop Session Host\Device and Resource
Redirection\Restrict clipboard transfer from server to client`

### Ensure 'Always prompt for password upon connection' is set to 'Enabled'\*+

Users have the option to store both their username and password when they create a
new Remote Desktop Connection shortcut. If the server that runs Remote Desktop
Services allows users who have used this feature to log on to the server but not enter
their password, then it is possible that an attacker who has gained physical access to
the user's computer could connect to a Remote Desktop Server through the Remote
Desktop Connection shortcut, even though they may not know the user's password.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session
Host\Security\Always prompt for password upon connection`

### Ensure 'Require secure RPC communication' is set to 'Enabled'\*+

Allowing unsecure RPC communication can exposes the server to man in the middle
attacks and data disclosure attacks.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session
Host\Security\Require secure RPC communication`

### Ensure 'Require use of specific security layer for remote (RDP) connections' is set to 'Enabled: SSL'\*+

The native RDP encryption is now considered a weak protocol, so enforcing the use of
stronger TLS encryption for all RDP communications between clients and RD Session
Host servers is preferred.
<br />
GP:`Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session
Host\Security\Require use of specific security layer for remote (RDP)
connections`

### Ensure 'Require user authentication for remote connections by using Network Level Authentication' is set to 'Enabled'\*

Requiring that user authentication occur earlier in the remote connection process
enhances security.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session
Host\Security\Require user authentication for remote connections by using
Network Level Authentication`

### Ensure 'Set client connection encryption level' is set to 'Enabled: High Level'\*+

If Remote Desktop client connections that use low level encryption are allowed, it is
more likely that an attacker will be able to decrypt any captured Remote Desktop
Services network traffic.
<br />
GP: `Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Security\Set
client connection encryption level`

### Ensure 'Set time limit for active but idle Remote Desktop Services sessions' is set to 'Enabled: 15 minutes or less, but not Never (0)'\*

This setting helps to prevent active Remote Desktop sessions from tying up the
computer for long periods of time while not in use, preventing computing resources from
being consumed by large numbers of inactive sessions. In addition, old, forgotten
Remote Desktop sessions that are still active can cause password lockouts if the user's
password has changed but the old session is still running. For systems that limit the
number of connected users (e.g. servers in the default Administrative mode - 2 sessions
only), other users' old but still active sessions can prevent another user from
connecting, resulting in an effective denial of service.
In addition, session timeouts that are misconfigured or set for a long period of time can
leave the system open to an attacker hijacking the session.
<br />
GP:`Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Session Time
Limits\Set time limit for active but idle Remote Desktop Services sessions`

### Ensure 'Set time limit for disconnected sessions' is set to 'Enabled: 1 minute'\*

This setting helps to prevent active Remote Desktop sessions from tying up the
computer for long periods of time while not in use, preventing computing resources from
being consumed by large numbers of disconnected but still active sessions. In addition,
old, forgotten Remote Desktop sessions that are still active can cause password
lockouts if the user's password has changed but the old session is still running. For
systems that limit the number of connected users (e.g. servers in the default
Administrative mode - 2 sessions only), other users' old but still active sessions can
prevent another user from connecting, resulting in an effective denial of service. This
setting is important to ensure a disconnected session is properly terminated.
In addition, session timeouts that are misconfigured or set for a long period of time can
leave the system open to an attacker hijacking the session.
<br />
GP:`Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Session Time
Limits\Set time limit for disconnected sessions`

### Ensure 'Do not delete temp folders upon exit' is set to 'Disabled'\*+

Sensitive information could be contained inside the temporary folders and visible to
other administrators that log into the system.
<br />
GP:`Computer Configuration\Policies\Administrative Templates\Windows
Components\Remote Desktop Services\Remote Desktop Session Host\Temporary
Folders\Do not delete temp folders upon exit`

### Ensure 'Access this computer from the network' is set to 'Administrators and Remote Desktop Users'+

Inappropriate granting of user rights can provide system, administrative, and other high-level capabilities. Accounts with the "Access this computer from the network" user right may access resources on the system, and must be limited to those that require it.
<br />
GP:`Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Access this computer from the network`

## Practice

DPRK(2 vulns), Tokyo 3(2 vulns), Baldi's Basics(2 vulns), Sunrise(3 vulns), Beyond Journey's End(2 vulns), Alphabet Soup(2 vulns), PPTH(3 vulns) are some images with RDP.
https://images.cypat.guide#gid=0

---

### References & Further Reading

- https://stigviewer.com/stigs/microsoft_windows_11
- https://workbench.cisecurity.org/benchmarks/21318
