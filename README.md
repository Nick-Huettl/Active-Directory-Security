# Active Directory Security (WIP)

## Tools Used

- VMware Workstation (virtualization)
- Windows Server 2022 (Domain Controller) / Windows 11 (domain workstation)
- Active Directory Domain Services (AD DS)
- Group Policy Management (Planned)
- Sysmon (Planned)
- Splunk (Planned)

## Objectives

- Build a functional Active Directory (AD) environment
- Deploy and configure a Windows Server 2022 DC
- Join Windows 11 workstation to the domain
- Create a structured Organizational Unit (OU) hierarchy
- Implement security monitoring and hardening strategies for a more secure environment

### Windows Server 2022 VM Setup

The first step of this lab involved a Windows Server 2022 virtual machine (VM) in VMware Workstation to serve as the domain controller.

This was accomplished by downloading the Windows Server ISO file to create the VM with appropriate resources for the lab environment.

The screenshots below show some of the configuration steps and the successful installation.

<img width="1011" height="795" alt="Screenshot 2026-02-24 145627" src="https://github.com/user-attachments/assets/fac3cb0e-0187-4019-9e9b-98a6813d0083" />

<img width="1013" height="809" alt="Screenshot 2026-02-24 145743" src="https://github.com/user-attachments/assets/0b065166-9887-4e88-94f7-e14af52e5102" />

<img width="1292" height="843" alt="Screenshot 2026-02-24 145927" src="https://github.com/user-attachments/assets/79eed8f6-6d41-4383-913e-8615b65254b6" />

After the initial boot, I renamed the server to "DC01" to clearly identify its role as the main domain controller. 

<img width="1274" height="853" alt="Screenshot 2026-02-24 150441" src="https://github.com/user-attachments/assets/d611a26d-aadb-4475-919e-73549abe3234" />

### Installing AD DS & Promoting Server to DC

Next, I installed Active Directory Domain Services (AD DS) through the Server Manager. The server was then promoted to a domain controller for the new domain.

This helps to centralize identity management, which is critical for authentication and authorization.

<img width="1022" height="813" alt="Screenshot 2026-02-24 150945" src="https://github.com/user-attachments/assets/f858e8bc-b9b4-4ba6-a956-1426b3202dd2" />

<img width="1026" height="800" alt="Screenshot 2026-02-24 151016" src="https://github.com/user-attachments/assets/071cddf1-7a3d-4c66-a8c7-632ff8570d71" />

<img width="781" height="548" alt="Screenshot 2026-02-24 151145" src="https://github.com/user-attachments/assets/b0b50e00-4bfb-4922-96c7-996a1ac91ebd" />

<img width="757" height="558" alt="Screenshot 2026-02-24 151323" src="https://github.com/user-attachments/assets/b07ba257-73df-4b61-8a2f-84b8a2dffc15" />

<img width="1024" height="819" alt="Screenshot 2026-02-24 152850" src="https://github.com/user-attachments/assets/cab9ff0e-9923-4298-b772-a346bd376e54" />

### DC Configurations















