<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1 align= "center">osTicket Installation on Azure Windows 10 VM</h1>
This lab shows users how to establish a Windows 10 Virtual Machine (VM) on Azure and install osTicket, a popular open-source help desk system. To guarantee that osTicket functions successfully, the process comprises configuring IIS, PHP, MySQL, and any requirements.<br />




<h2 align= "center" >Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Remote Desktop (RDP)
- Internet Information Services (IIS)

<h2  align= "center">Operating Systems Used </h2>

- Windows 10 (21H2) </b> 

<h2 align= "center">Prerequisites</h2>

- Azure Virtual Machine
- [osTicket Installation files](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)
- Heidi SQL

<h2 align= "center" >Installation Steps</h2>

<h4> Deploy Azure Windows 10 VM </h4>
<ul>
<li>Create a Windows 10 VM with 4 vCPUs.</li>
</ul>
<p>
 <img src="https://github.com/user-attachments/assets/9dc23b92-9aa1-4a35-9af9-8d8a697bd49f" height= 80% width= 80%/>
</p>
<ul>
<li>Connect to your VM using RDP using the public IPv4 address.</li>
</ul> 
<h6>If you are a Mac user download Microsoft Remote Desktop (RDP). </h6>

<img src="https://github.com/user-attachments/assets/980c3333-c479-41a4-9d00-45fe963a1c70"/>
</p>
<p>
Great, you are connected to your VM! &#128522; </p> 
<p></br></p>
<h4>Install Required Components</h4>
<ul><li>Open the <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> link</a> in the web browser of your osTicket-VM, download and extract its contents.</li></ul>
<h6> ( Optional) Add the folder containing extracted files to VM Desktop. </h6>

<p>  
<img src="https://github.com/user-attachments/assets/d70f3aac-c21b-45a9-9e9c-60bbe9e9e679"  height= 80% width= 80%/>
</p>

<ul>
<li>Enable IIS with CGI support.</li>
</ul>
<h5>Internet Information Services (IIS) is a web server that allows the creation of a working osTicket system.  </h5>
<h6>Open the Control Panel in the VM > Program > Turn Windows on or off > Internet Information Services > World Wide Web Services > Application Development Features > [X] CGI > OK </h6>
<p>
<img src="https://github.com/user-attachments/assets/b21c4c8b-9563-43ab-8233-761ec04ec794">
</p>
<h6> &#128680;Make sure these are marked.&#128680;</h6>
<p> <img src="https://github.com/user-attachments/assets/11e50b36-489a-419b-a410-ddd863687feb">
</p>
<p>
<img src="https://github.com/user-attachments/assets/be67a0ff-be22-4eea-ad99-81427c3a5e8e" height= 60% width= 60% >  
</p>
<h6> CGI is needed to download the PHP Manager. </h6> 
<p> <b>To confirm IIS is enabled: </b>Open the web browser and type in "127.0.0.1", this loop address allows the testing of osTicket without needing an external IP address. The following image should open:</p>
<p>
<img src="https://github.com/user-attachments/assets/c7f2efe9-fc02-4b3d-8f94-2d3fd53369c1"  height= 80% width= 60% >
</p>
<p></br></p>
<ul>
<li>Install PHP Manager for IIS and the Rewrite Module.</li>
</ul>
<p>
 The PHP manager is a back-end web programming language that allows osTicket to run off a web browser.
</p>
<p>
<img src="https://github.com/user-attachments/assets/d63f630b-635d-45eb-8687-4050f7abab6d" height= 80% width= 60%>
</p>
<p>
<img src="https://github.com/user-attachments/assets/fe099410-f772-4386-89a1-4169c75aff19" height= 50% width=50% >
</p>

<ul>
<li>Create the directory C:\PHP.</li>
</ul>
<p>
<img src="https://github.com/user-attachments/assets/2d72ceeb-5352-4882-a6a3-046005f8bd18" height= 60% width= 60%/>
</p>
<ul>
<li>Extract from the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
 </li>
</ul>
<p>
<img src="https://github.com/user-attachments/assets/d4508a73-aa11-4a70-97c1-88c6176d20d5" height= 80% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/4199653b-cc1c-4f86-9ae7-99fff5788982">

</p>
<ul>
<li>Install VC_redist.x86.exe.</li>
</ul>
<p>
<img src="https://github.com/user-attachments/assets/bfbcdd48-5512-4677-a3ba-dd008ad11db0"/>
</p>
<ul>
<li>Install MySQL 5.5.62 (mysql-5.5.62-win32.msi)</li>
</ul>

<p>
  <img src="https://github.com/user-attachments/assets/dda0afe8-f990-4fab-ba0c-f9fa35f80e99">
</p>
<p>
  <img src="https://github.com/user-attachments/assets/b4e86031-feb7-4c75-8b29-64f4f80d1ac1">
</p>
<p>
  <img src="https://github.com/user-attachments/assets/39d571ed-246f-4f78-a04b-50d4f62ee2d7">
</p>
<p>
  <img src="https://github.com/user-attachments/assets/845aa68c-1b38-4b62-9a0c-b2173d8bde90">
</p>
<p>
  <img src="https://github.com/user-attachments/assets/42b29b7c-67b8-44e2-8642-d80420dedb8f">
</p>
<h6> Username: root Password: root</h6>
<p>
  <img src="https://github.com/user-attachments/assets/e0a76697-7d83-499d-9474-43495717c8e1">
</p>
<p></br></p>
<h4>Configure IIS and Install osTicket</h4>
<ul>
<li> Register PHP in IIS and restart the web server.</li>
</ul>
<p>
  <img src="https://github.com/user-attachments/assets/cd5116e2-51c7-49c3-b950-cf2cf3d1a50a"  height= 60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/57b0571c-564b-4a50-8e20-b5f3106e8c18" height= 60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/b1973637-de6d-424b-9d33-93d73ded1906">
</p>
<p>
  <img src="https://github.com/user-attachments/assets/69cdeded-2ce8-4fc3-b890-6ba5da753f42"height=60% width= 60%>
</p>
<ul>
<li> Install osTicket v1.15.8 under c:\inetpub\wwwroot\osTicket. </li>
</ul>
<p>
  <img src="https://github.com/user-attachments/assets/1b29f7d8-1005-4e2b-af92-04a95a653456"height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/0b8c2d03-a542-4926-8cc7-8f1ffea78eb1"height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/8e3661ad-b48f-4ce0-bf32-ced5de04f91a"height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/39fd7c81-e608-4b99-9af9-ac73fbac997f"height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/69cdeded-2ce8-4fc3-b890-6ba5da753f42"height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/df00464b-7cd8-4965-a641-e7610463be63"height=60% width= 60%>
</p>
<ul>
<li>Enable required PHP extensions. </li>
</ul>
<p>
  <img src="https://github.com/user-attachments/assets/da3a21d5-0bb0-4a33-8553-c09077058a1a" height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/fe7f2728-2867-4678-9aca-d312e261cb8e" height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/0f0b5fe0-254e-4a30-8d57-1d4b85005a28" height=40% width= 30%>
</p>

<ul>
<li>Configure osTicket settings and rename ost-config.php</li>
</ul>
<p>
  <img src="https://github.com/user-attachments/assets/2e18d2e6-fabd-4217-9cab-7d176892e24a"height=60% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/a7e8fe6f-9f95-4b2a-b779-a7b30ed9ecbd"height=60% width= 60%>
</p>
<ul>
<li>Assign appropriate file permissions. </li>
</ul>
<p>
  <img src="https://github.com/user-attachments/assets/785acb62-b932-4be7-965b-48faef1f6f3b"height=40% width= 30%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/846e4750-d5d7-419b-b0b9-d29d49973073"height=50% width= 30%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/6725fd61-b2c3-4ad3-b3e1-f62bc8d65bd4"height=50% width= 50%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/e7981d99-4bd8-473d-a88a-48e876a74956"height=40% width= 50%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/eee7597e-7e86-4be2-9c8f-a1363443455b"height=50% width= 50%>
</p>
<h6> For test purposes only, use "everyone".</h6>
<p>
  <img src="https://github.com/user-attachments/assets/4ed7edba-1d0b-4b12-8211-dfa701ac3d53">
</p>
<h6> For test purposes only, select "full control".</h6>
<p>
  <img src="https://github.com/user-attachments/assets/0964f46b-9b68-49fd-94cb-11a298cb148f"height=50% width= 50%>
</p>

<h4> Database Setup (HeidiSQL & MySQL)</h4>
<ul>
<li>Install HeidiSQL and connect to MySQL. </li>
</ul>
<p>
  <img src="https://github.com/user-attachments/assets/d8cff54a-3a46-4cf2-93b5-171b461796f2"height=50% width= 60%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/c157a2a9-b21f-4bd1-a61d-7cd7355cc9fc"height=50% width= 40%>
</p>
<p>
  <img src="![image](https://github.com/user-attachments/assets/e54bbba6-ee09-4ce8-b430-31ef8b5a5b71"height=40% width= 40%>
</p>
<p>
  <img src="https://github.com/user-attachments/assets/1037f081-76ea-48e7-a597-94330fbc9216"height=50% width= 50%>
</p>
<h6> Username: root Password: root</h6>
<p></br></p>
<li>Create the osTicket database. </li>
</ul>
<p>
  <img src="https://github.com/user-attachments/assets/d52fcca5-9d53-4944-9d75-6abb73fea76d"height=50% width= 40%>
</p>
<p>
  <img src="![image](https://github.com/user-attachments/assets/35b78c3f-0d54-4c0b-82c9-a98276bde55e)
">
</p>
<ul>
<li>Complete osTicket browser setup using MySQL credentials.</li>
</ul>


<p>
  <img src="https://github.com/user-attachments/assets/6d2219bf-9c99-4ffb-b949-92a7a074d9cb"height=50% width= 40%>
</p>
<h6>System Settings and Admin User information can vary. </h6>
<p>
  <img src="https://github.com/user-attachments/assets/f16c59d2-1b8d-47e3-a162-ea3a54cec63b"height=50% width= 50%>
</p>
<p></br></p>
<h5>Clean up</h5>
<p>Delete: C:\inetpub\wwwroot\osTicket\setup</p>
<p> <img src="https://github.com/user-attachments/assets/d3c83ea5-07ca-44d5-b4b5-653f0edb74fe"height=60% width= 50%>
</p>
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
  <p>
    <img src="https://github.com/user-attachments/assets/5d5dbab3-d19e-473c-942d-326358f986ed"height=50% width= 50%>
</p>
   <p> <img src="https://github.com/user-attachments/assets/9ece7f32-0f57-43f7-b301-50b54a08b665"height=40% width= 30%>
</p>
Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)


<h5> Officially done with the Prerequisites! &#129325; </h5>
