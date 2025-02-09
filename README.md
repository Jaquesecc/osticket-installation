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

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Web Server: Microsoft IIS
- Database: MySQL
- PHP: Version 7.2 or later with extensions
- Web Browser: Latest version of Chrome or Safari
- Operating System: Windows or Mac


<h2>Create A Virtual Machine</h2>

In Azure, go to Virtual Machines and create a new Resource Group, choose a name of your liking. For the purpose of this demonstration, the Resource Group is named osTicket. Next, create a Virtual Machine name (osticket-vm). Set the correct region, and set the image to Windows 10 Pro. Select a Size, then create Administrator Account credentials. Select Next: Disks.
  
![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


Select Next: Networking. Create a new Virtual Network. Keep default settings for Ports, check the Licensing Agreement box at the bottom (don't skip this!), then select Review and Create, then click Create.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


Once the Virtual Machine deployment is complete, search Virtual Machine, and copy the Public IP Address for osticket-vm.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


Open Remote Desktop, Add PC, and then paste the Public IP Address into the PC Name. I will be naming the Virtual Machine osTicket. Select Add. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


Enter your User Account credentials, then Continue. Now you are logged in to the osTicket Remote Desktop. If done successfully, it will look like this. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  



The remaining information may seem ambiguous, but essentially, we are installing the dependencies that are required for osTicket. To work and run, osTicket runs in a web browser, so it requires a webserver and database to be installed and configured. 


<h2>Installation Steps</h2>
Within the VM (osticket-vm), download the osTicket-Installation-Files.zip (provided by CourseCareers), and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”.
We will use the files in this folder to install osTicket and some of the dependencies.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


 Once osTicket-Installation-Files.zip is downloaded, drag the folder onto the desktop.

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1) 


 Right-click the folder, then select Extract All. (Make sure it's going into the Desktop in osTicket). Select Extract.

  ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)









