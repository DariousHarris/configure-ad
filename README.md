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
- Windows 10 (21H2)

<h2> Create a Domain Controller and Client in Azure</h2>
<p>
<img src="https://i.imgur.com/L5MS4SR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this lab, we initiate the setup of an Azure environment, establishing a Domain Controller (DC-1) using Windows Server 2022 and a client machine (Client-1) running Windows 10. The Resource Group and Virtual Network (Vnet) are carefully noted during the Domain Controller VM creation. The Domain Controller's NIC Private IP address is set to static, and the Client-1 VM is configured to use the same Resource Group and Vnet, ensuring both VMs reside in the same Vnet, as validated through Network Watcher.

</p>
<br />

<h2> Ensure Connectivity and Installing Active Directory</h2>
<p>
<img src="https://i.imgur.com/YV0PyTb.png" height="50%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
With the infrastructure in place, the lab proceeds to ensure connectivity between Client-1 and DC-1. A perpetual ping is initiated from Client-1 to DC-1, prompting the configuration of ICMPv4 on the local Windows Firewall of the Domain Controller. After successfully establishing connectivity, the focus shifts to installing Active Directory on DC-1, creating a new forest (e.g., mydomain.com), and promoting it as a domain controller. The subsequent login as "mydomain.com\labuser" sets the stage for Active Directory operations.
  
</p>
<br />

<h2>Create Users and Organizational Units</h2>

<p>
<img src="https://i.imgur.com/TxhnIeq.png" height="30%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
Active Directory operations commence with the creation of Organizational Units (OUs) named "_EMPLOYEES" and "_ADMINS." Within these OUs, an employee named "Jane Doe" is created with the username "jane_admin." Jane_admin is strategically added to the "Domain Admins" Security Group. The Remote Desktop connection is then switched to Jane_admin, who becomes the designated admin account for subsequent tasks.
  
</p>
<br />

<h2>Join Client-1 to the Domain and Remote Desktop Setup</h2>
<p>
<img src="https://i.imgur.com/Zc6b7tX.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Client-1 is seamlessly integrated into the domain (mydomain.com), with DNS settings adjusted to the DC's Private IP address. The Remote Desktop setup on Client-1 allows domain users, like Jane_admin, to access it remotely. Organizational restructuring follows with the creation of an additional OU named "_CLIENTS," where Client-1 is moved for improved organization.
  
</p>
<br />

<h2>User Creation and Login Scenario</h2>

<p>
<img src="https://i.imgur.com/V2qpxGj.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
The final stage involves creating additional users through a PowerShell script. Jane_admin, now on DC-1, executes the script, observing the dynamic creation of accounts. Post-execution, the Active Directory Users and Computers (ADUC) tool is used to verify the presence of newly created accounts in the appropriate OU. A practical touch is added by attempting to log into Client-1 with one of the newly generated accounts, showcasing the successful integration of users into the domain environment.

</p>
<br />
