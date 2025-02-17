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

