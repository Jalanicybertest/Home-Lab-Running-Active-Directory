
# Home-Lab-Running-Active-Directory
![Home_Lab_Running_Active_Directory (1)](https://github.com/user-attachments/assets/896801b5-07c0-451a-ab39-c975c49dc967)


## Introduction
Recently, I embarked on an exciting project to set up a basic home lab running Active Directory using Oracle VirtualBox. This setup allows for hands-on practice with Active Directory and other network services in a controlled environment. Here's a brief overview of how I achieved this.

Components and Tools Used:

- Virtualization Platform: Oracle VirtualBox
- Operating Systems: Windows Server 2019 and Windows 10 ISO files
- Network Configuration: Internal and External Network Interface Cards (NICs)
- Automation Tools: PowerShell scripting

# Step-by-Step Setup Process

**1. Creating Virtual Machines**

Domain Controller (DC) - Server 2019:
- Created a new virtual machine in Oracle VirtualBox and installed Windows Server 2019.
- Allocated appropriate resources (CPU, RAM, storage) based on system capabilities.

Networking:
- Configured two NICs:
  - External NIC: Connected to the home router via DHCP for internet access.
  - Internal NIC: Static IP configuration (IP: 172.16.0.1, Subnet Mask: 255.255.255.0) for internal network communication.

Client Machine - Windows 10:
- Created a virtual machine for a Windows 10 client.
- Configure a single NIC connected to the internal network, set to receive an IP address from the DC’s DHCP.
  
**2. Installing and Configuring Active Directory on the Domain Controller**
   
Active Directory Domain Services (AD DS) Installation:
- Installed the AD DS role on the Windows Server 2019 VM using the Server Manager.
- Promoted the server to a domain controller for the domain mydomain.com.
- Configured DNS to point to the DC (127.0.0.1) for internal name resolution.

DHCP Configuration:
- Configured DHCP on the DC to provide IP addresses within the range 172.16.0.100-200 for devices on the internal network.
- Ensured proper scope options like default gateway and DNS server were set.

**3. Network Address Translation (NAT) and Remote Access Configuration**

Remote Access Service (RAS):
- Enabled the Remote Access role on the DC to facilitate NAT.
- Configured RAS to use the external NIC for outbound traffic and the internal NIC for internal traffic.

NAT Setup:
- Configured NAT in RAS to allow internal network devices to access the internet through the DC.

**4. PowerShell Scripting for User Account Creation**

Preparing the Environment:
- Created a CSV file names.txt containing first and last names of users to be created.
- Developed a PowerShell script to automate the creation of user accounts in AD.

PowerShell Script Details:
- The PowerShell script reads from names.txt, generates usernames, and creates user accounts in a specified organizational unit (OU). Below is the detailed script:

![Capture](https://github.com/user-attachments/assets/b05d9ad3-eaa9-41e8-a80b-7e862cf58222)

**Explanation:**
- The script sets a default password for all users and converts it to a secure string.
- It creates an OU named "USERS" to organize the user accounts.
- For each entry in the names.txt file, the script generates a username and creates a new AD user with specified attributes.

## Outcome
With this setup, I can now simulate a small network environment, allowing for experimentation and learning without impacting any production systems. This lab environment is an invaluable tool for anyone looking to deepen their understanding of Active Directory and network management.
 


