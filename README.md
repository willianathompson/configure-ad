<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Azure Virtural Machines
- Active Directory Domain Services Installed on Windows Server
- Windows 10 VM Joined to the Domain
- Domain Membership and Connectivity Verified
- Users and Group Policies Configured

<h2>Deployment and Configuration Steps</h2>

<p>
<h4>Create Azure Virtural Machines</h4>

![image](https://github.com/user-attachments/assets/8b239299-f7ac-4348-902e-e3cbd1d6ed9a)

Deploy an Azure VM running Windows Server 2022 to host Active Directory Domain Services, configuring the VM's size, region, and networking settings with a public IP and RDP access for remote connection. The server’s private IP address is set to static.

![image](https://github.com/user-attachments/assets/eea8af42-6473-4bea-843c-564b83252a1c)

Deploy a second VM running Windows 10 (22H2) to join the domain. Ensure the VM size, regions, and networking are configured, as it will also need RDP remote access.

![image](https://github.com/user-attachments/assets/15e43c64-b58d-47a2-a226-a66067c63042)

Disable the firewall for both VMs through Windows Defender Firewall to allow for connectivity testing.
</p>
<p>


</p>
<br />

<p>

![image](https://github.com/user-attachments/assets/41268788-e34a-4630-9d5f-34dff5768552)
![image](https://github.com/user-attachments/assets/cb4a2082-0350-413b-a9fa-5cb4587cf07c)
![image](https://github.com/user-attachments/assets/e873a841-e9dc-435f-b775-8faa1d502c97)


</p>
<p>
  
The Active Directory Domain Services (AD DS) role was installed on the Windows Server 2022 VM. Using Server Manager, the server was set up as a Domain Controller, and a new domain called mydomain.com was created. After restarting the server, the Domain Admin credentials were set up successfully.
  
</p>
<br />

<p>
  

![image](https://github.com/user-attachments/assets/2ab53e69-0d4d-4983-a306-0a36bf611175)
![image](https://github.com/user-attachments/assets/98f43f6d-8b5f-4a8b-973d-842b0800271d)  

</p>
<p>
The Windows 10 (22H2) VM was connected to the domain by accessing Control Panel and joining the domain (mydomain.com). The necessary Domain Admin credentials were entered, and after restarting the VM, users could log in using domain credentials.
</p>
<br />
<p>


![image](https://github.com/user-attachments/assets/41905e10-11ca-4502-9986-e3f5aa166a62)
![image](https://github.com/user-attachments/assets/811533a0-c2b5-4286-8371-989ce0418801)

</p>
<p>
Domain membership was verified by logging into the Windows 10 VM using the domain credentials, and pinging the domain from both the Windows Server 2022 and Windows 10 VMs confirmed proper connectivity between the domain controller and the client machine.
</p>
<br />

<p>

![image](https://github.com/user-attachments/assets/c4467ae6-1ed0-4a0e-9a09-1cac174643d9)
![image](https://github.com/user-attachments/assets/2119f041-b2d0-49cb-8b86-252a8c2a7d4e)

![image](https://github.com/user-attachments/assets/cbc0fe6e-de00-4bb5-94d7-e2bdf68781fc)
![image](https://github.com/user-attachments/assets/d45d00df-dbde-47d5-8120-5b6e789e0ff0)

</p>
<p>
</p>

![image](https://github.com/user-attachments/assets/6fbac9ba-07b6-41bb-a162-d3f093faea90)
![image](https://github.com/user-attachments/assets/fee21f53-6e96-4372-a06a-724cfb03d8b3)

</p>
<p>
</p>

![image](https://github.com/user-attachments/assets/ac0adf43-079b-4767-80d5-6c26f4310d94)

</p>
<p>

Users and groups were created and managed on the Windows Server 2022 VM using Active Directory Users and Computers. Group Policy Management was set up to create domain-wide policies, like password rules and account lockout settings, to make sure security was the same across the entire domain.

This setup successfully created a working On-premises Active Directory in Azure using Windows Server 2022 and Windows 10 (22H2), with domain management done efficiently through PowerShell and Remote Desktop.

</p>
<br />
