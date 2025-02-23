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


Next, I will rename the Upload folder. To do this, right-click Upload, and scroll down and select Rename. Make sure to type "osTicket" without any mistakes. There is no space between lowercase "os", and "Ticket". Select Continue.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Once again, I will stop and start the server to reload IIS. To do this, go to the Start Menu, and type IIS. Right-click Internet Information Services Mananger, and select Run as administrator. Under Connections, right-click osticket-vm. Select Stop. Wait a few moments to right-click again, and select Start.

Next, I will load the osTicket website. In IIS, expand osticket-vm by clicking the plus sign. Then select Site, Default Web Site, and osTicket. Then select Browse, all the way to the right of the screen. It is very important that every step is done precisely osTicket was installed correctly, it will look like this. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


In the Recommended section, some of the extensions are not enabled meaning some of the features will not be avaialble. I will continue the installion by going back to IIS and making some configurations. To do this, go to the Start Menu, and type IIS. Right-click Internet Information Services Mananger, and select Run as administrator. If not done already, expand osticket-vm by clicking the plus sign. Then select Sites, Default Web Site, and osTicket. Then double-click PHP Manager.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Then under PHP Extensions, select Enable or disable an extension. The extentions that I will enable are: php_imap.dll, php_intl.dll, and php_opcache.dll. The disabled extensions are inn gray text. To enable, click the particular extension you want, and then select Enable.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Now go back to osTicket within the browser, and refresh to make sure the changes were made. Now you can see that more of the extensions are now enabled. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Now I will be renaming one of the files on the hard drive that osTicket uses for configurations. (C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to ost-config.php). I will also be making sure osTicket has access to make changes to it.

To do this, right-click the manilla folder, and open File Explorer. Open the (C:) Drive on the left, then select inetpub. Select wwwroot, then osTicket. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)



Scroll down to include. Now scroll down to ost-sampleconfig.php, right-click and select Renanme. 
Type ost-config.php. It's very important that this is spelled correctly with no mistakes. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)



Since I renamed the file, I have to assign permissions specifically to osTicket so it can make changes on the backend.

To do this, right-click ost-config.php, and select Properties. Within Properties, select Security.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Within the Security tab, go to Advanced. I am going to select Disable inheritance to strip all the current permissions away. Then select Remove all inherited permissions from this object.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)

Observe the Permissions tab is completely empty.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Now, within the same box, select Add. Then click on Select a priniciple. Under "Enter the object name to select", type Everyone and then click Check Names. Doing this in real time is not ideal. But for the sake of this lab tutorial, I will give permissions to everyone to make sure osTicket will function properly. Select Ok.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Under Basic Permissions, check Full control, and select Ok. If done correctly, it should look like this. 
Observe to make sure Everyone has full control, then press Apply. Select Ok twice to continue. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


osTicket now has full control to the configuration file.

Now I will be going back to the osTicket website and continuing on with the set-up. 

Select Continue. In the System Settigns, Create a Helpdesk Name name of your liking. I will be usuing Jaquese's Help Desk. You can also use any email address. In the Admin User section, use your name. The email address in this section should be different than the one above. For the sake of this lab tutorial, I previously created an Admin Username and Password.  

Before moving on, I have to point out that I created the database application on the backend, so now I have to actually log in and create another database specific to osTicket. Then I will fill in those credentials in the Database Settings Sections. 

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


To do that, go back into the osTicket installions file folder on the desktop by right-clicking the manilla folder, and select File Explorer. Go to Desktop, and open the osTicket-Installation-Files” folder. 
Now we will be installing HeidiSQL-which is an application that allows me to make a connection and configure the database.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


After selecting HeidiSQL, select Yes, and accept the License Agreement. Select Next a few times, and then select install.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Make sure to check the box next to Launch HeidiSQL, then select Finish.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


There's an option of opening HeidiSQL manually, but select Skip for now.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Within the HeidiSQL Session Manager, I am going to make a connection to the database, and set up a database for osTicket to use and then finish filling in the credentials on the osTicket website. 

To do this, select New. When we set up the SQL server, we set root as the username




























