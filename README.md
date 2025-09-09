![AD1](https://github.com/user-attachments/assets/ff0dcd17-a335-40fb-883c-5067b58cde26)
# Active Directory Domain Setup & User Management in Azure

![Azure](https://img.shields.io/badge/Azure-Cloud-blue?logo=microsoft-azure&logoColor=white)
![Windows Server 2022](https://img.shields.io/badge/Windows_Server-2022-0078D6?logo=windows&logoColor=white)
![Windows 10](https://img.shields.io/badge/Windows-10-0078D6?logo=windows&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active_Directory-Domain_Services-008272?logo=windows&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-Scripting-5391FE?logo=powershell&logoColor=white)

---

## Objective
I wanted to practice setting up and managing a full **Active Directory environment in Azure**. This included:
- Creating and configuring a domain controller (DC-1).
- Joining a client machine (Client-1) to the domain.
- Managing users and groups with Organizational Units (OUs).
- Testing authentication, lockouts, account management, and log auditing.

This lab simulates the foundation of real-world enterprise IT environments.

---

## Environment Setup
- **Platform:** Microsoft Azure  
- **Domain Controller:** Windows Server 2022 (DC-1)  
- **Client Machine:** Windows 10 (Client-1)  
- **Credentials:**  
  - Username: `labuser` / Password: `Cyberlab123!`  
  - Created Domain Admin: `jane_admin` / Password: `Cyberlab123!`  

---

## What I Did

### Part 1 – Building the Domain
1. **Created Resource Group, VNet, and Subnet** in Azure.
2. **Deployed DC-1** (Windows Server 2022) and set its IP to static.
3. **Installed Active Directory Domain Services** on DC-1 and promoted it to a new forest: `mydomain.com`.
4. **Created OUs**: `_EMPLOYEES`, `_ADMINS`, `_CLIENTS`.
5. **Created a new Domain Admin (jane_admin)** inside `_ADMINS`.
6. **Joined Client-1** to the domain and moved it into the `_CLIENTS` OU.

---

### Part 2 – Managing Users & RDP Access
1. **Enabled Remote Desktop for domain users** on Client-1.
2. **Created bulk users with PowerShell script** inside `_EMPLOYEES`.
3. **Tested logins** with one of the created user accounts into Client-1.
4. Verified users populated correctly in ADUC.

---

### Part 3 – Account Lockouts & Security Operations
1. **Simulated account lockouts** by entering wrong credentials multiple times.
2. Configured **Group Policy** to lock accounts after 5 failed attempts.
3. **Unlocked and reset passwords** via Active Directory.
4. **Disabled and re-enabled accounts** and observed login behavior.
5. **Observed Security Logs** on both DC-1 and Client-1 to track authentication attempts and failures.

---

## What I Learned
- How to build a functioning **Active Directory environment** in the cloud.
- The importance of **static IPs and DNS configuration** for DC-client communication.
- How **OUs and Group Policies** enforce structure and security.
- How to manage **user accounts, lockouts, and authentication failures**.
- How to leverage **event logs** for basic security operations.

---

## Why This Matters
Active Directory is at the core of enterprise IT. Every IT support, sysadmin, or cybersecurity role interacts with AD daily:
- Helps enforce **security policies**.
- Centralizes **user and machine management**.
- Prepares for more advanced concepts like **Group Policy Objects (GPOs), Kerberos, and security auditing**.

This project built real intuition for **managing a domain from scratch**, which is directly transferable to IT help desk and sysadmin roles.

---

## 📸 Screenshots
- Azure Portal showing both **DC-1 and Client-1** up and running

<img width="1928" height="576" alt="1" src="https://github.com/user-attachments/assets/dfd7d3f5-827b-4d3a-a092-447d124edead" />

- **Active Directory Users and Computers (ADUC)** with `_EMPLOYEES`, `_ADMINS`, `_CLIENTS` OUs 

<img width="321" height="843" alt="1" src="https://github.com/user-attachments/assets/65cf10c2-f9cb-4c96-a585-41ee97701f14" />

- The **jane_admin** account inside `_ADMINS`.

<img width="1240" height="753" alt="2" src="https://github.com/user-attachments/assets/33d94756-94bd-43fa-a463-361766ec72fb" />

- **Client-1 successfully joined** to the domain in ADUC.

<img width="1177" height="692" alt="3" src="https://github.com/user-attachments/assets/19eeacc5-d033-489a-a2d4-ff6cb8c5511d" />

- **PowerShell script output** creating bulk users.

<img width="1851" height="953" alt="2" src="https://github.com/user-attachments/assets/b5748bfe-26c5-4e49-af03-ec598a4b0da8" />

- A **locked-out account** in ADUC.

<img width="1231" height="843" alt="1" src="https://github.com/user-attachments/assets/151c3f73-ece4-4e51-bcb2-9cb4c1ea1a1f" />

- **Security Event Viewer logs** showing failed login attempts and lockouts.

<img width="1698" height="939" alt="3" src="https://github.com/user-attachments/assets/a1219bbf-156c-4820-b425-8f0ff80d3fad" />
