<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure Subscription
- Remote Desktop Connection

<h2>Cloud Environment Setup</h2>

<p>
<img src="https://i.imgur.com/hkXsrwE.png" height="80%" width="80%" alt="Resource Group Creation"/>
</p>
<p>
First, we are going to create our resources in Azure. We'll start off by creating a resource group where we will allocate our virtual machine. By creating a resource group, it will conveniently allow us to organize and delete all of our resources for this project in one place. I've named mine "RG-Ticket".
</p>
<br />

<p>
<img src="https://i.imgur.com/ylIIzi2.png" height="80%" width="80%" alt="VM Creation"/>
</p>
<p>
Next, we'll create a Virtual Machine with Windows 10 that has at least 2-4 Virtual CPUs and we'll allow it to create a new Virtual Network (Vnet). Make sure to assign it to the resource group (RG-Ticket) and that RDP on port 3389 is enabled as this is what we will use to establish a connection to the VM. As far as the admin account is concerned, I used the username "labuser". The rest of the settings outside of the basics tab should be fine as default.
</p>
<br />

<p>
<img src="https://i.imgur.com/iVB2of5.png" height="80%" width="80%" alt="VM ip address"/>
</p>
<p>
Once the resources have deployed, you can navigate over to "VM1" in the Azure portal and find the public ip address. Copy the address, open up Remote Desktop Connection, and paste the address as pictured above. 
</p>
<br />

<p>
<img src="https://i.imgur.com/616WE6W.png" height="60%" width="60%" alt="alert box"/>
</p>
<p>
After entering the credentials that you used when creating the VM (in my case "labuser"), click "yes" when met with this warning. 
</p>
<br />

<p>
<img src="https://i.imgur.com/Rb7NdWD.png" height="80%" width="80%" alt="VM Desktop"/>
</p>
<p>
If you have done everything correctly up to this point, you should end up with a fresh Windows 10 desktop ready for our osTicket installation. Try not to get it confused with your personal machine.  
</p>
<br />

<h2>osTicket Install Steps</h2>

<p>
<img src="https://i.imgur.com/Pw11cw4.png" height="80%" width="80%" alt="Files link in edge browser"/>
</p>
<p>
We'll start this section off by opening up the edge browser on the VM and pasting the link to the intallation files and dependencies found <a href= "https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> here. </a> 
</p>
<br />

<p>
<img src="https://i.imgur.com/GkWg2Hw.png" height="80%" width="80%" alt="control panel windows features"/>
</p>
<p>
Now we need to go to the control panel and navigate to Programs and Features -> Turn Windows Features on or off. Here we will check the following folders you see pictured above. Don't forget to also go under Application Development Features and check CGI (not pictured). Hit "ok" and wait for the changes to be applied. 
</p>
<br />

<p>
<img src="https://i.imgur.com/U1LnAfV.png" height="80%" width="80%" alt="PHP manager install"/>
</p>
<p>
Let's get started with the downloads, shall we? We'll begin by downloading and installing "PHPManagerForIIS_V1.5.0.msi" and "rewrite_amd64_en-US.msi" from the installation files.
</p>
<br />

<p>
<img src="https://i.imgur.com/zICplet.png" height="60%" width="60%" alt="PHP Directory Creation"/>
</p>
<p>
Next, we'll create the directory C:\PHP
</p>
<br />

<p>
<img src="https://i.imgur.com/MdcBJvl.png" height="60%" width="60%" alt="unzip contents"/>
</p>
<p>
Now we'll go back to the installation files, download "php-7.3.8-nts-Win32-VC15-x86.zip" and unzip the contents into the C:\PHP directory.
</p>
<br />

<p>
<img src="https://i.imgur.com/psqDHe6.png" height="80%" width="80%" alt="Install files"/>
</p>
<p>
Back to the installation files we go and now we'll download and install both "VC_redist.x86.exe" and "mysql-5.5.62-win32.msi". When installing MySQL: 

  - Typical Setup ->
  - Launch Configuration Wizard (after install) ->
  - Standard Configuration ->
  - "Password1" for the password
</p>
<br />

<p>
<img src="https://i.imgur.com/cl7odnK.png" height="80%" width="80%" alt="Opening IIS"/>
</p>
<p>
Next up is opening IIS as an Admin. Type "iis" in the search bar, then right click and "run as administrator".
</p>
<br />

<p>
<img src="https://i.imgur.com/j9r3vvL.png" height="80%" width="80%" alt="Registering PHP"/>
</p>
<p>
Once you have opened IIS manager, double-click on PHP Manager. Here you will register the new PHP version by selecting the php-cgi executable file.
</p>
<br />

<p>
<img src="https://i.imgur.com/heE2AGq.png" height="80%" width="80%" alt="Renaming Folder"/>
</p>
<p>
Now we can finally get to installing osTicket. Head over to the installation files and download osTicket.
  
  - Extract and copy the "upload" folder to C:\inetpub\wwwroot
  - Within C:\inetpub\wwwroot rename "upload" to "osTicket"
</p>
<br />


<p>
<img src="https://i.imgur.com/lGYUmsT.png" height="80%" width="80%" alt="Browse osTicket"/>
</p>
<p>
Back in IIS we will stop and start the server (located on the right-hand side) and then navigate to sites -> Default Web Site -> osTicket and click on "Browse *:80". A new window will appear that will show extensions that are not enabled.
</p>
<br />

<p>
<img src="https://i.imgur.com/DEC3bRP.png" height="80%" width="80%" alt="Enable php extensions"/>
</p>
<p>
Back to IIS we go. Within the same osTicket folder, double-click PHP Manager and click "enable or disable an extension". Here we will enable the following: 
  - php_imap.dll
  - php_intl.dll
  - php_opcache.dll
Refresh the osTicket site and observe the changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/DEC3bRP.png" height="80%" width="80%" alt="Rename ost-config"/>
</p>
<p>
Now we need to go back to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file to "ost-config.php"
</p>
<br />

<p>
<img src="https://i.imgur.com/OsvFzlQ.png" height="80%" width="80%" alt="Assign Permissions"/>
</p>
<p>
Next we need to assign permissions and disable inheritance. Right-click the file -> Properties -> Security -> Advanced -> Disable Inheritance -> Remove all
</p>
<br />


<p>
<img src="https://i.imgur.com/lOYloEb.png" height="80%" width="80%" alt="Assign Permissions"/>
</p>
<p>
Assign new permissions by selecting a principal and adding "everyone" and assigning full control.
</p>
<br />

<p>
<img src="https://i.imgur.com/dyH7yl2.png" height="80%" width="80%" alt="Filling out osTicket"/>
</p>
<p>
Now we can go back to osTicket in the browser and click continue to finish setting it up. Don't forget your credentials because we will be using them later.  
</p>
<br />

 <p>
<img src="https://i.imgur.com/aeReT9i.png" height="80%" width="80%" alt="Heidi SQL Install"/>
</p>
<p>
Almost done! We need to download and install Heidi SQL from the installation files. Once that is done we will open Heidi SQL, create a new session, and enter our password from earlier (Password1) and connect to the session.
</p>
<br />

 <p>
<img src="https://i.imgur.com/aeReT9i.png" height="80%" width="80%" alt="Heidi SQL Install"/>
</p>
<p>
In the new window that appears, create a new database called osTicket.
</p>
<br />

 <p>
<img src="https://i.imgur.com/N02ag73.png" height="80%" width="80%" alt="Finish setting up osTicket"/>
</p>
<p>
Lastly, fill out the SQL portion of osTicket in the browser. 
</p>
<br />

 <p>
<img src="https://i.imgur.com/f8w59UV.png" height="80%" width="80%" alt="Finish setting up osTicket"/>
</p>
<p>
Congratulations! Hopefully you've made it this far without errors. Here is the end user URL: http://localhost/osTicket/

  And the help desk login page:
http://localhost/osTicket/scp/login.php 

Clean up:
    -Delete: C:\inetpub\wwwroot\osTicket\setup
    -Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

</p>
<br />
