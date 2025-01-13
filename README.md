# osticket-prereqs

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This is an outline/guide for preparing the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- osTicket
- PHPManagerForIIS
- ISS URL Rewrite Module
- Microsoft Visual C++ Redistributable
- MySQL
- HeidiSQL

<h2>Installation Steps</h2>

<p>
1) In Azure, I'm creating a basic Virtual Machine (VM) to operate a Help Desk from. This is all I configured before creating. 
</p>
<p>
<img src=https://i.imgur.com/jVpWRlC.png/>
  <img src=https://i.imgur.com/wzbkNZl.png/>
</p>
<br />

<p>
2) I've logged into my VM, and now I'm going to download an <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket installation zip file</a> and unzip it onto the desktop. osTicket has documentation for all the files required for setup, this zip just has them all compiled already.
</p>
<p>
<img src=https://i.imgur.com/6qnobCe.png/>
  <img src=https://i.imgur.com/n9fPIyq.png/>
</p>
<br />

<p>
3) From here I used the search bar to find the control panel, and then selected "programs and features". We opt to turn Windows features on/off and we enable Internet Information Services and CGI. 
</p>
<p>
<img src=https://i.imgur.com/AHXVFqd.png/>
  <img src=https://i.imgur.com/MWINerv.png/>
  <img src=https://i.imgur.com/aEzRLog.png/>
</p>
<br />

<p>
4) After this, I'm going to install PHP manager and Rewrite Module from the installation zip. These are required for installation. 
</p>
<p>
<img src=https://i.imgur.com/prqELE7.png/>
  <img src=https://i.imgur.com/3OAa7Q9.png/>
</p>
<br />

<p>
5) I need to make a directory/folder for PHP in our C drive, then extract the PHP zip from the installation folder into the directory.
</p>
<p>
<img src=https://i.imgur.com/l7YeoXq.png/>
  <img src=https://i.imgur.com/6D5uHKS.png/>
</p>
<br />

<p>
6) Just a few more files to install. I install this C++ Redistributable file and MySQL with the "Typical" setup option with "Standard" configuration.
</p>
<p>
<img src=https://i.imgur.com/2bXQNvH.png/>
  <img src=https://i.imgur.com/oq0E49W.png/>
  <img src=https://i.imgur.com/3QZPBeq.png/>
</p>
<br />

<p>
7) For this demo, when I arrive at this section of the MySQL, I'm just using "root" as our password here. This would NOT be practical/recommended for real applications, but since I'm just covering the install I don't wanna get too mixed up. 
</p>
<p>
<img src=https://i.imgur.com/garkODX.png/>
  <img src=https://i.imgur.com/C1cERCR.png>
</p>
<br />

<p>
8) Next I'm going to open IIS as an administrator so I can configure PHP. Select the PHP manager, register a new PHP version, and provide a path to the php-cgi file. 
</p>
<p>
<img src=https://i.imgur.com/dWh2vuJ.png/>
  <img src=https://i.imgur.com/YBf7vZj.png/>
  <img src=https://i.imgur.com/fBVKYTY.png/>
  <img src=https://i.imgur.com/dwPR9Jd.png/>
</p>
<br />

<p>
9) I use the restart option in IIS to ensure everything is up to speed.
</p>
<p>
<img src=https://i.imgur.com/6BBJ2g9.png/>
  <img src=https://i.imgur.com/pVvfcxD.png/>
</p>
<br />

<p>
10) From the installation folder, I can finally extract our osTicket! From there, I copy the "upload" folder and move it into "C:\inetpub\wwwroot" and rename it to "osTicket".
</p>
<p>
<img src=https://i.imgur.com/vzvxYu3.png/>
  <img src=https://i.imgur.com/ALebDsl.png/>
  <img src=https://i.imgur.com/s4jPAUn.png/>
</p>
<br />

<p>
11) I do another restart of IIS just as before. Then navigate to Sites > Default Web Site > osTicket and find browse *80. This should pull up an osTicket installer page that shows us what else we may need to configure. 
</p>
<p>
  <img src=https://i.imgur.com/JjphPUu.png/>
  <img src=https://i.imgur.com/Z7xs7nN.png/>
  <img src=https://i.imgur.com/z5MqsAG.png/>
</p>
<br />

<p>
12) Time to configure a few more settings from IIS. Within the osTicket file in IIS, I need to enable some extensions in PHP by right clicking greyed out options and selecting "enable". I'm looking for <b>php_imap.dll, php_intl.dll, and php_opcache.dll</b>. Refreshing the browser should show these things have been enabled.
</p>
<p>
<img src=https://i.imgur.com/eOcQRtK.png/>
  <img src=https://i.imgur.com/qyNCZ19.png/>
  <img src=https://i.imgur.com/FXYWkxv.png/>
</p>
<br />

<p>
13) Next I need to rename a file on the harddrive that osTicket uses to make configurations. I can navigate there from the file explorer with this C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php. What I'm trying to do is rename "ost-sampleconfig.php" to "ost-config.php".
</p>
<p>
<img src=https://i.imgur.com/7LiAERG.png/>
  <img src=https://i.imgur.com/vAE1Gz5.png/>
</p>
<br />

<p>
14) Now to set permissions for osTicket to make changes to this file. Right clicking that file, we can go to Properties > Security > Advanced > "Remove all inherited permissions from this object". From here, just for the sake of the demo, I'm going to Add "Everyone" and select full control from the check boxes. Just like the root password, this would be dangerous in a real world setting. But this is a demo and nobody is using this set up. Apply and Okay. Now osTicket has full control to the config file. 
</p>
<p>
<img src=https://i.imgur.com/hfWdsie.png/>
  <img src=https://i.imgur.com/mPZalRG.png/>
  <img src=https://i.imgur.com/wOZSFMh.png/>
  <img src=https://i.imgur.com/B1Qkd6m.png/>
</p>
<br />

<p>
15) From the setup page in the browser, I can continue setup and fill out some information. But before I can go past this page, I'm still missing database information. So I'll need to finally use our last install file from our installation folder, HeidiSQL.
</p>
<p>
<img src=https://i.imgur.com/whUBbnK.png/>
  <img src=https://i.imgur.com/uysnFRs.png/>
  <img src=https://i.imgur.com/pe6zC6A.png/>
</p>
<br />

<p>
16) After opening it, I need to connect HeidiSQL to the database and set it up for osTicket to use. I'll click "New" and the username is already set to root. I'll use that silly password from earlier that I also set to root. After opening it up you can see the database. Now I need to make a new database called "osTicket" just like the folder we renamed before. 
</p>
<p>
<img src=https://i.imgur.com/lhd5EGv.png/>
  <img src=https://i.imgur.com/8DCfxGE.png/>
  <img src=https://i.imgur.com/FTd1VDC.png/>
  <img src=https://i.imgur.com/h9fS5Jv.png/>
</p>
<br />

<p>
17) Back in the browser, I can now add the database settings and click install now! That should do it. osTicket should be operational now! Plus you can see some stuff in the HeidiSQL database. 
</p>
<p>
<img src=https://i.imgur.com/ZwFPUQk.png/>
  <img src=https://i.imgur.com/YWysw04.png/>
  <img src=https://i.imgur.com/fi0hAkX.png/>
</p>
<br />

<p>
Both the admin and end user logins, as well as the operational Helpdesk.
</p>
<p>
<img src=https://i.imgur.com/5LL8aFP.png/>
  <img src=https://i.imgur.com/YLKTwV9.png/>
  <img src=https://i.imgur.com/9jRxLIT.png/>
</p>
<br />
