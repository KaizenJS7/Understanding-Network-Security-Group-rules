# Understanding-Network-Security-Group-rules

<h2>Task 1: Creating a Virtual Machine</h2>

1. First, I navigate to the Azure Portal. In the search box at the top, I type <b>Virtual machine</b> and select <b>Virtual machines</b> from the search results.

 <img src="https://i.imgur.com/xL2tWVW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

2. In <b>Virtual machines</b> section, I click on <b>+ Create > Azure virtual machine</b>.

 <img src="https://i.imgur.com/xtJTqql.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

3. On the <b>Create a virtual machine</b> tab, I fill in the requiered details inder the <b>Basics</b> tab.
- Resource group: I select an existing resource group or create a new one.
- Instance details:
   - Virtual machine Name: I enter a name for my VM.
   - Region: I choose my preferred region.
   - Availability options: I select <b>No infrastructure redundancy required</b> & <b>Standard</b> as the Security type.
   - Image : I select  <b>Windows Server 2022 Datacenter - Azure Edition - Gen2</b>.
   -  Azure Spot instance : I leave it unchecked.
   -  Size : I click on <b>see all sizes</b>, select <b>B2s</b> and then click <b>select</b>.
- Administrator Account:
   - Username: I enter a username
   - Password: I enter a password
   - Confirm Password: I re-enter the password
 - Inbound Port rules:
   - Public inbound ports: I select <b>None</b>
   - I then click <b>Next:Disks</b> and select <b>Standard SSD</b> for the OS Disk type.
  
 <img src="https://i.imgur.com/eWv1Gbl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

4. I leave the default settings in the <b>Networking</b> and <b>Management</b> tabs. In the <b>Monitoring</b> tab, I <b>Disable</b> <b>Boot diagnostics</b>.

 <img src="https://i.imgur.com/tACGh3C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

5. I click on <b>Review + create button</b> and then <b>Create</b>. After a few minutes, the VM is deployed.

<img src="https://i.imgur.com/TDUCgoE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<h1>Task 2: Allowing RDP traffic via NSG Rules</h1>

1. I go to the Azure Portal and search for <b>Virtual Machines</b>. Then, I select my virtual machine, "<b>myWhizlabsVM1</b>".
2. In the <b>Overview</b> section, I click on <b>Networking</b>. Here, i can see the network interface, public and private IP addresses, and the inbound/outbound port rules.
3. I click on <b>+ Create port rule</b>, select <b>Inbound Port</b> rule, and enter the following details:

<img src="https://i.imgur.com/XufNupp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

   - Source: <b>Service Tag</b>
   - Source service tag: <b>Internet</b>
   - Destination: <b>Any</b>
   - Service: <b>RDP</b>
   - Action: <b>Allow</b>
   - Priority: <b>100</b>
   - Name: <b>myport_3389</b>

<img src="https://i.imgur.com/VrNLkXO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

4. I click <b>Add</b>, creating the security rule for RDP access on port 3389.

<img src="https://i.imgur.com/TGgBib4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

5. To connect to my VM, I go to overview and click <b></b>Connect > RDP</b>, then <b>Download RDP File</b>.
6. I open the downloaded RDP file, enter my creddentials, and click <b>Ok</b> to connect.

<img src="https://i.imgur.com/ON3LwFb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<h1>Task 4: Allowing HTTP Traffic via NSG Rules</h1>

1. Inside the <b>Windows VM</b>, I open <b>Server Manager</b> and select <b>Add Roles and Features</b>.

<img src="https://i.imgur.com/gzZ2uQK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

2. I click <b>Next</b> until I can select <b>Web Server (IIS)</b>. I continue clicking <b>Next</b> until I reach the installation page.

<img src="https://i.imgur.com/uHNd8KO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

3.  Once the installation completes, I click <b>Close</b> and open Microsoft Edge.
4.  In the browser I type <b>http://localhost/</b> to confrim ISS is installed.

<img src="https://i.imgur.com/PKt51uC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

5. Back in the Azure Portal, I go to <b>Networking</b> for my VM and click <b>+ Create port rule</b> and <b>Inbound Port rule</b> option.

   - Source : <b>Service Tag</b>
   - Source service tag : <b>Internet</b>
   - Destination : <b>Any</b>
   - Destination port ranges : <b>80</b> (HTTP)
   - Action : <b>Allow</b>
   - Priority : Enter <b>110</b>
   - Name : <b>myport_80</b>

 <img src="https://i.imgur.com/sbzrPKW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

6. I click <b>Add</b>, allowing traffic through port 80.

 <img src="https://i.imgur.com/WDUJCQa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

7. In the <b>networking</b> section, I copy the <b>Public IP address</b>.

 <img src="https://i.imgur.com/Oforjri.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

8. I paste the public IP into a web browser, and the ISS default page appears, confriming successful configuration.

<img src="https://i.imgur.com/1GlJvOf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<h1>Task 6: Deleting the Resources</h1>

1. In the Azure Portal, I search for <b>Resource Groups</b> and select my resource group.

<img src="https://i.imgur.com/vpjZEV1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

2. I select all the resources by clicking the <b>Name checkbox</b>.

<img src="https://i.imgur.com/Bo1MFoR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

3. I click the three-dot menu and choose <b>Delete</b>.

<img src="https://i.imgur.com/jEYpAZD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

4. I type <b>Delete</b> to confrim and finalize the deletion.

<img src="https://i.imgur.com/gJBjP3K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

5. Now type Delete to confirm deletion and confrim deletion.

<img src="https://i.imgur.com/QkgW1x4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<img src="https://i.imgur.com/0ZGnrx6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />    
