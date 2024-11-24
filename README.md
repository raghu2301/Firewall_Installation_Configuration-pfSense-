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


- Click on Accept

![image](https://github.com/user-attachments/assets/154520c0-7404-4022-83ac-cc555957b720)


- Click on **Install pfSense**

![image](https://github.com/user-attachments/assets/89bcbc4c-7f44-4172-aeaa-055ff1e361a4)


- Click **Ok** in Setting up the network to continue the installation 

![image](https://github.com/user-attachments/assets/a3d174c5-acba-48dc-897b-efdbbab034df)

- Click on **Assign/Configure** in **Interface Assignment and Configuration**

![image](https://github.com/user-attachments/assets/4687c6bd-981b-45a2-ba54-1b4649be0c8e)


- Click on **Continue**


![image](https://github.com/user-attachments/assets/1c88e7cb-a1fc-4373-a630-0ac0970c9aac)




- Select **WAN** and Click on **Continue**  in **Interface Assignment and Configuration**



![image](https://github.com/user-attachments/assets/173a1008-9f80-47dd-930a-30f24d269c71)


- Click on **Install CE** (CE means Community Edition)



![image](https://github.com/user-attachments/assets/ab007178-0aba-475e-a497-6eb292f6c1b2)


- Click on **Continue**

![image](https://github.com/user-attachments/assets/4ba7a458-6aa7-4756-bdbf-2f8cc1a0131a)


- Click **OK** in **Virtual Device Type Configuration**

![image](https://github.com/user-attachments/assets/da1edfa9-b1dc-4a85-b031-b0af5fe65ac3)


- Click **OK** in **Disk Selection**

![image](https://github.com/user-attachments/assets/dc962da8-0f8f-42be-b8e9-0e9eed76f7c7)


- Click **Yes** in **Confirmation**

![image](https://github.com/user-attachments/assets/2c023427-93f2-40b1-98e1-138fc1f91a0c)


- Select **Stable Release** and Click **Ok** for **Software Version**

![image](https://github.com/user-attachments/assets/47d69ed5-1d70-4dd5-a1c8-2b9ec476a7d3)


- Wait for complete installation in will take time.

- Goto **VirtualBox** Setting.
- Goto **Storage** tab.
- Remove **ISO** file.
- Restart **pfSense** 

![image](https://github.com/user-attachments/assets/1e30fd59-9741-4675-9d8c-8f9e56cce003)


**Configuration**


- Press **n** for **should VLANs be set up now**

<img width="581" alt="image" src="https://github.com/user-attachments/assets/8f2c5798-0283-4d80-8a2c-1e8d377a5eb8">



- For **Enter the WAN interface name** enter **le0**
- For **Enter the LAN interface name** enter **le1**


![image](https://github.com/user-attachments/assets/f42e13b4-1f98-4180-9828-0ef94682a653)


Now we are finished.

Head over to **another machine** which is in same network as **pfSense**
I will be using windows 10.

Windows machine should be using same **NAT Network** as **pfSense**

- Goto Network Setting.
- Change Adapter Setting.
- Select IPv4
- Click on Properties.
- Select Automatic settings.


- Goto Web Browser.
- Enter the LAN IP which is set for **pfSense**.


![image](https://github.com/user-attachments/assets/d5f7f807-5db7-40ea-baa7-4a41587251ff)

Username : admin
Password : pfsense


- A setup **Wizard** will open.
- On 4th step uncheck **RFC1918** (It will block private networks (10/8, 172.16, 192.168/16)


![image](https://github.com/user-attachments/assets/40f79869-5632-463e-b4aa-b82a350852f4)

- Finish the setup wizard.


**To Install third party packages**
- Goto **System**
- Select **Package Manager**
- **Available Packages**
- Search the package you want to install.

![image](https://github.com/user-attachments/assets/99e539ee-4774-41b4-a15b-c47f3f837e5f)

**Setting the Rules**
- Goto **Firewall**
- Select **Rules**

<img width="632" alt="image" src="https://github.com/user-attachments/assets/b58d564e-fec9-42dd-aaf7-9d1be51ef0c6">

- Add the Rules here

<img width="590" alt="image" src="https://github.com/user-attachments/assets/b62706fd-dacf-42f8-ac8b-1bf3ac6d13b1">




# Conclusion
Installing and configuring pfSense is a key step in creating a secure and efficient network environment. The process, from setting up hardware or a virtual machine to finalizing the configuration through its intuitive web interface, ensures that essential network components like firewalls, IP addressing, and routing are effectively managed. With powerful features such as VPNs, traffic shaping, and intrusion detection, pfSense provides flexibility and scalability for networks of all sizes. Its modular design allows for further customization through additional packages. Regular updates and careful configuration maintain security and performance, making pfSense a reliable, cost-effective solution for modern network management.


