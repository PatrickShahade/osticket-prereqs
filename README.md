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
