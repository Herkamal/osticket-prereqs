

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>


<h1>osTicket - Prerequisites and Installation</h1>

Welcome to this lab. I will perform a complete installation of osTicket from scratch using all the required setup files. Before installing the ticketing system, several preparatory steps must be completed. The lab is conducted on a Windows 10 Pro virtual machine hosted on Azure. All the necessary installation files can be found <b><a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here</a></b>. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- MySQL

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Installation Steps</h2>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/cgi.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>Before installing any files, Internet Information Services (IIS) must be enabled, as osTicket relies on it to function when installed locally. To enable IIS, start by opening the Control Panel. From there, navigate to Programs > Turn Windows features on or off. In the Windows Features window, expand Internet Information Services, then expand Web Management Tools, and check IIS Management Console. Next, expand World Wide Web Services, followed by Application Development Features, and ensure that CGI is selected. Click OK to apply the changes.</p>


<p>
<img src="https://github.com/Herkamal/osticket-prereqs/blob/main/php-install.png" height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>Once IIS is enabled, download and install PHP Manager for IIS (PHPManagerforIIS_V1.5.0) from the installation files folder.</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/rewrite-module.png height="80%" width="80%" alt="Installation Steps"/>
</p>

After installing PHP Manager for IIS, download and install the Rewrite Module (rewrite_amd64_en-US).

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/PHP-folder.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>Once the Rewrite Module is installed, create a new directory named C:\PHP on the Windows (C:) drive. This folder will serve as the destination for the extracted contents of the PHP 7.3.8 archive (php-7.3.8-nts-Win32-VC15-x86.zip) found in the installation files.</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/Php-extract.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>Unzip all contents of the archive into the C:\PHP directory.</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/vc-redist.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>Next, download and install VC_redist.x86.exe from the installation files directory.</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/mysql.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files. During the MySQL Setup Wizard, accept the license agreement by clicking "I agree", then choose Typical installation and click Install. Once installation is complete, launch the MySQL Configuration Wizard.
Select Standard Configuration, then check Install As Windows Service and ensure Launch the MySQL Server automatically is selected.
For credentials, set the username to root and the password to root.</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/iis.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/php-upload.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/php-stop-and-start.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>Before installing osTicket, some configurations must be made within IIS. Open Internet Information Services (IIS) Manager as an administrator and select PHP Manager. In PHP Manager, click on Register new PHP version, then choose Browse and navigate to the php-cgi.exe file located in the C:\PHP folder created earlier in the lab. Select the executable to register the PHP version.Once the PHP version is registered, reload the IIS server from within the IIS Management Console to apply the changes.</p>
