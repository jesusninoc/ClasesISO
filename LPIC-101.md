LPIC-1 101
https://www.lpi.org/study-resources/lpic-1-101-exam-objectives/

---------------------------------------------------
System Architecture
---------------------------------------------------
-Determine and configure hardware settings
--Key Knowledge Areas:
---Enable and disable integrated peripherals
Get-WmiObject Win32_USBControllerDevice |%{[wmi]($_.Dependent)} | Sort-Object Manufacturer,Description,DeviceID | ft -GroupBy Manufacturer Description,Service,DeviceID
Get-WmiObject -query "select * from Win32_PnPEntity where caption like '%cam%'"
---Configure systems with or without external peripherals such as keyboards
Get-WmiObject -query "select * from Win32_PnPEntity"
---Differentiate between the various types of mass storage devices
Get-WmiObject -Class win32_logicalDisk
---Know the differences between coldplug and hotplug devices
Get-WmiObject -query "select * from Win32_PnPEntity"
---Determine hardware resources for devices
Get-WmiObject -query "select * from Win32_PnPEntity"
---Tools and utilities to list various hardware information (e.g. lsusb, lspci, etc.)
---Tools and utilities to manipulate USB devices
---Conceptual understanding of sysfs, udev, dbus
--The following is a partial list of the used files, terms and utilities:
---/sys/
#Serial Number, Vendor, information
Get-WmiObject -Class Win32_ComputerSystem
#Bios Information , including Version Number of BIOS
Get-WmiObject -Class win32_bios
#Battery Information
Get-WmiObject -Class win32_battery
#Serial Number, Capacity, Part Number of Installed Memory Stick
Get-WmiObject -Class win32_Physicalmemory
#Capacity, Serial Number of Drive and other info of the Hard-disk
Get-WmiObject -Class win32_DiskDrive
#Monitor Information including Resolutions
Get-WmiObject -Class win32_DesktopMonitor
#Information Related Cd Drive
Get-WmiObject -Class win32_cdromdrive
#Network Adaptor information contains, manufacturer, MAC ID etc
Get-WmiObject -Class win32_networkadapter
#Mouse related information
Get-WmiObject -Class win32_pointingdevice
#OS Name, OSArchitecture, Version Info
Get-WmiObject -Class win32_operatingsystem
#DeviceID, Free Space, Size of Partition
Get-WmiObject -Class win32_logicalDisk
#Mapped Network Drives
Get-WmiObject -Class Win32_NetworkConnection
#List of Installed Printers
Get-WmiObject -Class win32_printer
#List of Printer Drivers
Get-WmiObject -Class win32_PrinterDriver
#IP Adress, DHCP , DNS and other information of Network Drivers
Get-WmiObject -Class Win32_NetworkAdapterConfiguration
#Command that runs automatically when a user logs onto the computer system
Get-WmiObject -Class win32_startupCommand
#All Running Processes
Get-WmiObject -Class win32_process
#List of All Services
Get-WmiObject -Class win32_Service
#List of Installed Software
Get-WmiObject -Class win32_Product
---/proc/
Get-Process
Get-WmiObject -Class win32_process
---/dev/
Get-WmiObject -Class win32_cdromdrive
---modprobe
---lsmod
---lspci
Get-WmiObject -Class Win32_NetworkConnection
---lsusb
Get-WmiObject Win32_USBControllerDevice |%{[wmi]($_.Dependent)} | Sort-Object Manufacturer,Description,DeviceID | ft -GroupBy Manufacturer Description,Service,DeviceID

-Boot the system
--Key Knowledge Areas:
---Provide common commands to the boot loader and options to the kernel at boot time
---Demonstrate knowledge of the boot sequence from BIOS to boot completion
---Understanding of SysVinit and systemd
---Awareness of Upstart
---Check boot events in the log files
--Terms and Utilities:
---dmesg
---BIOS
Get-WmiObject -Class win32_bios
---bootloader
(gwmi -name root\wmi -list bcdstore)
---kernel
Get-Service http | fl *
Get-Service * | Select-Object name, ServiceType
---initramfs
---init
Get-Process Idle | select *
---SysVinit
Get-Process -Id 4 | select *
---systemd

-Change runlevels / boot targets and shutdown or reboot system
--Key Knowledge Areas:
---Set the default runlevel or boot target
---Change between runlevels / boot targets including single user mode
---Shutdown and reboot from the command line
---Alert users before switching runlevels / boot targets or other major system events
---Properly terminate processes
--Terms and Utilities:
---/etc/inittab
---shutdown
Stop-Computer
---init
---/etc/init.d/
---telinit
---systemd
Get-Service
---systemctl
Get-Service
---/etc/systemd/
Get-Service
---/usr/lib/systemd/
Get-Service
---wall

---------------------------------------------------
Linux Installation and Package Management
---------------------------------------------------
-Design hard disk layout
--Key Knowledge Areas:
---Allocate filesystems and swap space to separate partitions or disks
Get-WmiObject -Class win32_logicalDisk
---Tailor the design to the intended use of the system
---Ensure the /boot partition conforms to the hardware architecture requirements for booting
---Knowledge of basic features of LVM
--Terms and Utilities:
---/ (root) filesystem
Get-WmiObject -Class win32_logicalDisk
---/var filesystem
---/home filesystem
---/boot filesystem
---swap space
Get-WMIObject -class win32_physicalmemory | Format-Table devicelocator, capacity -a
---mount points
---partitions
Get-WmiObject -Class win32_logicalDisk

-Install a boot manager
--Key Knowledge Areas:
---Providing alternative boot locations and backup boot options
---Install and configure a boot loader such as GRUB Legacy
---Perform basic configuration changes for GRUB 2
---Interact with the boot loader
--The following is a partial list of the used files, terms and utilities:
---menu.lst, grub.cfg and grub.conf
---grub-install
---grub-mkconfig
---MBR

-Manage shared libraries
--Key Knowledge Areas:
---Identify shared libraries
Get-Process -Module
---Identify the typical locations of system libraries
---Load shared libraries
--Terms and Utilities:
---ldd
---ldconfig
---/etc/ld.so.conf
---LD_LIBRARY_PATH

-Use Debian package management
--Key Knowledge Areas:
---Install, upgrade and uninstall Debian binary packages
Install-Package
Uninstall-Package
---Find packages containing specific files or libraries which may or may not be installed
Find-Package
---Obtain package information like version, content, dependencies, package integrity and installation status (whether or not the package is installed)
Get-Package
--Terms and Utilities:
---/etc/apt/sources.list
---dpkg
Install-Package
---dpkg-reconfigure
---apt-get
Get-Package
---apt-cache
---aptitude
Install-Package

-Use RPM and YUM package management
--Key Knowledge Areas:
---Install, re-install, upgrade and remove packages using RPM and YUM
---Obtain information on RPM packages such as version, status, dependencies, integrity and signatures
---Determine what files a package provides, as well as find which package a specific file comes from
--Terms and Utilities:
---rpm
Install-Package
---rpm2cpio
---/etc/yum.conf
---/etc/yum.repos.d/
---yum
Install-Package
---yumdownloader

---------------------------------------------------
GNU and Unix Commands
---------------------------------------------------
-Work on the command line
--Key Knowledge Areas:
---Use single shell commands and one line command sequences to perform basic tasks on the command line
powershell
powershell Start-Process cmd -Verb runAs
---Use and modify the shell environment including defining, referencing and exporting environment variables
Get-ChildItem Env:
---Use and edit command history
Get-History
---Invoke commands inside and outside the defined path
--Terms and Utilities:
---bash
powershell
powershell Start-Process cmd -Verb runAs
---echo
Write-Host
---env
Get-ChildItem Env:
---export
Get-History | Out-File
---pwd
Get-Location
---set
Set-Location
---unset
---man
Get-Help
---uname
Get-CimInstance Win32_OperatingSystem | Select-Object  Caption, InstallDate, ServicePackMajorVersion, OSArchitecture, BootDevice,  BuildNumber, CSName | FL
Get-CimInstance Win32_OperatingSystem | FL *
---history
Get-History
---.bash_history
Get-History

-Process text streams using filters
--Key Knowledge Areas:
---Send text files and output streams through text utility filters to modify the output using standard UNIX commands found in the GNU textutils package
--Terms and Utilities:
---cat
Get-Content fichero.txt
---cut
("hola;adios").Split(";")[0]
---expand
"     hola" -replace ("     ","")
("     hola").Trim()
---fmt
---head
New-Item
---join
foreach ($partes1 in Get-Content fichero1.txt){foreach ($partes2 in Get-Content fichero2.txt){$partes1,$partes2 | Out-File ficherocompuesto.txt}}
---less
Out-Host -Paging
---nl
---od
[Convert]::ToString(19,16)
[Convert]::ToString(19,8)
---paste
---pr
"hola" | Out-Printer
---sed
"hola" -replace "o","O"
---sort
Get-ChildItem | Sort-Object
Get-ChildItem | Sort-Object -Descending
---split
("hola;adios").Split(";")
---tail
Get-Content -Tail
Get-Content -ReadCount 10
---tr
"hola" -replace "o","O"
---unexpand
---uniq
Get-Process | Select-Object Name -Unique
---wc
Get-Process | Group-Object | Select-Object count

-Perform basic file management
--Key Knowledge Areas:
---Copy, move and remove files and directories individually
http://www.jesusninoc.com/2011/11/08/cmdlets-para-realizar-operaciones-con-archivos-y-directorios/
Copy-Item
Move-Item
Remove-Item
---Copy multiple files and directories recursively
Copy-Item -Recurse
---Remove files and directories recursively
Remove-Item -Recurse
---Use simple and advanced wildcard specifications in commands
Copy-Item *
---Using find to locate and act on files based on type, size, or time
Get-ChildItem -File
Get-ChildItem | Where-Object Length -GT 1
Get-ChildItem | Where-Object LastWriteTime -GT (get-date).AddDays(-1)
---Usage of tar, cpio and dd
--Terms and Utilities:
---cp
Copy-Item
---find
Get-ChildItem -File
---mkdir
New-Item -ItemType Directory
---mv
Move-Item
---ls
Get-ChildItem
---rm
Remove-Item
---rmdir
Remove-Item
---touch
New-Item -ItemType File -Value "hi"
---tar
Compress-Archive
---cpio
Compress-Archive
---dd
Copy-Item
---file
Get-ChildItem .\@TileEmpty1x1Image.png | select Extension
---gzip
Compress-Archive
---gunzip
Compress-Archive
---bzip2
Compress-Archive
---xz
Compress-Archive
---file globbing

-Use streams, pipes and redirects
--Key Knowledge Areas:
---Redirecting standard input, standard output and standard error
Get-Process | Sort-Object
---Pipe the output of one command to the input of another command
Get-Process | Sort-Object
---Use the output of one command as arguments to another command
Get-Process | Sort-Object
---Send output to both stdout and a file
Get-Process | Tee-Object | Out-File
--Terms and Utilities:
---tee
Get-Process notepad | Tee-Object -variable proc | Select-Object processname,handles
---xargs
Invoke-Command -ScriptBlock {Get-Process}

-Create, monitor and kill processes
--Key Knowledge Areas:
---Run jobs in the foreground and background
Debug-Job
Get-Job
Receive-Job
Remove-Job
Resume-Job
Start-Job
Stop-Job
Suspend-Job
Wait-Job
---Signal a program to continue running after logout
---Monitor active processes
Get-Process
---Select and sort processes for display
Get-Process
---Send signals to processes
Stop-Process
--Terms and Utilities:
---&
---bg
---fg
---jobs
Debug-Job
Get-Job
Receive-Job
Remove-Job
Resume-Job
Start-Job
Stop-Job
Suspend-Job
Wait-Job
---kill
Stop-Process
---nohup
Start-Job
Resume-Job
---ps
Get-Process
---top
Get-Process
---free
(Get-WmiObject -Class Win32_ComputerSystem).TotalPhysicalMemory/1gb
---uptime
Get-CimInstance -ClassName win32_operatingsystem | select *
Get-CimInstance -ClassName win32_operatingsystem | select csname, lastbootuptime
---pgrep
(Get-Process -Name powershell_ise).Id
---pkill
Stop-Process -Name notepad
---killall
Stop-Process -Name notepad
---screen

-Modify process execution priorities
--Key Knowledge Areas:
---Know the default priority of a job that is created
Get-WmiObject Win32_process -filter 'name = "notepad.exe"' | foreach-object {$_.SetPriority(32)}
---Run a program with higher or lower priority than the default
---Change the priority of a running process
--Terms and Utilities:
---nice
Get-WmiObject Win32_process -filter 'name = "notepad.exe"' | foreach-object {$_.SetPriority(32)}
---ps
Get-Process
---renice
---top
Get-Process

-Search text files using regular expressions
--Key Knowledge Areas:
---Create simple regular expressions containing several notational elements
Get-Process | Select-String "Notepad"
---Use regular expression tools to perform searches through a filesystem or file content
--Terms and Utilities:
---grep
Get-Process | Select-String "Notepad"
---egrep
---fgrep
---sed
---regex(7)
Get-Process | select-string -pattern idle, svchost -notmatch

-Perform basic file editing operations using vi
--Key Knowledge Areas:
---Navigate a document using vi
New-Item -Name nombre -Value "Hi"
---Use basic vi modes
---Insert, edit, delete, copy and find text
--Terms and Utilities:
---vi
New-Item -Name nombre -Value "Hi"
---/, ?
---h,j,k,l
---i, o, a
---c, d, p, y, dd, yy
---ZZ, :w!, :q!, :e!

---------------------------------------------------
Devices, Linux Filesystems, Filesystem Hierarchy Standard
---------------------------------------------------
-Create partitions and filesystems
Get-WmiObject Win32_LogicalDisk
--Key Knowledge Areas:
---Manage MBR partition tables
---Use various mkfs commands to create various filesystems such as:
----ext2/ext3/ext4
----XFS
----VFAT
---Awareness of ReiserFS and Btrfs
---Basic knowledge of gdisk and parted with GPT
--Terms and Utilities:
---fdisk
---gdisk
---parted
---mkfs
---mkswap

-Maintain the integrity of filesystems
Get-WmiObject Win32_LogicalDisk
--Key Knowledge Areas:
---Verify the integrity of filesystems
Get-FileHash
---Monitor free space and inodes
---Repair simple filesystem problems
--Terms and Utilities:
Get-WmiObject win32_logicaldisk
Get-PSDrive C | Select-Object Used,Free
---du
---df
---fsck
---e2fsck
---mke2fs
---debugfs
---dumpe2fs
---tune2fs
---XFS tools (such as xfs_metadump and xfs_info)

-Control mounting and unmounting of filesystems
--Key Knowledge Areas:
---Manually mount and unmount filesystems
New-PSDrive
---Configure filesystem mounting on bootup
---Configure user mountable removable filesystems
--Terms and Utilities:
New-PSDrive
---/etc/fstab
---/media/
---mount
---umount

-Manage disk quotas
--Key Knowledge Areas:
---Set up a disk quota for a filesystem
---Edit, check and generate user quota reports
--Terms and Utilities:
---quota
---edquota
---repquota
---quotaon

-Manage file permissions and ownership
--Key Knowledge Areas:
---Manage access permissions on regular and special files as well as directories
http://www.jesusninoc.com/2015/08/19/anadir-permiso-ntfs-a-una-carpeta/
Get-Acl
Set-Acl
---Use access modes such as suid, sgid and the sticky bit to maintain security
---Know how to change the file creation mask
---Use the group field to grant file access to group members
--Terms and Utilities:
---chmod
Get-Acl
Set-Acl
---umask
---chown
---chgrp

-Create and change hard and symbolic links
--Key Knowledge Areas:
---Create links
New-Item -ItemType SymbolicLink
---Identify hard and/or soft links
---Copying versus linking files
---Use links to support system administration tasks
--Terms and Utilities:
New-Item -ItemType SymbolicLink
---ln
---ls

-Find system files and place files in the correct location
--Key Knowledge Areas:
---Understand the correct locations of files under the FHS
---Find files and commands on a Linux system
---Know the location and purpose of important file and directories as defined in the FHS
--Terms and Utilities:
---find
Get-ChildItem
Select-String
---locate
Get-ChildItem
Select-String
---updatedb
---whereis
Get-ChildItem
Select-String
---which
Get-ChildItem
---type
Get-ChildItem | Get-Member
---/etc/updatedb.conf
