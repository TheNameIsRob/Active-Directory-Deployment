# Active-Directory-Deploy
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

<h2>High-Level Deployment and Configuration Steps</h2>

- Install Active Directory
- Create a Domain Admin user within the domain
- Join Client-1 to domain
- Set up remote desktop for non-administrative users on Client-1
- Create additional users and attempt to log into Client-1 with users created.

<h2>Deployment and Configuration Steps</h2>

<h3>Step 1: Install Active Directory</h3>
<h4>Use Remote Desktop Connection to log onto our DC-1 (Domain controller) virtual machine</h4>
<img src="https://i.imgur.com/3UfuPtN.png">

<h4>Open service manager and click "Add roles and features"</h4>
<img src="https://i.imgur.com/hMf3kDJ.png">

<h4>Click Server Roles</h4>
<img src="https://i.imgur.com/G4zKViV.png">

<h4>In the column of different roles identify "Active Directory Domain Services" and clock on it.Also click "features" when the new tab opens.</h4>
<img src="https://i.imgur.com/OPsN30T.png">

<h4>Click "Confirmation" and "Install. Observe the installation and wait until it is complete.</h4>
<img src="https://i.imgur.com/ydIwo5B.png">
<img src="https://i.imgur.com/TQGPHpP.png">

<h2>Step 2: Create a forest to promote the virtual machine as an actual domain controller.</h2>

<h4>Within the Server Manager's dashboard click  the flag icon. Then click "Promote this server to a domain controller"</h4>
<img src="https://i.imgur.com/wKHdgsC.png">

<h4>Within the Deployment Configuration tab, select "Add a new forest" and type the domain name under. After click next</h4>
<img src="https://i.imgur.com/MrFaX5f.png">

<h4>In Domain controller options simply write a password for Directory Services Restore Mode. After keep clicking next until you are in the "Confirmation Selection Selections" section. </h4>
<img src="https://i.imgur.com/tX1WSr9.png">

<h4>Within the "Confirmation" section simply click install. Then observe installation. Once it is finished the virtual machine will restart automatically.</h4>
<img src="https://i.imgur.com/lEathND.png">
<img src="https://i.imgur.com/U8KLXpU.png">

<h2>Step 3:Create a Domain Admin user within the domain.</h2>
<h4>Before logging back into the domain controller, we need to specify the root domain name that we created beforehand. Simply type mydomain.com/Labuser1 and login with the same password. </h4>
<img src="https://i.imgur.com/dLJIxWI.png">
<img src="https://i.imgur.com/apT61yh.png">

<h4> Click start in our domain controller, click "Windows Administrative Tools and then click "Active Directory Users and Computers"</h4>
<img src="https://i.imgur.com/0Y4Y1E3.png">

<h4>Indicate the domain name and right click , click "New and then "Organizational Unit"</h4>
<img src="https://i.imgur.com/i72IQyH.png">
<img src="https://i.imgur.com/O8J4ZTF.png">

<h4>Type _EMPLOYEES and click "Ok" below to create the Organizational unit. Follow the same previous steps and create an "_ADMINS" Organizational Unit</h4>
<img src="https://i.imgur.com/KCJFpyW.png"/>
<img src="https://i.imgur.com/V2TBoKr.png"/>

<h4>Right click the "_ADMINS" Organizational Unit and click new, then click User</h4>
<img src="https://i.imgur.com/LOb2OE0.png">
<img src="https://i.imgur.com/Y4vzbRs.png">

<h4>Type in a username for our new admin, click next and add password.</h4>
<img src="https://i.imgur.com/TIo5uyU.png">
<img src="https://i.imgur.com/4DQtyEx.png">

<h4>Simply click finish and observe our newly created admin</h4>
<img src="https://i.imgur.com/DfDFvlg.png">
<img src="https://i.imgur.com/g7NsnYM.png">

<h4>Before we logout, we need to add our admin user to the Domains Admins Security Group. We can click on "Rai Bow" our user and click, click "Member of" and then click "Ok" After Domain Users has been added simply click "Apply" and then "Ok"</h4>
<img src="https://i.imgur.com/vHiC0No.png">
<img src="https://i.imgur.com/h4B0SUs.png">

<h4>Log out</h4>
<img src="https://i.imgur.com/NkQepQV.png">

<h2>Step 4: Join Client-1 to our domain</h2>
<h4>Log into Client-1 virtual machine</h4>
<img src="https://i.imgur.com/2A6yjXH.png">
<h4>Click on systems </h4>
<img src="https://i.imgur.com/E0jJymW.png">
<h4>Click "Change", click "Domain" and write in the domain name, after click "Ok" and type in the credentials we would use to log into the domain controller virtual machine.The changes will be applied when we restart the virtual machine.</h4>
<img src="https://i.imgur.com/MffMZlw.png">
<img src="">

<h4>Step 5: Verify that Client-1 has been joined unto our domain.</h4>
<h4>Go back into "Active Directory Users and Computers" and make a new organizational unit called "_CLIENTS".</h4>
<img src="https://i.imgur.com/UwEe5JF.png">
<img src="https://i.imgur.com/GFgdObW.png">
<h4>Drag "Client-1" from "Computers" and put it into our "_CLIENTS" organization unit.Verify it's been dragged</h4>
<img src="https://i.imgur.com/2DDLRl8.png">

<h2>Now that we have successfully deployed the Active Directory services, we can execute different kinds of administrative tasks as an admin using a domain controller such as creating users, managing user accounts and configuring different rules for different kinds of accounts.</h2>
