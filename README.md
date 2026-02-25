# Active Directory Security (WIP)

## Tools Used

- VMware Workstation - Windows Server 2022 / Windows 11
-

## Objectives

- Create a VM for Windows Server and a Windows 11 machine
- Create a domain controller using the Windows Server VM
- Connect the Windows 11 machine to the DC
- 

### Windows Server 2022 VM Setup

The first step in this lab was to download the Windows Server 2022 ISO file and create a VM.

Screenshots below show some of the settings used for setup and install completion.

<img width="1011" height="795" alt="Screenshot 2026-02-24 145627" src="https://github.com/user-attachments/assets/fac3cb0e-0187-4019-9e9b-98a6813d0083" />

<img width="1013" height="809" alt="Screenshot 2026-02-24 145743" src="https://github.com/user-attachments/assets/0b065166-9887-4e88-94f7-e14af52e5102" />

<img width="1292" height="843" alt="Screenshot 2026-02-24 145927" src="https://github.com/user-attachments/assets/79eed8f6-6d41-4383-913e-8615b65254b6" />

After the first bootup, I decided to rename the PC to "DC01" for easy identification, as it will eventually act as the domain controller. 

<img width="1274" height="853" alt="Screenshot 2026-02-24 150441" src="https://github.com/user-attachments/assets/d611a26d-aadb-4475-919e-73549abe3234" />

### Installing AD DS & Promoting Server to DC

After a restart to confirm the change, I moved to the Server Manager to install Active Directory Domain Services and promote the server to a domain controller.

<img width="1022" height="813" alt="Screenshot 2026-02-24 150945" src="https://github.com/user-attachments/assets/f858e8bc-b9b4-4ba6-a956-1426b3202dd2" />

<img width="1026" height="800" alt="Screenshot 2026-02-24 151016" src="https://github.com/user-attachments/assets/071cddf1-7a3d-4c66-a8c7-632ff8570d71" />

<img width="781" height="548" alt="Screenshot 2026-02-24 151145" src="https://github.com/user-attachments/assets/b0b50e00-4bfb-4922-96c7-996a1ac91ebd" />

<img width="757" height="558" alt="Screenshot 2026-02-24 151323" src="https://github.com/user-attachments/assets/b07ba257-73df-4b61-8a2f-84b8a2dffc15" />

<img width="1024" height="819" alt="Screenshot 2026-02-24 152850" src="https://github.com/user-attachments/assets/cab9ff0e-9923-4298-b772-a346bd376e54" />

### DC Configurations















