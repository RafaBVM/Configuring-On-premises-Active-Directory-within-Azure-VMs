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
<img src="https://i.imgur.com/Wfw07rf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8jJ8Gqt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to virtual machines and make sure both DC-1 and Client-1 are in the same virtual network (command+click each one on mac) (control+click on windows)
Ensure connectivity between Client-1 and the Domain controller
<br />
<p>
<img src="https://i.imgur.com/oO7dtXR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FYduNQL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to Client-1 and ping DC 1’s Private IP address on the command prompt with ping -t. (perpetual ping(never ending ping)) 
<br />
<p>
<img src="https://i.imgur.com/dKUQLTy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/2tkxe1A.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login to the Domain Controller (DC-1) and enable ICMPv4 in on the local windows Firewall.
<br />
<p>
<img src="https://i.imgur.com/iXS4TZw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to Client-1 and type control+c on the command prompt
<br />
<p>
<img src="https://i.imgur.com/Z1sILpk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/U4WOpwY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4fuPIBQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/QXs4cqI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to DC-1 and install Active Directory and log back in after. You might have to use your domain you created to log back in. My ex: lilwhatshisname.com\RafaBVM
<br />
<p>
<img src="https://i.imgur.com/E4Nez4s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to Active Directory Users & Computers
<br />
<p>
<img src="https://i.imgur.com/T1pkk0f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/NlfOQvV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/78hky9N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on your domain then right click on it. Select New Organizational Unit and make an _EMPLOYEE and _ADMIN unit then refresh by right clicking on the domain to access them faster.
<br />
<p>
<img src="https://i.imgur.com/TXCQIl0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/b2oc6w4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/6EYeGgm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on _ADMINS and make a new user under your name or whatever you’d like
<br />
<p>
<img src="https://i.imgur.com/xHjuQGl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To assign your new user as a real admin, right click your _ADMINS user you just created and go to properties.
<br />
<p>
<img src="https://i.imgur.com/nzr85Dw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to the member of tab, and click Add.
<br />
<p>
<img src="https://i.imgur.com/hyCMlG0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Type domain in the text box and click Check Names. After click on Domain admins (first option) and ok/ok/apply/ok.
<br />
<p>
<img src="https://i.imgur.com/anln406.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/EKKisYk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log out of DC-1 and log back in as an admin.
<br />
<p>
<img src="https://i.imgur.com/h0jBwYf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/GC5amvY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to Azure->Virtual Machines->Click DC-1->Copy DC-1 Private IP Address->Click on Client-1->Go to Networking->Click Client-1’s Virtual NIC->Click on DNS Servers on the left->Click on custom and paste DC-1’s Private IP address->Save
<br />
<p>
<img src="https://i.imgur.com/L4dr10M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After update restart Client-1 from Azure and log back in.
<br />
<p>
<img src="https://i.imgur.com/gmYiw1v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After, go to Command Prompt and ipconfig /all to check the DNS server.
<br />
<p>
<img src="https://i.imgur.com/7xqDhAM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now go to system settings (right click Start menu, click system)->Rename this PC->Change->Domain->enter you website/domain and password->restart
<br />
<p>
<img src="https://i.imgur.com/O3uiJwp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log back in Client-1 using domain.com\username_admin and password
<br />
<p>
<img src="https://i.imgur.com/sXVVki0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Right click start menu->Click Remote Desktop->Click select “Select user that can remotely access this PC”->Click Add->Type Domain Users->Check Names->Ok
<br />


