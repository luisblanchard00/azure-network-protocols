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

<h2>High-Level Steps</h2>

- Creating the Virtual Machines (VMs) and Configuring the Network
- Observing Network Traffic Using Wireshark
- Configuring a Firewall (Network Security Group)
- Learning the Continuous Nature of Certain Protocols (RDP)

<h2>Actions and Observations</h2>


![image](https://github.com/user-attachments/assets/6131a450-b435-4705-b4a0-58fe8d9462ee)


- Within your Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and start packet capture
- Within Wireshark, filter for ICMP traffic only
- Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
- Observe ping requests and replies within WireShark
- From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark


<br />


![image](https://github.com/user-attachments/assets/2557f5ad-f029-472e-81bb-9df5f5ee08fc)


  (Configuring a Firewall [Network Security Group])
- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
- Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
- Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
- Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is
- Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
- Stop the ping activity
<br />


![image](https://github.com/user-attachments/assets/abb38ead-d1b1-4057-8bb8-1a60d2628ae5)

Example of traffic Observed - (Observe RDP Traffic)
- Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
- Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
- Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

<br />
