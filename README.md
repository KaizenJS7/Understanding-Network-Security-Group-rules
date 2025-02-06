# Understanding-Network-Security-Group-rules

<h2>Task 1: Create a virtual machine</h2>

1. in the search box at the top of the Azure Portal, enter <b>Viryual machine</b>. Select <b>Virtual machines</b> from the search results.

 <img src="https://i.imgur.com/xL2tWVW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

2. In <b>Virtual machines</b> section, select <b>+ Create > Azure virtual machine</b>.

 <img src="https://i.imgur.com/xtJTqql.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

3. In the <b>Create a virtual machine</b> tab, enter or select the following values in the <b>Basics</b> tab.
- Resource group: Select a resource group
- Instance details:
   - Virtual machine Name: Enter the name of VM
   - Region: Select prefered region
   - Availability options: Select <b>No infrastructure redundancy required</b> & <b>Standard as Security type</b>.
   - Image : Select  <b>Windows Server 2022 Datacenter - Azure Edition - Gen2</b>.
   -  Azure Spot instance : Leave the default of unchecked.
   -  Size : Click on <b>see all sizes</b> then select <b>B2s</b> and then click on <b>select</b>.
- Administrator Account:
   - Username: Enter a username
   - Password: Enter a password
   - Confirm Password: Re-enter password
 - Inbound Port rules:
   - Public inbound ports: Select <b>None</b>
   - Click on <b>Next:Disks</b>. Select <b>Standard SSD</b> in OS Disk types.
  
 <img src="https://i.imgur.com/eWv1Gbl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

3. Leave the defaults on <b>Networking</b> and <b>Management</b> tabs, go to the <b>Monitoring</b> tab and <b>Disable</b> the <b>Boot diagnostics</b>.

 <img src="https://i.imgur.com/tACGh3C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

4. Select the <b>Review + create button</b> at the bottom of the page and then click on <b>Create</b>. After a few minutes, the VM will be deployed.

<img src="https://i.imgur.com/TDUCgoE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<h1>Task 2: Allow RDP traffic via NSG rules</h1>

1. In the search box at the top of the Azure portal page, enter <b>Virtual machine</b>. Select Virtual Machines in the search results. Select the virtual machine you created “<b>myWhizlabsVM1</b>".
2. On the <b>Overview</b> page of your VM, go to the <b>Networking</b> section from left menu & select Network settings. Here you can see the network interface which has the public ip address and the private ip address and also the inbound and outbound port rules.
3. Click on <b>+ Create port rule</b>. Select <b>Inbound Port</b> rule and enter or select the following information:

<img src="https://i.imgur.com/XufNupp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

   - Source: Select <b>Service Tag</b>
   - Source service tag: Select <b>Internet</b>
   - Destination: Select <b>Any</b>
   - Service: Select <b>RDP</b>
   - Action: Select <b>Allow</b>
   - Priority: Enter <b>100</b>
   - Name: Enter <b>myport_3389</b>

<img src="https://i.imgur.com/VrNLkXO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

4. Click on the <b>Add button</b>. Now, the security rule will be created which will ensure that we can connect on port 3389 to the virtual machine.

<img src="https://i.imgur.com/TGgBib4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

5. Now, let’s try to connect the virtual machine. Go to the overview section and click on the <b></b>Connect > RDP</b> button on the overview page. Then, click on the <b>Download RDP</b> file option.
6. Open the downloaded RDP file, you will be asked to enter the <b>username</b> and </b>password</b> for the Remote Desktop Connection.

<img src="https://i.imgur.com/ON3LwFb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

7. Click <b>OK</b>. You will now be connected to your Virtual machine.

<h1>Task 4: Allow HTTP traffic via NSG rules</h1>

1. In the <b>Windows virtual machine</b>, open the <b>Server Manager</b> and click on <b>Add Roles and Features</b>. We will now install a web server on this particular machine by adding a network security group rule to allow traffic to flow into this virtual machine on Port 80 so that we can access the web server.

<img src="https://i.imgur.com/gzZ2uQK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

2. Click on <b>Next</b> until you get an option to select <b>Web Server (IIS)</b>. Then, again click on <b>Next</b> until you get an option to install.

<img src="https://i.imgur.com/uHNd8KO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

3.  Click on <b>Install</b>. Once the installation is complete, click on <b>Close</b>.
4.  Open <b>Microsoft edge</b> web browser on the windows VM and enter <b>http://localhost/</b> in the search bar to confirm that Internet Information Services (IIS) is installed on the machine.

<img src="https://i.imgur.com/PKt51uC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

5. Now, return to the Azure portal. In the <b>Networking</b> section of the virtual machine “<b>myWhizlabsVM1</b>”, select <b>+ Create port rule</b> and <b>Inbound Port rule</b> option. Enter or select the following information.

   - Source : Select <b>Service Tag</b>
   - Source service tag : Select <b>Internet</b>
   - Destination : Select <b>Any</b>
   - Destination port ranges : Select <b>80</b> for HTTP
   - Action : <b>Allow</b>
   - Priority : Enter <b>110</b>
   - Name : Enter <b>myport_80</b>

 <img src="https://i.imgur.com/sbzrPKW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

6. Click on the <b>Add</b> button. Now, the security rule will be created.

 <img src="https://i.imgur.com/WDUJCQa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

7. In the <b>networking</b> section, you will find the <b>public IP address</b>. Copy the public IP.

 <img src="https://i.imgur.com/Oforjri.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

8. Now, paste the public IP on your web browser. You will see the page displaying Internet Information Services.

<img src="https://i.imgur.com/1GlJvOf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<h1>Task 6: Deleting the resources</h1>

1. In the search box at the top of the Azure portal, enter <b>Resource Groups</b>. Select Resource groups from the results.

<img src="https://i.imgur.com/vpjZEV1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

2. Click on the name of the resource group.

<img src="https://i.imgur.com/Bo1MFoR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

3. Select all the resources in that Resource group by clicking on the <b>Name checkbox</b>.

<img src="https://i.imgur.com/jEYpAZD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

4. Go to the three dots on right and click <b>Delete</b>.

<img src="https://i.imgur.com/gJBjP3K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

5. Now type Delete to confirm deletion and confrim deletion.

<img src="https://i.imgur.com/QkgW1x4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 

<img src="https://i.imgur.com/0ZGnrx6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />    
