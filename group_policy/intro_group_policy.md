# Introduction to Group Policy
___
Author(s): a_person

Last Updated: 07-03-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
<p>None</p>
</details>


## What is it?

Group Policy is a feature in Microsoft Windows that allows administrators to manage settings for users and computers. It provides centralized configuration and enforcement of operating systems, applications, and user settings. It's either used in networks, or locally.


## Concepts
*   **Where Group Policy settings are stored:**
     *   **Registry Keys:** The actual policy settings are written to these protected registry locations, overriding standard user or application settings.
         *   `HKEY_LOCAL_MACHINE\Software\Policies` (for computer settings)
         *   `HKEY_CURRENT_USER\Software\Policies` (for user settings)
         *   *(And the corresponding ...\Microsoft\Windows\CurrentVersion\Policies locations)*
     *   **File System:** The `%SystemRoot%\System32\GroupPolicy\` directory stores the files that make up a GPO, including administrative templates and script files.


## Group Policy vs Registry
They are both used to configure settings, but Registry is basically an unc. Here are the main differences:
*  Each registry is local to its respective machine, while Group Policies can be applied to multiple computers
*  Group policy is more persistent as group policies apply during startup.
*  Group Policy is much easier to use as it gives setting names and explanations.

## How do I change Group Policies
*  ``gpedit.msc``
    * Locally. You can edit them just by selecting the policies you want to set.
*  ``gpmc.msc`` - For groups.
    * For groups. You can edit them by selecting them on the sidebar.


## Local Security Policy
`secpol.msc` is a specific section of the local group policy(`Computer Configuration > Windows Settings > Security Settings`). Any change you make in `secpol.msc` is actually being made within the Local Group Policy (`gpedit.msc`) and can be viewed there.



**Main Settings Configured in ``secpol.msc``:**

*   **Account Policies** - This is where you configure password requirements (length, complexity, history) and account lockout policies (e.g., lock an account after 5 bad password attempts).
*   **Audit Policy** - Determines which security-related events are logged in the Windows Security Event Log. For example, you can audit successful or failed logon attempts.
*   **User Rights Assignment** - Controls the specific rights and privileges that users and groups have on the local machine, such as "Shut down the system" or "Back up files and directories."
*   **Security Options** - A large collection of miscellaneous security settings, such as "Interactive logon: Do not display last user name" or policies related to User Account Control (UAC).


## Tools for automation and compliance
*  [LGPO](https://www.microsoft.com/en-us/download/details.aspx?id=55319) - Allows you to import and export GPOs
*  [Hardening Kitty](https://github.com/scipag/HardeningKitty) - Similar to lgpo, and has diverse modes which can allow you to see the most critical policies that are set incorrectly. It also contains some premade baselines.
*  [SCC](https://public.cyber.mil/stigs/scap/) - Developed by the Department of Defense. SCC has Security Content Automation Protocol (SCAP) content and tools to help with security compliance and automation.

## Premade baselines
*  [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks) - Baselines made by the Center for Internet Security. It provides two levels of baselining and is widely used.
*  [DoD Stigs](https://stigviewer.com/stigs) -  Security baselines created by the Department of Defense. These guides are used to harden military networks and systems.

## Practice
ALL images except for images like the persistence image contain Group Policy points:  
images.cypat.guide


___
### References, Further Reading, & Tools Mentioned
* https://en.wikipedia.org/wiki/Group_Policy
* https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-overview
* https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console
* https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265982(v=ws.11)
* https://www.microsoft.com/en-us/download/details.aspx?id=55319
* https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/how-to-configure-security-policy-settings
*  https://github.com/scipag/HardeningKitty
*  https://public.cyber.mil/stigs/scap/
*  https://www.cisecurity.org/cis-benchmarks
*  https://stigviewer.com/stigs
