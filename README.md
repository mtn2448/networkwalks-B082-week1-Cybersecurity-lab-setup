# networkwalks-B082-week1-Cybersecurity-lab-setup
Cybersecurity Lab Setup

Virtual Cybersecurity and Penetration-Testing Laboratory

Project Overview

This project involves the design and implementation of a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux. The laboratory provides a controlled and isolated environment for learning and performing authorized cybersecurity activities, including network reconnaissance, scanning, vulnerability assessment, and security testing.

The lab is configured on a dedicated private NAT Network, allowing multiple virtual machines to communicate within the controlled environment while maintaining network isolation from the external network. Additional virtual machines can be integrated into the laboratory in the future to serve as targets for authorized security assessments and practical cybersecurity exercises.

Objectives

The primary objectives of this project are to:

Install and configure Oracle VirtualBox as the virtualization platform.

Install and import Kali Linux as a virtual machine.

Create and configure a private NAT Network for the cybersecurity laboratory.

Establish and verify network connectivity for the Kali Linux virtual machine.

Configure a consistent IP address for the Kali Linux VM.

Verify network connectivity and DNS resolution.

Create a clean virtual machine snapshot to enable quick recovery and restoration.

Document the complete laboratory setup and configuration process.

Establish a reliable environment for future cybersecurity, penetration-testing, and network-security projects.


Purpose of the Lab


The primary purpose of this laboratory is to provide a secure, isolated, and controlled environment for cybersecurity education, practical skill development, and authorized security testing. It enables users to safely explore cybersecurity concepts, analyze network behavior, evaluate system security, and gain hands-on experience with industry-standard security tools without affecting production systems or external networks.


The laboratory can be utilized for the following authorized cybersecurity activities:


Network Reconnaissance: Gathering and analyzing information about systems, hosts, and network services within the controlled environment.

Port Scanning: Identifying open ports and available network services for security assessment purposes.

Vulnerability Assessment: Detecting and evaluating potential security weaknesses in systems and applications.

Packet Analysis: Capturing and analyzing network traffic to understand communication patterns and identify potential security issues.

Web Security Testing: Assessing web applications for common security vulnerabilities within an authorized testing environment.

Exploitation Practice: Developing practical knowledge of security vulnerabilities and understanding their potential impact using intentionally vulnerable systems.

Security Tool Experimentation: Learning and evaluating various cybersecurity tools and techniques in a safe and controlled environment.

## Lab Architecture


The cybersecurity laboratory is designed using **VirtualBox virtualization technology** with Kali Linux operating as the primary security-testing virtual machine. The virtual environment uses a dedicated **NAT Network** with the `10.0.0.0/24` address range, providing controlled communication between virtual machines while maintaining network isolation.


The architecture is designed to be scalable, allowing additional target and testing machines to be connected to the same virtual network for future cybersecurity exercises and authorized penetration-testing activities.



<img width="1919" height="1008" alt="image" src="https://github.com/user-attachments/assets/e1b090c8-b2bb-44f9-8bce-f4eca1db242d" />


### Lab Configuration


| Component                                | Configuration          |
| ---------------------------------------- | ---------------------- |
| **Host Operating System**                | Windows 10             |
| **Host Memory (RAM)**                    | 8 GB                   |
| **Processor**                            | Intel Core i7          |
| **Hypervisor**                           | VirtualBox 7.2         |
| **Security Operating System**            | Kali Linux 2026.2      |
| **Kali Linux Memory Allocation**         | 2048 MB (2 GB)         |
| **Virtual Network Type**                 | NAT Network            |
| **Network Address**                      | `10.0.0.0/24`          |
| **Kali Linux IP Address**                | `10.0.0.2/24`          |
| **Default Gateway**                      | `10.0.0.1`             |
| **DNS Server**                           | `8.8.8.8`              |
| **Future Virtual Machine Address Range** | `10.0.0.3 – 10.0.0.99` |


### Network Design


The `10.0.0.0/24` private network provides a dedicated address space for the laboratory environment. Kali Linux is assigned the address `10.0.0.2`, while `10.0.0.1` is configured as the default gateway. The address range from `10.0.0.3` to `10.0.0.99` is reserved for additional virtual machines that may be introduced for future security-testing and penetration-testing exercises.


This architecture provides a **structured, scalable, and controlled environment** for conducting cybersecurity experiments while minimizing the risk of affecting external or production systems.


Lab Setup Procedure


Step 1. Download & install 7-zip: https://7-zip.org/download.html

Installed 7-Zip to extract the Kali Linux virtual-machine package distributed in .7z format.

Step 2. Download & install Virtualbox on your laptop/PC: https://virtualbox.org/wiki/Downloads

Installed Oracle VirtualBox to create and manage the Kali Linux virtual machine.

Step 3.Configure the network settings on your Virtualbox (create NATNetwork in 10.0.0.0/24)

A dedicated NAT Network was created in VirtualBox.


Configuration: Network Name: NatNetwork IPv4 Prefix: 10.0.0.0/24 DHCP: Enabled IPv6: Disabled

<img width="1919" height="1001" alt="image" src="https://github.com/user-attachments/assets/6bb99dde-f22a-421c-8b2e-421f66ced16a" />

A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

 Step 4.Download & import Kali Linux Virtual Machine in your Virtualbox: https://kali.org/get-kali
 
 The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

Adapter 1

Attached to: NAT Network

Network:     NatNetwork

Adapter Type: Intel PRO/1000 MT Desktop

The VM was allocated:

RAM: 2048 MB

<img width="959" height="506" alt="image" src="https://github.com/user-attachments/assets/b3547e21-f4a5-4db1-b66d-8da66fcd28bc" />

A shared folder was also configured for transferring required files between the host operating system and the Kali VM.


Step 5. Setup the IP configuration of Kali Linux

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.


Example configuration:

IP Address: 10.0.0.2

Subnet Mask: 255.255.255.0

Gateway: 10.0.0.1

DNS: 8.8.8.8

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

<img width="959" height="500" alt="image" src="https://github.com/user-attachments/assets/467a305a-1f47-4829-a47b-c140b93f8f48" />

Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

Clean Kali - Network Setup

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

The following verification tests were performed to confirm that the Kali Linux virtual machine and its network configuration were functioning correctly.

Verification Test	Command	Expected Result

IP Address Verification	ip a	Kali Linux IP address 10.0.0.2/24 is displayed.

Default Gateway Test	ping 10.0.0.1	Successful replies are received from the gateway.

Internet Connectivity Test	ping 8.8.8.8	Successful replies confirm Internet connectivity.

DNS Resolution Test	nslookup networkwalks.com	The domain name resolves successfully to an IP address.

Nmap Verification	nmap --version	The installed Nmap version is displayed.

Snapshot Verification	Restore snapshot and run ip a	The baseline network configuration is successfully restored.

Verification Results

Configuration	Verified Value

Kali Linux IP Address	10.0.0.2/24

Default Gateway	10.0.0.1

DNS Server	8.8.8.8


Problems Encountered & Solutions

Documenting problems is an important part of the project.


Problem 1. Internet Connectivity After Static IP Configuration
After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.

One workaround used during this lab was:

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0

The network connection was then restarted/rebooted and connectivity was tested again.

Important: Network interface and connection names may differ between systems. Students should first identify their actual connection name before running an nmcli command.

Problem 2. VirtualBox VT-x / Virtualization Error

The VM initially failed to start because hardware virtualization was disabled in the system firmware/BIOS.

The issue was resolved by:

Restarting the computer.

Entering BIOS/UEFI settings.

Enabling Intel VT-x / hardware virtualization.

Saving the configuration.

Restarting the computer.

Starting the Kali VM again.

After enabling virtualization, the VM started successfully.


What I Learned ?


Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

1. NAT vs NAT Network
   
A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

2. Virtual Machine Networking
   
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

3. Static IP Configuration
 
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

4. VM Snapshots

I learned that a clean snapshot should be created before performing risky or experimental activities.

This provides a known-good recovery point for future cybersecurity exercises.

5. Documentation

I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

Author

Himal Bhandari

Cybersecurity Professional B082

LinkedIn:

 Project Information
 
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub










