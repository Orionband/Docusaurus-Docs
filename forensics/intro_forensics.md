# Introduction to Forensics
___
Author(s): a_person

Last Updated: 07-29-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
<p>None</p>

</details>

## Note

This article is for easy FQs as well as advice for practicing.

## What are forensics questions?

Forensics Questions are questions that ask about the current system or general information. These can ask you anything from recent CVEs to finding backdoors on the current machine or reversing a binary. These can also include file attachments include, but not limited to: network captures, images, and zip files. They are usually located on the Desktop

## What can I use for extra practice?

CTFs, practice images, and Hack the Box are great for Forensics practice. Here are some websites you can use to practice them:

- https://picoctf.org/
- https://github.com/alphyos/CyberStart-2024
- https://imaginaryctf.org/
- https://images.cypat.guide
- https://www.hackthebox.com/


## Practice!

These are questions more on the researching side, know that there are forensics questions dedicated to the machine rather than researching.

<details>
  <summary><strong>Find the CVEs fixed in Notepad++ v8.5.7</strong></summary>
  <p>
    <strong>Fixed CVEs:</strong> CVE-2023-40031, CVE-2023-40036, CVE-2023-40164, CVE-2023-40166<br />
    <strong>Reference:</strong> 
    <a href="https://notepad-plus-plus.org/downloads/v8.5.7/" target="_blank" rel="noopener">Notepad++ v8.5.7 Release Notes</a>
  </p>
</details>

<details>
  <summary><strong>Decode the encrypted message</strong>: <code>5a 47 39 75 61 32 56 35 49 47 6c 7a 49 47 35 76 64 43 42 7a 61 32 6c 69 61 57 52 70</code></summary>
<p>
  <strong>Decoded:</strong> donkey is not skibidi<br />
  
  You can decode it by decoding from hex, then decoding the result from Base64.
</p>

</details>

<details>
  <summary><strong>What is the PowerShell command to get the hash of a file?</strong></summary>
  <p>
    <strong>Command:</strong> <code>Get-FileHash</code><br />
    <strong>Documentation:</strong> 
    <a href="https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.5" target="_blank" rel="noopener">
      Microsoft Docs - Get-FileHash
    </a>
  </p>
</details>

<details>
  <summary><strong>Publication timestamp (ISO 8601) for CVE-2025-4561</strong></summary>
  <p>
    <strong>Timestamp:</strong> 2025-05-12T06:44:29.959Z<br />
    <strong>Source:</strong> 
    <a href="https://github.com/CVEProject/cvelistV5/blob/main/cves/2025/4xxx/CVE-2025-4561.json" target="_blank" rel="noopener">
      CVE Record on GitHub
    </a>
  </p>
</details>


