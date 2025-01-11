# Simulating-and-Detecting-A-Cyber-Attack

## Introduction

### Overview

In this digital world, it is critical to detect and analyse cyber threats so that appropriate responsive actions can be taken to mitigate them. This project simulates real-world cyber attacks in a virtual environment. The penetration testing tools used in this project are Metasploit and Burp Suite, while Nessus is used for vulnerability scanning, Wireshark is used for traffic analysis, and Splunk is used for log monitoring. A Kali Linux VM will be used as the attacker's environment while the Ubuntu VM will be used as the target system. With this in mind, various attacks will be conducted to observe and analyse their impact and the steps taken to detect, analyse, and mitigate these attacks will be showcased. 

### Objectives

- Simulate cyber attacks using Metasploit and Burp Suite
- Capture and analyse network traffic using Wireshark
- Utilise Nessus to scan for vulnerabilities in the target system
- Monitor and analyse logs using Splunk
- Implement threat detection and response

## Tools Used 

- Metasploit
- Burp Suite
- Nessus
- Wireshark
- Splunk
- Kali Linux VM (attack machine)
- Ubuntu VM (target machine)

## Project Setup 

### Prerequisites 
- Kali Linux VM - for running Metasploit, Burp Suite, and Nessus
- Ubuntu VM - target system for attacks
- Network - NAT or Bridged Adapter

Use platforms like VMWare or VirtualBox to install and run the virtual machines.

### Installation

#### Kali Linux VM:
1. Install Metasploit:
   - Open Terminal and type the following commands:
     ```
     sudo apt-get update && apt-get upgrade 
     sudo apt install metasploit-framework
     ```
2. Install Burp Suite:
   - Run the following command in Terminal:
     ```
     sudo apt install burpsuite
     ```
3. Install Nessus:
   - Go to the following link: <a href="https://www.tenable.com/products/nessus/nessus-essentials?source=post_page-----3a590489c18e--------------------------------">Tenable Nessus® Essentials</a>
   - Fill in your full name and email under "Register for Activation Code".
   - You will receive an email with the activation code and be redirected to the download page:
     ![image](https://github.com/user-attachments/assets/edbc1d2a-50b9-4ac4-825f-2dedfc7daf32)
   - Select the latest version for Nessus and "Linux-Debian-amd64" for the platform as shown above.
   - You can then download Nessus using the curl command in Terminal:
     ```
     curl --request GET \
       --url 'https://www.tenable.com/downloads/api/v2/pages/nessus/files/Nessus-10.8.3-debian10_amd64.deb' \
       --output 'Nessus-10.8.3-debian10_amd64.deb'
     ```




