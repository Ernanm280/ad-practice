<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Account Management</h1>
This repository showcases hands-on experience managing user accounts within Active Directory (AD) through practical, real-world administrative tasks. It includes step-by-step implementations of essential account management functions such as password resets, account lockout resolution, enabling/disabling users, and monitoring authentication activity.<br />


<h2>Environments and Technologies Used</h2>

<img src="https://skillicons.dev/icons?i=azure,windows,powershell" />

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Use Cases</h2>

### Account Lockout Policy

* Configure **Account Lockout Policies** through **Group Policy Management**.
* Simulate an account lockout by entering an incorrect password multiple times on the client machine.
* Verify the lockout event from the **Domain Controller**.
* Unlock the affected user account and reset the password using **Active Directory Users and Computers (ADUC)**.

### Enabling and Disabling User Accounts

* Disable a user account through **Active Directory Users and Computers (ADUC)**.
* Attempt to log in from the client machine using the disabled account.
* Observe the authentication error message.
* Re-enable the account and confirm successful login.

### Security Log Monitoring

* Access **Event Viewer → Windows Logs → Security** on both the **Domain Controller** and **Client VM**.
* Analyze log entries related to authentication events.
* Identify events such as:

  * Failed login attempts
  * Account lockouts
  * Successful login activity
* Use these logs to understand how Active Directory records and tracks authentication behavior.

> [!NOTE] 
> This project builds upon a prior lab where the Azure environment, virtual machines, Active Directory Domain Services, and DNS configuration were initially deployed. <br /> [Step 2: Active Directory: Deploying Active Directory](https://github.com/Ernanm280/deploying-ad)

<h2>Instructions</h2>

**1. Getting Started**

I begin by logging in to the DC-1 VM (Domain Controller) using an administrator account. Verify that a test user account exists in Active Directory, as this account will be used to simulate login attempts and observe account lockout behavior.

**2. Configuring Account Lockout Policies**

Once logged in, I opened the `Group Policy Management Console (GPMC)` on the Domain Controller, navigated to **mydomain.com**, expanded the domain tree, selected → **Default Domain Policy**, then right-clicked and selected **Edit**. In the **Group Policy Management Editor** section, I navigated to **Computer Configuration** → **Policies** → **Windows Settings** → **Security Settings** → **Account Policies** → **Account Lockout Policy**, where I configured the account lockout threshold to trigger after **5** failed login attempts, helping defend against repeated unauthorized access attempts.

<img width="629" height="422" alt="Screenshot 2026-04-11 193047" src="https://github.com/user-attachments/assets/d295abd8-f351-49f4-8bd5-f427fbb490b8" />
<img width="675" height="488" alt="Screenshot 2026-04-11 193303" src="https://github.com/user-attachments/assets/357f467e-ec49-4b86-95c5-4c7adc25577d" />

<br>
<br>

**3. Account Lockout Behavior** 

Returning to the **Client-1** VM, I try to trigger an account lockout by intentionally entering incorrect credentials for testing purposes. I select one of the newly created users in the _EMPLOYEES organizational unit and try to log in using Remote Desktop. After five consecutive failed login attempts, the account is locked in accordance with the configured policy.

<img width="695" height="604" alt="Screenshot 2026-04-11 194004" src="https://github.com/user-attachments/assets/9b6351af-43b0-499e-9851-4f70819a5b38" />

<br>
<br>

The account can be unlocked through `Active Directory Users and Computers (ADUC)`, and the password can be reset if needed to continue testing. I opened **Active Directory Users and Computers**, navigated to the **_EMPLOYEES** folder under **mydomain.com**, and located the user account. After opening the account properties, I checked the **Unlock Account** option following the failed login attempts, then selected **OK** to close the window. I then right-clicked the user and chose **“Reset Password.”** This option allows both unlocking the account and resetting the password simultaneously; however, in this case, it was demonstrated without applying any changes.

<img width="884" height="789" alt="Screenshot 2026-04-11 194311" src="https://github.com/user-attachments/assets/a2b0f3c6-0f7d-4aea-b7f5-11af5792b5b7" />

<br>
<br>

To verify that the account has been unlocked or accessible, I logged back in using the test user's credentials. I opened **PowerShell** and executed the `whoami` command to verify the currently logged-in user, confirming the account is authenticated within the domain.

<img width="711" height="341" alt="Screenshot 2026-04-11 195201" src="https://github.com/user-attachments/assets/ab34b59f-0b91-4299-a58e-1834e52c1f1a" />

<br>
<br>

**4. Enabling and Disabling Accounts**

This exercise demonstrates how administrators control user access within Active Directory. A user account is first disabled in `Active Directory Users and Computers (ADUC)`. Returning to the Domain Controller (DC-1), I right-clicked the user account and selected **Disable Account** to prevent the user from logging into the domain.

<img width="635" height="356" alt="Screenshot 2026-04-11 195251" src="https://github.com/user-attachments/assets/9afa49dd-c6b4-4e0b-9015-22b8f83b525c" />

<br>
<br> 

When attempting to sign in to the test user account (Client-1) using Remote Desktop, an error message confirmed that the account was disabled, preventing access to the system.

<img width="663" height="439" alt="Screenshot 2026-04-11 195401" src="https://github.com/user-attachments/assets/09b50edb-5030-47f5-a93e-2acd155cd4b1" />

<br>
<br>

As the Domain Controller, I then re-enabled the user account in **Active Directory Users and Computers** by right-clicking the account and selecting **Enable Account**, restoring access to the domain. Another login attempt is performed to verify that access has been successfully restored.

<img width="580" height="378" alt="Screenshot 2026-04-11 195521" src="https://github.com/user-attachments/assets/f1697fdf-8445-4b98-9598-211c10139bab" />

<br>
<br>

**5. Observing Logs**

This step involves reviewing authentication activity through system logs. On the Domain Controller, I navigated to
Event Viewer → Windows Logs → Security, where authentication events are recorded and audited. 

Using **Event Viewer** on the Domain Controller, I analyzed Security logs to track authentication events. Repeated failed login attempts were logged under Event ID 4776 (Credential Validation), providing visibility into invalid credential usage and reinforcing the importance of monitoring authentication activity in a domain environment. The **Security logs** on the **Domain Controller** are examined to identify events related to login attempts and account lockouts.

<img width="771" height="557" alt="Screenshot 2026-04-11 200025" src="https://github.com/user-attachments/assets/ca8eafc4-a1a3-4ef0-a1c8-3e75af574c66" />

Note: In a production environment, monitoring these events is essential for identifying suspicious activity, supporting incident response, and maintaining overall domain security.

<h2>Purpose</h2>
The purpose of this repository is to provide hands-on examples and insights into managing Active Directory accounts. It highlights practical scenarios that demonstrate how to configure policies, manage account states, and troubleshoot login issues using various tools and technologies. This repository is designed to help IT professionals and system administrators gain a deeper understanding of Active Directory management.
