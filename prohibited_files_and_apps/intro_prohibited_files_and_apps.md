# Introduction to Prohibited Files and Apps
___
Author(s): a_person

Last Updated: 07-03-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
<p>None</p>
</details>

## What is this about?
This is mainly about deleting and removing unwanted files and apps. Note that this article does not include malware, as it is a different subject.

## Why do we need to worry about this?
This is for several reasons:
*	Takes up space
*	Increases attack surface  (especially stuff like plaintext password files)
*	Violate company policies

## Concepts
 - Apps are stored in multiple locations
     - C:\Program Files\
       - 64 bit
     - C:\Program Files(x86)\
       - 32 bit on 64 bit computer
     - C:\Users\[User]\AppData\Local
       - User specific apps that don't require administrative privileges to download
       - also contains user specific app data
 - Prohibited files are very diverse. Examples:
   - Mp3 files
   - Plain text password files
   - Games
   - etc.


## Tools
### [Voidtools(Everything)](https://www.voidtools.com/) - Prohibited files
Voidtools is very helpful when finding prohibited files. It uses regex (Regular expresion) and is much faster than the Windows Explorer search. It is also helpful as you are able to see the creation date, which can help you determine whether a file is a system file or a prohibited file. If I wanted to find mp3 files, the regex would simply be``*.mp3``.

### Settings and Control Panel - Prohibited apps
Settings and Control Panel are the easiest ways to find and remove apps.

Uninstall in Settings:
1. Select Start(windows icon)  > Settings  > Apps > Installed apps.
2. Find the app you want to remove, select More  > Uninstall.
3. Note: Some apps can't be uninstalled from the Settings app right now. For help uninstalling these apps, follow the instructions to uninstall from Control Panel.  

Uninstall from Control Panel:
1. In search on the taskbar, enter Control Panel and select it from the results.
2. Select Programs > Programs and Features.
3. Press and hold (or right-click) on the program you want to remove and select Uninstall or Uninstall/Change. Then follow the directions on the screen.

### [WinDirStat](https://windirstat.net/) - Prohibited files
WinDirStat is a disk usage statistics viewer and cleanup assistant for Windows. It can assist in finding whether Users have prohibited files in their Common directories, as the percentage indicates empty directories, and it is easy to sift through common directories. It can also be used to find prohibited files in unusual locations, such as in ``C:\`` or in ``%HOMEPATH%``.





## Practice
Most images have prohibited files:  
https://images.cypat.guide#gid=0


___
### References, Further Reading, & Tools Mentioned
- https://support.microsoft.com/en-us/windows/uninstall-or-remove-apps-and-programs-in-windows-4b55f974-2cc6-2d2b-d092-5905080eaf98
- https://www.voidtools.com/
- https://windirstat.net/

