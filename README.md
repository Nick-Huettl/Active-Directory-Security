# Active Directory Security (WIP)

## Tools Used

- VMware Workstation (Virtualization)
- Windows Server 2022 (Domain Controller)
- Windows 11 (Domain Workstation)
- Active Directory Domain Services (AD DS)
- Group Policy Management
- Sysmon (Planned)
- Splunk (Planned)

## Objectives

- Build a functional Active Directory (AD) environment
- Deploy and configure a Windows Server 2022 DC
- Join Windows 11 workstation to the domain
- Create a structured Organizational Unit (OU) hierarchy
- Implement security monitoring and hardening strategies to simulate defensive operations

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

Now that the domain controller has been created, I changed the network adapter from Dynamic Host Configuration Protocol (DHCP) to a static IP address.

Domain controllers need static addressing to ensure authentication services, consistent DNS resolution, and reliable domain communications across the environment.

To do this, I needed the DC's IPv4 address, subnet mask, and default gateway.

<img width="1122" height="841" alt="Screenshot 2026-02-25 110153" src="https://github.com/user-attachments/assets/2fbf04d0-28de-4870-9d87-d830d6c7f10e" />

<img width="1124" height="835" alt="Screenshot 2026-02-25 111106" src="https://github.com/user-attachments/assets/914cad86-de08-4a4c-ab9d-f9d6a6384ecf" />

<img width="1144" height="849" alt="Screenshot 2026-02-25 111156" src="https://github.com/user-attachments/assets/3b259d6f-d6a8-4ff9-8f3d-abe6668f1ef6" />

### Good Practice

With the DC now configured, I wanted to create a clean snapshot of the configuration in case I needed to get back to this point. Before this, I also wanted to ensure all necessary Windows updates were installed to avoid having to reinstall them if I ever used this snapshot.

<img width="1123" height="807" alt="Screenshot 2026-02-25 113252" src="https://github.com/user-attachments/assets/2524d23b-0a5b-4e2f-83bd-43fd6dbeb69c" />

<img width="1079" height="825" alt="Screenshot 2026-02-25 114038" src="https://github.com/user-attachments/assets/de11b96e-c964-41e5-8ed1-9102f67cd877" />

### Creating Organizational Units / Users

Next, I created some basic OUs for better structure and organization. Using the default computers and users folder can become unorganized, especially in larger environments with more systems and users.

This will also help with Group Policy Management configurations later on.

I then created a domain admin (Rick), as this will be needed to join the Windows 11 system to the domain later, and an IT user to test log on once it is successfully joined.

<img width="1065" height="795" alt="Screenshot 2026-02-25 115237" src="https://github.com/user-attachments/assets/98363432-cf05-4fde-b4b3-3f2c9f129892" />

<img width="989" height="695" alt="Screenshot 2026-02-25 115328" src="https://github.com/user-attachments/assets/1d9b5632-d040-41bb-9ae7-217ce20a3d81" />

### Windows 11 Configuration

I created a clone of a previous Windows 11 VM I had, reset the PC completely, cleaned the disk, and reinstalled Windows 11 locally.

After the initial setup, I changed the preferred DNS in the network settings on the Windows 11 machine to the IP address of the DC. 

To confirm that everything had changed, I verified connectivity with "ipconfig /all" and pinged the DC to confirm proper DNS resolution and network communication.

<img width="1253" height="868" alt="Screenshot 2026-02-25 132130" src="https://github.com/user-attachments/assets/9ef55018-04d1-42af-a249-8ab425521686" />

<img width="1229" height="861" alt="Screenshot 2026-02-25 132239" src="https://github.com/user-attachments/assets/43b124f7-6836-4270-a4a4-f99b71b0e670" />

Then, to finally join the client system to the domain, I went into the system settings and changed it to a member of the domain.

<img width="1183" height="873" alt="Screenshot 2026-02-25 132654" src="https://github.com/user-attachments/assets/eed5c6bb-04d1-4431-8968-f4ea22fddaeb" />

<img width="1105" height="837" alt="Screenshot 2026-02-25 132833" src="https://github.com/user-attachments/assets/b344e718-87c0-41bb-ba83-0bdab65d960e" />

### Workstation OU Placement

After joining the client to the domain, DESK01 was initially in the default Computers container in the Active Directory Users and Computers.

To support proper Group Policy targeting and structure, I moved the workstation into the dedicated OU created earlier in the lab.

<img width="1059" height="828" alt="Screenshot 2026-02-25 133436" src="https://github.com/user-attachments/assets/93b805ff-99d0-4ed6-918f-8227a387d325" />

<img width="1063" height="829" alt="Screenshot 2026-02-25 133716" src="https://github.com/user-attachments/assets/dec0a9e1-486f-454c-96f9-f92012fc7b7f" />

### Group Policy Security Baseline Deployment

To harden endpoint security, I created a Workstation Security Baseline GPO and linked it to the Workstations OU to ensure consistent security configuration across managed systems.

<img width="1209" height="820" alt="Screenshot 2026-02-26 132814" src="https://github.com/user-attachments/assets/59a4d6b5-3b07-4da9-8d5c-b13a63f9ea31" />

<img width="1028" height="768" alt="Screenshot 2026-02-26 132951" src="https://github.com/user-attachments/assets/7b61ec0f-a77c-4f7a-8edd-439be95b7637" />

### Key Controls Implemented

The baseline focuses on account protection, audit visibility, and endpoint malware defense to strengthen the security posture. These configurations will help to defend against attacks such as brute force attacks, malware, and command-line attacks. Here are some of the controls implemented.
- Password policy
- Account lockout
- Audit logging
- Process creation logging
- Command line auditing
- Windows Defender Antivirus + real time protection
- Disable guest account status

<img width="1027" height="774" alt="Screenshot 2026-02-26 134201" src="https://github.com/user-attachments/assets/dc306bcf-05d4-4303-9b3d-f296e15deffe" />

<img width="1029" height="773" alt="Screenshot 2026-02-26 134440" src="https://github.com/user-attachments/assets/ccb3d3fc-d249-499b-9111-6c3040096886" />

<img width="1214" height="827" alt="Screenshot 2026-02-26 134652" src="https://github.com/user-attachments/assets/553e22e2-9d96-4a31-8f97-52f6cb2480cb" />

<img width="1211" height="821" alt="Screenshot 2026-02-26 134742" src="https://github.com/user-attachments/assets/02051733-2499-4b64-947d-bc245621cd6f" />

<img width="1193" height="825" alt="Screenshot 2026-02-26 134821" src="https://github.com/user-attachments/assets/168ed75b-817c-4347-9441-8c4ca1c6d6b8" />

<img width="1204" height="826" alt="Screenshot 2026-02-26 134853" src="https://github.com/user-attachments/assets/18410b8e-63de-49b2-a9d4-39911441a685" />

<img width="1227" height="829" alt="Screenshot 2026-02-26 135108" src="https://github.com/user-attachments/assets/934113df-25d5-421d-a89e-2540bd716411" />

<img width="1095" height="821" alt="Screenshot 2026-02-27 112020" src="https://github.com/user-attachments/assets/a058fedd-3438-4122-b145-7bcaccedd504" />

<img width="1117" height="840" alt="Screenshot 2026-02-27 105618" src="https://github.com/user-attachments/assets/dd416402-8ce3-4658-81fb-20d03baa25b3" />

<img width="1074" height="794" alt="Screenshot 2026-02-27 104847" src="https://github.com/user-attachments/assets/87c17de2-a5cf-4a41-8e7e-e412daa99390" />

### Verifying Policies are Implemented + Problem that Occurred

When I tried to force the group policy update, I encountered an error that prevented the policy from updating successfully. This problem was caused by a Kerberos time skew between the workstation and the DC, preventing Group Policy from processing correctly.

To fix this, I found that using the "w32tm /resync" command resyncs the workstation to the DC.

<img width="1097" height="812" alt="Screenshot 2026-02-27 102811" src="https://github.com/user-attachments/assets/143a732c-e3b1-4ab2-a233-f953441511d0" />

<img width="1118" height="817" alt="Screenshot 2026-02-27 102957" src="https://github.com/user-attachments/assets/094ff85b-c15f-4464-a759-9a60e079085a" />

After resynchronizing time, I could successfully force a policy refresh and verify using "gpresult /r /scope computer".

I also verified Windows Defender Antivirus was active and using real-time protection.

<img width="1050" height="833" alt="Screenshot 2026-02-27 113402" src="https://github.com/user-attachments/assets/45928aa8-0b41-46d9-b2f2-b80b992bbb04" />

<img width="1118" height="829" alt="Screenshot 2026-02-27 110336" src="https://github.com/user-attachments/assets/5b7144a7-679f-4130-ae44-2fb76316f778" />

<img width="1114" height="840" alt="Screenshot 2026-02-27 110349" src="https://github.com/user-attachments/assets/e0004604-9629-499a-9c3f-ea92a1616e56" />

With the security baseline successfully applied and validated, the environment is ready for endpoint telemetry collection with Sysmon.












