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
   - Run the following installation command:

     `sudo dpkg -i Nessus-10.8.3-debian10_amd64.deb`
   - Start Nessus using the following command:

     `sudo systemctl start nessusd`
   - To check if it is running, run the following command:

     `sudo systemctl status nessusd`
   - Open Nessus in the browser using the following link:

     `https://localhost:8834`
   - This will give you a warning. Accept the risk and continue.
   - You will then be directed to the Nessus page:
     ![image](https://github.com/user-attachments/assets/d2491998-c179-4307-80a7-fad4224922cb)
   - Click continue.
   - Select "Register for Nessus Essentials".
   - You can skip the following step and fill in the activation code you received earlier via email.
   - Create a username and password and then click "Submit". This will fully set up Nessus Essentials on the browser:
     ![image](https://github.com/user-attachments/assets/afc6434d-fe0a-4a2c-9dbc-cf36bd51e128)

#### Ubuntu VM:
Install Splunk:
- Go to the following link: <a href="https://www.splunk.com/en_us/download/splunk-enterprise.html">Download Splunk Enterprise</a>
- Create your account.
- Verify your email to activate your Splunk account.
- The verification link will take you to the download page where you must choose a platform to download Splunk.
- Choose Linux as the platform since it is being downloaded on the Ubuntu VM and you can choose any installation package.
- Open Terminal in the Ubuntu VM and paste and run the wget command for the selected installation package. 


## References
- <a href="https://docs.tenable.com/nessus/Content/InstallNessusLinux.htm">Install Tenable Nessus on Linux</a>  

     






