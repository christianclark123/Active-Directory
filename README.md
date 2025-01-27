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

Give the VM atleast 4 GB (4096 MB) and 1 CPU for optimal performance. Click finish.

![image](https://github.com/user-attachments/assets/f92195ab-ffd0-4260-801b-3ae2db6f6381)

Double-click or press Start on the VM to run the VM installation. 

![image](https://github.com/user-attachments/assets/9ca55e43-e89d-46a1-8ec5-f545b56e6551)

Follow the installation for Windows 10. When asked to Activate Windows click the "I don't have a product key" and for the operating system choose "Windows 10 Pro".

![image](https://github.com/user-attachments/assets/6b981107-2cdf-4da1-989f-5bf236098e40)
![image](https://github.com/user-attachments/assets/22857a83-be40-4842-a507-aba47f85e6ed)

Choose "Custom Install Windows", click next and Install.

![image](https://github.com/user-attachments/assets/5be18b6e-86f5-4423-8ad1-84ef90d69cb1)
![image](https://github.com/user-attachments/assets/995b3de4-283b-4182-a0ff-95eb676a500e)

