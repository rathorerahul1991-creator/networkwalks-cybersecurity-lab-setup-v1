# <p align="center"> <img width="34" height="38" alt="Padlock" src="https://github.com/user-attachments/assets/bc9aaa5f-d088-40dc-8ff8-814e4bb62f82" /> Cybersecurity Lab Envirnment Setup </p>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
</p>



# 1. Project Overview
This Cybersecurity Lab Setup project focuses on building a safe, isolated, and virtualized environment to simulate cyberattacks, analyze malware, perform vulnerability assessment and test defensive security controls.

The lab is setup and configured on a Private Virtual Network so that additional machines can be added later and used as targets for authorized security testing.

# 2. Project Objectives
The main objectives of this project are to:
* Installation and configuration of VirtualBox
* Install/import Kali Linux as a virtual machine.
* Create a private NAT Network for the cybersecurity lab.
* Configure network connectivity for Kali Linux.
* Assign a consistent IP address to the Kali VM.
* Verify network connectivity and DNS resolution.
* Take a clean VM snapshot for recovery.
* Document the complete setup process.
* Prepare the environment for future cybersecurity projects.

# 3. Purpose of the Lab
The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:
* Network reconnaissance
* Port scanning
* Vulnerability assessment
* Packet analysis
* Web security testing
* Exploitation practice
* Security-tool experimentation

# 4. Lab Setup Procedure
# <sub> Step 1:	Download and Install 7-Zip
7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive

Tool:	7-Zip

<img width="420" height="300" alt="7-Zip" src="https://github.com/user-attachments/assets/12b420e4-69e0-4185-91ba-3214d557eaa6" />

# <sub> Step 2:	Download and Install VirtualBox
VirtualBox was downloaded and installed as the hypervisor.
	
<img width="600" height="420" alt="VMB" src="https://github.com/user-attachments/assets/74e28a8f-90e9-4cef-a846-6a0162fe7c77" />
	
# <sub> Step 3:	Create the Nat Network
* A dedicated Nat Network was created in VirtualBox.
* The configuration is shown in the picture below.
* Network Address used: IPv4 Prefix: 10.0.0.0/24
<img width="994" height="720" alt="Nat" src="https://github.com/user-attachments/assets/452faa65-cb44-4105-b7ff-50b53ab89592" />

A **NAT Network** was selected because it is used to create an isolated private network for multiple virtual machines (VMs) that also needd internet access and communicate with one another
It will allow future attacker and ttarget VMs to communicate within the Lab.

# <sub> Step 4: Import Kali Linux Software into VirtualBox VM
The Kali Linux virtual was downloaded from their official website and imported into VirtualBox.

The VM network adapter was configure as follows:

	Adapter 1
	Attached to: Nat Network
	Network: NatNetwork
	Adapter type: Intel PRO/1000 MT Desktop

	The RAM allocated for the VM was 4086 MB

<img width="771" height="669" alt="kali" src="https://github.com/user-attachments/assets/d6ce3955-da3b-4a0d-9f7a-2bd738bfb358" />

A shared folder was also configured for transferring required files between the host operating system and the Kali Linux VM 

# <sub> Step 5: Configure the Kali Linux Network
The Kali Linux network was configured withh a consistent/static IPv4 address

Configuration is as follows:

	IP Address: 10.0.0.2
	Subnet  Mask: 255.255.255.0
	Gateway: 10.0.0.1
	DNS Server: 8.8.8.8
<img width="1366" height="745" alt="kali-linux-2023 4-virtualbox-amd64  Powered Off  - Oracle VirtualBox 9_10_2026 4_39_51 AM" src="https://github.com/user-attachments/assets/1cc2664a-8e87-4cd8-b441-82cd90cb8070" />

# <sub> Step 6: Create a Clean VM Snapshot
After the configuration, a VirtualBox snapshot was created

Example snapshot name:
	Clean Kali - Network Setup

This Snapshot created means the pristine baseline or "gold standard"

The baseline is for machine recovery if there is any damage of VM configuration.

<img width="1366" height="745" alt="Snapshot" src="https://github.com/user-attachments/assets/45b21e89-d623-4354-9ca6-9594fb8eef31" />

# Problems Encountered & Solutions
Documenting problems is an important part of the project.

# <sub> Problem 1. Internet Connectivity After Static IP Configuration
After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.

One workaround used during this lab was:

	sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
	
The network connection was then restarted/rebooted and connectivity was tested again.

# <sub> Problem 2. VirtualBox VT-x / Virtualization Error
The VM initially failed to start because hardware virtualization was disabled in the system firmware/BIOS.

The issue was resolved by:

* Restarting the computer.
* Entering BIOS/UEFI settings.
* Enabling Intel VT-x / hardware virtualization.
* Saving the configuration.
* Restarting the computer.
* Starting the Kali VM again.

After enabling virtualization, the VM started successfully.

# What I Learned
Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

# <sub> 1. NAT vs NAT Network
A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

# <sub> 2. Virtual Machine Networking
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

# <sub> 3. Static IP Configuration
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

# <sub> 4. VM Snapshots
I learned that a clean snapshot should be created before performing risky or experimental activities.

This provides a known-good recovery point for future cybersecurity exercises.

# <sub> 5. Documentation
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project

# Security & Ethical Use
This laboratory is intended strictly for education purposes only.

# Tools & Resources
7-Zip: https://7-zip.org/download.html

VirtualBox: https://virtualbox.org/wiki/Downloads

Kali Linux: https://kali.org/get-kali

# 👤 Author
**Rahul Rathore**

Cybersecurity Starter

LinkedIn: www.linkedin.com/in/rahul-rathore91

# Project Imformation

**Program Name:** Cybersecurity at Networkwalks | **Week: 01 | Project:** Cybersecurity & Pentesting Lab Setup | 
**Repository:** GitHub
