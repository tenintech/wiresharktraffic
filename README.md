<p align="center">
<img width="452" height="185" alt="wireshark logo" src="https://github.com/user-attachments/assets/35189992-432a-4a1f-80be-cd1aa2dd998d">

<h1> Network Traffic Analysis Lab (Wireshark)</h1>
This lab is part of my hands-on IT support and cloud infrastructure training portfolio.
<h2>Objective</h2>
This lab demonstrates how to capture and analyze network traffic using Wireshark.
The goal is to test connectivity and observe how different network ports and protocols operate in a cloud-hosted virtual machine environment.

This activity simulates basic network troubleshooting tasks commonly performed by IT support and help desk technicians.

### Lab Objectives

Install Wireshark on a virtual machine
Capture live network traffic
Filter traffic by protocol and port
Verify connectivity using multiple network tests


## Step 1: Connect to the Virtual Machine

Use Remote Desktop Connection to connect to Windows VM.
Log in using your administrator credentials.

Admin 10


Remote Desktop connected to the Azure VM.

## Step 2: Install Wireshark
Inside the VM I downloaded Wireshark Network Analyzer from the website (wireshark.org)

Ran Installer using default installation settings. 

<img width="902" height="478" alt="Screenshot 2026-04-01 233018" src="https://github.com/user-attachments/assets/1e339cc9-b10f-45a6-ab2e-1eabef8c80c9" />
<img width="374" height="283" alt="Screenshot 2026-04-01 233421" src="https://github.com/user-attachments/assets/b3943a83-dc9c-478d-b65c-b7245f7a85ef" />


Wireshark successfully installed.

## Step 3: Start Capturing Network Traffic
1.Within Wireshark I first located the active network adapter (Ethernet)

2. Double-clicked the adapter to begin capturing packets.

Live capture in progress. 
<img width="894" height="443" alt="live capture" src="https://github.com/user-attachments/assets/540e31de-08d2-42fc-b94e-47e2e79e925a" />

Packet capture running.

## Step 4: Analyze Web Traffic (HTTPS)

Generate web traffic to analyze encrypted connections.

Open a web browser.
Visit a website such as:
example.com
Return to Wireshark.
Apply the following display filter:
tcp.port == 443

This shows HTTPS traffic between your VM and the website.

Screenshot to include:
Filtered HTTPS traffic.

## Step 5: Analyze Remote Desktop Traffic

Since the VM is accessed through Remote Desktop, we can observe RDP communication.

Apply this filter in Wireshark:

tcp.port == 3389

This displays traffic used for Remote Desktop connections.

Screenshot to include:
RDP packets in Wireshark.

## Step 6: Test Connectivity Using Ping
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
<h2>Technologies/Environments Used</h2>
  
  - Microsoft Azure(Virtual Machines, Virtual Network)
    
       - Windows Server 2025 (Domain Controller)
 
       - Windows 10 Enterprise Version 22H2 x64 Gen 2 (Client Machine)
  
  - Active Directory Domain Services (AD DS)
  
  - Remote Desktop (RDP)
  
  - PowerShell
  


<br />




<hr />

<br />


## What I Learned

<h2>⏭️Next Steps</h2>

In the next phase of this lab I'll:
# wiresharktraffic
