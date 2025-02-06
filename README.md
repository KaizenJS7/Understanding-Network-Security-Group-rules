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
