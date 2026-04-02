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
  
  - Windows Powershell


---



##  1. Connect to the Virtual Machine and Install Wireshark

1. Used Remote Desktop Connection to connect to Windows VM.

2. Inside the VM I downloaded Wireshark Network Analyzer from the website (wireshark.org)

3. Ran Installer using default installation settings. 

<img width="902" height="478" alt="Screenshot 2026-04-01 233018" src="https://github.com/user-attachments/assets/1e339cc9-b10f-45a6-ab2e-1eabef8c80c9" />
<img width="374" height="283" alt="Screenshot 2026-04-01 233421" src="https://github.com/user-attachments/assets/b3943a83-dc9c-478d-b65c-b7245f7a85ef" />

Wireshark successfully installed.

---

## 2. Start Capturing Network Traffic 

1. Within Wireshark I first located the active network adapter (Ethernet)

2. Double-clicked the adapter to begin capturing packets.

Packet capture running. All traffic with no filter

Live capture in progress. 
<img width="894" height="443" alt="live capture" src="https://github.com/user-attachments/assets/540e31de-08d2-42fc-b94e-47e2e79e925a" />

---

## 3. Analyze Web Traffic 

1. Generated web traffic to analyze encrypted connections (https)

2. Navigated to google.com 

3. Returned to Wireshark and applied the display filter:

  - **tcp.port == 443**

This shows HTTPS traffic between the VM and the website.

Google's DNS (8.8.8.8) was visible in the capture.

<img width="905" height="484" alt="filterportcapture443" src="https://github.com/user-attachments/assets/bc03c151-08bd-4b50-8840-9abc200090a0" />


---

## 4. Analyze Remote Desktop Traffic

Since the VM is accessed through Remote Desktop, used Wireshark to observe RDP communication.

1. Applied this filter in Wireshark:

 - **tcp.port == 3389**

This displays traffic used for Remote Desktop connections. 

My public IP address is visible in the capture.

<img width="940" height="479" alt="filter3389" src="https://github.com/user-attachments/assets/709af4af-1005-44a1-ae92-86931480784e" />

RDP packets in Wireshark.

---

  ## 5. Test Connectivity Using Ping

1. Applied this filter in Wireshark:

  - **icmp**

2. Opened Windows Powershell inside the VM.

3. Ran command "ping" to verify Internet Control Message Protocol (ICMP) traffic. 

   - Command:
   **ping 10.0.0.5**(private IP address of 2nd VM on network)

<img width="901" height="437" alt="icmptraffic" src="https://github.com/user-attachments/assets/62542d45-7989-4394-8498-70088e6118d6" />

This shows the ping 'request' and 'reply' process of the ICMP packets. 


---


## 6. Configure a Firewall to disturb traffic 

1. Within the Ubuntu VM opened the Network Security Group and added a rule to disable incoming (inbound) ICMP traffic.

    - Virtual Machine --> Network Settings --> Rules(Network Security Group) --> 
Create Inbound Security Rule --> Deny ICMPv4 --> Make priority --> Click Add

<img width="862" height="398" alt="denyicmptraffic" src="https://github.com/user-attachments/assets/06289c46-277d-46c0-b93d-8337265baacb" />

2. Return to Wireshark and observe traffic. Observed only 'requests' with no 'reply', indicating that the rule was deployed successfully.
   
<img width="667" height="268" alt="requestnoreply" src="https://github.com/user-attachments/assets/63ac5131-17aa-4e76-b220-a0a6a8d4f06d" />

4. Delete Rule and observe traffic again. 

<img width="519" height="169" alt="deleterule" src="https://github.com/user-attachments/assets/94433d3d-5843-49f7-8232-7fdbe3e02cf6" />
<img width="634" height="173" alt="requestreplyping" src="https://github.com/user-attachments/assets/a418cf7e-30cc-4d7b-a30a-8679cf8c4ffb" />


Once ICMP is allowed again the ping 'requests' and 'replies' are visible.



## 💡 What I Learned 
Observing traffic in this project of network traffic analysis helped me better understand the communication between different machines on a network. Protocol Identification became much more clear as I filtered packets by port and protocol and observed the capture of different types of traffic. A tool like Wireshark can help you with connectivity troubleshooting and basic Network Security Awareness. 

  


<br />



<h2>⏭️Next Steps</h2>

In the next phase of this lab I'll:

