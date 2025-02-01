<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
In this tutorial, I will be showcasing the prerequisites necessary for installing and operating the open source ticketing system known as osTicket.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Setup and use Azure Virtual Machine
- Install all required programs and files (WITHIN VIRTUAL MACHINE) provided here : https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 
- Enable IIS for hosting osTicket
- Install MySQL server for osTicket database 
- Install and configure osTicket
- Enable osTicket to catch/process emails
- Setup and enable database for osTicket

<h2>Installation Steps</h2>

1.) First, you will need an Azure account alongside a virtual machine to begin setting up osTicket. This VM will need to be using windows 10 (21H2). Once your vm is setup, take note of its public IP Address within Azure, this will be used to connect remotely to it from your local desktop

![image](https://github.com/user-attachments/assets/ab52f620-c0a3-4b65-a2c4-2f2e4163deb4)

2.) Once within VM, copy provided download link, paste into internet browser and install all required files, when done correctly, you will find a folder within File Explorer that looks like this.

![image](https://github.com/user-attachments/assets/8636f650-42f3-46b6-b92a-d86db2e66cbe)


3.) Next, navigate to your control panel, select programs and click "Turn Windows Features on or off" as highlighted in image below.

![image](https://github.com/user-attachments/assets/71c38ff2-633f-467a-a5e1-b3886bf44227)

4.) Here you will want to check multiple boxes as listed: Internet Information Services, CGI as well as all boxes for Common HTTP Features 

![image](https://github.com/user-attachments/assets/97b5092b-5306-4903-97d7-01e58ea970c2)

5.) Furthermore, to insure you are on the right track, type the ip address 127.0.0.1 into your browser to locate your localhost page. You will be redirected to the IIS webpage.

6.) Once here, navigate back to the installation folder and begin installing all programs in the listed order. 
  * PHPManagerforIIS
  * Rewrite_amd64
  * PHP 7.3.8 (NOTE: For this program, create a new folder in your local disk (C:) and name it PHP, unzip the contents of PHP 7.3.8 into said folder
  * VC_redist.x86
  * MySQL 5.5.62 (NOTE: You will be prompted to choose a setup option, click "Typical Setup", after this select "Standard Configuration", you will be asked to fill in a root password, do this and the program will run.

![image](https://github.com/user-attachments/assets/d083c6de-4535-4d85-b4f9-33d43e59c049)

</p>
<p>
7.) Next, within the start menu, select IIS and run as an administator, you will be greeted with this page 

![image](https://github.com/user-attachments/assets/3c4ac3c0-021e-4b89-9109-0f05c5ce2395)

</p>
<br />
8.) From here, select the PHP Manager and navigate to "Register PHP from within IIS", locate your PHP folder previously created and select PHP-cgi. 
<p>
  
![image](https://github.com/user-attachments/assets/e02818d1-5533-4758-a599-d1c1eb570c82)

9.) After arriving on the PHP Extensions screen select and enable the following extensions
  * php_imap.dll
  * php_intl.dll
  * php_opcache.dll
    
10.) When done, go back to the homescreen of the IIS, right click the program and restart it.

11.) Navigate to the osTicket.zip folder you previously downloaded, extract the folder labeled "upload" to c:inetpub\wwwroot, afterwards, rename the folder from "upload" to "osTicket. 

![image](https://github.com/user-attachments/assets/f60288a5-b752-454a-ba8e-8a5b7c3fb865)

12.) Return to IIS, click Sites-> Default -> osTicket. After, click "Browse *.80", this will redirect you to the osTicket homepage

![image](https://github.com/user-attachments/assets/4f52a60a-2974-4200-8d77-0bd2513dab37)

13.) Navigate back to osTicket folder in wwwroot and locate the following file: 
  * C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  *  Next, rename to "ost-config.php", open properties with right-click.
  *  Select Security tab, go to Advanced tab, disable the inheritance
  *  Add a new principal and name it "everyone", select full control access and apply

![image](https://github.com/user-attachments/assets/6f3d3bdc-5bd7-46fd-bb60-70d55f7956c0)

14.) Scroll back to osTicket homepage in browser, click continue and begin setup.
  * NOTE: Make sure the email for system settings and the admin email are NOT the same
  * Do not fill in Database Settings yet, you will need to install HeidiSQL before continuing

![image](https://github.com/user-attachments/assets/5fc887ec-233d-4e4f-978e-f5692c097805)

15.) Within the Installion files folder used towards the beginning, download, install and launch HeidiSQL.
  * From here, open a new database, name it "osTicket"
  * The user here is the same as MySQL, which is "root", alongisde the same password. Once done, click "Open" option
  * Return to the screen of step 14, fill out the Database settings with the information used for HeidiSQL and click install when done.

16.) Once done, you will e gretted with this page and links to the other pages in the images below.

![image](https://github.com/user-attachments/assets/f3c5920e-9e8c-4929-802d-513d1bfa965b)

![image](https://github.com/user-attachments/assets/abe55dec-ca3c-4e20-820b-3af4b8efa79c)

![image](https://github.com/user-attachments/assets/cd10f2d4-d517-440d-ab81-64e0df050031)

17.) Now, navigate back to File Explorer, go into the osTicket folder and delete the "setup" folder

![image](https://github.com/user-attachments/assets/0dca032d-dbcd-4e45-9be8-e12bf7e42122)

</p>
<p>
18.) Congrats, you are all setup to utilize osTicket, click the following link for the post-install configuration.
<br />
