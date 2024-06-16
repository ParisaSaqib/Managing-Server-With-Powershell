# Managing server with powershell

## Objective


Our objective is to demonstrate the seamless management of servers using Remote Server Administration Tools (RSAT), PowerShell remoting, and Windows Remote Management. By configuring PowerShell remoting and installing necessary modules on the server, we aim to establish efficient communication between the server and client. This setup facilitates real-time management and administration of server resources, showcasing the power and versatility of PowerShell in enhancing operational control and efficiency across the network.


### Skills Learned

- Automated WinRM service setup, Group Policy adjustments, firewall port opening, and PowerShell remoting endpoint creation.
- Configured WinRM for secure remote PowerShell command execution.
- Installed and managed server roles such as Active Directory Domain Services and DHCP.
- Enabled RSAT on client machines to facilitate remote server management.
- Developed proficiency in PowerShell cmdlets (e.g., `Get-Command`, `Get-EventLog`, `Enter-PSSession`, `Exit-PSSession`) for scripting and automating administrative tasks.
- 
### Tools Used
- VMware Workstation: Used for virtualization to create and manage virtual machines (VMs) for testing and deployment.
- Windows Server 2022: Deployed as the server operating system to host various server roles and services in the lab environment.
- Windows 10 Education: Installed on client machines to enable Remote Server Administration Tools (RSAT) and PowerShell remoting for remote management.
- PowerShell: Utilized extensively for scripting, automation, and administrative tasks across both server and client environments.

## Steps
**Server Side:**

    Enable-PSRemoting -Frce
        
Enable-PSRemoting is essential as it configures the WinRM service, adjusts local Group Policy settings, opens firewall ports, and creates a PowerShell remoting endpoint, allowing efficient remote administration and automation on a Windows server. Running this command automates the setup process, enabling secure and streamlined remote PowerShell sessions.

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/c67d4e8c-58e9-4773-ae24-715d5f3814d1)

        winrm quickconfig
Ensure WinRM Configuration:
Validates and adjusts Windows Remote Management (WinRM) settings to enable secure communication and remote execution of PowerShell commands.
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/8f410ab4-dc3b-4b19-a36b-08f8ff5f974c)


      Install-WindowsFeature AD-Domain-Services

 Install Active Directory Domain Services (AD DS):
 Sets up a domain controller for managing network users, computers, and services.
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/5f1fbc6b-6f8b-4c4f-8cf9-e1276c1e2031)


        Install-WindowsFeature DHCP -IncludeManagementTools
Install DHCP Server with Management Tools:
Deploys DHCP (Dynamic Host Configuration Protocol) server for automatic IP address allocation and management.      
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/59f566a2-9882-45fd-bd79-7ef1f2d66e35)

        Command: Install-WindowsFeature DNS -IncludeManagementTools
        
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/a0465b0f-343c-404c-be95-aec406ef06df)

    
        Install-WindowsFeauture -Name RSAT-AD-Tools
        
  Install DHCP Server with Management Tools:
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/f78d0985-5abd-48a0-96be-2115fb84c553)

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/9c1d48e0-db1f-43ea-b6a2-2cbe585f2ef9)

**Client Side (RSAT Installation):**

RSAT Installation:
RSAT or Remote Server Admin Tools lets us manage Windows Servers remotely. It includes PowerShell cmdlets and providers which can be used to manage roles and features. Since it is not enabled by default in the Windows PC, we need to enable it by running Enable-PSremoting on an administrator PowerShell.

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/dca3f677-85b8-40e2-81de-3efcd56d5dc6)
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/acc411fa-51e5-492f-9fc3-9bab04261790)

    
       Enable-PSRemoting -Force
 Starting a Remote Session:
 
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/7aab8292-fb20-40f8-a81b-5afa302ea304)

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/6e4e0bca-1bda-42b2-ad4b-d8a978e8aee3)

        Enter-PSSession -ComputerName Win-Server -Credential (Get-Credential)
        
 Establish Remote Session:
Initiates a remote PowerShell session from the client to the server for administrative tasks.

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/8d9202f6-ba43-4cfd-b9a0-76546ccd9c2f)

       Get-EventLog -Logname Application -ComputerName 192.168.239.1 -Newest 10

  Retrieve Event Log Entries:
  Demonstrates fetching event log entries from the server using PowerShell cmdlets.
  
![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/cf6bbf66-9963-4723-b3da-b3119c2d0975)

      Exit-PSSession

Exit Remote Session:
Terminates the current remote PowerShell session from the client to the server.

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/add501ec-f200-46de-ac09-c9004e73e7ee)

Get-Commands:
To find other commands we can run, we can use the Get-Command cmdlet to get all the commands that are relevant to the server or the instance we are running the PSSession in

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/4a635d09-6cc9-4913-819a-cd71a7d27f38)

![image](https://github.com/ParisaSaqib/Managing-Server-With-Powershell/assets/96464987/1ba75984-b763-4ac6-b7aa-72afa29be8ac)

## References
- JasonGerend. (n.d.). Remote Server Administration Tools. Microsoft Learn. https://learn.microsoft.com/en-us/windows-server/remote/remote-server-administration-tools
- Sdwheeler. (2022, December 9). PowerShell remoting - PowerShell. Microsoft Learn. https://learn.microsoft.com/en-us/powershell/scripting/learn/ps101/08-powershell-remoting?view=powershell-7.4
- Sdwheeler. (2023, July 5). about_Remote - PowerShell. Microsoft Learn. https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.4

  ## Acknowledgement:

This project was completed in collaboration with Marian Aquilizan and Brhamjot Singh as our final project for the Virtualization class at BCIT. Their contributions and teamwork were invaluable to the successful execution of this project.
