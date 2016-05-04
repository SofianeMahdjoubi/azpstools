# Overview
Occasionally Azure IaaS VMs may not start because there is something wrong with the operating system (OS) disk preventing it from booting up correctly.
In such cases it is a common practice to recover the problem VM by performing the following steps:

- Delete the VM (but keep the disks)
- Attach the disk(s) to another bootable VM as a Data Disk
- Run the script https://github.com/sebdau/azpstools/blob/master/FixDisk/TS_RecoveryWorker2.ps1 as an elevated administrator from the recovery VM
- Detach the disk and recreate the original VM using the recovered operating system disk

> the full details on this recovery process are explained in this blog post:
> https://blogs.msdn.microsoft.com/mast/2014/11/20/recover-azure-vm-by-attaching-os-disk-to-another-azure-vm/

# Current version supports
- Azure Service Management (ASM) Cloud Service hosted VM recovery
- Windows 2008 R2 - 2012 R2

# Scenarios

##  When would you use the script?
If a Windows VM in Azure does not boot. Typically in this scenario VM screenshot from [boot diagnostics] (https://azure.microsoft.com/en-us/blog/boot-diagnostics-for-virtual-machines-v2/) does not show login screen but a boot issue.

# Execution guidance
- download and extract the entire project folder https://github.com/sebdau/azpstools/archive/master.zip to c:\azscripts\ (or custom)
- Or pull it using git client github-windows://openRepo/https://github.com/sebdau/azpstools
- Open Azure Powershell and and execute c:\azscripts\RecoverVM\RecoverVM.ps1 MYCLOUDSERVICENAME MYVMNAME
- follow the instructions and be patient (it may take between 15mins and multiple hours [if disk repair takes long])

## Parameters or input
- hosting service name (cloud service name)
- VM name

# Supported Platforms / Dependencies
 - current version of Azure PowerShell (Tested with 1.3.2)
 


