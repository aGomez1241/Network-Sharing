<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises File Sharing on an Active Directory Network made with Azure vitrual machines (Azure)</h1>
This tutorial outlines the implementation of network file sharing with an on-premises Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- File Explorer

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Starting with an Active Directory enviorment made in Azure go to the Domain controller make folders on the C Drive that will have various share permissions.
- Set the permissions for those folders.
- Go onto the client and test the share permissions as a normal user and an admin.
- Create an accountant class of users and make a user an account to test share permissions with that class.

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/WKcak3p.png"/>
</p>
<p>
On the Domain Controller's C Drive create folders with these names: read-access, write-access, no-access and accoutant
</p>
<br />

<p>
<img src="https://i.imgur.com/oftoYuw.png"/>
</p>
<p>
Right click on the folder and click properties then sharing and then the first option to set share permissions according for the folder on the network, as described below: 
  <br />
  read-access: Domain User: read
  <br />
  write-access: Domain User: read/write
  <br />
  no-access: Domain Admin: read/write
  <br />
  accountant: Accountant: read/write
</p>
<br />

<p>
<img src="https://i.imgur.com/4p9YNNL.png"/>
</p>
<p>
From the Active Directory and Users page create a new organizational unit called _SECURITY GROUPS and create an accountant group by right clicking inside of it and clicking new group. Give this group read write access to the account folder and set an account to be an accountant. 
</p>
<br />

<p>
<img src="https://i.imgur.com/On43O01.png"/>
</p>
<p>
Use the command \\DC-1 with 'DC-1' being the hostname of the Domain Controller in the search bar of file explore to access share files. Do this on the Client virtual machine logged in as an Admin, Accoutant and Domain User to ensure you set the proper permissions for each folder. This concludes the demonstration.
<br />


