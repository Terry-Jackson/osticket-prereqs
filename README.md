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

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


<h2>Installation Steps</h2>
1.) The first thing you will need to do is to create a resource group for your project. Don't forget to delete after completion.
</p>


2.) The second thing you are going to want to do is create a virtual machine by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. Note, you will want to create a virtual machine with atleast 2 vcpus and 16 gbs of memory.

3.) Once you have created your virtual machine you will want to conncet to it by using the public ip address the vm is setup with. You will connect using the remote desktop connection app. 
</p>

<br />


![create rg](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/daf20c06-2ff6-4d9a-b483-edd0d659e6af)



<p>

  ![tempsnip](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/adb74230-44fa-42fb-891e-7423d29f44c5)

</p>
<p>
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/d8bf4e4a-aa8a-46b8-9de9-7b0b7287bfc6)
</p>
<p>
  
3.) Once you have connected to your virtual machine you will want to go to your control panel. From the control panel open up programs. Select, Turn Windows features on and off.

<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/ab772589-7764-4736-a794-9eec1aa84986)
  
  </p>
<p>
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/ab8f7156-9bdf-4473-8b38-19253a3a4053)

</p>
<p>
  
4.) You will want to install / enable IIS in Windows with CGI and Common HTTP Features
  - World Wide Web Services -> Application Development Features -> 
[X] CGI
[X] Common HTTP Features
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/8e08a8a7-d1e2-402e-b744-652b335a5c25)

</p>
<p>
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/b3798235-8226-4202-8340-a01fd605f151)

</p>
<p>
  
***NOTE*** Make sure all Common HTTP Features are checked.
 
 To make sure the IIS is installed / enabled go to a browser of your choice and search for 127.0.0.1 
  It should look something like this. 
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/b7bdbc01-d878-4530-bb2b-57c2b625b21e)

</p>
<p>
  
  
  
  
5.) Now that the IIS is enabled, From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
  Go through the install wizard and complete the install.
  
6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
  
7.) Create a folder in the C drive called PHP.
  
8.) From the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
  
  !! ATTENTION !!
If this appears, choose to “Keep” the file:
  
<p>
<img src="https://imgur.com/xZv1Yhw.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/YwBhqo0.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

9.) Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe. 
  
10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  Run the setup wizard:
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

  Make the new root password: Password1
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/c14971c7-5664-4374-aacc-01de46366537)

</p>
<p>
  
  Finish the process.
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/81578b2e-b2f4-455d-ad7f-75464d925194)

</p>
<p>
  
11.) Now that we have the files downloaded and installed we will want to search for IIS in the windows search bar. Open IIS as an administrator.
  The program should look like this.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/32f1e878-2793-4ca6-97af-6c61870709e4)

</p>
<p>
  
12.) We will now want to register PHP from within IIS.
  Click on PHP Manager
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/314d7580-bbd8-4fcc-bbab-994349eac84d)

</p>
<p>
  
Register new PHP version.
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/6a76597d-df05-44dd-af59-2741f5b17073)

</p>
<p>
  
You will want to provide a path to the php executable file (php-cgi.exe)). 
  Go to C Drive -> PHP -> click on php-cgi file.
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/e9e7dab3-8f5a-4a99-90e7-e7a2853ca5b3)

</p>
<p>
  
  Restart the IIS server.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/0271ca85-0ef0-4a4e-86b9-b38250278015)

</p>
<p>
  
13.) Install osTicket v1.15.8
  -Download osTicket from the Installation Files Folder
  -Extract and copy "upload" folder to c:\inetpub\wwwroot
  -Within c:\inetpub\root, Rename "upload" to "osTicket"
  
  Reload IIS again.
  
14.) On IIS go to sites -> Default -> osTicket
  -On the right, click “Browse *:80”
  
<p>

![caps4](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/cf119334-824e-4877-a192-cf5f4ca05132)

</p>
<p>
  
  Some extensions are not enabled on the osTicket browser.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/f41fffb3-9388-4b69-b923-48b975c51fe4)

</p>
<p>
  
  To enable the extensions:
  -Go back to IIS, sites -> Default -> osTicket
  -Double click PHP manager
  -Click "Enable or disable an extension"
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/8f33700f-cf59-41dd-a6cc-6a437c8b836f)

</p>
<p>
  
<p>
</p>
</p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/94b1ef8e-66b3-4444-8b3e-18ad8dba63b3)


</p>
<p>
  
  We will want to enable three extensions from here.
  
  1.) php_imap.dll
 
  2.) php_intl.dll
  
  3.) php_opcache.dll
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/96cf13ea-be54-4136-9329-bbf10dda3f88)

</p>
<p>
  
  
15.) Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder.
  Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
  We are going to rename the ost-sampleconfig.php to ost-config.php
  
  Now that we have renamed the files, right click on the file and go to properties.
  From there click security, click on advance, and disable the inheritance.
  We will select Remove all inherited permissions from this object.
  
  Now we will add new permissions.
  
  Click Add
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/5d1ba32e-6a39-469b-8cea-2fc9305c3ec5)

</p>
<p>
  
Select a principal
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/505903b8-66bd-47b8-84fe-5d1291cd1d86)

</p>
<p>
  
  
 Type "Everyone" in the box.
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/dba0b94f-8477-48df-b41f-045ca30a4c49)


</p>
<p>
  
  Make sure Full Control and all the other boxes are checked.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/10a1b061-543f-4ec5-a1a3-cc226a230a04)

</p>
<p>
  
  Click Apply and Ok.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/2ed844d3-4ea0-4a74-99d6-10f524d8f957)

</p>
<p>
  
  Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page.
  Fill out the page as required except the Database Settings at the bottom of the page. We will get to that. 
  
  We will want to download and install HeidiSQL from the Installation Files. 
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/565a2dc8-0868-4c3c-aefb-0d35ca98a8f8)

</p>
<p>
  
  When the program is open we will create a new session in it.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/a8f54502-1362-4345-a1bf-34c5040b3bc3)

</p>
<p>
  
  We want to make sure the username is root and the password is Password1.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/af4b7832-853a-42e4-a965-0de340fd696f)

</p>
<p>
  
  Once we are connected to the session we will go back to the browser to finish setting everything up. Under the Database Settings in the browser the username will be root and the password will be Password1.
  
  We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". Name the new database osTicket. Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/53cbbb3f-ca92-413f-b36c-9568cdc15513)

</p>
<p>
  
  The last step is to do some clean up. We will want to delete the setup folder in our system. 
  -Delete: C:\inetpub\wwwroot\osTicket\setup
  Only delete the setup folder and nothing else.
  
  We then will want to set the permissions back to "Read" only in the ost-config.php file.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/b6dc5347-f70b-4702-8687-3c19074095fd)
</p>
<p>
  
<p>

  ![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/99b94e8d-6835-410b-b3fc-bcdf91692527)

</p>
<p>
  
  The last step after that is to login to osTicket on the browser.
  
<p>

![image](https://github.com/Terry-Jackson/osticket-prereqs/assets/155121596/4922cddd-1cd7-4416-a872-2744c7fe7d5e)

</p>
<p>
  
You have now successfully installed and setup osTicket!
