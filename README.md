<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Creating an Active Directory Infrastructure in the Cloud with Microsoft Azure</h1>


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

- Step 1: Create Resource Group and Virtual Machines
- Step 2: Assign a Static Private IP to DC-1

<h2>🛠️ Step 1: Create Resource Group and Virtual Machines</h2>

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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
