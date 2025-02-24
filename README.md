<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create Azure Virtural Machines
- Active Directory Domain Services Installed on Windows Server
- Windows 10 VM Joined to the Domain
- Domain Membership and Connectivity Verified
- Users and Group Policies Configured

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The virtual machines were successfully created in Azure, including one for Windows Server 2022 to host Active Directory Domain Services (AD DS), and another for Windows 10 (22H2) to join the domain. The appropriate VM sizes, regions, and networking settings were configured, with Public IP and RDP access enabled for remote connections. The Windows server private IP address was set to static and firewall disabled for connectivity testing.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The Active Directory Domain Services (AD DS) role was installed on the Windows Server 2022 VM. Using Server Manager, the server was promoted to a Domain Controller, and a new domain (mydomain.com) was created. The server was restarted, and Domain Admin credentials were set up successfully.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The Windows 10 (21H2) VM was connected to the domain by accessing Control Panel and joining the domain (mydomain.com). The necessary Domain Admin credentials were entered, and after restarting the VM, users could log in using domain credentials.
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Domain membership was verified by logging into the Windows 10 VM using the domain credentials, and pinging the domain from both the Windows Server 2022 and Windows 10 VMs confirmed proper connectivity between the domain controller and the client machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Users and groups were created and managed on the Windows Server 2022 VM using Active Directory Users and Computers. Group Policy Management was configured to set domain-wide policies, including password policies and account lockout policies, ensuring consistent security across the domain.

  This successful implementation resulted in a fully functional On-premises Active Directory deployment within Azure using Windows Server 2022 and Windows 10 (21H2), with domain management handled efficiently via PowerShell and Remote Desktop.
</p>
<br />
