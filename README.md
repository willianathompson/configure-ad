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

- Azure Active Directory Setup
- Azure AD Connect Deployment
- Hybrid Identity Configuration
- AD DS Deployment in Azure
- Testing and Monitoring

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
A new Azure Active Directory tenant was created in Microsoft Azure, establishing the core identity and access management system to integrate with the on-premises Active Directory. This was done using Azure Virtual Machines (VMs) running Windows 10 for administrative tasks, and Remote Desktop was configured for secure access to the VMs. The Windows server private IP address was set to static as it acts as a server.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Azure AD Connect was installed and configured on a Windows 10 VM in Azure, allowing for the synchronization of user accounts, groups, and passwords from the on-premises Active Directory to Azure AD. PowerShell was utilized to automate tasks and streamline the synchronization process between both directories.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The synchronization of identities was successfully configured using Azure AD Connect, ensuring a consistent identity management experience between on-premises AD and Azure AD. PowerShell scripts were used to verify synchronization and troubleshoot potential issues.
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Active Directory Domain Services (AD DS) was deployed on an Azure Virtual Machine running Windows Server. The AD DS role was installed, and Remote Desktop was configured for administrative access. PowerShell was employed for automation of AD DS configuration tasks and integration with Azure resources.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Hybrid authentication and directory synchronization were thoroughly tested to ensure proper functionality. Azure AD Connect Health was enabled to monitor synchronization status, and PowerShell scripts were used for ongoing validation and monitoring. Windows 10 VMs were used to manage and test the configurations remotely.
</p>
<br />
