<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b>

<h2>List of Prerequisites</h2>

- Web Server: Microsoft IIS
- Database: MySQL 
- PHP Mananger
- Web Browser: Latest version of Chrome or Safari
- Operating System: Windows or Mac


<h2>Create A Virtual Machine</h2>

The first step is to create a Virtual Machine in Microsoft Azure. To do this, create an account in Azure, and use credentials to log in. Once logged in, under Azure Services, select Virtual Machines. Create a new Resource Group, and choose a name of your liking. For the purpose of this tutorial, the Resource Group will be named osTicket. 

![image](https://github.com/user-attachments/assets/438d0c20-9dea-4a5f-a2e3-350cd7bdafce)


Next, create a Virtual Machine name (I will use osticket-vm). Set the correct Region, leave the default Availability Zone, and set the Image to Windows 10 Pro. Next, select a Size.
  
![image](https://github.com/user-attachments/assets/e7c15fdc-a6bf-4f1d-a677-e7e43cfc00e5)


Now create Administrator Account credentials. For the username and password, I will be using labuser and osTicketPassword1!. Select Next: Disks. Now select Next, then Networking. Keep default settings for Ports, and check the Licensing Agreement box at the bottom. It's important not to skip checking this box, as it will cause an error in the end. Then select Review and Create, then click Create.

![image](https://github.com/user-attachments/assets/fe8a425e-f9ee-47c4-ba6e-79d7ffc7e2f2)



Now the Virtual Machine deployment is complete. 

![image](https://github.com/user-attachments/assets/a627befe-80fe-4c10-b3cc-abd32935ca7c)



The next step is to obtain the IP Address for osticket-vm and log into the Remote Desktop. To do this, type Virtual Machine in the search bar, and right-click the IP Address of osticket-vm, then select Copy. 

![image](https://github.com/user-attachments/assets/db81cd8e-636e-480b-9950-3b691487a370)



In Windows, open Remote Desktop, and select Add PC. Paste osticket-vm Public IP Address into the PC Name. I will be naming the Virtual Machine osTicket (make sure the "T" is capitolized). Select Add. 

![image](https://github.com/user-attachments/assets/840f9be0-154e-4491-80a3-638f8428f224)


Enter your User Account credentials (I am using the credentials from when the Virtual Machine was created in Azure), then select Continue. Now I am logged in to the osTicket Remote Desktop. If done successfully, it will look like this. 

![image](https://github.com/user-attachments/assets/728fb0cd-019d-4117-ad9a-9f589d1271cd)



For the remainder of this tutorial, I will be installing the dependencies that are required for osTicket. To work and run, osTicket runs in a web browser, so it requires a webserver and database to be installed and configured. The remaining work will be done inside the Virtual Machine.

<h2>Installation Steps</h2>
Within the Virtual Machine, open Microsoft Edge. 

![image](https://github.com/user-attachments/assets/1b90c091-d7f1-45a8-9abd-92f929ba903f)


The document that I will be usuing to install osTicket dependencies is from the Lab Checklist obtained in the CourseCareers Information Technology Course: Module 4 Lab 3: Ticketing Systems. 

![image](https://github.com/user-attachments/assets/ef9e02e0-bd38-44df-bf66-f0aca6ff4bfc)



I copied the Lab Checklist URL, and pasted it inside the Virtual Machine browser. 
Now that the Lab Checklist is open inside the Virtual Machine, click the link and download osTicket-Installation-Files.zip 
We will use the files in this folder to install osTicket and some of the dependencies.

 ![image](https://github.com/user-attachments/assets/0682e5ef-e76a-4d69-8a31-085010901f08)


 Once osTicket-Installation-Files.zip is downloaded, open the folder and drag onto the desktop.

![image](https://github.com/user-attachments/assets/4c06b31a-bb17-4581-82c4-519e26cbf338)


 Right-click the folder, then select Extract All. 

 ![image](https://github.com/user-attachments/assets/596e9696-1831-4bcd-b0dc-76f1ab2fc39f)


 Then select Extract. Make sure it's going onto the desktop in osTicket. 
![image](https://github.com/user-attachments/assets/54ab4a12-cdc6-400b-8449-0eb125259cbb)


If done correctly, it will look like this.
![image](https://github.com/user-attachments/assets/9725ed2b-7afd-48b2-bc7a-4adc3715e2cd)

 
 


Next, we will enable IIS within Windows, with CGI installed as well. IIS is the webserver that allows you to host and manage websites, web applications, and services on a Windows server. CGI (Common Gateway Interface) is a standard protocol used to enable web servers to interact with external programs allowing them to generate dynamic content. It acts as a bridge between the web server and applications running on the server.


To enable IIS, click the Start Menu, and go to the Control Panel by typing "control". Open the Control Panel, and click on Programs-Uninstall a program. I'm not going to actually unistall anything, but this opens the window I need to use.

![image](https://github.com/user-attachments/assets/4463f15b-a73d-4365-8bcd-70ec2bcfc613)




On the left, select Turn Windows Feature On or Off. Scroll down, and check the box that says Internt Information Services. Expand by clicking the plus sign.

  ![image](https://github.com/user-attachments/assets/8299b15d-2120-4e38-aee7-f055f2aa47b7)
  


Continue on to install CGI. Underneath Internet Information Services, select the plus sign to expand World Wide Web Services. Expand Application Development Features, then check the box next to CGI. Select Ok.


![image](https://github.com/user-attachments/assets/1b7642b7-27e7-4ac9-8bc5-3277a1af9a2b)



Next I will continue installing the remaining files. Next, I will be installing PHP Manager for IIS. PHP Manager for IIS is a management tool that helps configure and manage PHP installations on Microsoft IIS.  It simplifies the process of setting up, configuring, and optimizing PHP on IIS servers.


From the “osTicket-Installation-Files” folder, select PHP Manager for IIS. Continue the prompts to install by selecting Next, I Agree, and Install.

![image](https://github.com/user-attachments/assets/36cc06b0-fd8a-44f5-9b44-e0830a6b9ddb)


From the “osTicket-Installation-Files” folder, install the Rewrite Module. This is a feature that allows you to modify URLs dynamically. It helps create user-friendly and SEO-friendly URLs by rewriting incoming requests before they reach your web application. From the “osTicket-Installation-Files” folder, select Rewrite. Check the box to agree, and install.

![image](https://github.com/user-attachments/assets/b8e5015d-bad4-4fb8-b5d4-877210ae41b0)


Next, I will create a directory on Local Disk C:. The C: drive is the primary partition on a Windows computer where the operating system, system files, and installed programs are typically stored.
In the same File, scroll down to the C: drive. Right-click to create a New folder, and name it PHP.

![image](https://github.com/user-attachments/assets/e15807da-5531-4d2c-8322-b34e943eec72)


 Next, I will unzip PHP into the “C:\PHP” folder. From the “osTicket-Installation-Files” folder, Right-click PHP, then select Extract All.

 ![image](https://github.com/user-attachments/assets/c77977d8-38c6-47e9-9005-d9bc812ab356)



Instead of selecting Extract right away, select Browse. Click on Windows C:, select PHP, then Select Folder. Now select Extract. The PHP folder is now extracted along with the files. If done correctly, it will look like this.

![image](https://github.com/user-attachments/assets/e9d92b4e-4cb8-453f-bc7b-9ab636fccbd1)


Next, install the VC Redistributable File. This is another requirement that osTicket will need to use to be able to function properly. From the “osTicket-Installation-Files” folder, scroll down to VC Redistributable, double-click, and install.

![image](https://github.com/user-attachments/assets/f3a9ec13-b440-4e39-a806-9e8a09582345)


Next, I will install MySQL. MySQL serves as the database management system where osTicket stores all its data. osTicket uses MySQL to store ticket information, user details, settings, and other data required for its operation. From the “osTicket-Installation-Files” folder, douoble-click on MySQL, agree to the terms and conditions by checking the box, selelct Next, Typical, and Install. 

![image](https://github.com/user-attachments/assets/84eef51c-cd06-4e61-b0db-ea7ae7c4da2b)


Check the box to launch the MySQL Configuration Wizard. Then select Finish.

![image](https://github.com/user-attachments/assets/1b76df07-a5f6-4895-9051-79c87e3c9d63)


For the MySQL Configuration Wizard, select Next, then click on Standard Configuration. Select "Next" twice. 

![image](https://github.com/user-attachments/assets/aac9ec98-4c6d-49cc-834c-c1a09dbabe02)



For Security options, check the box to Modify Security Settings. It is very important to make sure that the username and password are the same word with no errors. For the purpose of this demo, I will be using the word "root". Select Next, Execute, and Finish.

![image](https://github.com/user-attachments/assets/8925ec8b-aee1-4fc6-b1ca-6332792a2952)


Now that the datatbase is installed, I will be configuring systems inside of the web server. Next, I will open IIS as an Administrator. Click the Start Menu, and start typing IIS. Right-click Internet Information Services, then select Run As Administrator.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, I will register PHP from within IIS. This basically means I'm making the web server aware of the existence of PHP, and telling the computer where it is located. 
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


Within the HeidiSQL Session Manager, I am going to make a connection to the database and set up a database for osTicket to use. Then I will finish filling in the credentials on the osTicket website. 

To do this, select New... When I set up the SQL server, I set "root" as the username and password. Fill in both the User and Password, then select Open. This opened a connection in the database. If done correctly, it will look like this.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Next, I will create a database and name it osTicket. To do this, right-click Unnamed, and select Create new. Click on Database, and then name the database "osTicket". Make sure not to make any mistakes. Select Ok, and you can see that osTicket was created, and is now listed in the database list.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Now I will continue setting up osTicket in the browser.
So going back to the browser, I already entered the details for the admin user. Enter the credentails for osTicket for the MySQL database settings. Enter "root" for the username and password. Now select Install Now.

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)


Congratulations! osTicket has successfully been installed!

![image](https://github.com/user-attachments/assets/affc680d-dd0a-4416-8fc5-64f78d4808a1)

























