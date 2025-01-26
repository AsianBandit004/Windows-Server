## 🖥️ Tutorial: Setting Up Active Directory in Proxmox with Windows Server 2019
In this tutorial, we'll guide you through setting up Active Directory (AD) in a Windows Server 2019 VM running on Proxmox. Active Directory is the backbone of network management, handling user authentication, permissions, and more. Whether you're a beginner or an experienced sysadmin, this tutorial will walk you through every step.

## 📋 Prerequisites
Before we begin, make sure you have:

A Proxmox server set up and running.
The Windows Server 2019 ISO downloaded from Microsoft.
At least 2 GB of RAM and 2 CPU cores for your VM (more resources are recommended for larger environments).
## ⚙️ Step 1: Create the Windows Server 2019 VM in Proxmox
Let’s start by creating the Windows Server 2019 VM in Proxmox.

Log in to Proxmox and navigate to the Datacenter view.

Click on the Create VM button in the upper right.


Configure the VM settings:

General:
VM ID: Choose a unique ID for your VM.
Name: Name it something like WinServer2019-AD.
OS:
Select Windows 10/2016/2019 as the template.
Select the ISO Image you downloaded for Windows Server 2019.
System:
Enable UEFI for modern operating systems (recommended).
Hard Disk:
Set the disk size (e.g., 50 GB).
Use SCSI for disk interface.
CPU:
Allocate 2 CPU cores (or more, based on your system).
Memory:
Assign at least 2 GB RAM (preferably 4 GB or more).
Network:
Choose virtio for better performance.
After configuring, click Finish to create your VM.

## 🔄 Step 2: Install Windows Server 2019
Start the VM by clicking Start in the VM menu.

Open the Console by clicking the Console button in the top menu.

The VM will boot from the Windows Server 2019 ISO. Follow these installation steps:

Select your language and keyboard layout.
Click Install Now.
Choose Windows Server 2019 Standard edition and click Next.
Select Custom Install and create a partition for Windows on the virtual disk.
Complete the on-screen instructions.

Once the installation is complete, the VM will restart. Set up your Administrator password during the initial setup.

## 🏗️ Step 3: Install Active Directory Domain Services (AD DS)
Log in to Windows Server 2019 with the Administrator account.

Open Server Manager, which should launch automatically.

Click on Add roles and features to launch the wizard.


In the wizard, click Next until you reach the Select Features page:

Check the box for Active Directory Domain Services (AD DS).
A pop-up will appear, click Add Features.
Click Next.
On the Confirmation screen, click Install to begin the installation of AD DS.


Once installation completes, click Promote this server to a domain controller to start the AD configuration process.

## 🔧 Step 4: Configure Active Directory Domain
In this step, we will configure the Domain Controller (DC) for your Active Directory setup.

Active Directory Domain Services Configuration Wizard will appear. Select:

Add a new forest.
Root domain name: Enter a name like homelab.local.
Set Domain and Forest Functional Levels:

Choose Windows Server 2016 or higher.
Set a Directory Services Restore Mode (DSRM) password (make sure to remember this).

Click Next and follow the wizard until the server restarts.

## ✅ Step 5: Verify Active Directory Installation
Once the server restarts, you can verify the AD installation:

Open Server Manager.

Click Tools and select Active Directory Users and Computers.


In the Active Directory Users and Computers window, you should see your domain (e.g., homelab.local) listed.

## ✨ Step 6: Create Your First User in AD
Let’s create a user to test your setup.

In Active Directory Users and Computers, right-click Users in the left pane and select New > User.
Fill in the details for your new user (e.g., username: john.doe).
Set a password for the user and configure account options (e.g., set to User must change password at next logon).
## 💬 Conclusion
## 🎉 Congratulations! You've successfully set up Active Directory Domain Services (AD DS) on a Windows Server 2019 VM in Proxmox. You now have a fully functional Domain Controller (DC) for managing users, groups, and other resources in your homelab network.

## 🔄 Next Steps:
Explore Group Policies to manage user settings and security policies.
Set up DNS for name resolution in your network.
Install Remote Desktop Services (RDS) for remote access.
Dive deeper into other Windows Server roles like DHCP and File Services.
## 💬 Need Help?
If you encounter any issues during setup or have questions, feel free to open an issue in the repository or reach out to the community. Happy homelabbing! 🚀
