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
- Database: MySQL 5.5.62
- PHP: PHPManagerForIIS_V1.5.0.msi
- Web Browser: Latest version of Chrome or Safari
- Operating System: Windows or Mac


<h2>Create A Virtual Machine</h2>

In Azure, go to Virtual Machines and create a new Resource Group, choose a name of your liking. For the purpose of this demonstration, the Resource Group will be named osTicket. Next, create a Virtual Machine name (osticket-vm). Set the correct region, and set the image to Windows 10 Pro. Select a Size, then create Administrator Account credentials. Select Next: Disks.
  
![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


Select Next: Networking. Create a new Virtual Network. Keep default settings for Ports, check the Licensing Agreement box at the bottom (don't skip this!), then select Review and Create, then click Create.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


Once the Virtual Machine deployment is complete, search Virtual Machine, and copy the Public IP Address for osticket-vm.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


The next step is to open Remote Desktop, and login to the osticket-vm. Next add PC, and then paste osticket-vm Public IP Address into the PC Name. I will be naming the Virtual Machine osTicket. Select Add. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


Enter your User Account credentials (same credentials from when the Virtual Machine was created in Azure), then Continue. Now you are logged in to the osTicket Remote Desktop. If done successfully, it will look like this. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  



The remaining information may seem ambiguous, but essentially, I will be installing the dependencies that are required for osTicket. To work and run, osTicket runs in a web browser, so it requires a webserver and database to be installed and configured. The remaining work will be done inside the Virtula Machine.

<h2>Installation Steps</h2>
Within the Virtual Machine, open Microsoft Edge. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


The document that I will be usuing is the Lab Checklist URL obtained from the CourseCareers Information Technology Course: Module 4 Lab 3: Ticketing Systems. I copied the Lab Checklist URL, and pasted it inside the Virtual Machine browser. 
![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Now that the Lab Checklist is open inside the Virtual Machine, click the link and download osTicket-Installation-Files.zip 
We will use the files in this folder to install osTicket and some of the dependencies.

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)  


 Once osTicket-Installation-Files.zip is downloaded, open the folder and drag onto the desktop.

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1) 


 Right-click the folder, then select Extract All. Then select Extract. Make sure it's going onto the desktop in osTicket. If done correctly, it will look like this.

  ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, we will enable IIS within Windows, with CGI installed as well. IIS is the webserver that allows you to host and manage websites, web applications, and services on a Windows server. CGI (Common Gateway Interface) is a standard protocol used to enable web servers to interact with external programs allowing them to generate dynamic content. It acts as a bridge between the web server and applications running on the server.


To enable IIS, click the Start Menu, and go to the Control Panel by typing "control". Open the Control Panel, and click on Programs (Uninstall a program). I'm not going to actually unistall anything, but this opens the window I need to use.

  ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


On the left, select Turn Windows Feature On or Off. Scroll down, and check the box that says Internt Information Services. Expand by clicking the plus sign.

   ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


  Continue on to install CGI. Underneath Internet Information Services, select the plus sign to expand World Wide Web Services. Expand Application Development Features, then check the box next to CGI. Select Ok.

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next I will continue installing the remaining files. Next, I will be installing PHP Manager for IIS. PHP Manager for IIS is a management tool that helps configure and manage PHP installations on Microsoft IIS.  It simplifies the process of setting up, configuring, and optimizing PHP on IIS servers.


From the “osTicket-Installation-Files” folder, and select PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi). Continue the prompts to install by selecting Next, I Agree, and Install.

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


From the “osTicket-Installation-Files” folder, install the Rewrite Module. This is a feature that allows you to modify URLs dynamically. It helps create user-friendly and SEO-friendly URLs by rewriting incoming requests before they reach your web application. From the “osTicket-Installation-Files” folder, select rewrite_amd64_en-US.msi. Check the box to agree, and install.

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, I will create a directory on Local Disk C: (C:\PHP). The C: drive is the primary partition on a Windows computer where the operating system (Windows), system files, and installed programs are typically stored.
In the same File, scroll down to the C: drive. Right-click to create a New folder, and name it PHP.

 ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


 Next, I will unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder. From the “osTicket-Installation-Files” folder, Right-click php-7.3.8-nts-Win32-VC15-x86.zip, then select Extract All.

  ![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)



Instead of selecting Extract right away, select Browse. Click on Windows C:, select PHP, then Select Folder. Now select Extract. The PHP folder is now extracted along with the files. If done correctly, it will look like this.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, install the VC Redistributable File. From the “osTicket-Installation-Files” folder, scroll down to VC_redist.x86.exe., double-click, and install.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, I will install MySQL 5.5.62. MySQL serves as the database management system where osTicket stores all its data. osTicket uses MySQL to store ticket information, user details, settings, and other data required for its operation. From the “osTicket-Installation-Files” folder, douoble-click on MySQL, agree to the terms and conditions by checking the box, selelct Next, Typical, and Install. Check the box to launch the MySQL Configuration Wizard. Then select Finish.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


For the MySQL Configuration Wizard, select Next, then click on Standard Configuration. Select "Next" twice. For Security options, check the box to Modify Security Settings. It is very important to make sure that the username and password are the same word with no errors. For the purpose of this demo, I will be using the word "root". Select Next, Execute, and Finish.
![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)



Now that the datatbase is installed, I will be configuring systems inside of the web server. Next, I will open IIS as an Administrator. Click the Start Menu, and start typing IIS. Right-click Internet Information Services, then select Run As Administrator.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, I will register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe). This basically means I'm making the web server aware of the existence of PHP, and telling the computer where it is located. 
Double-click PHP Manager, then select Register new PHP version. Click the 3 dots to the right to browse to the C: drive, select the PHP folder, then double-click the php-cgi folder. Select Ok.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, I will reload IIS (open IIS, stop and start the server). When changes are made to the configuration files or settings related to osTicket or other web applications hosted on IIS, you often need to reload IIS to apply these changes without restarting the entire server. Reloading IIS can help refresh application pools, which can resolve certain performance issues or memory leaks that might affect osTicket's operation.
Underneath Connections, right-click osticket-vm, select Stop. Wait a few moments, and right-click osticket-vm once more, select Start.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Now it's time to install osTicket! Back inside of the “osTicket-Installation-Files” folder, I will unzip osTicket by right-clicking osTicket, and selecting Extract All. Select Extract.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Another osTicket folder was created within the “osTicket-Installation-Files” folder and it contains 2 folders (scripts and upload). Next, I will be copying the “upload” folder into “c:\inetpub\wwwroot” which is the default root directory for websites hosted on a Windows server running IIS. Within “c:\inetpub\wwwroot”, I will rename “upload” to “osTicket”. Make sure to keep this window open.

Still working inside the osticket-vm, right-click the manilla folder, select File Exlplorer,  and then scroll to the C: drive. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Select inetpub, click wwwroot (this is the root of the webserver). Now drag the upload folder into wwwroot. Select Continue to provide administrator permission. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


To rename the upload folder to osTicket, right-click the folder and make sure to name the folder osTicket without any mistakes. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)























