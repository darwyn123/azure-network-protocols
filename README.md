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

- RDP to Windows 11 Pro Virtual Machine
- Open Web Browser and go to www.wireshark.org -> Click Download Now -> Windows x64 Installer
- Open file, and double click file to open installer
- Click Next -> Noted -> Next -> Next -> Next -> Next -> Next -> Install -> I Agree -> Install -> Next -> Finish -> Next -> Finsh

<p>
<img <img width="628" height="591" alt="Labuser login" src="https://github.com/user-attachments/assets/eefaa24f-2d71-4338-90d4-c2ae2e52b473" />
</p>
<p>
<img <img width="628" height="591" alt="Labuser " src="https://github.com/user-attachments/assets/d7d5387a-14db-4039-a996-450392adbb4e" />
</p>
<p>
<img <img width="1119" height="731" alt="Wireshark Download Now" src="https://github.com/user-attachments/assets/d658c559-35fe-48a5-a80a-c4f31afa99a3" />
</p>
<p>
<img <img width="1057" height="362" alt="Windows x64 Installer" src="https://github.com/user-attachments/assets/2bce45b4-2af1-40e3-b64d-4c8b0bdf5a6e" />
</p>
<p>
<img <img width="887" height="621" alt="Wireshark wizard" src="https://github.com/user-attachments/assets/84ac5193-cc1b-4872-9647-2deb96e246af" />
</p>
<p>
<img <img width="887" height="621" alt="Installer" src="https://github.com/user-attachments/assets/eeb9df78-c5c3-4cb1-9122-090770eee8c5" />
</p>
<p>
<img <img width="887" height="621" alt="I Agree INstaller" src="https://github.com/user-attachments/assets/bcba1636-9462-4e6f-9d40-277eba27e9a1" />
</p>
<p>
<img <img width="887" height="621" alt="Finish Installer" src="https://github.com/user-attachments/assets/ca7c19e3-0f2a-457e-b393-94b22d3a6007" />
</p>

<br />

<h2>Observe ICMP Traffic</h2>

- Open Wireshark
- Highlight Ethernet and click "Start capturing packets" (Blue Fin)
- In search bar type "icmp" than enter
- Go back to Azure Portal, and head over to the virtual machines section and click on linux-vm and copy private IP address
- Go back to Windows 11 Pro Virtual Machine, open PowerShell and ping linux-vm private IP address (e.g. 10.1.0.5)
- Go back to Wireshark and observe ICMP Traffic (e.g Request, Reply: Source, Destination)
- Expand Ethernet II Src, Internet Protocol Verison 4, Internet Control Message Protocol for more observation

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


