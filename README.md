<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Overview</h2>

<h2>Part 1: Create Resources</h2>

- Step 1: Create a Windows 10 Virtual Machine (VM)
- Step 2: Create a Linux (Ubuntu) VM
- Step 3: Observe Your Virtual Network within Network Watcher

<h2>Part 2: Observe ICMP, SSH, DHCP, DNS, and RDP Traffic with WireShark</h2>

- Step 1: Observe ICMP Traffic 
- Step 2: Observe SSH Traffic
- Step 3: Observe DHCP Traffic
- Step 4: Observe DNS Traffic
- Step 5: Observe RDP Traffic
- Step 6: Lab Cleanup


<h2>Steps</h2>

<h2>Part 1</h2>

<p>
<img src="https://imgur.com/1wYq7o5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/HEmhOJ8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 1: While creating first virtual machine, name  a resource group called RG-Lab-2, that will create a resource group at the same time as the VM. In networking tab, a new Virtual Network and subnet will be created. Finally Review + Create, then Create.

<p>
<img src="https://imgur.com/KHtxLhH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/ZyOtjU9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 2: Select RG-Lab-2 as resource group while creating virtual machine. In networking tab, select the same Virtual Network used in VM1, which is RG-Lab-2-vnet. Finally Review + Create, then Create.

<p>
<img src="https://imgur.com/vecbTz2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 3: In home, search for Network Watcher. In Network Watcher, go to Topology. Select resource group, and Vnet. Notice that the VM are connected to each other with the same Vnet.
</p>
<br />

<h2>Part 2</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 1: Connect to Windows 10 VM with Remote Desktop. Then install Wireshark in the VM. Open Wireshark and filter for ICMP traffic only. Get VM2’s private IP address, then ping it from VM1. In WireShark, there will be requests and replys meaning the ping has been successful. Next, initiate a perpetual ping with ping “Private IP address of VM2” -t. Then Go to VM2 network watcher and deny inbound ICMP traffic. Notice in VM1 that ICMP is timing out. If inbound ICMP traffic is allowed again, ICMP traffic will resume and be successful. To stop ping write control -c
 
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 2: Open Wireshark and filter for SSH traffic only. In VM1 get into VM2 comand line by typing ssh username@private ip address of VM2. To exit, type exit and press enter.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 3: Now filter for DHCP traffic only. In command line type(ipconfig /renew) to give VM1 a new IP address.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 4: Now filter for DNS traffic. In VM1 command line type nslookup to see what google.com and disney.com’s IP addresses are.

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 5: Now filter for RDP traffic by typing (tcp.port == 3389) in WireShark. It is spamming non stop now because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted.
 
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Step 6: Close the Remote Desktop connection then Delete the Resource Group.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
