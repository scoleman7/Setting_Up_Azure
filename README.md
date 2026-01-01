# Azure

<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Preparing Active Directory using Azure </h1>
This tutorial outlines step by step of setting up the infrastructure for active directory using Azure virtual machine. For practicing purposes we will start by setting the domain controller vm first and then creating a client and setting up that vm afterwards. During these steps you will create a username and password of your choosing when prompted. *Note---please jot down this information because it will be needed to login remotely. 


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 Setup Domain Controller in Azure
—
Create a Resource Group
Create a Virtual Network and Subnet
Create the Domain Controller VM (Windows Server 2022) named “DC-1” (Domain Controller)

After VM is created, set Domain Controller’s NIC Private IP address to be static
Log into the VM and disable the Windows Firewall (for testing connectivity)

Step 2 Setup Client-1 in Azure
—
Create the Client VM (Windows 10) named “Client-1”

Attach it to the same region and Virtual Network as DC-1
After VM is created, set Client-1’s DNS settings to DC-1’s Private IP address
From the Azure Portal, restart Client-1

Step 3 Login to Client-1

Step 4 Attempt to ping DC-1’s private IP address
Ensure the ping succeeded

Step 5 From Client-1, open PowerShell and run ipconfig /all
The output for the DNS settings should show DC-1’s private IP Address



<h2>Deployment and Configuration Steps</h2>

<p>
<img <img width="1598" height="769" alt="Screenshot 2025-11-04 0535132" src="https://github.com/user-attachments/assets/35bcbc44-7688-4c18-a0fb-ccc326683bfb" />
 />

</p>
<p>
Prepaing Active Directory Infrastructure in Azure. Here I setup domain controller in Azure and named it DC-1. 

</p>
<br />

<p>
<img <img width="1598" height="763" alt="Screenshot 2025-11-04 054445" src="https://github.com/user-attachments/assets/7107be8f-6986-4c57-853a-2949688a49ec" />
/>
/>
</p>
<p>
I then continued on to set ipconfig for DC-1 to "static" so that it will not change because I’m telling client-1 to use dc-1 as the DNS server. If it stayed in dynamic the DNS settings would no longer work if the IP address changes for dc-1. 

 *(Client-1 process not pictured but same steps occurred)
</p>
<br />

<p>
<img <img width="994" height="776" alt="Screenshot 2025-11-04 054639" src="https://github.com/user-attachments/assets/61964733-c344-4332-a8b9-99bb48da9200" />
/>
</p>
<p>
Here, I'm logging into the VM for dc-1 and will do the same for client-1
</p>
<br />

<img width="989" height="544" alt="Screenshot 2026-01-01 131524" src="https://github.com/user-attachments/assets/e79a846e-73f1-402d-91e8-dd7dedc4b46e" />

Pining DC-1 IP address ensuring it's successful 

<img <img width="830" height="517" alt="Screenshot 2026-01-01 131153" src="https://github.com/user-attachments/assets/6b3e9853-99ee-43c3-8ade-13f143f0cc5e" />

Running ipconfig to show that the DNS server is the same for both CLient-1 and DC-1
