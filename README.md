<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Installation</h1>
In this lab I will explain the process of installing the help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services
- PHP Manager
- MySQL
- Rewrite Module
- VC Redist
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

<p>
Go to https://portal.azure.com/. 
  - Create a virtual machine with Windows 10 Pro, version 22H2. 
  - Run this virtual machine using atleast 2 vcpu and 16gb of memory or more, to ensure that the VM runs smoother.

Once you have created your VM
  - Go to the VM's page on Azure and look for the Public IP Address
  - Copy and paste the IP address into Remote Desktop Connection
 
 <img src="https://i.imgur.com/06VP3um.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/5T9pqfX.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
Once connected to the VM 
  - Go to your control panel.
  - Open up Programs.
  - Select the Turn windows features on and off.
 <img src="https://i.imgur.com/NUMI6K8.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
  <img src="https://imgur.com/zpvg2P1.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
 
The next step is to install/ enable IIS with CGI and Common HTTP Features.
  
  <img src="https://i.imgur.com/clISORm.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/hhgmFY1.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
  *Make sure that every common HTTP feature is checked*

  To ensure that you have properly installed/ enabled IIS. Open up a browser and type in the search bar 127.0.0.1. If your screen looks similar to the one below, you have properly installed IIS.
  
  <img src="https://imgur.com/25Yy9YP.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
  Now that IIS is running, Go over to the installation files and download the PHP manager for IIS (PHPManagerForIIS_V1.5.0msi), go through with the install wizard and complete the installation.
  Next from the Installation files, Download and install the rewrite module (rewrite_amd64_en-US.msi)
  
  Create a folder in the (C:) drive and name it PHP

   <img src="https://i.imgur.com/2Q43AUT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
    <img src="https://i.imgur.com/U8IJ136.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

From the installation files, download PHP 7.3.8((php-7.3.88-nts-Win32-VC15-x866.zip). Theres a chance you may recieve a warning on the file. If so, choose to "keep" the file and continue.

 After downloading PHP unzip the contents into the C:\PHP folder.

  <img src="https://i.imgur.com/D50jGFl.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

  Download and install the VC_redist.x86.exe. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe.
  
  Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->

Set the password to "Password1".

 <img src="https://i.imgur.com/NfJ4QRL.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

 The next step is to run IIS as an administrator, right click on IIS just before opening the application and select the "run as administrator" option.

  <img src="https://i.imgur.com/M5lyTXU.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

  You will now register PHP in IIS, Double click the PHP manager
 
<img src="https://i.imgur.com/0g2yDqm.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

 Register the new PHP version

 <img src="https://i.imgur.com/DilKdQ8.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

Provide a path to the php executable file (php-cgi.exe)). Click on the three dots, from there go to C Drive -> PHP -> click on php-cgi file.

 <img src="https://i.imgur.com/oMXXNAz.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>    

 Restart the server

  <img src="https://i.imgur.com/D9LBuoO.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>  

 Install osTicket v1.15.8 -
   - Download osTicket
   - Extract and copy "upload" folder to c:\inetpub\wwwroot 
   - Within c:\inetpub\root, Rename "upload" to "osTicket"

  <img src="https://i.imgur.com/73kPfNa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
 
 Reload IIS

  On IIS go to sites -> osTicket. On the right, click “Browse *:80

 <img src="https://i.imgur.com/liX6ivP.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 

 A screen will pop up> You will observe that some extensions are disabled.

   <img src="https://i.imgur.com/UT55J6B.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 

  To enable the extensions: 
  - Go back to IIS
  - sites
  - Default 
  - osTicket 
  - Double click PHP manager -
  - Click "Enable or disable an extension"

 <img src="https://i.imgur.com/1AWzeX0.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

 Enable three extensions from here.

  - php_imap.dll

  - php_intl.dll

  - php_opcache.dll

 <img src="https://i.imgur.com/uWwJk5t.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
  
Open file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

Rename the ost-sampleconfig.php to ost-config.php, just removing the sample part of the name

Right click on the file and go to properties. Click security, click on advance, and disable the inheritance. We will select Remove all inherited permissions from this object.

Add new permissions.

<img src="https://i.imgur.com/leT4sDi.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

Select a principal

<img src="https://i.imgur.com/xrtwdzi.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

In the box, type "Everyone"

<img src="https://i.imgur.com/ORqV57T.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

Select the full control box to automatically select the rest of the boxes

<img src="https://i.imgur.com/lXXwQqA.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

Click Apply and OK

<img src="https://i.imgur.com/i4SJiRL.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

You will continue to setup osTicket in the browser. Click Continue on the osTicket browser page. Fill out the page as required

From the Installation files we will download, HeidiSQL

<img src="https://i.imgur.com/RaYmFUQ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

Create a new session

<img src="https://i.imgur.com/JsHM1I5.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

Make sure that the user is "root" and that the password is "password1"

<img src="https://i.imgur.com/mZ3QG0e.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

Once connected to the session, go back to the Database settings and in the user you will put "root" and the password is "Password1"

We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". Name the new database "osTicket". Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.

<img src="https://i.imgur.com/KOqDRiJ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

The last step is to do some clean up. -Delete: C:\inetpub\wwwroot\osTicket\setup. Make sure to only delete the setup folder

Set the permissions back to "Read" in the ost-config.php file.

<img src="https://i.imgur.com/tHvqKKE.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/d6vA1YZ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

The final step is to login to osTicket

<img src="https://i.imgur.com/iZleuoS.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

osTicket has been successfully installed!!
