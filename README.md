# Active-Directory

## Objective

The Active Directory Home Lab project is designed to create a simulated enterprise environment using Windows Server 2022 and Windows 10. The primary focus is configuring a basic network with organizational units, groups, users, and permissions, mimicking a real-world IT infrastructure. This hands-on experience aimed to enhance understanding of Active Directory, network management, and access control in a structured enterprise setting.

### Skills Learned

- Proficiency in Active Directory installation, configuration, and management.
- Practical knowledge of organizational unit (OU) structuring and group policy implementation.
- Advanced understanding of user authentication, group-based permissions, and access control.
- Hands-on experience in setting up and managing a Windows Server and client network.
- Improved troubleshooting and problem-solving skills in system administration.
- Enhanced knowledge of enterprise IT infrastructure and network security fundamentals.

### Tools Used

- Draw.io for enterprise network visualization
- VirtualBox for virtual machine creation and network simulation.
- Windows Server 2022 ISO for setting up the Domain Controller.
- Windows 10 ISO for configuring client machines.
- Active Directory tools for user, group, and policy management.
- Group Policy Management Console (GPMC) for configuring and enforcing group policies.

## Steps
Before we begin we will set up our simulated Enterprise Domain Network Topology Diagram using the free website draw.io https://app.diagrams.net/

Once the website has loaded, choose "Blank Diagram" and click Create.

Use the search bar to search up the icons we will use for this topology.

![image](https://github.com/user-attachments/assets/f9fb3b7c-f548-4d0f-8149-9fea3aa07e3a)

The icons we will use are:
- Computer
- Server
- Switch
- Router
- Cloud (ISP)

Connect the icons together by clicking on the icon and hitting the arrow and connecting it to the appropriate icon.

Connections:
- Computer and Server to the Switch
- Switch to the Router
- Router to the Cloud (ISP)

![image](https://github.com/user-attachments/assets/53396ad6-8d27-4d34-893d-40b5454849e9)

Next, we will document the network information. To add a text box double click the diagram anywhere and choose "Text". 
Name the icons in your diagram with the names of the PC you will use. For the server you will use Windows Server 2022. For the Client PC you will use Windows 10 Pro.

![image](https://github.com/user-attachments/assets/5e1bfae8-959f-406c-a6b0-c4cd22ea821a)


Add a text box for your domain and network information
For my network, I will be using 192.168.10.0/24.
My Active Directory Server will have a static IP of 192.168.10.5/24.
My Client PC will have a static IP of 192.168.10.100/24.
Also, add the network information underneath each icon

![image](https://github.com/user-attachments/assets/e9578b7f-bc5e-4390-b16c-b64edc88f1ba)

Save the diagram to your computer. This is the network topology we will use when setting up our network and active directory.

Next, we will download Virtual Box for Windows Hosts. https://www.virtualbox.org/wiki/Downloads. VirtualBox is the application that will host the virtual machines for this lab. 

![image](https://github.com/user-attachments/assets/e0345df9-d222-40f4-9f58-96c2c9c9ffb7)

*BONUS* Check SHA256 Checksum with Virtualbox.org SHA256 Checksum to ensure integrity of download.
Head to your downloads File Explorer Folder and open a PowerShell prompt by holding Shift + Right Click in the downloads folder.

![image](https://github.com/user-attachments/assets/7f416933-8039-49ef-ab73-8f3843e11796)

Once Powershell is opened type in "Get-FileHash" "Virtual" and tab to autocomplete. 

![image](https://github.com/user-attachments/assets/7b8e2ab1-f091-4ffd-b4b8-21c4c7106afb)

On the virtualbox downloads page scroll down until you see the File Checksum for SHA256. Click on it to bring you to the SHA256 Hash page where you can copy and paste your hash into the Find in Page (Ctrl+F) to ensure the download is safe. 

![image](https://github.com/user-attachments/assets/3d6c76ca-777a-4333-8b1a-f35f79e06de1)
![image](https://github.com/user-attachments/assets/32ab4bed-aca7-4c3c-9efa-6b5ca69820e1)

From there double click the VirtualBox download in your downloads folder and install VirtualBox. Once installed Oracle VirtualBox Manager will open. 

![image](https://github.com/user-attachments/assets/5ce983b0-9a27-42d5-80ff-6c16e8b1eac9)

Download the media creation tool Windows 10 ISO image for Virtual Box. Download from the "create Windows 10 installation media" https://www.microsoft.com/en-ca/software-download/windows10

![image](https://github.com/user-attachments/assets/8536da4e-d96d-424f-8d32-d29e13cbd5e2)

Follow the installation instructions and choose Create Installation media, choose "Use recommended options for this PC", and under "Choose which media to use" select ISO file. Save the file wherever you would like. *Note* Create a folder for your ISO images so they are all in one place.

![image](https://github.com/user-attachments/assets/adc38606-4199-48f1-b881-35bed45bb67a)
![image](https://github.com/user-attachments/assets/3a31a1a3-bfa9-4e9c-a69b-77b6a6fe4d84)
![image](https://github.com/user-attachments/assets/bda4cb52-33b8-4e4d-b9f5-e9147c0c26d8)

Open the window for your Virtualbox to create your Windows 10 client using the Windows.iso file. 

![image](https://github.com/user-attachments/assets/c2a3a08c-0c02-40ca-9ffc-8713643f8ed3)

Name the VM, Choose a folder where you will install the VM, and navigate to your downloaded Windows.iso image. *NOTE* Click "Skip Unattended Installation" if you want to configure the Windows 10 machine yourself.

![image](https://github.com/user-attachments/assets/7d738866-4d0c-4043-a7fc-590bce3aa9c7)

Give the VM at least 4 GB (4096 MB) and 1 CPU for optimal performance. Click finish.

![image](https://github.com/user-attachments/assets/f92195ab-ffd0-4260-801b-3ae2db6f6381)

Double-click or press Start on the VM to run the VM installation. 

![image](https://github.com/user-attachments/assets/9ca55e43-e89d-46a1-8ec5-f545b56e6551)

Follow the installation for Windows 10. When asked to Activate Windows click the "I don't have a product key" and for the operating system choose "Windows 10 Pro".

![image](https://github.com/user-attachments/assets/6b981107-2cdf-4da1-989f-5bf236098e40)
![image](https://github.com/user-attachments/assets/22857a83-be40-4842-a507-aba47f85e6ed)

Choose "Custom Install Windows", click next, and Install. Follow the setup prompts. Create a user, password, and security questions. You can turn off all privacy settings for the device and skip Cortana. 

![image](https://github.com/user-attachments/assets/5be18b6e-86f5-4423-8ad1-84ef90d69cb1)
![image](https://github.com/user-attachments/assets/995b3de4-283b-4182-a0ff-95eb676a500e)

Install Windows Server 2022. Search "Windows server 2022 iso" Click the first link, that will bring you to the registration page. Click on the "Download ISO". After registration, you will be able to download the ISO image. *NOTE* This may take a while depending on your download speeds.

![image](https://github.com/user-attachments/assets/9f16ab41-0a3e-411a-8990-be82b9488aa4)
![image](https://github.com/user-attachments/assets/aab087ce-8872-47d4-b588-1c53e9328435)
![image](https://github.com/user-attachments/assets/2140a72c-8563-40d3-bdec-fc85a19ed8ea)

 Once Windows Server 2022 is downloaded. Open VirtualBox and add a new VM. This VM will contain your Windows Server 2022 Active Directory Domain Controller. Follow the instructions for setting up a new VM from before. Name this VM ADDC01 (Active Directory Domain Controller 01) 
 *REMEMBER* Use the newly downloaded Windows Server 2022 ISO image.

![image](https://github.com/user-attachments/assets/afdaf56e-f2d9-4bd4-962a-f00013b9d787)
![image](https://github.com/user-attachments/assets/fe045503-ecf9-45d1-a3ae-a90e75320f8f)
![image](https://github.com/user-attachments/assets/61fc21ec-d91c-40f2-9671-b0b3e8f0116c)

Follow the setup. Choose Windows Server 2022 Standard Evaluation (Desktop Experience). *NOTE* If you do not choose this one and choose the first option, your Windows server will be a Command Line Interface(CLI) only making it difficult to navigate.
Choose Custom Installation and click next to install the operating system on the Drive 0 Unallocated Space. 
Installation will take around 10 minutes. 

![image](https://github.com/user-attachments/assets/b7e04604-80e9-4a9e-89bb-ad6c507ef741)
![image](https://github.com/user-attachments/assets/eac0163c-b12d-4c9a-9548-6fd9b285a82a)
![image](https://github.com/user-attachments/assets/b80b4235-0e0c-4d54-81a8-709ffa9d08c5)
![image](https://github.com/user-attachments/assets/e5062373-707b-4257-a7c9-2a68dd24135d)

After installation is complete and your VM reboots, a customize settings screen where you will be asked to provide a password for your administrator account. 
*NOTE* If you are prone to forgetting, write this password down. 

![image](https://github.com/user-attachments/assets/73bcc381-f37a-4e20-ae56-af74e82be455)

After setting your Admin password, the log-on screen will appear. In VirtualBox the default "Host" button is the right CTRL. In order to use CTRL+ALT+DEL on your VM you will press right CTRL+DEL or in the ribbon tabs on top click Input -> Keyboard -> Insert CTRL+ALT+DEL.
Log on to your Administrator account using the password you set up in the previous screen.

![image](https://github.com/user-attachments/assets/ece1a205-8c65-4d16-bdef-56c8e3b1b2e7)

When logged on to your administrator account a Network screen will popup asking you if you want the PC to be discoverable. You can click "No" as we will configure this according to the Network topology diagram we created at the beginning of this lab.

![image](https://github.com/user-attachments/assets/92ddd4db-a78a-4aba-b0b9-f35a9010ef2e)

When you log into your ADDC01 VM a program called Server Manager will popup. Server manager is where you will go to configure your Active Directory Domain Controller(ADDC). In the server manager you will also be able to configure organizational units, groups, accesses, and users. 

![image](https://github.com/user-attachments/assets/a9fc96ff-1dc9-4a5a-b118-1b957e8cf90c)

Before we configure anything, we will rename our Server and Windows 10 Client PCs. 
Right click the Windows icon, click settings, system, scroll down to "About", and click "Rename This PC". Rename both your DC controller and client PC according to your diagram.
Restart the VM after renaming.

![image](https://github.com/user-attachments/assets/68563a0f-a684-4e4e-a361-bb2b0403755b)
![image](https://github.com/user-attachments/assets/a53165cd-4e9b-4804-9a12-217faa2ba057)
![image](https://github.com/user-attachments/assets/471e798e-15c2-467e-8abe-af52d0f35d9c)
![image](https://github.com/user-attachments/assets/60dc46ba-a7c2-4cbd-b82a-7bda32bcfd1c)
![image](https://github.com/user-attachments/assets/752816c4-f026-4722-ae97-51dcb5d3bc74)

In order to get the Domain Controller(DC) and the Client PC on the same network we will set up a NAT network in Virtual Box.
In VirtualBox Manager, click Tools and click the three bullet points and select Network.

![image](https://github.com/user-attachments/assets/121170bd-cc25-44b7-b01c-e53c61ad24ba)

Click "NAT Networks" and "Create". At the bottom under General Options name the network and use the IPv4 Prefix from your network diagram. You can leave Enable DHCP. Both the server and client will have static IP addresses but if the client can use DHCP. When done hit apply.

![image](https://github.com/user-attachments/assets/45a2fadd-023f-493a-8eff-0cd52f92eb11)

Go to both your ADDC and Client in VirtualBox manager and click settings and Network and change the attached adapter to the newly created NAT network. 

![image](https://github.com/user-attachments/assets/ae3619f8-ed75-4d46-8a76-292ff8e5fd43)

Open either your ADDC or Client and under the search type "cmd" and click it. This will bring up the command prompt. In the command prompt type "ipconfig"

![image](https://github.com/user-attachments/assets/248072f4-0166-4cc0-87aa-4d274c4a0f31)
![image](https://github.com/user-attachments/assets/cc9cd2e9-2e97-4f63-a581-ca34dbc88c9f)

On my command prompt my client PC IP is 192.168.10.4. According to my diagram i want my client PC to have a static IP of 192.168.10.100/24.
To change the IP address we will click on the network icon in the bottom right and click "Network & Internet Settings"

![image](https://github.com/user-attachments/assets/13453e96-f0e6-46fa-b5c7-a0b827f2f4a2)

Under Advanced network settings click "Change adapter options" 

![image](https://github.com/user-attachments/assets/e1e0d9e8-5368-4a09-a1e1-110c4b48f745)

This will bring up a Network Connections window with a Ethernet connection. Right click on the Ethernet connection and click properties.

![image](https://github.com/user-attachments/assets/2941a880-c08c-417e-b850-5d0341857e7e)

Double click the "Internet Protocol Version 4 (TCP/IPv4). In order to set a static IP choose "Use the following IP address and fill in the information according to your network diagram. Until we set up the DNS on our domain controller use 8.8.8.8 for the DNS server (Google). When done click "OK" and rerun the command "ipconfig" This should display your new IP address. When done do this for your ADDC to reflect your network diagram.

![image](https://github.com/user-attachments/assets/32e41135-c8cf-4dff-9e5a-67d8a7d27770)
![image](https://github.com/user-attachments/assets/b20ebc64-af1e-42ce-ba75-ca533e45ab68)
![image](https://github.com/user-attachments/assets/1bfa8815-31fc-4493-afb2-614e40569dc1)

Now we will configure our ADDC-01 to a domain controller. 
On the Server VM, open Server manager and click Manage -> Add Roles and Features

![image](https://github.com/user-attachments/assets/e830d46c-7fb2-4083-a2fd-6c37cce42b09)

On the Before You Begin page click Next

![image](https://github.com/user-attachments/assets/379cf982-7f81-4562-a10d-8e9c38ee3663)

Choose Role-based or feature-based installation and click Next

![image](https://github.com/user-attachments/assets/43ba8aff-1318-4b89-aeba-0711dc5416f1)

Select your server it should have the name you chose in the earlier step that reflects your topology. Click Next.

![image](https://github.com/user-attachments/assets/3ae74423-6828-402d-9d30-6cc8f3490768)

Select the Active Directory Domain Services Role and include management tools. Click Add Features and Next.

![image](https://github.com/user-attachments/assets/6dbe4716-d0cf-4b1a-9816-fed5381f078b)
![image](https://github.com/user-attachments/assets/6ed1abb2-aa03-4dcc-b1c3-6a95a814e7c4)

On the Features and AD DS windows click Next. On the Confirmation window click "Restart the destination server automatically if required" and click Yes on the popup window. Click Install.

![image](https://github.com/user-attachments/assets/9acf6729-3c5d-4622-8fa0-a5622369fe2d)

After installation on your Server Manager there will be a Cuation Flag click on that and choose "Promote this server to a domain controller". A Deployment Configuration Window will pop up.

![image](https://github.com/user-attachments/assets/b4923633-7d06-4aa7-977a-1b04672b29f0)
![image](https://github.com/user-attachments/assets/8dfebb26-7f55-40ad-8dff-d540fc923df7)

Since this is the first domain choose "Add a new forest" and name your domain. For my domain i named it ADLab.local

![image](https://github.com/user-attachments/assets/5f084601-15f3-4ba2-929a-4d9ac818e1da)

Set a password for your domain and click next until you reach Additional Options.

![image](https://github.com/user-attachments/assets/59fda96e-8967-4c2b-bd00-f276fe65a549)

On the Additional OPtions window your NETBIOS name should be what you named your root domain. Click Next

![image](https://github.com/user-attachments/assets/fdaedd60-8f84-438a-bfe2-909ce04c35f0)

Click Next on the Paths window, review your domain options, and click Next. Click Install once your prerequisite checks pass successfully. After installation the computer will restart.

![image](https://github.com/user-attachments/assets/d1162496-6dc7-4108-83e2-b3124ad04ba2)

Once the ADDC VM is restarted your administrator account will have the domain name in front of it. 

![image](https://github.com/user-attachments/assets/46853485-7951-4c90-8704-29b2780c4ab5)

After logging in, on your Server Manager dashboard you should see the AD DS and DNS in green. Now your domain is ready for the client to join.

![image](https://github.com/user-attachments/assets/6f67c525-8da5-4462-8444-358b6e65f951)

Before connecting to the domain you have to change your "Preferred DNS server:" to the IP of your domain. Use the steps above to change your DNS server.

![image](https://github.com/user-attachments/assets/275cbca3-f4ea-4466-a962-99cd04540195)

In order to join the domain on your client PC right-click the Windows and click Settings -> System -> About -> Advanced system settings -> Computer Name Tab -> Change... -> Click Domain and type in your domain name. You will be asked to enter admin permissions to connect. If connected successfully, you should get a "Welcome to the ...local domain" message. Restart your client VM to apply the changes. 

![image](https://github.com/user-attachments/assets/7dc5a3b4-13a0-499d-a941-820e45582b87)
![image](https://github.com/user-attachments/assets/06802d3c-210a-4b37-a379-ec992e639c21)
![image](https://github.com/user-attachments/assets/ae9f7265-7d16-462b-a9d2-931888da5e8a)
![image](https://github.com/user-attachments/assets/18eea638-b2e8-44a4-b5e7-52b77af3826e)

Now that our client is connected we can add organizational units, groups, users, and policies to simulate an enterprise network. For this lab I will stick to a simple structure. 

First, we will create an organizational unit. In your Server Manager under Tools, Click Active Directory Users and Computers. 

![image](https://github.com/user-attachments/assets/45e59710-292e-4bd0-b1b1-188e2ee47ae0)

In the Active Directory Users and Computers expand your domain

![image](https://github.com/user-attachments/assets/78f1bbfa-3ec3-4900-9ba1-3b504d278ba7)

Right-click your domain and under New -> click Organizational Unit(OU) to create an OU. In an enterprise you have a top-level OU (company) under which you have the different departments (IT, HR, Finance, Sales). For this lab, I'm going to create the top-level OU (AD Lab) and IT as my sub-OU.

![image](https://github.com/user-attachments/assets/f7543f2b-ada7-427a-a633-33c0d90697f5)
![image](https://github.com/user-attachments/assets/40759ad0-5238-448c-809e-c0f625c115b3)

Within the IT OU I created I will create two groups IT_Admin and IT_Support. To create a group right click on the OU you created and click New -> Group. For the IT_Admin and IT_Support, this is going to be a Global Security group. 

![image](https://github.com/user-attachments/assets/a86a9366-c33b-4fa4-a368-7d88d382b621)
![image](https://github.com/user-attachments/assets/f657e26c-1ef0-49ab-b6a9-b753322c5837)
![image](https://github.com/user-attachments/assets/37fa8fcc-30f1-4b82-8d36-3d4a8b345eda)

Within those groups, I will create users that will be members of IT_Admin and IT_Support. To create users right-click on the Users -> New -> User under Active Directory Users and Computers. Fill out the information and click Next. Choose a password for your users configure the settings you would like for your organization and click Finish. 

![image](https://github.com/user-attachments/assets/994fe8d7-1828-4604-9699-715e6078234e)
![image](https://github.com/user-attachments/assets/30953b77-69c5-4bc3-829f-81d17d4b87f2)
![image](https://github.com/user-attachments/assets/a18579e1-d2ff-4541-8e5a-7ebc226eb93f)

In order to add users to specific groups right click the user and "Add to a group.." I will be adding my users to the IT_Admin and IT_Support groups. A window will pop up where you will type in the name of the group and use the "Check Names" feature to make sure it is the proper group. You will get a confirmation that the user has been added to the group.

![image](https://github.com/user-attachments/assets/7ef787aa-9d93-4ef5-9b13-38a350ea0b64)
![image](https://github.com/user-attachments/assets/0f1cfce9-cf19-4364-8235-745564a42c67)
![image](https://github.com/user-attachments/assets/a89d0fba-4a26-4085-bc6f-fc5cdf22fd6b)

To further check which members are in what groups you can right-click on either the group or the user to see what group the member is a part of or what members are in a group. 

![image](https://github.com/user-attachments/assets/4d66f830-027e-475b-a3ab-94ebe6e7c919)
![image](https://github.com/user-attachments/assets/0f28aa51-d328-4653-9585-f4db5641a368)

For my IT_Admin group, I want it to have full administrator access so I will add that group to the Administrators and Domain Admins groups. 

![image](https://github.com/user-attachments/assets/10f1bf02-c88c-4e7c-9c76-ab1bf1d7dc2f)
![image](https://github.com/user-attachments/assets/4c44483b-e62c-4d6c-8ebc-266f084d3e75)




