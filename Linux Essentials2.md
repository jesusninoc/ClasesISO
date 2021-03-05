Linux Essentials  
https://www.lpi.org/study-resources/linux-essentials-exam-objectives/  
  
---------------------------------------------------  
Introduction  
---------------------------------------------------  
Windows PowerShell uses a "verb-noun" naming system  
  
---------------------------------------------------  
The Linux Community and a Career in Open Source  
---------------------------------------------------  
-Linux Evolution and Popular Operating Systems  
 --Key Knowledge Areas:  
  ---Desktop Applications  
---Server Applications  
---Development Languages  
---Package Management Tools and repositories  
--Terms and Utilities:  
---OpenOffice.org, LibreOffice, Thunderbird, Firefox, GIMP  
---Apache HTTPD, NGINX, MySQL, NFS, Samba  
---C, Java, Perl, shell, Python, Samba  
---dpkg, apt-get, rpm, yum  
-Understanding Open Source Software and Licensing  
--Key Knowledge Areas:  
---Licensing  
---Free Software Foundation (FSF), Open Source Initiative (OSI)  
--Terms and Utilities:  
---GPL, BSD, Creative Commons  
---Free Software, Open Source Software, FOSS, FLOSS  
---Open Source business models  
-ICT Skills and Working in Linux  
--Key Knowledge Areas:  
---Desktop Skills  
---Getting to the Command Line  
---Industry uses of Linux, Cloud Computing and Virtualization  
--Terms and Utilities:  
---Using a browser, privacy concerns, configuration options, searching the web and saving content  
---Terminal and Console  
---Password issues  
---Privacy issues and tools  
---Use of common open source applications in presentations and projects  
  
---------------------------------------------------  
Finding Your Way on a Linux System  
---------------------------------------------------  
-Command Line Basics  
--Key Knowledge Areas:  
---Basic shell  
---Command line syntax  
Get-Verb  
Get-Command -Noun  
---Variables  
http://www.jesusninoc.com/2014/12/31/curso-de-powershell/  
---Globbing  
*  
?  
---Quoting  
"  
'  
--Terms and Utilities:  
---Bash  
---echo  
Write-Host  
---history  
Get-History  
---PATH env variable  
$Env:Path  
[Environment]::GetEnvironmentVariable("Path")  
---export  
---type  
Get-Content  
-Using the Command Line to Get Help  
--Key Knowledge Areas:  
---Man  
Get-Help  
---Info  
--Terms and Utilities:  
---man  
Get-Help  
---info  
Get-Help  
---Man pages  
Get-Help  
---/usr/share/doc/  
Get-Help  
---locate  
  
-Using Directories and Listing Files  
--Key Knowledge Areas:  
---Files, directories  
Get-ChildItem -File  
Get-ChildItem -Directory  
---Hidden files and directories  
Get-ChildItem -Hidden  
---Home  
$home  
---Absolute and relative paths  
c:\  
..\  
--Terms and Utilities:  
---Common options for ls  
Get-ChildItem  
---Recursive listings  
Get-ChildItem -Recurse  
---cd  
Set-Location  
---. and ..  
.  
..  
---home and ~  
Set-Location ~  
  
-Creating, Moving and Deleting Files  
--Key Knowledge Areas:  
---Files and directories  
Get-ChildItem -File  
Get-ChildItem -Directory  
---Case sensitivity  
---Simple globbing and quoting  
"  
'  
--Terms and Utilities:  
---mv, cp, rm, touch  
Move-Item  
Copy-Item  
Remove-Item  
New-Item  
---mkdir, rmdir  
New-Item  
Remove-Item  
  
---------------------------------------------------  
The Power of the Command Line  
---------------------------------------------------  
-Archiving Files on the Command Line  
--Key Knowledge Areas:  
---Files, directories  
Get-ChildItem -File  
Get-ChildItem -Directory  
---Archives, compression  
Get-ChildItem -File  
--Terms and Utilities:  
---tar  
Compress-Archive  
Expand-Archive  
---Common tar options  
---gzip, bzip2  
Compress-Archive  
Expand-Archive  
---zip, unzip  
Compress-Archive  
Expand-Archive  
  
-Searching and Extracting Data from Files  
--Key Knowledge Areas:  
---Command line pipes  
Get-Command | Select-Object CommandType, name  
---I/O re-direction  
Get-Command > fichero.txt  
---Basic Regular Expressions ., [  ], *, ?  
Get-ChildItem .  
Get-ChildItem | Where-Object {$_.Name -match "\d\.[^\d]"}  
Get-ChildItem *.iso  
Get-ChildItem *.is?  
--Terms and Utilities:  
---grep  
Get-ChildItem | select-object name | Select-String 2015  
---less  
more  
---cat, head, tail  
Get-Content  
Get-Content -ReadCount  
---sort  
Get-ChildItem | Sort-Object  
---cut  
Get-ChildItem | Select-Object Name  
---wc  
(Get-ChildItem | Select-Object Name).count  
  
-Turning Commands into a Script  
--Key Knowledge Areas:  
---Basic shell scripting  
---Awareness of common text editors  
--Terms and Utilities:  
---#! (shebang)  
---/bin/bash  
---Variables  
http://www.jesusninoc.com/2014/12/31/curso-de-powershell/  
---Arguments  
---for loops  
https://github.com/jesusninoc/PowerShell/tree/master/Bucles  
---echo  
Write-Host "Hi"  
---Exit status  
exit  
  
---------------------------------------------------  
The Linux Operating System  
---------------------------------------------------  
-Choosing an Operating System  
--Key Knowledge Areas:  
---Windows, Mac, Linux differences  
---Distribution life cycle management  
--Terms and Utilities:  
---GUI versus command line, desktop configuration  
---Maintenance cycles, Beta and Stable  
  
-Understanding Computer Hardware  
--Key Knowledge Areas:  
---Hardware  
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
--Terms and Utilities:  
---Motherboards, processors, power supplies, optical drives, peripherals  
Get-WmiObject -Class Win32_Processor | Select -Property Name, Number*  
Get-WmiObject Win32_BIOS –computername $computer  
Get-WmiObject -query “select Name,Status from Win32_PnPEntity”  
---Hard drives and partitions, /dev/sd*  
Get-WmiObject -Class win32_DiskDrive  
---Drivers  
Get-Process -Module  
  
-Where Data is Stored  
--Key Knowledge Areas:  
---Programs and configuration, packages and package databases  
Get-WmiObject -Class Win32_Product  
Get-Package  
Install-Package filezilla  
---Processes, memory addresses, system messaging and logging  
Get-Process  
@(Get-Process).where{$_.WorkingSet -gt 100MB}  
@(Get-Process).where{$_.WS -gt 100MB}  
--Terms and Utilities:  
---ps, top, free  
Get-Process  
---syslog, dmesg  
Get-EventLog -LogName System  
---/etc/, /var/log/  
Get-EventLog -LogName System  
---/boot/, /proc/, /dev/, /sys/  
  
-Your Computer on the Network  
http://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/  
--Key Knowledge Areas:  
---Internet, network, routers  
---Querying DNS client configuration  
---Querying Network configuration  
--Terms and Utilities:  
---route, ip route show  
---ifconfig, ip addr show  
---netstat, ip route show  
---/etc/resolv.conf, /etc/hosts  
---IPv4, IPv6  
---ping  
---host  
  
---------------------------------------------------  
Security and File Permissions  
---------------------------------------------------  
-Basic Security and Identifying User Types  
--Key Knowledge Areas:  
---Root and Standard Users  
Get-WmiObject -Class Win32_Account  
net user  
---System users  
Get-WmiObject -Class Win32_Account  
net user  
--Terms and Utilities:  
---/etc/passwd, /etc/group  
Get-WmiObject -Class Win32_Account  
net user  
---id, who, w  
net user  
---sudo, su  
Get-WmiObject -Class Win32_Account  
net user  
  
-Creating Users and Groups  
--Key Knowledge Areas:  
---User and group commands  
Get-WmiObject -Class Win32_Account  
net user  
net localgroup  
---User IDs  
Get-WmiObject -Class Win32_Account  
net user  
net localgroup  
--Terms and Utilities:  
---/etc/passwd, /etc/shadow, /etc/group, /etc/skel/  
Get-WmiObject -Class Win32_Account  
net user  
net localgroup  
---id, last  
---useradd, groupadd  
Get-WmiObject -Class Win32_Account  
net user  
net localgroup  
---passwd  
net user  
  
-Managing File Permissions and Ownership  
--Key Knowledge Areas:  
---File/directory permissions and owners  
Get-Acl  
--Terms and Utilities:  
---ls -l, ls -a  
Get-Acl  
---chmod, chown  
Set-Acl  
http://www.jesusninoc.com/2015/08/19/anadir-permiso-ntfs-a-una-carpeta/  
  
-Special Directories and Files  
--Key Knowledge Areas:  
---Using temporary files and directories  
---Symbolic links  
--Terms and Utilities:  
---/tmp/, /var/tmp/ and Sticky Bit  
---ls -d  
---ln -s  
