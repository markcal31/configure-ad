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

