# Firewall_Installation_Configuration_pfSense
## Overview
A firewall is a security device or software that monitors and controls incoming and outgoing network traffic based on predetermined security rules. It acts as a barrier between a trusted internal network and untrusted external networks, such as the internet. Firewalls are a critical component of any network security architecture, helping to prevent unauthorized access and mitigate cyber threats.

**Advantages of Firewalls**
- **Enhanced Security:** Blocks malicious traffic and prevents unauthorized access.
- **Policy Enforcement:** Ensures compliance with organizational security policies.
- **Monitoring Capabilities:** Provides insights into network activity and potential threats.

**Challenges and Limitations**
- **Configuration Complexity:** Misconfigured firewalls can lead to vulnerabilities or block legitimate traffic.
- **Performance Impact:** Intensive inspection of traffic can slow down the network.
- **Evasion Techniques:** Sophisticated attackers may use encrypted traffic or bypass methods to avoid detection.

## Objective
Here we will learn about how to Install and Configure **Firewall** **(pfSense)**

**Installation**
- Go to pfSense [download page]( https://www.pfsense.org/)
  

![image](https://github.com/user-attachments/assets/0eb24001-2ccb-4d09-a50e-5e2542bc72c6)


- Click on download.
- Select ISO fromm dropdown menu
- Click on **Add to Cart**


![image](https://github.com/user-attachments/assets/e904471d-f5ba-4a28-bc5e-d1ea121803b7)


- Create a account
- Fill the details
- Complete the order
- Click on **Download now**


- After the file is downloaded extract it 7zip
- If you don’t have 7 zip install it from its [download page]( https://7-zip.org/download.html)


- Open **VirtualBox**
- Click on **New**


<img width="670" alt="image" src="https://github.com/user-attachments/assets/2f51d17e-82c7-4a4f-b1a9-060c4741e2f4">


    - Fill the name
    - Folder path
    - ISO image path
    - Type : Other
    - Version : Other/Unknown(64-bit)

- Click on **Finish**


For firewall we can create a different network adapter

Create a nat network


**Why creating a nat network?**

In real world setup a firewall  will typically use 2 interfaces.
One is for WAN and other for LAN and that is your internal network.


Since we are using a type 2 hypervisor such as vmware or VirtualBox with one physical net card this setting will act still strange but it will work. It is strange because WAN card will have public IP, but in our case it will be a private IP.


In adapter 1 we will be selecting **Bridged Network**  that way it will make it less confusing.

In adapter 2 we will be selecting **NAT Network**
When we select Bridged Adapter this virtual machine with this specific network adapter is going to obtain an ip same network as our host machine.

The **important** point here is to have 2 network adapters.

![image](https://github.com/user-attachments/assets/b5a8606a-240b-4bec-be16-7194445ef450)


Now click on **Start**


Click on Accept

![image](https://github.com/user-attachments/assets/154520c0-7404-4022-83ac-cc555957b720)










