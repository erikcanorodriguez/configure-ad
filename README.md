<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Ensure Connectivity between the client and Domain Controller
- Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
- Login to DC-1 and install Active Directory Domain Service
- Join Client-1 to your domain (mydomain.com)

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/erikcanorodriguez/configure-ad/assets/168192619/551d0564-1c03-47aa-a0a7-94f203b7cca1" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the screenshot above we are ensuring connectivity between DC-1 which is our Domain Controller and our other VM which is labeled Client-1. We observe that when we connect to DC-1 from our Client-1 the request will time out showing no connectivity. We must then log in to our Domain Controller and enable ICMPv4 on the local windows Firewall. After we do this, notice how we get a response.

</p>
<br />

<p>
<img src="https://github.com/erikcanorodriguez/configure-ad/assets/168192619/9ef6a6d7-68d0-4820-8bda-d43c9b6eb68f" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After making sure there is connectivity between the two virtual machines we then go and install the Active Domain Services on our server manager on the “DC-1” VM. From here is where we will create our new forest labeled “mydomain.com”. 

</p>
<br />

<p>
<img src="https://github.com/erikcanorodriguez/configure-ad/assets/168192619/a40e4dd6-2b6b-408f-a87e-94755fc2d4a9" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We can create the forest as a DC from the previously installed Domain Services. We go on our main server and just promote a new forest and we call it “mydomain.com” which is what will be used whenever a user connected to the DC will have to use it when trying to log in.
</p>
<br />
<img src="https://github.com/erikcanorodriguez/configure-ad/assets/168192619/3f9c14eb-78cd-4647-8961-7523c3a8b3ed" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, We log into the client-1 virtual machine and connect it to the forest we just created in our DC-1 VM. When we make client-1 a member of the domain created on the other VM it will restart and once it restarts we have successfully connected the two VMS on one domain.
