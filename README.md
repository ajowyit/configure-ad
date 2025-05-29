<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Deployment and Configuration of Active Directory in the Cloud with Microsoft Azure</h1>

In this project, we set up the foundation for an Active Directory environment in Microsoft Azure. We use a Windows Server 2022 virtual machine as the Domain Controller and a Windows 10 virtual machine as the client.

We assign static private IP addresses, configure custom DNS settings, and test network connectivity using PowerShell and Remote Desktop Protocol (RDP). This setup prepares us to deploy and manage Active Directory services for future projects.

<br />

<h2>⚠️ Prerequisites</h2>

- [Creating Virtual Machines in the Cloud](https://github.com/ajowyit/creating-virtual-machines)
*(Refer to this project for help creating Virtual Manchines if necessary)*

- A Microsoft Azure account and subscription with access to:
  - Resource Group creation
  - Virtula Network configuration
  - Deployment of Windows Server and Windows 10 virtual machines

- Remote Desktop Connection (RDP) access and the Windows App

<h2>💻 Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop (Windows App)
- Active Directory Domain Services
- PowerShell

<h2>👨‍💻 Operating Systems Used </h2>

- macOS Sequoia
- Windows Server 2022
- Windows 10 (21H2)

<h2>🪜 High-Level Steps</h2>

- Step 1: Create Resource Group, Virtual Network and Virtual Machines
- Step 2: Assign a Static Private IP to DC-1
- Step 3: Disable Domain Controller Firewall
- Step 4: Change Client-1's DNS server to DC-1
- Step 5: Test the connection between DC-1 and Client-1

<h2>🛠️ Step 1: Create Resource Group, Virtual Network and Virtual Machines</h2>

<p>
<img width="949" alt="Screenshot 2025-05-28 at 8 50 39 PM" src="https://github.com/user-attachments/assets/3f5afa48-dc28-4436-b8b1-923299325f58" />

<img width="948" alt="Screenshot 2025-05-28 at 8 49 12 PM" src="https://github.com/user-attachments/assets/40f46868-5acc-43ff-a233-d51b5bbb3f5f" />


<img width="948" alt="Screenshot 2025-05-28 at 8 50 10 PM" src="https://github.com/user-attachments/assets/e756afc0-b655-4103-b649-1b522fb9c7fc" />

</p>
<p>
- Log into the Azure Portal and navigate to Resource groups.
</p>
<p>
- Create a new resource group.
</p>

<p>
  <img width="1031" alt="Screenshot 2025-05-28 at 10 06 53 PM" src="https://github.com/user-attachments/assets/e9e11702-51af-4c7d-8acd-090463be9b6c" />
  <img width="1032" alt="Screenshot 2025-05-28 at 9 53 34 PM" src="https://github.com/user-attachments/assets/8ee3f808-c938-4df2-a93c-015ec4381cb8" />
  <img width="1021" alt="Screenshot 2025-05-28 at 9 56 42 PM" src="https://github.com/user-attachments/assets/f1412b20-6c0c-4f6c-a7e4-e5dc5b8a44c5" />
</p>
<p>
  - Create a virtual network inside of the resource group we created. Make sure it is in the same region.
</p>

<p>
  <img width="1011" alt="Screenshot 2025-05-28 at 8 54 07 PM" src="https://github.com/user-attachments/assets/d8ef9e73-5a32-4cbf-95bb-e87c3dfa050a" />

  <img width="1481" alt="Screenshot 2025-05-28 at 9 13 04 PM" src="https://github.com/user-attachments/assets/a363b35a-f0fd-4c80-8d0f-73d4fbdf142b" />

</p>

<p>
- Create two virtual machines. Make sure that the virtual machines are in the same   Virtual Network and Region as the resource group we created. 
</p>

### 🖥️ VM #1: Domain Controller (DC-1)

- **Name**: `DC-1`
- **Image**: Windows Server 2022
- **Size**: At least 2 vCPUs, 8 GiB memory 
- **Authentication**: Password
- **Network**: Place inside the same Virtual Network and Resource Group we created

### 💻 VM #2: Client Machine (Client-1)

- **Name**: `Client-1`
- **Image**: Windows 10 Pro (22H2)
- **Size**: At least 2 vCPUs, 8 GiB memory
- **Authentication**: Password
- **Network**: Make sure to use the same Virtual Network and Region as DC-1

<br />

<h2>🛠️ Step 2: Assign a Static Private IP to DC-1</h2>

<p>
  <img width="1428" alt="Screenshot 2025-05-28 at 10 21 45 PM" src="https://github.com/user-attachments/assets/e5ea1099-8d8e-483f-8a42-c9b97531f351" />
</p>

<p>
- Navigate back to the Virtual machines page. Click on DC-1. Select Network settings. Click the Network interface/IP configuration option.
</p>
<br />

<p>
<img width="1432" alt="Screenshot 2025-05-28 at 10 23 58 PM" src="https://github.com/user-attachments/assets/747956b3-9639-4344-a6f2-32f2601c1d3e" />
</p>
<p>
- Under IP Settings, click ipconfig1 to edit IP configuration. Select Static under Allocation to change the alloaction from Dynamic to Static. Click Save.
</p>
<p>
-A static internal IP ensures that the DNS server (DC-1) consistently uses the same address, which is crucial for domain joining and reliable communication with client machines.
</p>
<p>
  <img width="1436" alt="Screenshot 2025-05-28 at 10 36 40 PM" src="https://github.com/user-attachments/assets/dfe554dc-6c1b-4cc3-a8ea-4b7746219c8d" />
</p>
<p>
  - Confirm our changes were saved by looking to see that out Private IP address is static. 
</p>

<br />

<h2>🛠️ Step 3: Disable Domain Controller Firewall </h2>

<p>
<img width="797" alt="Screenshot 2025-05-28 at 10 45 31 PM" src="https://github.com/user-attachments/assets/a60b44ab-e1ac-473f-b628-ee01e08e3b53" />

<img width="419" alt="Screenshot 2025-05-28 at 10 45 40 PM" src="https://github.com/user-attachments/assets/24d19f0f-af44-4c08-b12d-284e9697d4e9" />

<img width="1047" alt="Screenshot 2025-05-28 at 10 45 52 PM" src="https://github.com/user-attachments/assets/8bf02745-7cd3-44c1-a64d-8b2afa69e8a4" />
  
</p>

<p>
- In DC-1, search for Run at the bottom search bar and then open Run or right-click the Start Menu and open Run. Once open, Ttpe wf.msc and click OK. This will open firewall settings for DC-1. 
</p>

<p>
  <img width="1047" alt="Screenshot 2025-05-28 at 10 45 52 PM copy" src="https://github.com/user-attachments/assets/43e1cdb7-9ac0-4a90-8ca0-a9c1143fad4d" />
<img width="402" alt="Screenshot 2025-05-28 at 10 46 01 PM" src="https://github.com/user-attachments/assets/63496841-3fd1-4426-9494-03febdc288d7" />
<img width="404" alt="Screenshot 2025-05-28 at 10 46 16 PM" src="https://github.com/user-attachments/assets/2812bd21-cff9-49fc-b4d1-655d94fe1589" />
</p>

<p>
  - Click Windows Defender Firewall Properties. Once the Windows Defender Firewall with Advanced Security on Local Computer window pops up, for The Domain Profile, Private Profile, and Public Profile tabs, change Firewall state to Off. Click Apply and then click OK to save the changes
</p>

<br />

<h2>🛠️ Step 4: Change Client-1's DNS server to DC-1</h2>
<p>
<img width="1433" alt="Screenshot 2025-05-28 at 10 47 17 PM" src="https://github.com/user-attachments/assets/3623cdec-5431-43ef-a54d-c2724fc70e91" />

<img width="1435" alt="Screenshot 2025-05-28 at 10 48 57 PM" src="https://github.com/user-attachments/assets/92b8196d-99f6-4668-b87c-2c24d913f3dc" />

</p>
<p>
  - Go back to the Virtual machines page in Azure. Click Client-1. Select Network settings, then click inside Network interface /IP configuration.
</p>
<p>
  - Under Settings, select DNS servers. Select Custom. Inside the text field under DNS server, type in DC-1's private IP address. 
</p>

<p>
  <img width="1436" alt="Screenshot 2025-05-28 at 10 50 34 PM" src="https://github.com/user-attachments/assets/5a4e618b-559d-4995-af4e-b246b1277ad6" />
</p>
<p>
  - Since we changed Client-1's DNS server, we should restart the virtual machine. Go back to the Virtual machine's page in Azure, select Client-1, click Restart, and click Yes to restart the virtual machine.
</p>

<br />
<h2>🛠️ Step 5: Test the connection between DC-1 and Client-1</h2>
<p>
  <img width="787" alt="Screenshot 2025-05-28 at 11 08 23 PM" src="https://github.com/user-attachments/assets/b6fb1108-ed88-4a98-80aa-e3d8fd86b13d" />
</p>
<p>
  - Log into Client-1 on the Windows App with a RDP connection just like how we did with DC-1 earlier. Open PowerShell. 
</p>
<p>
  <img width="859" alt="Screenshot 2025-05-28 at 11 10 05 PM" src="https://github.com/user-attachments/assets/e58d1a84-48e0-4ba8-bee7-071624ef9efb" />

</p>
<p>
  - Ping the private IP address of DC-1 with the command ping 10.0.0.4 and then observe whether we get a reply or if the request times out. If we get a reply, then it means the connection is working!
</p>

<p>
  <img width="858" alt="Screenshot 2025-05-28 at 11 10 31 PM" src="https://github.com/user-attachments/assets/90cee524-e0a6-4924-bd57-6e7881b387d9" />

</p>
<p>
  - Finally ensure that the DNS Server of Client-1 is set to DC-1's private IP address. To do this type the command ipconfig /all into PowerShell. Make sure under DNS Servers we see DC-1's private IP address (10.0.0.4).
</p>

<p>
  Congratulations! We have finished setting up our Active Directory Infrastructure!
</p>
<br />
