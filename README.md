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
