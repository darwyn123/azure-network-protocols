<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Actions and Observations</h2>

<h2>Create a Resource Group</h2>

- Head over to the Azure Portal and sign in (create an account and start a subscription if needed).
- Now head over to the Resource Group section (in the search bar type "Resource Group") than click "Create".
- Resource Group name: "RG-Network-Activities"
- Click Review + create -> Create

<p>
<img <img width="646" height="695" alt="Resource G Network" src="https://github.com/user-attachments/assets/3bbc7a22-f47b-4d43-8a8c-1186bac16fb7" />
</p>

<br />

<h2>Create 2 Microsoft Virtual Machine's <a href="https://github.com/darwyn123/azure-vm">(example guide)</a></h2>

- Azure Virtual Machine 1:
   - Resource Group: New one you created (RG-Network-Activities)
   - Virtual Machine Name: "windows-vm" running Windows 11 Pro, version 25H2 - x64 Gen2
   - Virtual Network: Create a new Virtual Network called "Lab2-Vnet"

<p>
<img <img width="646" height="695" alt="windows-vm" src="https://github.com/user-attachments/assets/d558c7fc-f174-4134-979f-5b79c7409faa" />
</p>
<p>
<img <img width="683" height="664" alt="Create VNet Lab2" src="https://github.com/user-attachments/assets/a93745a1-2138-4c32-898c-0b75e5155424" />
</p>
<p>
<img <img width="628" height="664" alt="Lab2-Vnet" src="https://github.com/user-attachments/assets/ba2e2757-de3c-4777-8924-2901b2860044" />
</p>

- Azure Virtual Machine 2:
   - Resource Group: RG-Network-Activities
   - Virtual Machine Name: "linux-vm" running Ubuntu Server 24.04 LTS - x64 Gen2
   - Authentication type: Select Password and enter credentials
   - Virtual Network: Lab2-Vnet

<p>
<img <img width="628" height="694" alt="linux-vm" src="https://github.com/user-attachments/assets/a827ba51-159e-417c-b6ec-d80e685f736c" />
</p>
<p>
<img <img width="628" height="694" alt="Lab2-Vnet linux" src="https://github.com/user-attachments/assets/4aca47ee-6142-4c43-b9c8-3424b7ee0a3a" />
</p>

<br />

<h2>Install Wireshark</h2>

- RDP to Windows 10 Virtual Machine

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h2>Observe ICMP Traffic</h2>

- 

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h2>Configuring a Firewall (Network Security Group)</h2>

- 

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h2>Observe SSH Traffic</h2>

- 

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h2>Observe DHCP Traffic</h2>

- 

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h2>Observe DNS Traffic</h2>

- 

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<h2>Observe RDP Traffic</h2>

- 

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />


