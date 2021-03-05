```PowerShell  
LPIC-1 101
```  
```PowerShell  
https://www.lpi.org/study-resources/lpic-1-101-exam-objectives/
```  
  
---------------------------------------------------  
```PowerShell  
System Architecture
```  
---------------------------------------------------  
->Determine and configure hardware settings  
->->Key Knowledge Areas:  
->->->Enable and disable integrated peripherals  
```PowerShell  
Get-WmiObject Win32_USBControllerDevice |%{[wmi]($_.Dependent)} | Sort-Object Manufacturer,Description,DeviceID | ft -GroupBy Manufacturer Description,Service,DeviceID
```  
```PowerShell  
Get-WmiObject -query "select * from Win32_PnPEntity where caption like '%cam%'"
```  
->->->Configure systems with or without external peripherals such as keyboards  
```PowerShell  
Get-WmiObject -query "select * from Win32_PnPEntity"
```  
->->->Differentiate between the various types of mass storage devices  
```PowerShell  
Get-WmiObject -Class win32_logicalDisk
```  
->->->Know the differences between coldplug and hotplug devices  
```PowerShell  
Get-WmiObject -query "select * from Win32_PnPEntity"
```  
->->->Determine hardware resources for devices  
```PowerShell  
Get-WmiObject -query "select * from Win32_PnPEntity"
```  
->->->Tools and utilities to list various hardware information (e.g. lsusb, lspci, etc.)  
->->->Tools and utilities to manipulate USB devices  
->->->Conceptual understanding of sysfs, udev, dbus  
->->The following is a partial list of the used files, terms and utilities:  
->->->/sys/  
```PowerShell  
#Serial Number, Vendor, information
```  
```PowerShell  
Get-WmiObject -Class Win32_ComputerSystem
```  
```PowerShell  
#Bios Information , including Version Number of BIOS
```  
```PowerShell  
Get-WmiObject -Class win32_bios
```  
```PowerShell  
#Battery Information
```  
```PowerShell  
Get-WmiObject -Class win32_battery
```  
```PowerShell  
#Serial Number, Capacity, Part Number of Installed Memory Stick
```  
```PowerShell  
Get-WmiObject -Class win32_Physicalmemory
```  
```PowerShell  
#Capacity, Serial Number of Drive and other info of the Hard-disk
```  
```PowerShell  
Get-WmiObject -Class win32_DiskDrive
```  
```PowerShell  
#Monitor Information including Resolutions
```  
```PowerShell  
Get-WmiObject -Class win32_DesktopMonitor
```  
```PowerShell  
#Information Related Cd Drive
```  
```PowerShell  
Get-WmiObject -Class win32_cdromdrive
```  
```PowerShell  
#Network Adaptor information contains, manufacturer, MAC ID etc
```  
```PowerShell  
Get-WmiObject -Class win32_networkadapter
```  
```PowerShell  
#Mouse related information
```  
```PowerShell  
Get-WmiObject -Class win32_pointingdevice
```  
```PowerShell  
#OS Name, OSArchitecture, Version Info
```  
```PowerShell  
Get-WmiObject -Class win32_operatingsystem
```  
```PowerShell  
#DeviceID, Free Space, Size of Partition
```  
```PowerShell  
Get-WmiObject -Class win32_logicalDisk
```  
```PowerShell  
#Mapped Network Drives
```  
```PowerShell  
Get-WmiObject -Class Win32_NetworkConnection
```  
```PowerShell  
#List of Installed Printers
```  
```PowerShell  
Get-WmiObject -Class win32_printer
```  
```PowerShell  
#List of Printer Drivers
```  
```PowerShell  
Get-WmiObject -Class win32_PrinterDriver
```  
```PowerShell  
#IP Adress, DHCP , DNS and other information of Network Drivers
```  
```PowerShell  
Get-WmiObject -Class Win32_NetworkAdapterConfiguration
```  
```PowerShell  
#Command that runs automatically when a user logs onto the computer system
```  
```PowerShell  
Get-WmiObject -Class win32_startupCommand
```  
```PowerShell  
#All Running Processes
```  
```PowerShell  
Get-WmiObject -Class win32_process
```  
```PowerShell  
#List of All Services
```  
```PowerShell  
Get-WmiObject -Class win32_Service
```  
```PowerShell  
#List of Installed Software
```  
```PowerShell  
Get-WmiObject -Class win32_Product
```  
->->->/proc/  
```PowerShell  
Get-Process
```  
```PowerShell  
Get-WmiObject -Class win32_process
```  
->->->/dev/  
```PowerShell  
Get-WmiObject -Class win32_cdromdrive
```  
->->->modprobe  
->->->lsmod  
->->->lspci  
```PowerShell  
Get-WmiObject -Class Win32_NetworkConnection
```  
->->->lsusb  
```PowerShell  
Get-WmiObject Win32_USBControllerDevice |%{[wmi]($_.Dependent)} | Sort-Object Manufacturer,Description,DeviceID | ft -GroupBy Manufacturer Description,Service,DeviceID
```  
  
->Boot the system  
->->Key Knowledge Areas:  
->->->Provide common commands to the boot loader and options to the kernel at boot time  
->->->Demonstrate knowledge of the boot sequence from BIOS to boot completion  
->->->Understanding of SysVinit and systemd  
->->->Awareness of Upstart  
->->->Check boot events in the log files  
->->Terms and Utilities:  
->->->dmesg  
->->->BIOS  
```PowerShell  
Get-WmiObject -Class win32_bios
```  
->->->bootloader  
```PowerShell  
(gwmi -name root\wmi -list bcdstore)
```  
->->->kernel  
```PowerShell  
Get-Service http | fl *
```  
```PowerShell  
Get-Service * | Select-Object name, ServiceType
```  
->->->initramfs  
->->->init  
```PowerShell  
Get-Process Idle | select *
```  
->->->SysVinit  
```PowerShell  
Get-Process -Id 4 | select *
```  
->->->systemd  
  
->Change runlevels / boot targets and shutdown or reboot system  
->->Key Knowledge Areas:  
->->->Set the default runlevel or boot target  
->->->Change between runlevels / boot targets including single user mode  
->->->Shutdown and reboot from the command line  
->->->Alert users before switching runlevels / boot targets or other major system events  
->->->Properly terminate processes  
->->Terms and Utilities:  
->->->/etc/inittab  
->->->shutdown  
```PowerShell  
Stop-Computer
```  
->->->init  
->->->/etc/init.d/  
->->->telinit  
->->->systemd  
```PowerShell  
Get-Service
```  
->->->systemctl  
```PowerShell  
Get-Service
```  
->->->/etc/systemd/  
```PowerShell  
Get-Service
```  
->->->/usr/lib/systemd/  
```PowerShell  
Get-Service
```  
->->->wall  
  
---------------------------------------------------  
```PowerShell  
Linux Installation and Package Management
```  
---------------------------------------------------  
->Design hard disk layout  
->->Key Knowledge Areas:  
->->->Allocate filesystems and swap space to separate partitions or disks  
```PowerShell  
Get-WmiObject -Class win32_logicalDisk
```  
->->->Tailor the design to the intended use of the system  
->->->Ensure the /boot partition conforms to the hardware architecture requirements for booting  
->->->Knowledge of basic features of LVM  
->->Terms and Utilities:  
->->->/ (root) filesystem  
```PowerShell  
Get-WmiObject -Class win32_logicalDisk
```  
->->->/var filesystem  
->->->/home filesystem  
->->->/boot filesystem  
->->->swap space  
```PowerShell  
Get-WMIObject -class win32_physicalmemory | Format-Table devicelocator, capacity -a
```  
->->->mount points  
->->->partitions  
```PowerShell  
Get-WmiObject -Class win32_logicalDisk
```  
  
->Install a boot manager  
->->Key Knowledge Areas:  
->->->Providing alternative boot locations and backup boot options  
->->->Install and configure a boot loader such as GRUB Legacy  
->->->Perform basic configuration changes for GRUB 2  
->->->Interact with the boot loader  
->->The following is a partial list of the used files, terms and utilities:  
->->->menu.lst, grub.cfg and grub.conf  
->->->grub-install  
->->->grub-mkconfig  
->->->MBR  
  
->Manage shared libraries  
->->Key Knowledge Areas:  
->->->Identify shared libraries  
```PowerShell  
Get-Process -Module
```  
->->->Identify the typical locations of system libraries  
->->->Load shared libraries  
->->Terms and Utilities:  
->->->ldd  
->->->ldconfig  
->->->/etc/ld.so.conf  
->->->LD_LIBRARY_PATH  
  
->Use Debian package management  
->->Key Knowledge Areas:  
->->->Install, upgrade and uninstall Debian binary packages  
```PowerShell  
Install-Package
```  
```PowerShell  
Uninstall-Package
```  
->->->Find packages containing specific files or libraries which may or may not be installed  
```PowerShell  
Find-Package
```  
->->->Obtain package information like version, content, dependencies, package integrity and installation status (whether or not the package is installed)  
```PowerShell  
Get-Package
```  
->->Terms and Utilities:  
->->->/etc/apt/sources.list  
->->->dpkg  
```PowerShell  
Install-Package
```  
->->->dpkg-reconfigure  
->->->apt-get  
```PowerShell  
Get-Package
```  
->->->apt-cache  
->->->aptitude  
```PowerShell  
Install-Package
```  
  
->Use RPM and YUM package management  
->->Key Knowledge Areas:  
->->->Install, re-install, upgrade and remove packages using RPM and YUM  
->->->Obtain information on RPM packages such as version, status, dependencies, integrity and signatures  
->->->Determine what files a package provides, as well as find which package a specific file comes from  
->->Terms and Utilities:  
->->->rpm  
```PowerShell  
Install-Package
```  
->->->rpm2cpio  
->->->/etc/yum.conf  
->->->/etc/yum.repos.d/  
->->->yum  
```PowerShell  
Install-Package
```  
->->->yumdownloader  
  
---------------------------------------------------  
```PowerShell  
GNU and Unix Commands
```  
---------------------------------------------------  
->Work on the command line  
->->Key Knowledge Areas:  
->->->Use single shell commands and one line command sequences to perform basic tasks on the command line  
```PowerShell  
powershell
```  
```PowerShell  
powershell Start-Process cmd -Verb runAs
```  
->->->Use and modify the shell environment including defining, referencing and exporting environment variables  
```PowerShell  
Get-ChildItem Env:
```  
->->->Use and edit command history  
```PowerShell  
Get-History
```  
->->->Invoke commands inside and outside the defined path  
->->Terms and Utilities:  
->->->bash  
```PowerShell  
powershell
```  
```PowerShell  
powershell Start-Process cmd -Verb runAs
```  
->->->echo  
```PowerShell  
Write-Host
```  
->->->env  
```PowerShell  
Get-ChildItem Env:
```  
->->->export  
```PowerShell  
Get-History | Out-File
```  
->->->pwd  
```PowerShell  
Get-Location
```  
->->->set  
```PowerShell  
Set-Location
```  
->->->unset  
->->->man  
```PowerShell  
Get-Help
```  
->->->uname  
```PowerShell  
Get-CimInstance Win32_OperatingSystem | Select-Object  Caption, InstallDate, ServicePackMajorVersion, OSArchitecture, BootDevice,  BuildNumber, CSName | FL
```  
```PowerShell  
Get-CimInstance Win32_OperatingSystem | FL *
```  
->->->history  
```PowerShell  
Get-History
```  
->->->.bash_history  
```PowerShell  
Get-History
```  
  
->Process text streams using filters  
->->Key Knowledge Areas:  
->->->Send text files and output streams through text utility filters to modify the output using standard UNIX commands found in the GNU textutils package  
->->Terms and Utilities:  
->->->cat  
```PowerShell  
Get-Content fichero.txt
```  
->->->cut  
```PowerShell  
("hola;adios").Split(";")[0]
```  
->->->expand  
```PowerShell  
"     hola" -replace ("     ","")
```  
```PowerShell  
("     hola").Trim()
```  
->->->fmt  
->->->head  
```PowerShell  
New-Item
```  
->->->join  
```PowerShell  
foreach ($partes1 in Get-Content fichero1.txt){foreach ($partes2 in Get-Content fichero2.txt){$partes1,$partes2 | Out-File ficherocompuesto.txt}}
```  
->->->less  
```PowerShell  
Out-Host -Paging
```  
->->->nl  
->->->od  
```PowerShell  
[Convert]::ToString(19,16)
```  
```PowerShell  
[Convert]::ToString(19,8)
```  
->->->paste  
->->->pr  
```PowerShell  
"hola" | Out-Printer
```  
->->->sed  
```PowerShell  
"hola" -replace "o","O"
```  
->->->sort  
```PowerShell  
Get-ChildItem | Sort-Object
```  
```PowerShell  
Get-ChildItem | Sort-Object -Descending
```  
->->->split  
```PowerShell  
("hola;adios").Split(";")
```  
->->->tail  
```PowerShell  
Get-Content -Tail
```  
```PowerShell  
Get-Content -ReadCount 10
```  
->->->tr  
```PowerShell  
"hola" -replace "o","O"
```  
->->->unexpand  
->->->uniq  
```PowerShell  
Get-Process | Select-Object Name -Unique
```  
->->->wc  
```PowerShell  
Get-Process | Group-Object | Select-Object count
```  
  
->Perform basic file management  
->->Key Knowledge Areas:  
->->->Copy, move and remove files and directories individually  
```PowerShell  
http://www.jesusninoc.com/2011/11/08/cmdlets-para-realizar-operaciones-con-archivos-y-directorios/
```  
```PowerShell  
Copy-Item
```  
```PowerShell  
Move-Item
```  
```PowerShell  
Remove-Item
```  
->->->Copy multiple files and directories recursively  
```PowerShell  
Copy-Item -Recurse
```  
->->->Remove files and directories recursively  
```PowerShell  
Remove-Item -Recurse
```  
->->->Use simple and advanced wildcard specifications in commands  
```PowerShell  
Copy-Item *
```  
->->->Using find to locate and act on files based on type, size, or time  
```PowerShell  
Get-ChildItem -File
```  
```PowerShell  
Get-ChildItem | Where-Object Length -GT 1
```  
```PowerShell  
Get-ChildItem | Where-Object LastWriteTime -GT (get-date).AddDays(-1)
```  
->->->Usage of tar, cpio and dd  
->->Terms and Utilities:  
->->->cp  
```PowerShell  
Copy-Item
```  
->->->find  
```PowerShell  
Get-ChildItem -File
```  
->->->mkdir  
```PowerShell  
New-Item -ItemType Directory
```  
->->->mv  
```PowerShell  
Move-Item
```  
->->->ls  
```PowerShell  
Get-ChildItem
```  
->->->rm  
```PowerShell  
Remove-Item
```  
->->->rmdir  
```PowerShell  
Remove-Item
```  
->->->touch  
```PowerShell  
New-Item -ItemType File -Value "hi"
```  
->->->tar  
```PowerShell  
Compress-Archive
```  
->->->cpio  
```PowerShell  
Compress-Archive
```  
->->->dd  
```PowerShell  
Copy-Item
```  
->->->file  
```PowerShell  
Get-ChildItem .\@TileEmpty1x1Image.png | select Extension
```  
->->->gzip  
```PowerShell  
Compress-Archive
```  
->->->gunzip  
```PowerShell  
Compress-Archive
```  
->->->bzip2  
```PowerShell  
Compress-Archive
```  
->->->xz  
```PowerShell  
Compress-Archive
```  
->->->file globbing  
  
->Use streams, pipes and redirects  
->->Key Knowledge Areas:  
->->->Redirecting standard input, standard output and standard error  
```PowerShell  
Get-Process | Sort-Object
```  
->->->Pipe the output of one command to the input of another command  
```PowerShell  
Get-Process | Sort-Object
```  
->->->Use the output of one command as arguments to another command  
```PowerShell  
Get-Process | Sort-Object
```  
->->->Send output to both stdout and a file  
```PowerShell  
Get-Process | Tee-Object | Out-File
```  
->->Terms and Utilities:  
->->->tee  
```PowerShell  
Get-Process notepad | Tee-Object -variable proc | Select-Object processname,handles
```  
->->->xargs  
```PowerShell  
Invoke-Command -ScriptBlock {Get-Process}
```  
  
->Create, monitor and kill processes  
->->Key Knowledge Areas:  
->->->Run jobs in the foreground and background  
```PowerShell  
Debug-Job
```  
```PowerShell  
Get-Job
```  
```PowerShell  
Receive-Job
```  
```PowerShell  
Remove-Job
```  
```PowerShell  
Resume-Job
```  
```PowerShell  
Start-Job
```  
```PowerShell  
Stop-Job
```  
```PowerShell  
Suspend-Job
```  
```PowerShell  
Wait-Job
```  
->->->Signal a program to continue running after logout  
->->->Monitor active processes  
```PowerShell  
Get-Process
```  
->->->Select and sort processes for display  
```PowerShell  
Get-Process
```  
->->->Send signals to processes  
```PowerShell  
Stop-Process
```  
->->Terms and Utilities:  
->->->&  
->->->bg  
->->->fg  
->->->jobs  
```PowerShell  
Debug-Job
```  
```PowerShell  
Get-Job
```  
```PowerShell  
Receive-Job
```  
```PowerShell  
Remove-Job
```  
```PowerShell  
Resume-Job
```  
```PowerShell  
Start-Job
```  
```PowerShell  
Stop-Job
```  
```PowerShell  
Suspend-Job
```  
```PowerShell  
Wait-Job
```  
->->->kill  
```PowerShell  
Stop-Process
```  
->->->nohup  
```PowerShell  
Start-Job
```  
```PowerShell  
Resume-Job
```  
->->->ps  
```PowerShell  
Get-Process
```  
->->->top  
```PowerShell  
Get-Process
```  
->->->free  
```PowerShell  
(Get-WmiObject -Class Win32_ComputerSystem).TotalPhysicalMemory/1gb
```  
->->->uptime  
```PowerShell  
Get-CimInstance -ClassName win32_operatingsystem | select *
```  
```PowerShell  
Get-CimInstance -ClassName win32_operatingsystem | select csname, lastbootuptime
```  
->->->pgrep  
```PowerShell  
(Get-Process -Name powershell_ise).Id
```  
->->->pkill  
```PowerShell  
Stop-Process -Name notepad
```  
->->->killall  
```PowerShell  
Stop-Process -Name notepad
```  
->->->screen  
  
->Modify process execution priorities  
->->Key Knowledge Areas:  
->->->Know the default priority of a job that is created  
```PowerShell  
Get-WmiObject Win32_process -filter 'name = "notepad.exe"' | foreach-object {$_.SetPriority(32)}
```  
->->->Run a program with higher or lower priority than the default  
->->->Change the priority of a running process  
->->Terms and Utilities:  
->->->nice  
```PowerShell  
Get-WmiObject Win32_process -filter 'name = "notepad.exe"' | foreach-object {$_.SetPriority(32)}
```  
->->->ps  
```PowerShell  
Get-Process
```  
->->->renice  
->->->top  
```PowerShell  
Get-Process
```  
  
->Search text files using regular expressions  
->->Key Knowledge Areas:  
->->->Create simple regular expressions containing several notational elements  
```PowerShell  
Get-Process | Select-String "Notepad"
```  
->->->Use regular expression tools to perform searches through a filesystem or file content  
->->Terms and Utilities:  
->->->grep  
```PowerShell  
Get-Process | Select-String "Notepad"
```  
->->->egrep  
->->->fgrep  
->->->sed  
->->->regex(7)  
```PowerShell  
Get-Process | select-string -pattern idle, svchost -notmatch
```  
  
->Perform basic file editing operations using vi  
->->Key Knowledge Areas:  
->->->Navigate a document using vi  
```PowerShell  
New-Item -Name nombre -Value "Hi"
```  
->->->Use basic vi modes  
->->->Insert, edit, delete, copy and find text  
->->Terms and Utilities:  
->->->vi  
```PowerShell  
New-Item -Name nombre -Value "Hi"
```  
->->->/, ?  
->->->h,j,k,l  
->->->i, o, a  
->->->c, d, p, y, dd, yy  
->->->ZZ, :w!, :q!, :e!  
  
---------------------------------------------------  
```PowerShell  
Devices, Linux Filesystems, Filesystem Hierarchy Standard
```  
---------------------------------------------------  
->Create partitions and filesystems  
```PowerShell  
Get-WmiObject Win32_LogicalDisk
```  
->->Key Knowledge Areas:  
->->->Manage MBR partition tables  
->->->Use various mkfs commands to create various filesystems such as:  
->->->-ext2/ext3/ext4  
->->->-XFS  
->->->-VFAT  
->->->Awareness of ReiserFS and Btrfs  
->->->Basic knowledge of gdisk and parted with GPT  
->->Terms and Utilities:  
->->->fdisk  
->->->gdisk  
->->->parted  
->->->mkfs  
->->->mkswap  
  
->Maintain the integrity of filesystems  
```PowerShell  
Get-WmiObject Win32_LogicalDisk
```  
->->Key Knowledge Areas:  
->->->Verify the integrity of filesystems  
```PowerShell  
Get-FileHash
```  
->->->Monitor free space and inodes  
->->->Repair simple filesystem problems  
->->Terms and Utilities:  
```PowerShell  
Get-WmiObject win32_logicaldisk
```  
```PowerShell  
Get-PSDrive C | Select-Object Used,Free
```  
->->->du  
->->->df  
->->->fsck  
->->->e2fsck  
->->->mke2fs  
->->->debugfs  
->->->dumpe2fs  
->->->tune2fs  
->->->XFS tools (such as xfs_metadump and xfs_info)  
  
->Control mounting and unmounting of filesystems  
->->Key Knowledge Areas:  
->->->Manually mount and unmount filesystems  
```PowerShell  
New-PSDrive
```  
->->->Configure filesystem mounting on bootup  
->->->Configure user mountable removable filesystems  
->->Terms and Utilities:  
```PowerShell  
New-PSDrive
```  
->->->/etc/fstab  
->->->/media/  
->->->mount  
->->->umount  
  
->Manage disk quotas  
->->Key Knowledge Areas:  
->->->Set up a disk quota for a filesystem  
->->->Edit, check and generate user quota reports  
->->Terms and Utilities:  
->->->quota  
->->->edquota  
->->->repquota  
->->->quotaon  
  
->Manage file permissions and ownership  
->->Key Knowledge Areas:  
->->->Manage access permissions on regular and special files as well as directories  
```PowerShell  
http://www.jesusninoc.com/2015/08/19/anadir-permiso-ntfs-a-una-carpeta/
```  
```PowerShell  
Get-Acl
```  
```PowerShell  
Set-Acl
```  
->->->Use access modes such as suid, sgid and the sticky bit to maintain security  
->->->Know how to change the file creation mask  
->->->Use the group field to grant file access to group members  
->->Terms and Utilities:  
->->->chmod  
```PowerShell  
Get-Acl
```  
```PowerShell  
Set-Acl
```  
->->->umask  
->->->chown  
->->->chgrp  
  
->Create and change hard and symbolic links  
->->Key Knowledge Areas:  
->->->Create links  
```PowerShell  
New-Item -ItemType SymbolicLink
```  
->->->Identify hard and/or soft links  
->->->Copying versus linking files  
->->->Use links to support system administration tasks  
->->Terms and Utilities:  
```PowerShell  
New-Item -ItemType SymbolicLink
```  
->->->ln  
->->->ls  
  
->Find system files and place files in the correct location  
->->Key Knowledge Areas:  
->->->Understand the correct locations of files under the FHS  
->->->Find files and commands on a Linux system  
->->->Know the location and purpose of important file and directories as defined in the FHS  
->->Terms and Utilities:  
->->->find  
```PowerShell  
Get-ChildItem
```  
```PowerShell  
Select-String
```  
->->->locate  
```PowerShell  
Get-ChildItem
```  
```PowerShell  
Select-String
```  
->->->updatedb  
->->->whereis  
```PowerShell  
Get-ChildItem
```  
```PowerShell  
Select-String
```  
->->->which  
```PowerShell  
Get-ChildItem
```  
->->->type  
```PowerShell  
Get-ChildItem | Get-Member
```  
->->->/etc/updatedb.conf  
