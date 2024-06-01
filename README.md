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

<h2>High-Level Steps</h2>

- Create Resource Groups and Virtual Machines
- Install & Run Wireshark
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<h3>Create Resource Groups and Virtual Machines</h3>

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/2467ea0d-b93d-475a-b280-9194f981faf3)

</p>
<p>
In Microsoft Azure, create a resource group and two virtual machines. Creating the VM will also allow you to create a new virtual network aka (Vnet). Create a Windows client virtual machine and an Linux (Ubuntu) server. Use the same Vnet that was created for your Windows VM.
</p>
<br />

<h3>Install and Run Wireshark</h3>

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/dd09c55e-eab2-4279-9683-3147fbfe3fe6)


<p>
Go into your Windows Virtual Machine and open an internet browser and search "download Wireshark" and download it from the actual website.
Wireshark is a network protocol analyzer. It is used to troubleshoot networks, analysis, software & protocol development, and education.  It is the most widely used network analyzer. 
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/80dda340-6011-4da7-b8f0-1ca21de5634c)

</p>
<p>
On the website, click on Windows Installer to download-->Click Open File from the Downloads window on your browser-->Click next on the setup dialog box and advance next to install all of the prerequisite programs required to install Wireshark.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/8a24728c-e989-47a0-b64e-aaad3eb039dc)
![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/7c6915ce-f9f0-4057-9f96-8e230ab53844)


</p>
<p>
Open Wireshark and click on the blue fin icon located right under the file menu.  Once you click  on that icon, Wireshark will start analyzing all network traffic on the virtual machine.
</p>
<br />

<h3>Observe ICMP Traffic</h3>

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/ec56d6fc-2743-4fa0-9043-9dc0a9b8dc04)


</p>
<p>
Use the Remote Destkop Windows 10 Virtual Machine. Use Wireshark to filter traffic for ICMP by typing it in the filter bar and click on the blue arrow button to the right to start the filter.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/c6da35a9-fec3-4727-9f95-fae5c1b2fc21)

</p>
<p>
Retrieve the private IP address of the Linux (Ubuntu) virtual machine and attepmt to ping it in the Windows 10 virtual machine.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/76749cb2-03b6-4933-8ac8-92b1474df477)

</p>
<p>
From the Windows 10 virtual machine, open Powershell and attempt to ping the private IP address of VM 2 server and observe the requests and replies within Wireshark.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/192d959e-e096-4f30-819a-f49313b1b2bf)

</p>
<p>
From the Windows 10 virtual machine, open PowerShell and attempt to ping www.google.com and observe the traffic in Wireshark. 

From the PowerShell, you can see the packets of data sent and the statics at the bottom.  

From Wireshark, you can see the packets of data replied through google.com and the data being sent.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/3bd152d4-4c75-4eff-8f15-893828afb21d)

</p>
<p>
From the Windows 10 virtual machine. Send a non-stop ping request in Windows Powershell buy typing ping -t www.google.com. 

It will receive non-stop packet requests until you cancel it.  To cancel the ping request go to PowerShell and hit ctrl+C.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/9d75a3cb-653c-4b28-ae18-1fb64f7782c9)

</p>
<p>
In the Microsoft Azure portal open Network Security Group on your VM2  to initiate a perpetual/non-stop ping from your Windows 10 virtual machine to your Ubuntu VM.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/9c481ad2-49a7-4309-8e78-dfa557acfbbb)

</p>
<p>
From your Windows 10 virtual machine, observe the ICMP traffic in WireShark and the command line Ping activity.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/91725aa6-8482-4784-a4c3-5b3cbf607b16)

</p>
<p>
In Microsoft Azure network security group settings, Select your deny ICMP settings and allow ICMP traffic to resume. 
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/4c073372-5f29-4abd-bf90-c8e50f0cc050)

</p>
<p>
From your Windows 10 virtual machine, ping your Ubuntu server VM2 private IP address and observe the packets of data resume. 
</p>
<br />

<h3>Observe SSH Traffic</h3>

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/3a9749e8-19aa-4205-865c-ef2ca0d1d09a)

</p>
<p>
From Your Windows 10 virtual machine, connect to your Unbuntu (VM2) virtual machine using SSH via Powershell.  
Use the command SSH your VM2 username@VM2 private address and hit enter. 
Type your password and hit enter.
</p>
<br />

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/cba9377e-32d3-41fe-8839-5052bbd91167)

</p>
<p>
From your Window 10 virtual machine (VM1), type in commands (ld, uname -a, pwd, and ls lasth) and observe the output in PowerShell and data packets in WireShark. 

To logout out of the server, type "exit" in the command line in PowerShell and hit enter.
</p>
<br />

<h3>Observe DHCP Traffic</h3>

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/423e4b05-2893-484a-b76e-62e381f302f7)

</p>
<p>
From your Windows 10 virtual machine, Filter DHCP traffic in the search bar on WireShark.  On PowerShell renew your IP address lease by typing in the command line ipconfig /renew. *Your virtual machine will get assigned a new IP address. Observe the DHCP traffic in WireShark echo request. 

*Note your VM may disconnect when getting assigned a new IP address.
</p>
<br />

<h3>Observe DNS Traffic</h3>

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/e531d533-1cbb-4e31-9ef8-014aea0d79e2)

</p>
<p>
From Windows 10 virtual machine, Filter out DNS network traffic in Wireshark by typing DNS in the search bar. From Windows PowerShell give command line "nslookup www.google.com" Observe Google's IP address and DNS returned in PowerShell. Observe the IP address and DNS returned in the data packets in WireShark
</p>
<br />

<h3>Observe RDP Traffic</h3>

![image](https://github.com/JustinPeguero/azure-network-protocols/assets/170198869/9908b615-989b-41ab-beb6-91aee841be90)

</p>
<p>
From your Windows 10 virtual machine, Go to WireShark and type RDP in the search bar to filter only RDP traffic.  Click on the blue arrow to the right to activate the filter.
Observe the network traffic in WireShark. 
</p>
<br />
