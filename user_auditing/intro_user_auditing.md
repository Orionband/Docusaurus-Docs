# Introduction to User Auditing
___
Author(s): a_person

Last Updated: 07-03-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
- None
</details>

## Concepts
 - Users are the accounts that represent individuals or entities who interact with the operating system. Each user account has its own profile, which includes personalized settings, files, and access permissions. Each User is assigned a unique SID
 - Groups are a collection of user accounts that can be managed as a single unit. Instead of configuring access for each user individually, administrators can assign users to groups, and then assign permissions or roles to the group.
 - There are two main Built in accounts. These are the Administrator account and the Guest account. Both should be disabled.
 - There are also Built-in System accounts, which are accounts used by Windows. Some of the main ones are included below:
     - SYSTEM 
     - LOCAL SERVICE
     - NETWORK SERVICE
     - TrustedInstaller
     - WDAGUtilityAccount

## Tools
 - User auditing can be done in the following applications. Each has its benefits and drawbacks.
    - lusrmgr.msc
    - Control Pannel
    - Settings
    - Command Prompt/Powershell

## Practice
Most basic images contain the content covered in this article. Other images will go beyond this, especially ones with Active Directory:  
https://images.cypat.guide#gid=0

## What is User Auditing?
User auditing is configuring of Authorized Users, Groups, and other settings unique to users. This mainly includes:
1. Disabling the Administrator and Guest accounts
2. Removing Unauthorized users
3. Removing administrator privileges from users
4. Creating Users/Groups if requested by the ReadMe
5. Changing insecure passwords
6. Creating Passwords

## Why do we need to do this?
This is important because of the principle of least privilege, which is only giving a user/group only the privilages that they need, nothing more. For example, if students had administrator privileges, they could potentially bypass filtering software and hack the schools network. User Auditing also contains creating/making strong passwords, which stops attackers from easily gaining access.


## Using each tool


### Disabling the Administrator and Guest accounts
**lusrmgr.msc**  
1. Press `Win + R`, type `lusrmgr.msc`, and press Enter.  
2. Click on **Users**.  
3. Right-click `Administrator` > **Properties**.  
4. Check **Account is disabled**, then click **OK**.  
5. Repeat for the `Guest` account.

**Control Panel**  
Control Panel does not offer a reliable or consistent way to disable these accounts.
**Settings**  
You can't

**Command Prompt / PowerShell**  
```powershell
net user Administrator /active:no
net user Guest /active:no
```


Note that this can also be done through a GPO.

---

### Removing Unauthorized Users

**lusrmgr.msc**  
1. Open **Users**.  
2. Right-click any unauthorized user > **Delete**.

**Control Panel**  
1. Open **User Accounts** > **User Accounts** > **Manage Another Account**.  
2. Click on the User.
3. Click **Delete User**.

**Settings**  
1. Go to **Settings** > **Accounts** > **Other Users**.  
2. Click on the user > **Remove**.

**Command Prompt / PowerShell**  
```powershell
net user username /delete
```
---

### Removing Administrator Privileges from Users

**lusrmgr.msc**  
1. Go to **Groups** > Double-click **Administrators**.  
2. Select user > **Remove**.

**Control Panel**  
1. Open **User Accounts** > **User Accounts** > **Manage Another Account**.  
2. Click on the User.
3. Click **Change Account Type**. It will automatically select standard if it is an Admin
4. Click the **Change Account Type** to finalize.

**Settings**  
1. Go to **Settings** > **Accounts** > **Other Users**.  
2. Click the user > **Change account type** > **Standard User**.

**Command Prompt / PowerShell**  
```powershell
net localgroup Administrators username /delete
```

---

### Creating Users/Groups if Requested by the ReadMe

**lusrmgr.msc**  
1. Right-click **Users** > **New User**.  
2. Fill out details and click **Create**.  
3. For groups: Right-click **Groups** > **New Group**.

**Control Panel**  
1. Open **User Accounts** > **User Accounts** > **Manage Another Account**.  
2. Click **Add new user in settings**

Don't use control pannel to create a group

**Settings**  
1. Go to **Settings** > **Accounts** > **Other Users** > **Add someone else to this PC**.
2. When you get prompted for a microsoft account, just click **I don't have this person's sign-in information**, then **I don't have this person's sign-in information**

Don't use settings to create a group

**Command Prompt / PowerShell**  
```powershell
net user newusername newpassword /add
net localgroup groupname /add
net localgroup groupname username /add
```
---

### Changing Insecure Passwords

**lusrmgr.msc**  
1. Right-click on a user > **Set Password**.
2. Enter a secure new password.

**Control Panel**  
1. Open **User Accounts** > **User Accounts** > **Manage Another Account**.  
2. Click the user
3. Click "Change Password"

**Settings**  
*Not available for local users.*

**Command Prompt / PowerShell**  
```powershell
net user username newsecurepassword
```
---

### Creating Passwords
Note: Control Pannel will show you if someone has a password or not. If an account has "Password Protected", that means that they have a password.

**lusrmgr.msc**  
1. Right-click on a user > **Set Password**.
2. Enter a secure new password.

**Control Panel**  
1. Open **User Accounts** > **User Accounts** > **Manage Another Account**.  
2. Click the user
3. Click "Create a Password"

**Settings**  

Don't do it. It will make you create security questions.

**Command Prompt / PowerShell** 
```powershell
net user username password
```

## Practice
Most basic images contain the content covered in this article. Other images will go beyond this, especially ones with Active Directory:  
https://images.cypat.guide#gid=0
___
### References & Further Reading
- https://www.lastpass.com/features/password-generator
- https://support.microsoft.com/en-us/windows/manage-user-accounts-in-windows-104dc19f-6430-4b49-6a2b-e4dbd1dcdf32
- https://support.microsoft.com/en-us/windows/change-or-reset-your-password-in-windows-8271d17c-9f9e-443f-835a-8318c8f68b9c
- https://learn.microsoft.com/en-us/windows/security/identity-protection/access-control/local-accounts
