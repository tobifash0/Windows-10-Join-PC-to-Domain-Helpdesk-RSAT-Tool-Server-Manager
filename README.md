# Overview: Lab 4 Windows 10, Join PC to Domain (Helpdesk), RSAT Tool, Server Manager
This section of my home lab documentation demonstrates the process of joining a Windows 10 PC to a domain using RSAT (Remote Server Administration Tools) and managing server roles through Server Manager. The project covers the steps for configuring a Windows 10 PC to be part of an Active Directory domain, using the RSAT tools to perform administrative tasks, and leveraging Server Manager to manage server roles and features within the domain.

## Objectives
Join a Windows 10 PC to a domain as part of a helpdesk setup.
Install and configure RSAT tools on Windows 10 for remote administration of servers and network resources.
Use Server Manager to manage server roles and features in a domain environment.
Perform basic administrative tasks such as user management and role configuration from a client machine.
## Documentation
In this home lab, I will demonstrate how to install Windows 10 for a local account and join it to our domain (tobifash.com). To achieve this, we will create a separate virtual machine for the Windows 10 installation, specifically for our local Help Desk account. Next, we will download and install the RSAT (Remote Server Administration Tools) tools to enable the Help Desk account to access and manage Active Directory.

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

<br>

11. Enter "User" as the name, skip the password creation, and click Next.

<br>

![68747470733a2f2f692e696d6775722e636f6d2f7854614c4871332e706e67](https://github.com/user-attachments/assets/9587d8cd-4b19-455c-b190-d155a25a73a0)

<br>

12. Now we should have our Windows 10 ready.

<br> 

![68747470733a2f2f692e696d6775722e636f6d2f683962565245502e706e67](https://github.com/user-attachments/assets/28d1f12c-5c52-4595-837a-9a9d831778c7)

<br>

13. For best practice in a lab environment, we’ll configure static IP addresses for both virtual machines. This ensures consistent network communication and allows us to successfully connect the Windows 10 machine to the domain, enabling seamless interaction between the two virtual machines. Next, switch to the Windows Server 2022 virtual machine. Open the Control Panel and go to View network status and tasks → Change adapter settings.

<br>

![68747470733a2f2f692e696d6775722e636f6d2f615531337432662e706e67 (1)](https://github.com/user-attachments/assets/03f7a381-3736-4c9f-b34e-83602cf5b393)

<br>

14.Open the Control Panel and go to View network status and tasks → Change adapter settings.

<br>

![68747470733a2f2f692e696d6775722e636f6d2f394a35684b67642e706e67](https://github.com/user-attachments/assets/49e9e4c0-4d79-4b31-800b-636639833587)

<br>
15. Right-click the network connection (Ethernet) and select Properties to begin configuring the network settings.
<br>

![68747470733a2f2f692e696d6775722e636f6d2f4b71507a5372692e706e67](https://github.com/user-attachments/assets/de03aecc-85b0-4022-85db-489d3d6727ba)


<br>

16. Double-click on Internet Protocol Version 4 (TCP/IPv4).

<br>

![image](https://github.com/user-attachments/assets/24a66167-64c5-40b5-ae3a-b3137d35cba4)

<br>
17. Select Use the following IP address, then configure the static IP address as follows:

IP Address: 192.168.1.100
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
Preferred DNS: 168.192.1.1


Click OK to save the settings. 

<br>

<img width="951" alt="Screenshot 2025-02-22 at 5 00 31 PM" src="https://github.com/user-attachments/assets/86546f46-8db7-4058-b657-256234a068ca" />

<br>


18. Next, modify the network settings on the virtual machine by selecting Devices at the top, then choose Network and go to Network Settings.

<br>

![68747470733a2f2f692e696d6775722e636f6d2f454a70393435302e706e67](https://github.com/user-attachments/assets/3c9443c2-18c2-452a-bfd3-c751f2370265)


<br>


19. Now, change Attached to: NAT to Intenal Network.


<br>

![Screenshot 2025-02-22 at 5 06 50 PM](https://github.com/user-attachments/assets/96aed26b-bc81-45b7-9ec4-4d6c234e4e2c)

<br>

20. Now, switch back to the Windows 10 Project machine and enable the administrator account. Open File Explorer, right-click This PC, and select Manage. This will open Computer Management.

    <br>

![68747470733a2f2f692e696d6775722e636f6d2f4e4658775651762e706e67](https://github.com/user-attachments/assets/6da0e8af-595e-4a76-ae87-1eab3a6d72c6)


<br>

21. Expand Local Users and Groups, then select Users. Right-click on Administrator and click Properties.

<br>

![image](https://github.com/user-attachments/assets/8a632dfa-8f87-460c-8c05-8b09a3540b8b)


<br>

22. The Account is disabled option is checked by default. Uncheck it, then select Apply and click OK.

<br>

![image](https://github.com/user-attachments/assets/24aa9cdc-e1c1-4c64-ad2f-dbbc5ac1dabc)

<br>

23. Next, click on Administrator again and select Set Password 
    <br>

![image](https://github.com/user-attachments/assets/a84f19f8-3bc0-4980-8d3f-0efcc302d214)

<br>

24.  Proceed. Create a password, then click OK. A prompt will appear confirming that your password has been set.

<br>

![image](https://github.com/user-attachments/assets/b8bdc401-3907-4587-a2fc-3c7c8bc37d0f)

<br>

25. Now that the Administrator account is enabled and the password is set, log into that account by first signing out of your Windows 10 Project machine. Right-click the bottom-left Windows icon, select Shut down or sign out, and then choose Sign out.

<br>

![image](https://github.com/user-attachments/assets/f5d49faa-3426-41af-9324-cd9dbbd87134)

<br>

26. Now that the Administrator account is available, we will log into it instead.

<br> 

![image](https://github.com/user-attachments/assets/1d0c6b15-e798-4833-a001-8848cf4ca949)

<br>


27. Since the default 'User' account can be accessed without a password, we will remove it to enhance security and prevent unauthorized access. Open File Explorer, right-click This PC, and choose Manage. Navigate to Local Users and Groups and select Users. To delete the 'User' account, right-click on it and select Delete.

<br>


![image](https://github.com/user-attachments/assets/568cdeaa-c135-41b6-8f6c-865d9193115e)


<br>


28. To confirm that the 'User' account has been successfully removed, log out and ensure that the only password-protected account remaining is the 'Administrator' account. We have now successfully set up our local Help Desk account. This procedure removes weak default accounts, enhancing the security of Windows 10.

<br>


![image](https://github.com/user-attachments/assets/8d63024b-0daa-4aff-b875-eaa010d22987)

<br>

29. Next, we will download the RSAT tools to enable access to Active Directory on a local level. Type "Optional" in the search bar at the bottom left and click on Add an optional feature, then select Add a feature.

<br>

![image](https://github.com/user-attachments/assets/5e2035e8-3d5e-431e-a81b-f74e1c3b348c)


<br>

30. <br>

    ![image](https://github.com/user-attachments/assets/12b1bd6c-48aa-4bfb-97bb-795a31196c5f)


<br>


31. Type "RSAT" in the search bar for a quicker search, then install the following 7 features:

RSAT: Active Directory Certificate Services Tools
RSAT: Active Directory Domain Services and Lightweight Directory Services Tools
RSAT: DHCP Server Tools
RSAT: DNS Server Tools
RSAT: Group Policy Management Tools
RSAT: Remote Desktop Services Tools
RSAT: Server Manager
Click Install (7). Once the installation is complete, restart the virtual machine.

<br>

![image](https://github.com/user-attachments/assets/36ede1e4-b5f8-4ff7-b423-6a14e76f5cd7)

<br>

32. <br>
 ![image](https://github.com/user-attachments/assets/152cc87e-22bc-4643-a4d8-014ab4e1c8b8)

<br>


33. Now that all of our administrative tools are installed, we can verify this by clicking the Windows icon at the bottom left and looking for Windows Administrative Tools.

<br>

![image](https://github.com/user-attachments/assets/62aa8778-d3ed-43ba-b12c-3df76a5ba952)

<br>

34. Now, let's add our PC to the domain SimoTech.com. Before doing that, let's rename our PC to Desktop1. To do this, open File Explorer, right-click on This PC, and select Properties. Then, click on Rename this PC (advanced), followed by Change. In the Computer name field, enter Desktop1, click OK, and then select Restart now.

<br>

![image](https://github.com/user-attachments/assets/d6d96f01-24bf-4c93-826e-3fb6be415283)

<br>

35. After the restart, open Internet Explorer and download Google Chrome from the web. Once Chrome is installed, download the TeamViewer Full Client 64-bit. We will be using TeamViewer in our upcoming homelabs.

<br>

![image](https://github.com/user-attachments/assets/c669e8ba-c08e-40b2-8f1c-df489457fcad)

![image](https://github.com/user-attachments/assets/a6ee9162-431e-436f-bd72-8d9707f9b1d4)


<br>


36. Next, we will set a static IP on our Windows 10 machine, just as we did with the Windows Server 2022 machine, and join it to the domain tobifash.com. As before, open Control Panel on your Windows 10 Project machine, select View network status and tasks, then Change adapter settings. Right-click on the Ethernet connection and select Properties, then double-click Internet Protocol Version 4 (TCP/IPv4). Select Use the following IP address and enter the following:

IP Address: 192.168.1.101
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
Preferred DNS: 192.168.1.1

Next, update the network settings on your virtual machine as we did earlier by selecting Devices → Network → Network Settings, and change NAT to Host-only Adapter.


<br>

![Screenshot 2025-02-22 at 6 26 25 PM](https://github.com/user-attachments/assets/384fdb21-bdff-4062-80e7-92b1f1bc7d91)

<br>

37. Now that our networks and static IPs are set up, let's test the connection by pinging our Windows 10 machine from the Windows Server 2022 machine. On the Windows 10 Project machine, open Command Prompt and type: ping 192.168.1.100

This is the static IP we set up for the Windows Server 2022 machine.
<br>

<img width="797" alt="Screenshot 2025-02-22 at 6 39 40 PM" src="https://github.com/user-attachments/assets/0e470ac2-ac93-4f21-b9bc-9dbb43178068" />

<br>

38. Now that we can ping the Windows Server 2022 machine, we can finally join our Windows 10 machine to the SimoTech.com domain. First, open File Explorer, right-click on This PC, and select Properties. Then, click on Rename this PC (advanced), followed by Change. Under Domain, type SimoTech.com.


<br>

![Screenshot 2025-02-19 at 2 33 09 AM](https://github.com/user-attachments/assets/6e77da9e-6c8f-4537-8648-4c00fd2e0e8b)

<br>

39. Next, we will use our Administrator account and password to join the domain. Afterward, a prompt will appear asking us to restart the virtual machine to apply the changes.

<br>

![Screenshot 2025-02-19 at 3 03 05 AM](https://github.com/user-attachments/assets/ba253eaa-267d-4f59-9297-91d843adfe48)

<br>

40. To verify that Desktop1 has been successfully added to the SimoTech.com domain, open Active Directory Users and Computers on the Windows Server 2022 machine. Select Computers, and you should see DESKTOP1 listed as part of the domain. Desktop1 will serve as our Helpdesk account.

<br> 

![Screenshot 2025-02-19 at 3 09 59 AM](https://github.com/user-attachments/assets/f20ca0a8-360e-4605-b2a8-cd1e7acd794a)

<br>
41. Next, on the Windows Server 2022 machine, still in Active Directory Users and Computers, select Users, right-click on Helpdesk, and choose Reset Password. Create a new password for the Helpdesk account. Afterward, use this new password to log into the Windows 10 virtual machine.

<br>



