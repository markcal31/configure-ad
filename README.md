<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
In this lab I will outline the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>
<p> Setup Resources in Azure
<br> - Create the Domain Controller VM (Windows Server 2022) named “DC-1” </b>
<br> - Resource group: "AD-Lab" , Virtual Network (vnet): "DC-1-vnet"  </b>
</p>

![image](https://github.com/user-attachments/assets/2a80b8b3-5e64-44b7-9b16-306d3a65d55b)

![image](https://github.com/user-attachments/assets/2396368d-cc3a-4e8f-9be9-3758cdea963d)

<p>
  <br> - Set Domain Controller’s NIC Private IP address to be static </b>
</p>

![image](https://github.com/user-attachments/assets/fca29710-ec83-4a77-afb4-e7219bd634a5)

![image](https://github.com/user-attachments/assets/e609a85b-478b-4e56-a431-cc7a25102b4b)

<p>
  <br> - Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created for DC-1 </b>
</p>

![image](https://github.com/user-attachments/assets/4a322454-f53d-4675-9547-f5e3a327997d)

![image](https://github.com/user-attachments/assets/86811e72-1554-4253-9330-b1aa2d5127c4)

<p>
  <br> - Ensure that both VMs are in the same Vnet </b>
</p>

![image](https://github.com/user-attachments/assets/1f9cc18a-01fa-4f8f-a53d-0f221c4cd6fd)

![image](https://github.com/user-attachments/assets/0f8551a3-75c2-449b-ba90-a651c83baa7d)

<p>
  <br> Ensure Connectivity between the client and Domain Controller </b>
  <br> - Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping) </b>
</p>

![image](https://github.com/user-attachments/assets/8ab8be7b-2264-418c-a3b4-5616d3bf4220)

![image](https://github.com/user-attachments/assets/ac249ea3-e1b4-4770-9d5f-ec47d70102ab)

![image](https://github.com/user-attachments/assets/ccb2b77c-4323-4c29-bcef-1e527d9518c9)

![image](https://github.com/user-attachments/assets/3120b46c-b37e-4f23-89c7-4be4080ea832)

![image](https://github.com/user-attachments/assets/2c0a3f44-3aee-4563-b285-324929b3aea9)

![image](https://github.com/user-attachments/assets/bf2c6284-2804-443c-a899-84b4b6bbf639)

<p>
  <br> - Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall </b>
</p>

![image](https://github.com/user-attachments/assets/0a866243-dd2b-4cc2-aab1-bcb6cdf5aee7)

![image](https://github.com/user-attachments/assets/3795c108-cc37-45ec-968a-a33c02c78cc5)

![image](https://github.com/user-attachments/assets/6d819846-a3aa-496a-b5b1-5e7dbbd840b5)

![image](https://github.com/user-attachments/assets/766afe33-3535-4d20-ae85-e159e4a1357f)

![image](https://github.com/user-attachments/assets/96484acc-c88c-48c1-9f8d-47282a0757b1)

![image](https://github.com/user-attachments/assets/3c4a2d2c-261d-4942-a1cf-2af67b892961)

<p>
  <br> Install Active Directory </b>
  <br> - Login to DC-1 and install Active Directory Domain Services </b>
</p>

![image](https://github.com/user-attachments/assets/0cfc64c7-2655-4933-a80d-e1402290a13c)

![image](https://github.com/user-attachments/assets/71c9bd9e-e775-41f7-8cae-c6241c35078a)

![image](https://github.com/user-attachments/assets/e5b6dc7d-4318-451e-b2c2-ca8904d836f3)

![image](https://github.com/user-attachments/assets/0a6c066d-15d2-4ef1-baf3-717685407741)

![image](https://github.com/user-attachments/assets/52b3c744-8626-4612-b6e8-e9cdeae3ed3b)

![image](https://github.com/user-attachments/assets/8c89f7f5-e8bd-4537-ba90-8ae8a2e20102)

![image](https://github.com/user-attachments/assets/52cffe81-30ae-4378-995b-50c694e27370)

![image](https://github.com/user-attachments/assets/f52c1f37-b4a2-44af-b5aa-8b82286c5cb1)

![image](https://github.com/user-attachments/assets/8deaea51-d17b-4846-bed7-44374ed9e1bc)

<p>
  <br> - Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is) </b>
</p>

![image](https://github.com/user-attachments/assets/521cd73c-0a04-46a4-aea3-1552eb441d0a)

![image](https://github.com/user-attachments/assets/94f331a0-c68c-420a-a66e-312581cd971c)

![image](https://github.com/user-attachments/assets/e16576a1-d2b2-4184-a783-96b5709d08c9)

![image](https://github.com/user-attachments/assets/8d9ff08b-43bd-42ee-bc82-2252fef4794e)

<p>
  <br> - Restart and then log back into DC-1 as user: mydomain.com\labuser </b>
</p>

![image](https://github.com/user-attachments/assets/06f0c119-0a86-4476-8b6d-78d84c5f3c65)

<p>
  <br> Create an Admin and Normal User Account in AD </b>
  <br> - In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES” </b>
</p>

![image](https://github.com/user-attachments/assets/3762b577-2015-4859-aa3c-8c846c41f25d)

![image](https://github.com/user-attachments/assets/f1050673-326d-48a4-b45c-8e018eab14b3)

![image](https://github.com/user-attachments/assets/d283fb31-f860-41e4-84e5-1b602bee1aec)

![image](https://github.com/user-attachments/assets/2f71a0c6-e25b-49df-b04c-6af3043acc97)

<p>
  <br> - Create a new OU named “_ADMINS” </b>
</p>

![image](https://github.com/user-attachments/assets/4a0c611e-1f7a-4e59-ada2-6a8ea7bb785d)

<p>
  <br> - Create a new employee named “Jane Doe” (same password) with the username of “jane_admin” </b>
</p>

![image](https://github.com/user-attachments/assets/b5784cc5-f9b9-4c9f-8fb1-9bf80400480e)

![image](https://github.com/user-attachments/assets/fe55f5c5-549c-4f91-af3f-3bef920f93f3)

<p>
  <br> - Add jane_admin to the “Domain Admins” Security Group </b>
</p>

![image](https://github.com/user-attachments/assets/ede3d426-5800-4958-b3a0-cf3e8ad6b55b)

![image](https://github.com/user-attachments/assets/9cd10bf1-8021-4f9c-b4c3-607a17599d20)

![image](https://github.com/user-attachments/assets/8f67171f-7691-4d37-ac1b-4a2f1f79e4d1)

<p>
  <br> - Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin” </b>
</p>

![image](https://github.com/user-attachments/assets/44cef51e-661c-4dc5-a337-d801752335b0)

![image](https://github.com/user-attachments/assets/f9c37a89-afe8-4f05-857e-da7e7ea5c14a)

![image](https://github.com/user-attachments/assets/a7db085f-b2e1-4461-9342-b2d4fcd034ca)

<p>
  <br> Join Client-1 to your domain (mydomain.com) </b>
  <br> From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address </b>
</p>

![image](https://github.com/user-attachments/assets/440a6c0d-fcd8-4430-ba7e-7dcecbd9657f)

![image](https://github.com/user-attachments/assets/4a85818b-1211-466c-a321-cf821c056c23)

![image](https://github.com/user-attachments/assets/c80b4b16-7e0e-41d3-a9e4-26c5f34b8140)

![image](https://github.com/user-attachments/assets/440c8eb0-59db-4cd4-b811-54155b1461ef)

<p>
  <br> From the Azure Portal, restart Client-1 </b>
</p>

![image](https://github.com/user-attachments/assets/dc894af3-9f7b-4cc8-90ed-4d6b44fc06db)

<p>
  <br> Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart)
 </b>
</p>

![image](https://github.com/user-attachments/assets/ae0fec30-5095-4853-9c11-f9e3e6aa4459)

![image](https://github.com/user-attachments/assets/cd70d944-3af7-4fa5-8711-27d8184c44ad)

![image](https://github.com/user-attachments/assets/118ea166-0239-436f-abfe-6bb9e050dc6f)

![image](https://github.com/user-attachments/assets/4b17b1de-4786-451c-a00e-56f454816206)

<p>
  <br> - Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain </b>
</p>

![image](https://github.com/user-attachments/assets/d0d9757e-b9ad-49df-aee6-7e819458ea02)

<p>
  <br> Setup Remote Desktop for non-administrative users on Client-1 </b>
  <br> - Click “Remote Desktop” </b>
  <br> - Allow “domain users” access to remote desktop </b>
</p>

![image](https://github.com/user-attachments/assets/35adebe8-4f7d-4cc3-a65f-7b87b3164258)

![image](https://github.com/user-attachments/assets/26e37380-6d6f-4068-8b99-c89ad757acba)

![image](https://github.com/user-attachments/assets/a55778b4-a290-41bf-96ec-00b0edb6eaaa)

<p>
  <br> Create a bunch of additional users and attempt to log into client-1 with one of the users </b>
  <br> - Login to DC-1 as jane_admin </b>
</p>

![image](https://github.com/user-attachments/assets/9c1e54c1-71ab-4ba1-9be0-9fd3cf488673)

<p>
  <br> Create a new File and paste the contents of the script into it (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) </b>
</p>

![image](https://github.com/user-attachments/assets/4494fb2c-0b4e-423d-8758-74658640548a)

<p>
  <br> Run the script and observe the accounts being created </b>
</p>

![image](https://github.com/user-attachments/assets/c62340bb-40df-4526-ad0b-a05ea122658d)

<p>
  <br> When finished, open ADUC and observe the accounts in the appropriate OU
 </b>
</p>

![image](https://github.com/user-attachments/assets/4f373b2c-02b4-4031-925b-bebfec24e8f2)

<p>
  <br> attempt to log into Client-1 with one of the accounts (take note of the password in the script) </b>
</p>

![image](https://github.com/user-attachments/assets/5fd621da-656c-4b46-b496-3f5c8dd08936)

![image](https://github.com/user-attachments/assets/bd8f8875-5ada-4aae-a060-7a9b6f01650f)

Lab complete!
