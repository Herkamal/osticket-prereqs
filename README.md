

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

<p>Before installing osTicket, some configurations must be made within IIS. Open Internet Information Services (IIS) Manager as an administrator and select PHP Manager. In PHP Manager, click on Register new PHP version, then choose Browse and navigate to the php-cgi.exe file located in the C:\PHP folder created earlier in the lab. Select the executable to register the PHP version. Once the PHP version is registered, reload the IIS server from within the IIS Management Console to apply the changes.</p>


<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/osticket-extract.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/upload-transfer.png height="80%" width="80%" alt="Installation Steps"/>
</p>

From the installation files, download osTicket v1.15.8. Extract the contents and copy the "upload" folder to the following path: C:\inetpub\wwwroot. Once copied, rename the "upload" folder to "osTicket" within the wwwroot directory. After renaming, reload the IIS server to apply the changes.


<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/osticket-open.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/enable.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>In the IIS Manager, navigate to Sites > Default Web Site > osTicket. Click "Browse *:80" to open the osTicket installation page in your default browser. At this point, you may see warnings about missing or disabled PHP extensions.

To resolve this, return to the osTicket site menu in IIS and open PHP Manager. Click on "Enable or disable an extension" and enable the following extensions:

-  php_imap.dll

-  php_intl.dll

-  php_opcache.dll

These extensions are required for osTicket to function properly.</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/rename-ost-sampleeconfig-php.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/ost-config-property.png height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before proceeding with the osTicket installation, a configuration file needs to be renamed and its permissions adjusted.

Navigate to C:\inetpub\wwwroot\osTicket\include and rename the file ost-sampleconfig.php to ost-config.php.

Next, update the file’s permissions by right-clicking on ost-config.php and selecting Properties. In the Security tab, click Advanced, then Disable inheritance and choose Remove all inherited permissions from this object. After that, click Add, select Select a principal, type Everyone, and click Check Names. Set Full control permissions for Everyone and click OK to apply.
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/heidisql.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/heidi-setup.png height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>Download and install HeidiSQL from the installation files. Once installed, open HeidiSQL and create a new session. Use the password that was set during the MySQL installation (Password1 by default).

Within the newly created session, right-click on Unnamed and select the option to create a new database. Name the new database osTicket.</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/osticket-login.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>
<img src=https://github.com/Herkamal/osticket-prereqs/blob/main/osticket-admin.png height="80%" width="80%" alt="Installation Steps"/>
</p>

<p>After completing the installation, osTicket should now be up and running! Before using the system, a bit of cleanup is required.
First, delete the setup folder located at C:\inetpub\wwwroot\osTicket to secure the installation.
Then, go back to C:\inetpub\wwwroot\osTicket\include and adjust the permissions on the ost-config.php file. This file should no longer have Full control access for Everyone. Update the permissions to allow Read access only to enhance security.</p>

<h2>osTicket is now installed</h2>

