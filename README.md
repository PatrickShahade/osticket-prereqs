# osticket-prereqs

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This is an outline for the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Set up VM
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
First, in Azure, I'm creating a basic VM to operate our Help Desk from. For size, I used Standard_D2s_v3 - 2 vcpus, 8GiB memory. 
</p>
<p>
<img src=https://i.imgur.com/jVpWRlC.png/>
  <img src=https://i.imgur.com/wzbkNZl.png/>
</p>
<br />

<p>
From within the VM, we're going to download an osTicket installation zip file and unzip it onto our desktop. The one I'm using has additional files we'll need for setup. osTicket has documentation for all these files, this zip just has them all compiled already for us.
</p>
<p>
<img src=https://i.imgur.com/6qnobCe.png/>
  <img src=https://i.imgur.com/n9fPIyq.png/>
</p>
<br />

<p>
From here we can click start and open the control panel, then access programs and features. We opt to turn Windows features on/off and we enable Internet Information Services and CGI. 
</p>
<p>
<img src=https://i.imgur.com/AHXVFqd.png/>
  <img src=https://i.imgur.com/MWINerv.png/>
  <img src=https://i.imgur.com/aEzRLog.png/>
</p>
<br />

<p>
After this, we're going to install PHP manager and Rewrite Module from our installation zip. Both of these are required for our osTicket setup, though they might seem unrelated.
</p>
<p>
<img src=https://i.imgur.com/prqELE7.png/>
  <img src=https://i.imgur.com/3OAa7Q9.png/>
</p>
<br />

<p>
We'll make a directory for PHP real quick in our C drive, then extract our PHP zip from our installation folder into our directory.
</p>
<p>
<img src=https://i.imgur.com/l7YeoXq.png/>
  <img src=https://i.imgur.com/6D5uHKS.png/>
</p>
<br />

<p>
We have a few more files to install. So we'll go ahead and install this C++ Redistributable file and MySQL with the "Typical" setup option with "Standard" configuration.
</p>
<p>
<img src=https://i.imgur.com/2bXQNvH.png/>
  <img src=https://i.imgur.com/oq0E49W.png/>
  <img src=https://i.imgur.com/3QZPBeq.png/>
</p>
<br />

<p>
For this demo, when we arrive at this section of the MySQL, we're just using "root" as our password here. This wouldn't be practical for real applications, but here we're just covering the install. 
</p>
<p>
<img src=https://i.imgur.com/garkODX.png/>
  <img src=https://i.imgur.com/C1cERCR.png>
</p>
<br />

<p>
Next we're going to open IIS as an admin so we can configure PHP. We access the PHP manager, register a new PHP version, and provide/browse to our path to the php-cgi file. 
</p>
<p>
<img src=https://i.imgur.com/dWh2vuJ.png/>
  <img src=https://i.imgur.com/YBf7vZj.png/>
  <img src=https://i.imgur.com/fBVKYTY.png/>
  <img src=https://i.imgur.com/dwPR9Jd.png/>
</p>
<br />

<p>
We'll do a quick restart of our IIS to ensure everything is up to speed.
</p>
<p>
<img src=https://i.imgur.com/6BBJ2g9.png/>
  <img src=https://i.imgur.com/pVvfcxD.png/>
</p>
<br />

<p>
From our installation folder, we're going to finally extract our osTicket! From there, we can copy our "upload" folder and move it into "C:\inetpub\wwwroot" and rename it to "osTicket".
</p>
<p>
<img src=https://i.imgur.com/vzvxYu3.png/>
  <img src=https://i.imgur.com/ALebDsl.png/>
  <img src=https://i.imgur.com/s4jPAUn.png/>
</p>
<br />

<p>
We'll do a quick restart of our IIS just like we did a couple steps before. Then we can navigate to Sites > Default Web Site > osTicket and find browse *80. This should pull up an osTicket installer page that shows us what else we may need to configure. 
</p>
<p>
  <img src=https://i.imgur.com/JjphPUu.png/>
  <img src=https://i.imgur.com/Z7xs7nN.png/>
  <img src=https://i.imgur.com/z5MqsAG.png/>
</p>
<br />

<p>
We'll go ahead and configure a few more settings from our IIS. If we go to our osTicket in IIS, we can enable some settings in PHP. If we right click these greyed out options, we're looking for php_imap.dll, php_intl.dll, and php_opcache.dll. Refreshing the browser should show that we enabled some new things!
</p>
<p>
<img src=https://i.imgur.com/eOcQRtK.png/>
  <img src=https://i.imgur.com/qyNCZ19.png/>
  <img src=https://i.imgur.com/FXYWkxv.png/>
</p>
<br />

<p>
Next we need to rename a file on the harddrive that osTicket uses to make configurations. We can navigate get here from the file explorer with this C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php. What we're trying to do is rename "ost-sampleconfig.php" to "ost-config.php".
</p>
<p>
<img src=https://i.imgur.com/7LiAERG.png/>
  <img src=https://i.imgur.com/vAE1Gz5.png/>
</p>
<br />

<p>
Now we need to set permissions for osTicket to make changes to this file. Right clicking that file, we can go to Properties > Security > Advanced > "Remove all inherited permissions from this object". From here, just for the sake of the demo, we're going to Add "Everyone" and select full control from the check boxes. Obviously, this would be dangerous is we were actually in a real world setting, but nobody is using this set up. Apply and Okay. Now osTicket has full control to the config file. 
</p>
<p>
<img src=https://i.imgur.com/hfWdsie.png/>
  <img src=https://i.imgur.com/mPZalRG.png/>
  <img src=https://i.imgur.com/wOZSFMh.png/>
  <img src=https://i.imgur.com/B1Qkd6m.png/>
</p>
<br />

<p>
From the setup page in the browser, we can continue our setup and fill out some information. But before we can go past this page, we're sstill missing database information. So we'll need to finally use our last install file from our installation folder, HeidiSQL.
</p>
<p>
<img src=https://i.imgur.com/whUBbnK.png/>
  <img src=https://i.imgur.com/uysnFRs.png/>
  <img src=https://i.imgur.com/pe6zC6A.png/>
</p>
<br />

<p>
After opening it, we need to connect HeidiSQL to our database and set it up for osTicket to use. We'll click "New" and the username is already set to root. We'll use our password from earlier that we also set to root. After opening it up we can see our database. Now we need to make a new database called "osTicket" just like our folder we renamed before. 
</p>
<p>
<img src=https://i.imgur.com/lhd5EGv.png/>
  <img src=https://i.imgur.com/8DCfxGE.png/>
  <img src=https://i.imgur.com/FTd1VDC.png/>
  <img src=https://i.imgur.com/h9fS5Jv.png/>
</p>
<br />

<p>
Back in our browser, we can now add our database settings and click install now! That should do it. osTicket should be operational now! Plus we can see some stuff in our HeidiSQL database. 
</p>
<p>
<img src=https://i.imgur.com/ZwFPUQk.png/>
  <img src=https://i.imgur.com/YWysw04.png/>
  <img src=https://i.imgur.com/fi0hAkX.png/>
</p>
<br />

<p>
You can see both the admin and end user logins, as well as our operational Helpdesk.
</p>
<p>
<img src=https://i.imgur.com/5LL8aFP.png/>
  <img src=https://i.imgur.com/YLKTwV9.png/>
  <img src=https://i.imgur.com/9jRxLIT.png/>
</p>
<br />
