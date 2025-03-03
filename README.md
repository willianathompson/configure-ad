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
<h4>Active Directory Domain Services Installed on Windows Server</h4>



![image](https://github.com/user-attachments/assets/82f5b9b3-5704-4012-8e62-939b90ed2f0c)


Add the Active Directory Domain Services (AD DS) role to the Windows Server 2022 VM using Server Manager.

![image](https://github.com/user-attachments/assets/41268788-e34a-4630-9d5f-34dff5768552)

Install the AD DS role on the server.

![image](https://github.com/user-attachments/assets/cb4a2082-0350-413b-a9fa-5cb4587cf07c)

Promote the server to a Domain Controller by selecting "Promote this server to a domain controller."

![image](https://github.com/user-attachments/assets/e873a841-e9dc-435f-b775-8faa1d502c97)

Add a new forest and specify the domain name (e.g., mydomain.com).

![image](https://github.com/user-attachments/assets/4fffae21-eb50-4801-b13f-81d94f9b08d4)

Provide the Domain Admin credentials during the promotion process.

![image](https://github.com/user-attachments/assets/6b95c2e1-c5ad-458e-bc12-dc0f256dd50f)

Install the Domain Controller (DC) role and complete the configuration. After the server restarts, the Domain Admin credentials are set up successfully.
</p>
<p>


</p>
<br />

<p>
<h4>Windows 10 VM Joined to the Domain</h4>


![image](https://github.com/user-attachments/assets/9c63196b-6db1-4628-997b-11a5bd618f74)

Change the DNS settings on the Windows 10 (client) VM to point to the domain controller using the server's VNet private IP, then restart the VM.

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


To join the Windows 10 VM to the Domain, right-click This PC, select Properties, and click Change settings next to the computer name. In the System Properties window, click Change, select Domain, and enter the domain name (e.g., example.com). Enter domain admin credentials when prompted, click OK, and restart the VM. After the restart, the Windows 10 VM will be part of the domain.








</p>
<p>

  
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
<h>Domain Membership and Connectivity Verified</h> 

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
