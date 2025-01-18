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
- Choose Linux as the platform since it is being downloaded on the Ubuntu VM and you can choose the .deb installation package.
- Open Terminal in the Ubuntu VM and paste and run the wget command to download the selected installation package:
  ![image](https://github.com/user-attachments/assets/7e333cc9-6bc7-41f0-8b32-0f57be9e25b3)
- Install Splunk using the command:

  `sudo dpkg -i splunk-9.4.0-6b4ebe426ca6-linux-amd64.deb`
- To check the status of the installation, run the following command:

  `sudo dpkg --status splunk`
- Next, start Splunk using the following command:

  `sudo /opt/splunk/bin/splunk start`
- Accept the license and create an administrator username and password:
  ![image](https://github.com/user-attachments/assets/0db65ea8-7186-4372-a5e1-09f89b6c681f)
- Once you have successfully created a username and password, you will be provided with the Splunk web interface:
  ![image](https://github.com/user-attachments/assets/d26d2b33-d5c5-4d25-8c0c-a74ec02d3c3a)
- Open the link on the web browser in the Ubuntu VM. This will take you to the login page where you will be asked to use the credentials that you created earlier:
  ![image](https://github.com/user-attachments/assets/1df131f9-9885-4e75-8002-ef3b25ca8b4a)


## Simulating an Attack

### Metasploit
- Open Terminal in the Kali VM.
- Type in "msfconsole" to start Metasploit:
  ![image](https://github.com/user-attachments/assets/2054305d-2586-4d41-9d23-52e1c07f23b0)
- Once Metaslpoit is started, type in "help" to see the description of each command that you can use in Metasploit:
  ![image](https://github.com/user-attachments/assets/8d6d3123-027a-4d96-891b-0631140c7d10)
- Since the Ubuntu VM is the target, search for Linux-specific exploits using the command:

  `search vsftpd`
  ![image](https://github.com/user-attachments/assets/a05e396d-0dba-4e12-8491-431ab8132f7e)

- Once you have found the exploit that you are looking for, run the following "use" command:

  `use exploit/unix/ftp/vsftpd_234_backdoor`
- Go to the Terminal in the Ubuntu VM and identify its IP address using the "ifconfig" command. The IP address is under "inet".
- Return to the Terminal in the Kali VM, in the same tab where Metasploit is running.
- Set the target using the Ubuntu VM IP address with the "set" command:

  `set RHOST <UBUNTU-VM-IP>`
- Check compatible payloads using the "show" command:

  `show payloads`
  ![image](https://github.com/user-attachments/assets/ef5ac111-fca3-4688-b1f4-1712096c3e1d)
- Set the payload shown:

  `set payload payload/cmd/unix/interact`
- Set the attacker's IP address and listening port using the Kali VM IP:
  ```
  set LHOST <KALI-VM-IP>
  SET LPORT 4444
  ```










## References
- <a href="https://docs.tenable.com/nessus/Content/InstallNessusLinux.htm">Install Tenable Nessus on Linux</a>
- <a href="https://docs.splunk.com/Documentation/Splunk/9.4.0/Installation/InstallonLinux">Install Splunk on Linux</a>
- <a href="https://medium.com/@dannyopara/installing-splunk-enterprise-on-ubuntu-step-by-step-guide-b545982038c3">Installing Splunk Enterprise on Ubuntu: Step-by-Step Guide</a>
- <a href="https://www.hackthebox.com/blog/metasploit-tutorial">A step-by-step guide to the Metasploit Framework</a>
- <a href="https://www.varonis.com/blog/what-is-metasploit">What is Metasploit? The Beginner's Guide</a>
- <a href="https://www.eccouncil.org/cybersecurity-exchange/penetration-testing/metasploit-framework-for-penetration-testing/">How To Use The Metasploit Framework For Penetration Testing</a>
- <a href="https://youtu.be/QynUOJanNqo?si=Oyjl9fNDvtPMmJ_3">Metasploit Tutorial for Beginners</a>


     






