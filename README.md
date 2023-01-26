# Configuring On premises Active Directory within Azure VM's

Here are the steps to set up and configure on premises Active Directory through Azure's Virtual Machines.
<br />
<p>
</p>
<p>
First, set up two virtual machines on azure, one domain controller and one client. I recommend setting up DC-1 (Domain Controller) first so you can automatically create a resource group.
</p>
<br />
<p>
</p>
<p>
Go to Azure->virtual machines->DC-1->Image: Windows Server 2022->Size: 2 vcpus->Username: your_username->Password: yourpassword->Check Boxes->Review+Create->Domain: yourdomain.com->Admin Login: name_Admin->Password: yourpassword
</p>
<br />
</p>
<p>
Now create Client-1's virtual machine->Image: Windows 10->Username: your-username->Password: yourpassword->Go to network and choose the AD-vnet
</p>
<br />
<p>
<img src="https://i.imgur.com/qLxKiL4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to virtual machines in Azure and click on the domain controller (DC-1) in Azure->Go to the networking tab on the left->Click on the network interface (NIC)->Click on IP configurations on the left->Click on the Private IP address in which it says (Dynamic) after->Switch Dynamic to Static->Save
</p>
<br />
