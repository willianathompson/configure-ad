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
- Domain Membership and Connectivity Verified
- Windows 10 VM Joined to the Domain
- Users and Group Policies Configured

<h2>Deployment and Configuration Steps</h2>

<p>
<h4>Create Azure Virtural Machines</h4>

![image](https://github.com/user-attachments/assets/8b239299-f7ac-4348-902e-e3cbd1d6ed9a)

</p>
<p>
Deploy an Azure VM running Windows Server 2022 (DC-1) to host Active Directory Domain Services, configuring the VM's size, region, and networking settings with a public IP and RDP access for remote connection. The server’s private IP address is set to static.
</p>
<p>

![image](https://github.com/user-attachments/assets/eea8af42-6473-4bea-843c-564b83252a1c)

</p>
<p>
Deploy a second VM running Windows 10 (22H2) (Client-1) to join the domain. Ensure the VM size, regions, and networking are configured, as it will also need RDP remote access.
</p>
<p>



![image](https://github.com/user-attachments/assets/15e43c64-b58d-47a2-a226-a66067c63042)

</p>
<p>
Disable the firewall for the DC-1 VM through Windows Defender Firewall to allow for connectivity testing.
</p>
<p>


</p>
<br />

<p>
<h4>Active Directory Domain Services Installed on Windows Server</h4>

![image](https://github.com/user-attachments/assets/82f5b9b3-5704-4012-8e62-939b90ed2f0c)

</p>
<p>
Add the Active Directory Domain Services (AD DS) role to the DC-1 VM using Server Manager.
</p>
<p>

![image](https://github.com/user-attachments/assets/41268788-e34a-4630-9d5f-34dff5768552)

</p>
<p>
Install the AD DS role on the server.
</p>
<p>

![image](https://github.com/user-attachments/assets/cb4a2082-0350-413b-a9fa-5cb4587cf07c)

</p>
<p>
Promote the server to a Domain Controller by selecting "Promote this server to a domain controller."
</p>
<p>

![image](https://github.com/user-attachments/assets/e873a841-e9dc-435f-b775-8faa1d502c97)

</p>
<p>
Add a new forest and specify the domain name (e.g., mydomain.com).
</p>
<p>

![image](https://github.com/user-attachments/assets/4fffae21-eb50-4801-b13f-81d94f9b08d4)

</p>
<p>
Provide the Domain credentials (labuser) during the promotion process.
</p>
<p>
  
![image](https://github.com/user-attachments/assets/6b95c2e1-c5ad-458e-bc12-dc0f256dd50f)

</p>
<p>
Install the Domain Controller (DC) role and complete the configuration. After the server restarts, the Domain credentials are set up successfully.
</p>
<p>


</p>
<br />

<p>
<h4>Domain Membership and Connectivity Verified</h4>

![image](https://github.com/user-attachments/assets/61480065-cd96-4a0c-992a-50089eebac00)

</p>
<p>
The necessary Domain credentials are entered, and after restarting the VM, users can log in using domain credentials (mydomain.com\labuser).
</p>
<p>

![image](https://github.com/user-attachments/assets/32353a93-c307-40d5-9cf9-08f148578a9b)

</p>
<p>
Open Active Directory Users and Computers on DC-1, create an Organizational Unit (OU) called _EMPLOYEES, and a second OU named _ADMINS under your domain.
</p>
<p>

![image](https://github.com/user-attachments/assets/3eb974b2-f424-4b90-b3ce-9226c368e68c)

</p>
<p>
Right-click on the _ADMINS OU and create a new user to set up a Domain Admin user (jane_admin). 
</p>
<p>

![image](https://github.com/user-attachments/assets/2ab53e69-0d4d-4983-a306-0a36bf611175)

</p>
<p>
Right-click on the user, select Properties, and assign them Domain Admin privileges.
</p>
<p>

![image](https://github.com/user-attachments/assets/98f43f6d-8b5f-4a8b-973d-842b0800271d)  
 
</p>
<p>


</p>
<br />

<p>
<h4>Windows 10 VM Joined to the Domain</h4>

![image](https://github.com/user-attachments/assets/9c63196b-6db1-4628-997b-11a5bd618f74)

</p>
<p>
In Azure change the DNS settings on the Windows 10 (Client-1) VM to point to the domain controller using the server's VNet private IP, then restart the VM.
</p>
<p>

![image](https://github.com/user-attachments/assets/e50a1a76-92f9-4520-aadc-4aede8a30008)

</p>
<p>
Sign into the Client-1 domain with domain credentials (labuser). Then, connect Client-1 to the domain by going to Start > Settings > System > About. Under PC name, click Rename this PC (Advanced) > Change. Enter 'mydomain.com' in the domain field and confirm. 
</p>
<p>

![image](https://github.com/user-attachments/assets/98f43f6d-8b5f-4a8b-973d-842b0800271d)

</p>
<p>
Use the domain admin credentials to log in to the domain on Client-1.
</p>
<p>

![image](https://github.com/user-attachments/assets/7bd54faf-31b7-49c0-b2f3-10dc0c5b4eb8)

</p>
<p>
The Client-1 VM is now connected to the domain. A restart is required. Upon logging back in, the Client-1 VM will be a member of the domain.
</p>
<p>

![image](https://github.com/user-attachments/assets/41905e10-11ca-4502-9986-e3f5aa166a62)

</p>
<p>
Return to DC-1 VM and log in as mydomain.com\domain admin (jane_admin). Verify that the Client-1 is connected to the domain by checking Active Directory Users and Computers in the Computers OU.
</p>
<p>


</p>
<br />

<p>

<h4>Users and Group Policies Configured</h4>


![image](https://github.com/user-attachments/assets/ea334f3f-332b-4208-834c-09eeac93253e)
</p>
<p>

Log into Client-1 as the domain admin (mydomain.com\jane_admin). Then, go to Start > Settings > System > Remote Desktop. Under User Accounts, click Select users that can remotely connect to this PC. Next, click Add and enter Domain users. This will grant all domain users access to log into Client-1 remotely.
</p>
<p>

![image](https://github.com/user-attachments/assets/c4467ae6-1ed0-4a0e-9a09-1cac174643d9)

</p>
<p>
Go to Start > PowerShell ISE (run as Administrator). Split the screen to show the script. Download the provided script and save it to the desktop. Open the script in PowerShell ISE, then paste the script into the editor. Finally, click Run Script to execute the script and create Domain Users.
</p>
<p>

![image](https://github.com/user-attachments/assets/2119f041-b2d0-49cb-8b86-252a8c2a7d4e)

</p>
<p>
Verify the domain users by opening Active Directory Users and Computers. Navigate to the _EMPLOYEES Organizational Unit (OU) and select a random user. Use that user's credentials to log into Client-1.
</p>
<p>

![image](https://github.com/user-attachments/assets/d45d00df-dbde-47d5-8120-5b6e789e0ff0)

</p>
<p>
Navigate to Client-1 using the newly created domain user credentials. Once logged in, open This PC > Windows (C:) > Users to view the Domain User profile on Client-1.
</p>
<p>

![image](https://github.com/user-attachments/assets/6fbac9ba-07b6-41bb-a162-d3f093faea90)

</p>
<p>
Open the Group Policy Management Console by pressing Start > Run, and typing gpmc.msc.
Next, edit the existing Default Domain Policy by navigating to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy.

Configure the policy according to your security requirements. 
</p>
<p>

![image](https://github.com/user-attachments/assets/fee21f53-6e96-4372-a06a-724cfb03d8b3)
</p>
<p>

Navigate to the Password Policy to further define the password settings according to your needs.
</p>
<p>

![image](https://github.com/user-attachments/assets/cf2bf5b1-a37e-43c3-8eeb-97ec01965357)

</p>
<p>
To initiate an automatic update of the Group Policy changes, simply open the Command Prompt and enter the command: gpupdate /force.

</p>
<p>
