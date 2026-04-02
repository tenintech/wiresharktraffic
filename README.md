<p align="center">
<img width="452" height="185" alt="wireshark logo" src="https://github.com/user-attachments/assets/35189992-432a-4a1f-80be-cd1aa2dd998d">

<h1> Network Traffic Analysis Lab (Wireshark)</h1>
This lab is part of my hands-on IT support and cloud infrastructure training portfolio.
<h2>Objective</h2>
This lab demonstrates how to capture and analyze network traffic using Wireshark.
The goal is to test connectivity and observe how different network ports and protocols operate in a cloud-hosted virtual machine environment.

<h2>Technologies/Environments Used</h2>
  
  - Microsoft Azure(Virtual Machines)
 
       - Windows 10 Enterprise Version 22H2 x64 Gen 2 
       - Linux (ubuntu 24.04) 
  
  - Remote Desktop (RDP)
  
  - Wireshark Network Analyzer

##  1: Connect to the Virtual Machine and Install Wireshark

Used Remote Desktop Connection to connect to Windows VM.
Log in using administrator credentials.

Admin 10

<img width="743" height="460" alt="Screenshot 2026-04-01 232424" src="https://github.com/user-attachments/assets/c457c4c5-a812-423e-ab6d-450c9463d89a" />

Remote Desktop connected to the Azure VM.

## 2: Install Wireshark
Inside the VM I downloaded Wireshark Network Analyzer from the website (wireshark.org)

Ran Installer using default installation settings. 

<img width="902" height="478" alt="Screenshot 2026-04-01 233018" src="https://github.com/user-attachments/assets/1e339cc9-b10f-45a6-ab2e-1eabef8c80c9" />
<img width="374" height="283" alt="Screenshot 2026-04-01 233421" src="https://github.com/user-attachments/assets/b3943a83-dc9c-478d-b65c-b7245f7a85ef" />


Wireshark successfully installed.

## 3: Start Capturing Network Traffic 
1.Within Wireshark I first located the active network adapter (Ethernet)

2. Double-clicked the adapter to begin capturing packets.

Packet capture running. All traffic with no filter

Live capture in progress. 
<img width="894" height="443" alt="live capture" src="https://github.com/user-attachments/assets/540e31de-08d2-42fc-b94e-47e2e79e925a" />



## - Analyze Web Traffic (HTTPS)

Generate web traffic to analyze encrypted connections.

I opened Microsoft Edge and visited google.com 

I return to Wireshark and applied the display filter:

 **tcp.port == 443**

This shows HTTPS traffic between the VM and the website.
Googles DNS 8.8.8.8 was visible in the capture.
<img width="905" height="484" alt="filterportcapture443" src="https://github.com/user-attachments/assets/bc03c151-08bd-4b50-8840-9abc200090a0" />


Filtered HTTPS traffic.

## - Analyze Remote Desktop Traffic

Since the VM is accessed through Remote Desktop, I know use Wireshark to observe RDP communication.

Apply this filter in Wireshark:

**tcp.port == 3389**

This displays traffic used for Remote Desktop connections. My public IP address is visible in the capture.
<img width="940" height="479" alt="filter3389" src="https://github.com/user-attachments/assets/709af4af-1005-44a1-ae92-86931480784e" />

RDP packets in Wireshark.

## - Test Connectivity Using Ping
Open Command Prompt inside the VM.
Run the following command:
ping google.com
Return to Wireshark.
Apply the filter:
icmp

This shows ICMP packets used in the ping request and reply process.

Screenshot to include:
ICMP traffic displayed in Wireshark.

### Lab Results

In this lab I successfully:

Installed Wireshark on a cloud virtual machine
Captured real network traffic
Filtered packets by port and protocol
Verified connectivity using multiple network tests

This demonstrates basic network troubleshooting and traffic analysis skills.

## Skills Demonstrated
Network Traffic Analysis
Packet Capture
Protocol Identification
Connectivity Troubleshooting
Basic Network Security Awareness
Tools Used
Wireshark
Microsoft Azure Virtual Machine
Remote Desktop Protocol (RDP)

  


<br />




<hr />

<br />


## What I Learned

<h2>⏭️Next Steps</h2>

In the next phase of this lab I'll:

