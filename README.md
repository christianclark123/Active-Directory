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
Download Virtual Box for Windows Hosts. https://www.virtualbox.org/wiki/Downloads

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

