# Hardening Web Browsers
___
Author(s): a_person

Last Updated: 07-06-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
- Basic knowledge of Windows  <br />
- Registry<br />
- Group Policy<br />
</details>

## What are web browsers?
An app that helps you browse the web 🤯. In other words, a web browser is a software application that allows users to access and display web pages on the internet. The most common browsers are:
1. Google Chrome
2. Firefox
3. Microsoft Edge
These Web Browsers can be configured through the registry and are very similar when configuring security policies.

## Why do we need to secure them?
Securing web browsers are important for a variety of reasons, such as:
1. Preventing the download of malicious software and reduce the likelihood of phishing attacks
2. Protecting Sensitive Data(passwords, history, etc) 
3. Preventing Tracking

## Administrative Templates
Administrative Templates are a set of Group Policy settings in Windows that allow administrators to manage and configure the behavior and appearance of the Windows operating system and its components. Think of it as an add-on to group policy.

This is by far the easiest way of configuring policies, as it is much harder to go through documentation and find the right registry keys and set them to the right value. You can find them here:
1. [Google Chrome](https://support.google.com/chrome/a/answer/187202#zippy=%2Cwindows)
2. [Firefox](https://github.com/mozilla/policy-templates/releases)
3. [Microsoft Edge](https://www.microsoft.com/en-us/edge/business/download?cs=1873324239&form=MA13FJ)

## Main methods to secure Web Browsers  
Because there are so many web browsers, this guide will cover the main concepts for hardening them. These principles apply with any web browser.

### 1. Keep Your Browser and Extensions Updated  
**What it is:** Self explanitory.

**Why it's important:** Attackers often exploit known vulnerabilities in outdated browser versions to install malware, steal data, or take control of your system.

### 2. Enforce Secure Connections with HTTPS-Only Mode  
**What it is:** This is a browser setting that forces connections to websites to use the encrypted HTTPS protocol. If a site doesn't support HTTPS, the browser will warn you before connecting or block the connection altogether.

**Why it's important:** An unencrypted HTTP connection lets anyone on the same network, like public Wi-Fi, potentially intercept and read your data, including passwords and personal information.

### 3. Enable Safe Browsing and Phishing Protection  
**What it is:** This is a security feature that checks the sites you visit and the files you download against a regularly updated list of known threats. It will warn you or block access to websites suspected of hosting malware, phishing schemes, or unwanted software.

**Why it's important:** This feature prevents accidentally going to a fraudulent banking site or downloading a virus disguised as a legitimate file. 

### 4. Block Third-Party Cookies and Tracking Content  
**What it is:** This is a privacy setting that stops websites from using cookies and scripts from services you are not directly visiting. While first-party cookies can be useful, like keeping you logged in, third-party cookies are mainly used by advertisers and data brokers to build a profile of your online activity.

**Why it's important:** Blocking third-party trackers improves privacy, reduces targeted advertising, and protects you from malicious scripts that can be delivered through ad networks.

### 5. Restrict Site Permissions  
**What it is:** This allows you to control which websites can access your computer's hardware and sensitive information, such as your microphone, camera, location, and notifications. Browsers typically ask for your permission the first time a site requests access.

**Why it's important:** Unchecked permissions can be abused. A malicious or compromised website could spy on you through your camera, track your location, or spam you with unwanted notifications.


### 6. Block Pop-ups and Malicious Redirects  
**What it is:** This is a default browser feature that prevents websites from opening unexpected new windows or tabs.

**Why it's important:** Pop-ups are often used for phishing attacks and malware delivery. By blocking them, you prevent these.

### 7. Manage Passwords and Autofill Securely  
**What it is:** The browser's built-in password manager and autofill feature store sensitive data. Secure management means using a strong primary password, if available, to protect your stored credentials and being selective about what information the browser saves automatically.

**Why it's important:** If someone gains access to your unlocked computer, they could see all your saved passwords or use autofill to steal your identity or financial information.

### 8. Configure Download Security Settings  
**What it is:** This extends Safe Browsing by focusing on downloaded files. You can set it to automatically scan files for malware and warn you about potentially unwanted programs or files that are not commonly downloaded, which could indicate a threat.

**Why it's important:** Drive-by downloads and Trojan horse files are common ways malware infects a system. This setting adds an important checkpoint, prompting you to think twice before opening a potentially harmful file.

## Practice
Images such as potanic(4 vulns), Titan(2 vulns),DPRK(2 vulns), King Aurthor's castle(2 vulns), Tokyo(2 vulns), Apeture Science(3 vulns), and Kali's image(3 vulns), and PPTH(3 vulns) are some images with Browser Security vulnerabilities(excluding updating browsers)
https://images.cypat.guide#gid=0

___
### STIGs, Benchmarks, and Documentation
- https://workbench.cisecurity.org/benchmarks/8691
- https://workbench.cisecurity.org/benchmarks/18454
- https://workbench.cisecurity.org/benchmarks/18501
- https://stigviewer.com/stigs/google_chrome_current_windows
- https://stigviewer.com/stigs/mozilla_firefox
- https://stigviewer.com/stigs/microsoft_edge
- https://chromeenterprise.google/policies/
- https://mozilla.github.io/policy-templates/
- https://learn.microsoft.com/en-us/deployedge/microsoft-edge-policies