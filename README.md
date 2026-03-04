<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Account Management</h1>
This repository demonstrates various use cases and examples for managing user accounts in Active Directory (AD). It provides step-by-step instructions on common tasks, such as account lockouts, password resets, account enabling/disabling, and log observations.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Use Cases</h2>

- Account Lockouts
  - How to configure account lockout policies via Group Policy.
  - Simulating account lockouts by attempting multiple failed login attempts.
  - Unlocking a locked account and resetting the password.

- Enabling and Disabling Accounts
  - Disabling and enabling a user account within Active Directory.
  - Observing the behavior and error messages when attempting to log in with a disabled account.

- Log Observations
  - How to observe and analyze security logs from both the Domain Controller and client machine.
  - Identifying failed login attempts, account lockouts, and other relevant events in the logs.

<h2>Instructions</h2>

**1. Getting Started**

- Log in to the Domain Controller (dc-1) using an administrator account.
- Ensure you have a user account created in Active Directory for testing purposes.

**2. Configuring Account Lockout Policies**

- Open the Group Policy Management Console (GPMC) and configure the Account Lockout Policy to lock the account after 5 failed login attempts.
- Test by attempting 6 failed logins with a bad password.

<img width="448" alt="Screenshot 2025-01-23 at 6 43 36 PM" src="https://github.com/user-attachments/assets/0d424068-0be0-4580-be80-cc4abc554b0e" />
<img width="395" alt="Screenshot 2025-01-23 at 6 45 12 PM" src="https://github.com/user-attachments/assets/f105c6d8-ae9c-4703-82d6-1704a238d0be" />
<img width="791" alt="Screenshot 2025-01-23 at 6 45 33 PM" src="https://github.com/user-attachments/assets/32bc91e8-8b5f-4fbb-98a2-6ef4ea6ad1b1" />
<img width="859" alt="Screenshot 2025-01-23 at 6 46 31 PM" src="https://github.com/user-attachments/assets/8e1203c0-dcf7-4c9a-b53a-89bbf340de0f" />
<img width="436" alt="Screenshot 2025-01-23 at 6 47 23 PM" src="https://github.com/user-attachments/assets/9572d678-b0b3-433c-b281-fcb3735a1cbb" />


**3. Account Lockout Behavior** 

- Observe that the account locks after the 5th failed attempt.
- Unlock the account and reset the password for testing.

<img width="527" alt="Screenshot 2025-01-23 at 6 47 37 PM" src="https://github.com/user-attachments/assets/1ab65701-9f50-43eb-b3fd-555272c876d7" />
<img width="419" alt="Screenshot 2025-01-23 at 6 48 22 PM" src="https://github.com/user-attachments/assets/5e8c41e6-70cd-475a-86f4-ff9ad1967d42" />
<img width="931" alt="Screenshot 2025-01-23 at 6 48 37 PM" src="https://github.com/user-attachments/assets/8ced3e12-bd2c-4a9f-ab8f-54e3f632ea6f" />
<img width="417" alt="Screenshot 2025-01-23 at 6 48 45 PM" src="https://github.com/user-attachments/assets/7daf1604-4a14-4659-bb9d-5d195026e2cc" />
<img width="425" alt="Screenshot 2025-01-23 at 6 49 20 PM" src="https://github.com/user-attachments/assets/00a1e4a6-5db1-49d4-b26b-42242882fce2" />
<img width="500" alt="Screenshot 2025-01-23 at 6 51 14 PM" src="https://github.com/user-attachments/assets/d0d1b6bf-c632-4152-a644-ddb9e9fcd43b" />
<img width="387" alt="Screenshot 2025-01-23 at 6 51 20 PM" src="https://github.com/user-attachments/assets/4d8c71f1-3a68-4324-b062-68393155958a" />


**4. Enabling and Disabling Accounts**

- Disable a user account in Active Directory.
- Attempt to log in with the disabled account and observe the error message.
- Re-enable the account and attempt to log in again.

<img width="503" alt="Screenshot 2025-01-23 at 6 51 51 PM" src="https://github.com/user-attachments/assets/45750d32-a894-49a1-945e-b9a65adeff5e" />
<img width="392" alt="Screenshot 2025-01-23 at 7 41 45 PM" src="https://github.com/user-attachments/assets/a0a34457-eabc-463c-be6c-5b3d01e7ca2d" />
<img width="543" alt="Screenshot 2025-01-23 at 6 52 54 PM" src="https://github.com/user-attachments/assets/49d4c42e-20c9-4d65-bf21-5663d64f6da7" />


  
**5. Observing Logs**

- View the security logs on the Domain Controller to see the details of login attempts and account lockouts.
- Check the client machine’s event logs for any relevant information regarding login failures.

<img width="432" alt="Screenshot 2025-01-23 at 7 42 02 PM" src="https://github.com/user-attachments/assets/963d4b20-c8b6-45da-9095-8abe250660c2" />
<img width="1402" alt="Screenshot 2025-01-23 at 7 42 24 PM" src="https://github.com/user-attachments/assets/bca6d2a0-a992-4414-8e3d-54c34ecea5f2" />

<h2>Purpose</h2>
The purpose of this repository is to provide hands-on examples and insights into managing Active Directory accounts. It highlights practical scenarios that demonstrate how to configure policies, manage account states, and troubleshoot login issues using various tools and technologies. This repository is designed to help IT professionals and system administrators gain a deeper understanding of Active Directory management.
