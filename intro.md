# **CyberPatriot Introduction**

**CyberPatriot** is a national K–12 youth cyber education program in the United States, created by the Air Force Association. Its goal is to guide students toward careers in cybersecurity and other STEM (science, technology, engineering, and mathematics) fields. The program's centerpiece is the **National Youth Cyber Defense Competition**, which culminates in an in-person **National Finals Competition** for top-performing high school and middle school teams.

---

## **Competition Rounds**

### **Practice rounds**
- Open to all participants 
- Very basic images. Similar or a bit less as R1 and R2 in difficulty.


### **Round 1**
- Open to all participants except the Middle School Division.  
- Beginner-level virtual machine images.

### **Round 2**
- Open to all divisions.  
- Intermediate-level images.

### **State Round**
- All teams compete using intermediate to advanced images.  
- Based on performance in Rounds 1 and 2, teams are placed into one of three tiers:
  - **Platinum**
  - **Gold**
  - **Silver**  
- Tiers apply across all divisions: **All Service**, **Open**, and **Middle School**.

### **Semifinals**
- Only the top 25% of each tier (plus wildcard teams) advance.  
- Advanced-level images are used.

### **National Finals**
- Top teams from each division qualify.  
- Features advanced images and the presence of a **Red Team** (offensive security team).

---

## **Vulnerability Categories**

Each virtual machine (VM) contains vulnerabilities grouped into categories. This guide focuses on these categories:

- **Account Policies**  
  Password and lockout policies.

- **Application Security Settings**  
  Critical services, required settings, and permissions.

- **Application Updates**  
  Update status and automatic update configurations.

- **Defensive Countermeasures**  
  Firewalls, antivirus software, encryption, etc.

- **Forensic Questions**  
  Scenario-based questions assessing investigative skills.

- **Local Policies**  
  Audit policies, user rights assignments, and security options (e.g., network security, privilege elevation).

- **Operating System Updates**  
  Windows updates, service packs, and automatic update settings.

- **Policy Violation: Malware**  
  Includes backdoors, remote admin tools, keyloggers, sniffers, etc.

- **Policy Violation: Prohibited Files**  
  Unauthorized software archives, confidential files, etc.

- **Policy Violation: Unwanted Software**  
  Games, scareware, adware, PUPs, hacking tools, etc.

- **Service Auditing**  
  Enable/disable services.

- **Uncategorized OS Settings**  
  Remote access, file sharing, screen locking, group policy settings, OS permissions, etc.

- **User Auditing**  
  Authorized users, groups, and user-specific settings.

---

## **Main Challenges**

The primary challenges include **Windows**, **Windows Server**, **Linux**, and **Cisco**. This guide groups Windows and Windows Server together due to their similarities. Semifinals introduce additional challenges such as the **Boeing** and **Web-based Challenges**.

Unofficial practice images are available for preparation [here](https://images.cypat.guide).

---

## Common Mistakes in CyberPatriot
Many people fall into the  “Gotta Catch ‘em all!” mindset as akshay put this. Some of these people just try to get all the points they can; they don't focous on the *why* and what they are actually doing. This is obviously dangerous as in the end, you will never learn anything in cybersecurity.

Many people do not know that they are breaking the rules and cheating in CyberPatriot, as they have not read the rule book or have been informed about it. Main rules and misconceptions as the rules themselves can be found **[here](/guide/docs/rules)**. If you cheat in CyberPatriot, you will again, never learn anything and you will just harmful to the community.

---

## Research
CyberPatriot is a very research heavy competition, and it is vital to be able to research effectively. You will never know everything there is to know, and you will always have to research. 

## **Tips**

More information and helpful tips can be found on Akshay’s blog:  
https://akshayrohatgi.com/blog/posts/How-To-Win-CyberPatriot/
## FAQ
<details>
<summary>Where can I find the practice image spreadsheet?</summary>

https://images.cypat.guide
</details>

<details>
<summary>What can I do to practice for the competition?</summary>

Playing CTFs, doing practice images, and doing research are some main ways to get more proficient. There are also similar competitions, such as eCitadel.

</details>

<details>
<summary>How do I open a virtual image?</summary>

1. Download zip file
2. Unzip
3. Enter password if any
4. Open Vmware
5. File > Open
6. Go inside folder
7. Click .vmx file
8. Power on

</details>
<details>
<summary>What is the current competition schedule and challanges?</summary>

https://www.uscyberpatriot.org/competition/current-competition/competition-schedule

https://www.uscyberpatriot.org/competition/current-competition/challenges-by-round
</details>
<details>
<summary>Am I allowed to take virtual image snapshots?</summary>

Yes. According to section 3012E, "Using image snapshots or similar capabilities is allowed during the competition. Snapshots include host system file copy mechanisms to create a backup copy of an image. Snapshots or backups may be used to roll back to a previously known good state. If the competition image becomes corrupted or unusable, snapshots are an acceptable way of attempting to recover the competition image.

</details>

<details>
<summary>Why am I seeing an Overtime Penalty?</summary>

A team’s 4-hour competition window begins the moment they open the first virtual image in VMware. If you open an image before your planned competition time, your time begins. If you re-open the image later, you’ll see on the scoring report that the clock has been running, and your four hours may already be expired.

</details>

<details>
<summary>What is a multiple instance penalty?</summary>

During a competition round, no more than a single copy of the same virtual image may be opened at the same time. For example, if you are running the Windows 10 images on Computer 1 you cannot open a second copy of the Windows 10 image on Computer 2 or 3.

</details>

<details>
<summary>There is an issue with my score. Who should I contact?</summary>

Score Correction Requests will only be accepted via the official Score Correction Request Form. The Score Correction Request Form allows coaches to self-report scoring discrepancies or issues during and immediately after the competition (until 11:59 PM ET on the last the day the round ends – Late requests are NOT accepted). Please do not email the CyberPatriot Program Office with documentation unless requested.

Once the score correction requests are reviewed, coaches will receive an email with the preliminary scores. The email provides information about the Preliminary Score Discrepancy Form​, which is the last opportunity for coaches to request changes to their scores before the scores are finalized and made official. Technical issues and scoring issues such as not recieving points for a fix, image crashes, etc. will not be considered in the Preliminary Score Discrepancy Report form.

</details>

<details>
<summary>When / where are final scores published?</summary>

Final scores are published on www.uscyberpatriot.org under Competition > Current Competition > Scores. It takes 7-10 business days after the end of the round for scores to be published. Coaches will be notified once the final scores are posted. Until then, please refrain from contacting us about when scores will be available.

</details>
<details>
<summary>How do I access official training/round images and the netacad course?</summary>

Your coach will provide you with these material. **DO NOT ASK OTHERS FOR THESE.**


</details>

## References
- https://en.m.wikipedia.org/wiki/CyberPatriot
- https://www.uscyberpatriot.org/Pages/Competition/FAQ.aspx
