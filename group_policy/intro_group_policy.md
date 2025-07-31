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
## Concepts
* Where Group Policy settings are stored:
    * `HKEY_LOCAL_MACHINE\Software\Policies` and `HKEY_CURRENT_USER\Software\Policies`
    * `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies` and `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies`
    * `%SystemRoot%\System32\GroupPolicy\`
* Group Policies can be applied to specific groups within Active Directory (a Windows Server feature). For example, users in a ``Students`` group can have different Group Policy Objects (GPOs) applied compared to users in a ``Teachers`` group.
* Group Policy settings are processed in the following order: Local, Site, Domain, and Organizational Unit (OU). Later policies override earlier ones, with OU policies having the highest precedence.


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

## Tools for automation and compliance
*  [LGPO](https://www.microsoft.com/en-us/download/details.aspx?id=55319) - Allows you to import and export GPOs
*  [Hardening Kitty](https://github.com/scipag/HardeningKitty) - Similar to lgpo, and has diverse modes which can allow you to see the most critical policies that are set incorrectly. It also contains some premade baselines.
*  [SCC](https://public.cyber.mil/stigs/scap/) - Developed by the Department of Defense. SCC has Security Content Automation Protocol (SCAP) content and tools to help with security compliance and automation.

## Premade baselines
*  [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks) - Baselines made by the Center for Internet Security. It provides two levels of baselining and is widely used.
*  [DoD Stigs](https://stigviewer.com/stigs) -  Security baselines created by the Department of Defense. These guides are used to harden military networks and systems.

## Quiz
<details>
  <summary><strong>Who developed STIGs and what are they used for?</strong></summary>
  <p>
    <strong>The US Department of Defense. They are used to harden government networks and systems.</strong>
  </p>
</details>
<details>
  <summary><strong>What is the difference between gpedit.msc and gpmc.msc?</strong></summary>
  <p>
    <strong>``gpedit.msc`` is used to configure local(on the computer) policies, while ``gpmc.msc`` is used to configure policies for networks and groups.</strong>
  </p>
</details>
<details>
  <summary><strong>Where are group policies stored?</strong></summary>
  <p><strong>Group policies are stored in the following locations:</strong></p>
<ul>
  <li>HKEY_LOCAL_MACHINE\Software\Policies and HKEY_CURRENT_USER\Software\Policies</li>
  <li>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies and HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies</li>
  <li>%SystemRoot%\System32\GroupPolicy\ </li>
</ul>

</details>



## Practice
ALL images except for the persistence image contain Group Policy points:  
images.cypat.guide


___
### References, Further Reading, & Tools Mentioned
* https://en.wikipedia.org/wiki/Group_Policy
* https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-overview
* https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console
* https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265982(v=ws.11)
*  https://www.microsoft.com/en-us/download/details.aspx?id=55319
*  https://github.com/scipag/HardeningKitty
*  https://public.cyber.mil/stigs/scap/
*  https://www.cisecurity.org/cis-benchmarks
*  https://stigviewer.com/stigs
