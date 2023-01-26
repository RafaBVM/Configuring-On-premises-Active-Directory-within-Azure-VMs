# Configuring On premises Active Directory within Azure VM's

Here are the steps to set up and configure on premises Active Directory through Azure's Virtual Machines.
<br />
<p>
</p>
<p>
Set up two virtual machines on azure, one domain controller and one client. I recommend setting up DC-1 (Domain Controller) first so you can automatically create a resource group.
</p>
<br />
<p>
</p>
<p>
Go to Azure->virtual machines->DC-1->Image: Windows Server 2022->Size: 2 vcpus->Username: your_username->Password: yourpassword->Check Boxes->Review+Create->Domain: yourdomain.com->Admin Login: name_Admin->Password: Password1
</p>
<br />
