# Overview: Lab 4 Windows 10, Join PC to Domain (Helpdesk), RSAT Tool, Server Manager
This section of my home lab documentation demonstrates the process of joining a Windows 10 PC to a domain using RSAT (Remote Server Administration Tools) and managing server roles through Server Manager. The project covers the steps for configuring a Windows 10 PC to be part of an Active Directory domain, using the RSAT tools to perform administrative tasks, and leveraging Server Manager to manage server roles and features within the domain.

## Objectives
Join a Windows 10 PC to a domain as part of a helpdesk setup.
Install and configure RSAT tools on Windows 10 for remote administration of servers and network resources.
Use Server Manager to manage server roles and features in a domain environment.
Perform basic administrative tasks such as user management and role configuration from a client machine.
## Documentation
In this home lab, I will demonstrate how to install Windows 10 for a local account and join it to our domain (SimoTech.com). To achieve this, we will create a separate virtual machine for the Windows 10 installation, specifically for our local Help Desk account. Next, we will download and install the RSAT (Remote Server Administration Tools) tools to enable the Help Desk account to access and manage Active Directory.

The process begins with downloading the Windows 10 Installation Media Tool from the official Microsoft website: [Windows 10 Installation Media Tool](https://www.microsoft.com/en-us/software-download/windows10).

<br>
1. Open the media tool installer and click 'Accept.' Next, select 'Create installation media (USB flash drive, DVD, or ISO file) for another PC.' Save the download to your 'Downloads' folder, and you should be able to access it from the VirtualBox ISO.

<br>

![68747470733a2f2f692e696d6775722e636f6d2f47474c415032742e706e67](https://github.com/user-attachments/assets/6e72f8e9-198c-40e5-aa5e-7663e86e72d4)

<br>

2. Next, open your VirtualBox application and create a new virtual machine. Click Machine in the top-left corner, then select New.

 <br>

   ![68747470733a2f2f692e696d6775722e636f6d2f79736b347051382e706e67](https://github.com/user-attachments/assets/4f965529-f22d-4d28-8601-d95fbf1f794a)

   <br>
3. Name the virtual machine "Windows 10 Project." For the ISO image, navigate to the Downloads folder, click the dropdown icon, select "Other," and choose the "Windows" ISO file. Then, select "Skip unattended installation.”
<br>

<img width="951" alt="Screenshot 2025-02-17 at 2 52 04 AM" src="https://github.com/user-attachments/assets/5d3356d8-d212-4e1e-9e3b-98006d95d211" />

<br>

4. Select Hardware, and by default, the base memory is set to 2048 MB. Youc can increase it. Finally, click Finish and start the machine by pressing Start. 

<br> 

![68747470733a2f2f692e696d6775722e636f6d2f6d43454f5036382e706e67](https://github.com/user-attachments/assets/219a87c8-817b-4e72-bce1-3a499b42962b)

<br> 
5. On the Windows Setup screen, click Next, then Install Now.
<br>

![68747470733a2f2f692e696d6775722e636f6d2f42594c355261622e706e67](https://github.com/user-attachments/assets/923ac63d-68fa-442c-8cf2-ad005068f1a1)

<br> 

6. Select “I don’t have a product key”.

<br>

![68747470733a2f2f692e696d6775722e636f6d2f43716a346d47322e706e67](https://github.com/user-attachments/assets/5fcb5233-ee6d-4c24-8ee3-3ad5a6690fbe)

<br> 

7. Make sure to select "Windows 10 Pro," check the box to accept the license terms, and click Next.
<br>

![68747470733a2f2f692e696d6775722e636f6d2f6f656f413567702e706e67](https://github.com/user-attachments/assets/02344120-ef61-4c29-842e-f442bcabdfa6)

<br>

8. Select "Custom: Install Windows only," then click Next to begin the installation of Windows 10.

<br>

![68747470733a2f2f692e696d6775722e636f6d2f47356c775051732e706e67](https://github.com/user-attachments/assets/3b61e3cf-b90a-4fa5-a992-828cbab24971)

<br>

9.  Select “Personal use”.

<br> 

![68747470733a2f2f692e696d6775722e636f6d2f7937534f5942502e706e67](https://github.com/user-attachments/assets/1fa16350-3c80-43a9-b9db-fc3a7cc59e9e)

<br>

10. On the bottom left, select “Offline account”.
    <br>

![68747470733a2f2f692e696d6775722e636f6d2f4658736d7044562e706e67](https://github.com/user-attachments/assets/740da4a5-43c1-47ce-88cb-a4e074b2db44)















