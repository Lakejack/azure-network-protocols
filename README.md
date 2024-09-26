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

<h2>Actions and Observations</h2>

</p> 
Begin by creating two virtual machines (VMs) on Microsoft Azure. The first VM will run Windows 10 as its operating system, while the second will use Linux (Ubuntu). Each VM should be configured with two CPUs and must be connected to the same Virtual Network (VNet). After setting this up, use Remote Desktop to connect to your Windows 10 VM. Once you're in, open a web browser and download Wireshark from the following link: http://www.wireshark.org/download.html. Once you get Wireshark up and running, you're going to filter for ICMP (Internet Control Message Protocol). ICMP can be described as a communication method between two computers where, if one encounters a problem, ICMP sends a message indicating that something is wrong. Wireshark will allow us to monitor and analyze packets after applying a filter to display only ICMP traffic and ping the private IP address of our Linux VM. Ping, which uses ICMP, helps us test the connectivity between two hosts.
</p>

![image](https://github.com/user-attachments/assets/94f5a5b4-fe27-4b4e-8b9b-8ab57a5e059a)


<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
  
![Screenshot 2024-09-24 221824](https://github.com/user-attachments/assets/90c4b20d-b8ff-4e32-84bc-d7abe312b426)

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>

  ![Screenshot 2024-09-24 222500](https://github.com/user-attachments/assets/43fff794-d96a-49fb-ac4b-0991c14224dd)

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
