<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we analyze network traffic to and from Azure Virtual Machines using Wireshark and explore Network Security Groups through hands-on experimentation. <br />




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

<p>Begin by creating two VMs (Virtual Machines) on Microsoft Azure. The first VM will run Windows 10 as its operating system, while the second will use Linux (Ubuntu). Each VM should be configured with two CPUs and must be connected to the same Virtual Network (VNet). After setting this up, use Remote Desktop to connect to your Windows 10 VM. Once you're in, open a web browser and download Wireshark from the following link: http://www.wireshark.org/download.html. Once you get Wireshark up and running, you're going to filter for ICMP (Internet Control Message Protocol). ICMP can be described as a communication method between two computers where, if one encounters a problem, ICMP sends a message indicating that something is wrong. Wireshark will allow us to monitor and analyze packets after applying a filter to display only ICMP traffic and ping the private IP address of our Linux VM. Ping, which uses ICMP, helps us test the connectivity between two hosts.
</p>

![image](https://github.com/user-attachments/assets/94f5a5b4-fe27-4b4e-8b9b-8ab57a5e059a)


<p>We can examine each packet individually and view the actual data being transmitted in each ping. The image below illustrates this process.</p>

![Screenshot 2024-09-24 221824](https://github.com/user-attachments/assets/90c4b20d-b8ff-4e32-84bc-d7abe312b426)


<p>In the next part of the lab, we will use the "-t" option with the "ping" command and the private IP address of the Linux Virtual Machine. This will start a continuous ping that will run indefinitely until a response is received or manually stopped. While the Windows 10 VM is pinging the Linux VM, we will switch to the Linux VM and block all ICMP traffic through its firewall. This will be done by creating a new Network Security Group on the Linux VM, configured to deny ICMP traffic. As a result, the Linux VM will stop sending echo replies.</p>



![Screenshot 2024-09-24 222500](https://github.com/user-attachments/assets/43fff794-d96a-49fb-ac4b-0991c14224dd)

![image](https://github.com/user-attachments/assets/f5c47158-82d5-44ee-9990-ca770b20bcbf)


<p> As shown below, when incoming or inbound ICMP traffic is disabled, the message will display 'Request Timed Out'. To allow ICMP traffic, we can enable it by configuring the Linux Network Security Group. To stop the pings, simply use 'Control-C'.</p>

![image](https://github.com/user-attachments/assets/31316832-57d9-4dae-a76c-7de06d2f60a6)

![image](https://github.com/user-attachments/assets/533f8a09-0e05-4f29-9e14-eb720d36da20)



<p>Next, we will filter SSH (Secure Shell) traffic on our Windows 10 VM in preparation for establishing an SSH connection to our Linux VM. Since SSH doesn't have a GUI (graphical interface), it simply provides access to the command line. Using the command prompt, we’ll enter 'ssh username@10.0.0.5', and we’ll observe that Wireshark immediately starts capturing SSH packets.</p>


![image](https://github.com/user-attachments/assets/eb58b4df-bd32-4e98-ac0d-54201099e958)



<p> As we monitor SSH traffic, we will execute a few Linux commands and observe the resulting traffic captured in Wireshark.

* Linux Commands
  * id
  * hostname
  * pwd
  * touch 
  * ls
<p/>


![image](https://github.com/user-attachments/assets/c0df6743-b7e0-4250-ac0e-04964aff9c9b)

<p>
In Wireshark, we'll be applying a filter for DHCP (Dynamic Host Configuration Protocol). DHCP is responsible for assigning network configurations and IP addresses to devices, facilitating proper communication. It operates on ports 67 and 68. Once you've filtered for DHCP, open the command prompt and run the command `ipconfig/renew`. This will refresh the device's network settings by requesting a new IP address.</p>

![image](https://github.com/user-attachments/assets/e058d3c9-7046-4a39-8879-696628835fb4)

<p>DNS (Domain Name System) converts human-readable domain names into IP addresses, which computers use to recognize each other on a network. In Wireshark, apply a DNS filter and then, in the command line, enter nslookup www.google.com. This command queries the DNS to retrieve the IP address linked to Google.</p>

![image](https://github.com/user-attachments/assets/fa97e09d-929f-4274-9025-d13c65b2ece9)

<p>Finally, we'll filter RDP (Remote Desktop Protocol) traffic by entering tcp.port==3389. This will display continuous traffic, as RDP constantly transmits data between computers in real-time, streaming live updates, resulting in ongoing network activity.</p>

![image](https://github.com/user-attachments/assets/83f4942a-ea59-4866-b90d-6866f603d1e2)


















