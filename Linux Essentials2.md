---------------------------------------------------  
# Introduction
---------------------------------------------------  
Windows PowerShell uses a "verb-noun" naming system
  
---------------------------------------------------  
# The Linux Community and a Career in Open Source
---------------------------------------------------  
->Linux Evolution and Popular Operating Systems  
->->Key Knowledge Areas:  
->->->Desktop Applications  
->->->Server Applications  
->->->Development Languages  
->->->Package Management Tools and repositories  
->->Terms and Utilities:  
->->->OpenOffice.org, LibreOffice, Thunderbird, Firefox, GIMP  
->->->Apache HTTPD, NGINX, MySQL, NFS, Samba  
->->->C, Java, Perl, shell, Python, Samba  
->->->dpkg, apt-get, rpm, yum  
->Understanding Open Source Software and Licensing  
->->Key Knowledge Areas:  
->->->Licensing  
->->->Free Software Foundation (FSF), Open Source Initiative (OSI)  
->->Terms and Utilities:  
->->->GPL, BSD, Creative Commons  
->->->Free Software, Open Source Software, FOSS, FLOSS  
->->->Open Source business models  
->ICT Skills and Working in Linux  
->->Key Knowledge Areas:  
->->->Desktop Skills  
->->->Getting to the Command Line  
->->->Industry uses of Linux, Cloud Computing and Virtualization  
->->Terms and Utilities:  
->->->Using a browser, privacy concerns, configuration options, searching the web and saving content  
->->->Terminal and Console  
->->->Password issues  
->->->Privacy issues and tools  
->->->Use of common open source applications in presentations and projects  
  
---------------------------------------------------  
# Finding Your Way on a Linux System
---------------------------------------------------  
->Command Line Basics  
->->Key Knowledge Areas:  
->->->Basic shell  
->->->Command line syntax  
```PowerShell  
Get-Verb
```  
```PowerShell  
Get-Command -Noun
```  
->->->Variables  
* http://www.jesusninoc.com/2014/12/31/curso-de-powershell/  
->->->Globbing  
```PowerShell  
*
```  
```PowerShell  
?
```  
->->->Quoting  
```PowerShell  
"
```  
```PowerShell  
'
```  
->->Terms and Utilities:  
->->->Bash  
->->->echo  
```PowerShell  
Write-Host
```  
->->->history  
```PowerShell  
Get-History
```  
->->->PATH env variable  
```PowerShell  
$Env:Path
```  
```PowerShell  
[Environment]::GetEnvironmentVariable("Path")
```  
->->->export  
->->->type  
```PowerShell  
Get-Content
```  
->Using the Command Line to Get Help  
->->Key Knowledge Areas:  
->->->Man  
```PowerShell  
Get-Help
```  
->->->Info  
->->Terms and Utilities:  
->->->man  
```PowerShell  
Get-Help
```  
->->->info  
```PowerShell  
Get-Help
```  
->->->Man pages  
```PowerShell  
Get-Help
```  
->->->/usr/share/doc/  
```PowerShell  
Get-Help
```  
->->->locate  
  
->Using Directories and Listing Files  
->->Key Knowledge Areas:  
->->->Files, directories  
```PowerShell  
Get-ChildItem -File
```  
```PowerShell  
Get-ChildItem -Directory
```  
->->->Hidden files and directories  
```PowerShell  
Get-ChildItem -Hidden
```  
->->->Home  
```PowerShell  
$home
```  
->->->Absolute and relative paths  
```PowerShell  
c:\
```  
```PowerShell  
..\
```  
->->Terms and Utilities:  
->->->Common options for ls  
```PowerShell  
Get-ChildItem
```  
->->->Recursive listings  
```PowerShell  
Get-ChildItem -Recurse
```  
->->->cd  
```PowerShell  
Set-Location
```  
->->->. and ..  
```PowerShell  
.
```  
```PowerShell  
..
```  
->->->home and ~  
```PowerShell  
Set-Location ~
```  
  
->Creating, Moving and Deleting Files  
->->Key Knowledge Areas:  
->->->Files and directories  
```PowerShell  
Get-ChildItem -File
```  
```PowerShell  
Get-ChildItem -Directory
```  
->->->Case sensitivity  
->->->Simple globbing and quoting  
```PowerShell  
"
```  
```PowerShell  
'
```  
->->Terms and Utilities:  
->->->mv, cp, rm, touch  
```PowerShell  
Move-Item
```  
```PowerShell  
Copy-Item
```  
```PowerShell  
Remove-Item
```  
```PowerShell  
New-Item
```  
->->->mkdir, rmdir  
```PowerShell  
New-Item
```  
```PowerShell  
Remove-Item
```  
  
---------------------------------------------------  
# The Power of the Command Line
---------------------------------------------------  
->Archiving Files on the Command Line  
->->Key Knowledge Areas:  
->->->Files, directories  
```PowerShell  
Get-ChildItem -File
```  
```PowerShell  
Get-ChildItem -Directory
```  
->->->Archives, compression  
```PowerShell  
Get-ChildItem -File
```  
->->Terms and Utilities:  
->->->tar  
```PowerShell  
Compress-Archive
```  
```PowerShell  
Expand-Archive
```  
->->->Common tar options  
->->->gzip, bzip2  
```PowerShell  
Compress-Archive
```  
```PowerShell  
Expand-Archive
```  
->->->zip, unzip  
```PowerShell  
Compress-Archive
```  
```PowerShell  
Expand-Archive
```  
  
->Searching and Extracting Data from Files  
->->Key Knowledge Areas:  
->->->Command line pipes  
```PowerShell  
Get-Command | Select-Object CommandType, name
```  
->->->I/O re-direction  
```PowerShell  
Get-Command > fichero.txt
```  
->->->Basic Regular Expressions ., [  ], *, ?  
```PowerShell  
Get-ChildItem .
```  
```PowerShell  
Get-ChildItem | Where-Object {$_.Name -match "\d\.[^\d]"}
```  
```PowerShell  
Get-ChildItem *.iso
```  
```PowerShell  
Get-ChildItem *.is?
```  
->->Terms and Utilities:  
->->->grep  
```PowerShell  
Get-ChildItem | select-object name | Select-String 2015
```  
->->->less  
```PowerShell  
more
```  
->->->cat, head, tail  
```PowerShell  
Get-Content
```  
```PowerShell  
Get-Content -ReadCount
```  
->->->sort  
```PowerShell  
Get-ChildItem | Sort-Object
```  
->->->cut  
```PowerShell  
Get-ChildItem | Select-Object Name
```  
->->->wc  
```PowerShell  
(Get-ChildItem | Select-Object Name).count
```  
  
->Turning Commands into a Script  
->->Key Knowledge Areas:  
->->->Basic shell scripting  
->->->Awareness of common text editors  
->->Terms and Utilities:  
->->->#! (shebang)  
->->->/bin/bash  
->->->Variables  
```PowerShell  
http://www.jesusninoc.com/2014/12/31/curso-de-powershell/
```  
->->->Arguments  
->->->for loops  
```PowerShell  
https://github.com/jesusninoc/PowerShell/tree/master/Bucles
```  
->->->echo  
```PowerShell  
Write-Host "Hi"
```  
->->->Exit status  
```PowerShell  
exit
```  
  
---------------------------------------------------  
# The Linux Operating System
---------------------------------------------------  
->Choosing an Operating System  
->->Key Knowledge Areas:  
->->->Windows, Mac, Linux differences  
->->->Distribution life cycle management  
->->Terms and Utilities:  
->->->GUI versus command line, desktop configuration  
->->->Maintenance cycles, Beta and Stable  
  
->Understanding Computer Hardware  
->->Key Knowledge Areas:  
->->->Hardware  
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
->->Terms and Utilities:  
->->->Motherboards, processors, power supplies, optical drives, peripherals  
```PowerShell  
Get-WmiObject -Class Win32_Processor | Select -Property Name, Number*
```  
```PowerShell  
Get-WmiObject Win32_BIOS –computername $computer
```  
```PowerShell  
Get-WmiObject -query “select Name,Status from Win32_PnPEntity”
```  
->->->Hard drives and partitions, /dev/sd*  
```PowerShell  
Get-WmiObject -Class win32_DiskDrive
```  
->->->Drivers  
```PowerShell  
Get-Process -Module
```  
  
->Where Data is Stored  
->->Key Knowledge Areas:  
->->->Programs and configuration, packages and package databases  
```PowerShell  
Get-WmiObject -Class Win32_Product
```  
```PowerShell  
Get-Package
```  
```PowerShell  
Install-Package filezilla
```  
->->->Processes, memory addresses, system messaging and logging  
```PowerShell  
Get-Process
```  
```PowerShell  
@(Get-Process).where{$_.WorkingSet -gt 100MB}
```  
```PowerShell  
@(Get-Process).where{$_.WS -gt 100MB}
```  
->->Terms and Utilities:  
->->->ps, top, free  
```PowerShell  
Get-Process
```  
->->->syslog, dmesg  
```PowerShell  
Get-EventLog -LogName System
```  
->->->/etc/, /var/log/  
```PowerShell  
Get-EventLog -LogName System
```  
->->->/boot/, /proc/, /dev/, /sys/  
  
->Your Computer on the Network  
```PowerShell  
http://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/
```  
->->Key Knowledge Areas:  
->->->Internet, network, routers  
->->->Querying DNS client configuration  
->->->Querying Network configuration  
->->Terms and Utilities:  
->->->route, ip route show  
->->->ifconfig, ip addr show  
->->->netstat, ip route show  
->->->/etc/resolv.conf, /etc/hosts  
->->->IPv4, IPv6  
->->->ping  
->->->host  
  
---------------------------------------------------  
# Security and File Permissions
---------------------------------------------------  
->Basic Security and Identifying User Types  
->->Key Knowledge Areas:  
->->->Root and Standard Users  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
->->->System users  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
->->Terms and Utilities:  
->->->/etc/passwd, /etc/group  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
->->->id, who, w  
```PowerShell  
net user
```  
->->->sudo, su  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
  
->Creating Users and Groups  
->->Key Knowledge Areas:  
->->->User and group commands  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
```PowerShell  
net localgroup
```  
->->->User IDs  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
```PowerShell  
net localgroup
```  
->->Terms and Utilities:  
->->->/etc/passwd, /etc/shadow, /etc/group, /etc/skel/  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
```PowerShell  
net localgroup
```  
->->->id, last  
->->->useradd, groupadd  
```PowerShell  
Get-WmiObject -Class Win32_Account
```  
```PowerShell  
net user
```  
```PowerShell  
net localgroup
```  
->->->passwd  
```PowerShell  
net user
```  
  
->Managing File Permissions and Ownership  
->->Key Knowledge Areas:  
->->->File/directory permissions and owners  
```PowerShell  
Get-Acl
```  
->->Terms and Utilities:  
->->->ls -l, ls -a  
```PowerShell  
Get-Acl
```  
->->->chmod, chown  
```PowerShell  
Set-Acl
```  
* http://www.jesusninoc.com/2015/08/19/anadir-permiso-ntfs-a-una-carpeta/
  
->Special Directories and Files  
->->Key Knowledge Areas:  
->->->Using temporary files and directories  
->->->Symbolic links  
->->Terms and Utilities:  
->->->/tmp/, /var/tmp/ and Sticky Bit  
->->->ls -d  
->->->ln -s  
