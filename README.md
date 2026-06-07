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
- Go back to Windows 11 Pro Virtual Machine, open PowerShell (make sure directory is in "Users" and not "Windows" - type cd \Users\labuser) and than ping linux-vm private IP address (e.g. 10.1.0.5)
- Go back to Wireshark and observe ICMP Traffic (e.g Request, Reply: Source, Destination)
- Expand Ethernet II Src, Internet Protocol Verison 4, Internet Control Message Protocol for more observation

<p>
<img <img width="887" height="621" alt="Ethernet Start Capturing" src="https://github.com/user-attachments/assets/1d6b5573-c785-4fd7-b740-7a40db78ce07" />
</p>
<p>
<img <img width="887" height="621" alt="icmp search" src="https://github.com/user-attachments/assets/d87a89ee-b1a8-4af2-83fc-b86013c50298" />
</p>
<p>
<img <img width="1106" height="469" alt="Copy Private IP address" src="https://github.com/user-attachments/assets/39f437c6-3cfc-4b1b-a155-f390f936db36" />
</p>
<p>
<img <img width="1112" height="625" alt="Real ping linux" src="https://github.com/user-attachments/assets/198c5dcd-e45d-4c06-8cb4-fbd2202345e6" />
</p>
<p>
<img <img width="1091" height="423" alt="ICMP Traffic" src="https://github.com/user-attachments/assets/8585a6fb-6e72-4bce-9f07-0d4f34ea7a2a" />
</p>
<p>
<img <img width="1270" height="826" alt="Ethernet II" src="https://github.com/user-attachments/assets/da57d6ad-6371-4c64-896c-9c3489b74fdb" />
</p>
<p>
<img <img width="1270" height="826" alt="Internet Protocol" src="https://github.com/user-attachments/assets/de0064cd-e18e-4571-8a09-ae1287b973ec" />
</p>
<p>
<img <img width="1270" height="826" alt="Internet Control" src="https://github.com/user-attachments/assets/b725f1ec-ed75-44ac-8b0b-6711d6f8b798" />
</p>

<br />

<h2>Configuring a Firewall (Network Security Group)</h2>

- Initiate a perpetual/non-stop ping from your Windows 11 Virtual Machine to your Ubuntu VM:
     - Go to Windows 11 Virtual Machine and Open PowerShell
     - Enter ping "Linux-vm private IP address" (e.g 10.1.0.5) -t

<p>
<img <img width="1112" height="625" alt="ping -t linux real" src="https://github.com/user-attachments/assets/5cc9e81b-6fec-4b9b-9e23-994077589b5b" />
</p>

- Disable Inbound ICMP Traffic:
     - Go back to Azure Portal, and head over to the Virtual Machines section and click on linux-vm
     - Expand Networking -> Network settings
     - Under Network security group, click "linux-vm-nsg"
     - Expand Settings -> Inbound security rules -> +Add
     - Add Inbound security rules:
        - Source: Any
        - Source port ranges: *
        - Destination: Any
        - Service: Custom
        - Destination port ranges: *
        - Protocol: Select ICMPv4
        - Action: Deny
        - Priority: 290
        - Name: DenyAnyCustomAnyInbound
        - Click Add
          
<p>
<img <img width="1440" height="519" alt="linux-vm-nsg" src="https://github.com/user-attachments/assets/739f3d35-96ab-41e7-ae79-c2752da77ece" />
</p>
<p>
<img <img width="1440" height="662" alt="Add Inbound Rule" src="https://github.com/user-attachments/assets/f31e3a33-a1bf-49d3-bb83-fb63734e977c" />
</p>
<p>
<img <img width="1440" height="662" alt="DenyCustomRule" src="https://github.com/user-attachments/assets/a762f061-a364-4c20-88a9-8b7bbfd25cb9" />
</p>

 - The Request from the ping command in Windows 11 Virtual Machine is now going to be timed out in PowerShell and WireShark

<p>
<img <img width="1440" height="771" alt="Request Timed out" src="https://github.com/user-attachments/assets/92d02d74-caa3-41aa-b00d-02cf7b812453" />
</p>
<p>
<img <img width="1440" height="771" alt="WireShark Timed out" src="https://github.com/user-attachments/assets/89b32ff1-f899-44ad-a3c6-64a26f3caa9d" />
</p>


- Re-Enable Inbound ICMP Traffic:
     - Go back to Azure Portal, and head over to the Virtual Machines section and click on linux-vm
     - Expand Networking -> Network settings
     - Under Network security group, click "linux-vm-nsg"
     - Expand Settings -> Inbound security rules -> click on the trash button to delete the rule

<p>
<img <img width="1440" height="662" alt="Trash Button" src="https://github.com/user-attachments/assets/6d140720-a7b7-4d36-82f0-c3e3a1b28e63" />
</p>
<p>
<img <img width="1440" height="662" alt="Delete Rule" src="https://github.com/user-attachments/assets/a645723e-6a52-4890-aed2-4e3f26ecb441" />
</p>

- Verify Inbound ICMP Traffic is back Enabled:
     - Go back to Windows 11 Virtual Machine
     - Go back to PowerShell verify you get a reply from request, no more timed out
     - Go back to WireShark and observe reply and request ICMP traffic

<p>
<img <img width="1111" height="626" alt="Ping Reply" src="https://github.com/user-attachments/assets/f4373bee-9d5e-44eb-a63c-7d2cd60e486a" />
</p>
<p>
<img <img width="1440" height="748" alt="WireShark Reply" src="https://github.com/user-attachments/assets/53452d5c-94b2-4e09-bc4e-0e3b5c9100df" />
</p>

- In PowerShell press "Control C" to stop ping command

<p>
<img <img width="1112" height="625" alt="Control C end ping real" src="https://github.com/user-attachments/assets/2049fefe-da60-432b-b3f4-ef9517ce3643" />
</p>

<br />

<h2>Observe SSH Traffic</h2>

- Go back in WireShark and clear filter (press the "X" button on the right side of search bar)
- Filter for SSH traffic only (in search bar type "SSH" click enter)

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- From your Windows 11 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address e.g 10.1.0.5)
     - Open PowerShell, and type: ssh labuser@<10.1.0.5> (ssh (username)@<(Linux Private IP Address)>)
     - Than type yes to connect
     - Enter password credentials

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- You are now connected to Linux Machine, you can observe traffic in WireShark
- In PowerShell type hostname, pwd, uname -a, and observe ssh traffic in WireShark
     - Expand Ethernet II Src, Internet Protocol Verison 4 Src, Transmission Control Protocol Src port, SSH Protocol for more information          and observation
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Type exit in PowerShell it end connection with Linux

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


