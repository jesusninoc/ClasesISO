---------------------------------------------------  
# Capacity Planning
---------------------------------------------------  
->Measure and Troubleshoot Resource Usage  
->->Key Knowledge Areas:  
->->->Measure CPU usage  
```PowerShell  
Get-Process | Select-Object Name, CPU | Format-Custom
```  
->->->Measure memory usage  
```PowerShell  
Get-Process | Select-Object WorkingSet
```  
```PowerShell  
@(Get-Process) | Select-Object WorkingSet
```  
```PowerShell  
@(Get-Process).where{$_.WorkingSet -gt 100MB}
```  
```PowerShell  
@(Get-Process).where{$_.WS -gt 100MB}
```  
->->->Measure disk I/O  
```PowerShell  
$query = "SELECT * FROM Win32_PerfRawData_PerfProc_Process"
```  
```PowerShell  
Get-WMIObject -Query $query
```  
->->->Measure network I/O  
```PowerShell  
Get-NetAdapterStatistics
```  
```PowerShell  
Get-NetAdapterStatistics | Select-Object *
```  
->->->Measure firewalling and routing throughput  
```PowerShell  
Get-NetFirewallAddressFilter
```  
```PowerShell  
Get-NetFirewallApplicationFilter
```  
```PowerShell  
Get-NetFirewallInterfaceFilter
```  
```PowerShell  
Get-NetFirewallInterfaceTypeFilter
```  
```PowerShell  
Get-NetFirewallPortFilter
```  
```PowerShell  
Get-NetFirewallProfile
```  
```PowerShell  
Get-NetFirewallRule
```  
```PowerShell  
Get-NetFirewallSecurityFilter
```  
```PowerShell  
Get-NetFirewallServiceFilter
```  
```PowerShell  
Get-NetFirewallSetting
```  
->->->Map client bandwidth usage  
```PowerShell  
Get-WmiObject -class Win32_PerfFormattedData_Tcpip_NetworkInterface |select BytesTotalPersec, CurrentBandwidth,PacketsPersec|where {$_.PacketsPersec -gt 0}
```  
->->->Match / correlate system symptoms with likely problems  
```PowerShell  
Get-EventLog
```  
->->->Estimate throughput and identify bottlenecks in a system including networking  
```PowerShell  
Get-Process | Select-Object Name, CPU | Format-Custom
```  
```PowerShell  
Get-Process | Select-Object WorkingSet
```  
```PowerShell  
Get-WmiObject -class "Win32_PhysicalMemoryArray"
```  
->->The following is a partial list of the used files, terms and utilities:  
->->->iostat  
```PowerShell  
Get-counter
```  
```PowerShell  
Get-counter -Counter "\\lamiw81\disco físico(_total)\longitud actual de la cola de disco"
```  
->->->netstat  
```PowerShell  
Get-NetNeighbor
```  
```PowerShell  
Get-NetAdapterStatistics
```  
```PowerShell  
Get-NetRoute
```  
```PowerShell  
Get-NetTCPConnection
```  
```PowerShell  
Get-NetUDPEndpoint
```  
->->->w  
```PowerShell  
Get-WmiObject win32_process |% {Write-Host $_.processname $_.getowner().user}
```  
->->->top  
```PowerShell  
Get-Process
```  
->->->sar  
```PowerShell  
Get-Process
```  
->->->processes blocked on I/O  
```PowerShell  
(Get-WmiObject Win32_PerfFormattedData_PerfProc_Process)
```  
```PowerShell  
(Get-WmiObject Win32_PerfFormattedData_PerfOS_memory)
```  
->->->blocks out  
```PowerShell  
(Get-WmiObject Win32_PerfFormattedData_PerfProc_Process)
```  
```PowerShell  
(Get-WmiObject Win32_PerfFormattedData_PerfOS_memory)
```  
->->->vmstat  
```PowerShell  
Get-Process
```  
->->->pstree, ps  
```PowerShell  
Get-Process
```  
->->->Isof  
```PowerShell  
(Get-WmiObject win32_process) | Select-Object Name,CommandLine
```  
```PowerShell  
Get-WmiObject win32_process | Select-Object Path,ExecutablePath,ProcessName
```  
```PowerShell  
Get-Process -Module
```  
->->->uptime  
```PowerShell  
Get-CimInstance -ClassName win32_operatingsystem | select csname, lastbootuptime
```  
```PowerShell  
Get-WmiObject win32_operatingsystem | select csname, @{LABEL='LastBootUpTime';EXPRESSION={$_.ConverttoDateTime($_.lastbootuptime)}}
```  
->->->swap  
```PowerShell  
Get-Process | Select-Object PagedMemorySize64,NonpagedSystemMemorySize,NonpagedSystemMemorySize64,PagedMemorySize64,PagedSystemMemorySize,PagedSystemMemorySize64,PeakPagedMemorySize,PeakPagedMemorySize64,PeakWorkingSet,PeakWorkingSet64,PeakVirtualMemorySize,PeakVirtualMemorySize64
```  
->->->blocks in  
```PowerShell  
(Get-WmiObject Win32_PerfFormattedData_PerfProc_Process)
```  
```PowerShell  
(Get-WmiObject Win32_PerfFormattedData_PerfOS_memory)
```  
  
->Predict Future Resource Needs  
->->Key Knowledge Areas:  
->->->Use collectd to monitor IT infrastructure usage  
->->->Predict capacity break point of a configuration  
->->->Observe growth rate of capacity usage  
->->->Graph the trend of capacity usage  
->->->Awareness of monitoring solutions such as Nagios, MRTG and Cacti  
->->The following is a partial list of the used files, terms and utilities:  
->->->diagnose  
->->->predict growth  
->->->resource exhaustion  
  
---------------------------------------------------  
# Linux Kernel
---------------------------------------------------  
->Kernel Components  
->->Key Knowledge Areas  
->->->Kernel 2.6.x documentation  
->->->Kernel 3.x documentation  
->->Terms and Utilities:  
->->->/usr/src/linux/  
->->->zImage  
->->->/usr/src/linux/Documentation/  
->->->bzImage  
  
->Compiling a kernel  
->->Key Knowledge Areas:  
->->->/usr/src/linux/  
->->->Kernel Makefiles  
->->->Kernel 2.6.x/3.x make targets  
->->->Customize the current kernel configuration.  
->->->Build a new kernel and appropriate kernel modules.  
->->->Install a new kernel and any modules.  
->->->Ensure that the boot manager can locate the new kernel and associated files.  
->->->Module configuration files  
->->->Awareness of dracut  
->->Terms and Utilities:  
->->->mkinitrd  
->->->mkinitramfs  
->->->make  
->->->bzip2  
->->->make targets (all, config, xconfig, menuconfig, gconfig, oldconfig, mrproper, zImage, bzImage, modules, modules_install, rpm-pkg, binrpm-pkg, deb-pkg)  
->->->gzip  
->->->module tool  
->->->/usr/src/linux/.confi  
->->->/lib/modules/kernel-version/  
->->->depmod  
  
->Kernel runtime management and troubleshooting  
->->Key Knowledge Areas:  
->->->Use command-line utilities to get information about the currently running kernel and kernel modules  
->->->Manually load and unload kernel modules  
->->->Determine when modules can be unloaded  
->->->Determine what parameters a module accepts  
->->->Configure the system to load modules by names other than their file name.  
->->->/proc filesystem  
->->->Content of /, /boot/ , and /lib/modules/  
->->->Tools and utilities to analyze information about the available hardware  
->->->udev rules  
->->Terms and Utilities:  
->->->/lib/modules/kernel-version/modules.dep  
->->->module configuration files in /etc/  
->->->/proc/sys/kernel/  
->->->/sbin/depmod  
->->->/sbin/rmmod  
->->->/sbin/modinfo  
->->->/bin/dmesg  
->->->/sbin/lspci  
->->->/usr/bin/lsdev  
->->->/sbin/lsmod  
->->->/sbin/modprobe  
->->->/sbin/insmod  
->->->/bin/uname  
->->->/usr/bin/lsusb  
->->->/etc/sysctl.conf, /etc/sysctl.d/  
->->->/sbin/sysctl  
->->->udevmonitor  
->->->udevadm monitor  
->->->/etc/udev/  
  
---------------------------------------------------  
# System Startup
---------------------------------------------------  
->Customizing SysV->init system startup  
```PowerShell  
Get-WmiObject -Class win32_startupCommand
```  
```PowerShell  
Get-WmiObject -Query "Select StartMode From Win32_Service Where Name='winmgmt'"
```  
->->Key Knowledge Areas:  
->->->Linux Standard Base Specification (LSB)  
->->->SysV init environment  
->->Terms and Utilities:  
```PowerShell  
New-ScheduledTaskAction
```  
```PowerShell  
New-ScheduledTaskTrigger
```  
```PowerShell  
Register-ScheduledTask
```  
->->->/etc/inittab  
->->->/etc/init.d/  
->->->/etc/rc.d/  
->->->chkconfig  
->->->update-rc.d  
->->->init and telinit  
  
->System Recovery  
->->Key Knowledge Areas:  
->->->GRUB version 2 and Legacy  
->->->Grub shell  
->->->Boot loader start and hand off to kernel  
->->->Kernel loading  
->->->Hardware initialization and setup  
->->->Daemon/service initialization and setup  
->->->Know the different boot loader install locations on a hard disk or removable device  
->->->Overwriting standard boot loader options and using boot loader shells  
->->->Awareness of UEFI  
->->Terms and Utilities:  
->->->mount  
->->->fsck  
->->->inittab, telinit and init with SysV init  
->->->the contents of /boot/ and /boot/grub/  
->->->GRUB  
->->->grub-install  
->->->initrd, initramfs  
->->->Master boot record  
  
->Alternate Bootloaders  
->->Key Knowledge Areas:  
->->->LILO  
->->->SYSLINUX, ISOLINUX, PXELINUX  
->->->Understanding of PXE  
->->Terms and Utilities:  
->->->lilo, /etc/lilo.conf  
->->->syslinux  
->->->extlinux  
->->->isolinux.bin  
->->->isolinux.cfg  
->->->pxelinux.0  
->->->pxelinux.cfg/  
  
---------------------------------------------------  
# Filesystem and Devices
---------------------------------------------------  
->Operating the Linux filesystem  
->->Key Knowledge Areas:  
->->->The concept of the fstab configuration  
->->->Tools and utilities for handling SWAP partitions and files  
->->->Use of UUIDs  
->->Terms and Utilities:  
->->->/etc/fstab  
->->->/etc/mtab  
->->->/proc/mounts  
->->->mount and umount  
->->->sync  
->->->swapon  
->->->swapoff  
  
->Maintaining a Linux filesystem  
->->Key Knowledge Areas:  
->->->Tools and utilities to manipulate and ext2, ext3 and ext4  
->->->Tools and utilities to manipulate xfs  
->->->Awareness of Btrfs  
->->Terms and Utilities:  
->->->fsck (fsck.*)  
->->->mkfs (mkfs.*)  
->->->dumpe2fs, xfsdump, xfsrestore  
->->->debugfs  
->->->tune2fs  
->->->mkswap  
->->->xfs_info, xfs_check and xfs_repair  
->->->smartd, smartctl  
  
->Creating and configuring filesystem options  
->->Key Knowledge Areas:  
->->->autofs configuration files  
->->->UDF and ISO9660 tools and utilities  
->->->Awareness of CD-ROM filesystems (UDF, ISO9660, HFS)  
->->->Awareness of CD-ROM filesystem extensions (Joliet, Rock Ridge, El Torito)  
->->->Basic feature knowledge of encrypted filesystems  
->->Terms and Utilities:  
->->->/etc/auto.master  
->->->/etc/auto.[dir]  
->->->mkisofs  
  
---------------------------------------------------  
# Advanced Storage Device Administration
---------------------------------------------------  
->Configuring RAID  
->->Key Knowledge Areas:  
->->->Software raid configuration files and utilities  
->->Terms and Utilities:  
->->->mdadm.conf  
->->->mdadm  
->->->/proc/mdstat  
->->->partition type 0xFD  
  
->Adjusting Storage Device Access  
->->Key Knowledge Areas:  
->->->Tools and utilities to configure DMA for IDE devices including ATAPI and SATA  
->->->Tools and utilities to manipulate or analyze system resources (e.g. interrupts)  
->->->Awareness of sdparm command and its uses  
->->->Tools and utilities for iSCSI  
->->Terms and Utilities:  
->->->hdparm, sdparm  
->->->tune2fs  
->->->sysctl  
->->->/dev/hd*, /dev/sd*  
->->->iscsiadm, scsi_id, iscsid and iscsid.conf  
->->->WWID, WWN, LUN numbers  
  
->Logical Volume Manager  
->->Key Knowledge Areas:  
->->->Tools in the LVM suite  
->->->Resizing, renaming, creating, and removing logical volumes, volume groups, and physical volumes  
->->->Creating and maintaining snapshots  
->->->Activating volume groups  
->->Terms and Utilities:  
->->->/sbin/pv*  
->->->/sbin/lv*  
->->->/sbin/vg*  
->->->mount  
->->->/dev/mapper/  
  
---------------------------------------------------  
# Networking Configuration
---------------------------------------------------  
->Basic networking configuration  
* http://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/

->->Key Knowledge Areas:  
->->->Utilities to configure and manipulate ethernet network interfaces  
->->->Configuring basic access to wireless networks with iw, iwconfig and iwlist  
->->Terms and Utilities:  
->->->/sbin/route  
```PowerShell  
Get-NetRoute
```  
->->->/sbin/ifconfig  
```PowerShell  
Get-NetIPv4Protocol
```  
```PowerShell  
Get-NetIPv6Protocol
```  
```PowerShell  
New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress 192.168.1.56 -PrefixLength 24 -DefaultGateway 192.168.1.1
```  
->->->/sbin/ip  
```PowerShell  
Get-NetIPv4Protocol
```  
```PowerShell  
Get-NetIPv6Protocol
```  
```PowerShell  
New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress 192.168.1.56 -PrefixLength 24 -DefaultGateway 192.168.1.1
```  
->->->/usr/sbin/arp  
```PowerShell  
Get-NetAdapter | Select-Object Name,MacAddress
```  
```PowerShell  
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Select-Object Description,MACAddress
```  
```PowerShell  
Get-NetNeighbor
```  
->->->/sbin/iwconfig  
->->->/sbin/iwlist  
  
->Advanced Network Configuration and Troubleshooting  
->->Key Knowledge Areas:  
->->->Utilities to manipulate routing tables  
->->->Utilities to configure and manipulate ethernet network interfaces  
->->->Utilities to analyze the status of the network devices  
->->->Utilities to monitor and analyze the TCP/IP traffic  
->->Terms and Utilities:  
->->->/sbin/route  
```PowerShell  
Get-NetRoute
```  
->->->/sbin/ifconfig  
```PowerShell  
Get-NetIPv4Protocol
```  
```PowerShell  
Get-NetIPv6Protocol
```  
```PowerShell  
New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress 192.168.1.56 -PrefixLength 24 -DefaultGateway 192.168.1.1
```  
->->->/bin/netstat  
```PowerShell  
Get-NetTCPConnection
```  
```PowerShell  
Get-NetTCPConnection | Group State, RemotePort | Sort Count | FT Count, Name –Autosize
```  
```PowerShell  
Get-NetTCPConnection | ? State -eq Established | FT –Autosize
```  
```PowerShell  
Get-NetTCPConnection | ? State -eq Established | ? RemoteAddress -notlike 127* | % { $_; Resolve-DnsName $_.RemoteAddress -type PTR -ErrorAction SilentlyContinue}
```  
```PowerShell  
Get-NetUDPEndpoint
```  
->->->/bin/ping  
```PowerShell  
Test-NetConnection
```  
```PowerShell  
Test-NetConnection www.jesusninoc.com
```  
```PowerShell  
Test-NetConnection -ComputerName www.jesusninoc.com -InformationLevel Detailed
```  
```PowerShell  
Test-NetConnection -ComputerName www.jesusninoc.com | Select -ExpandProperty PingReplyDetails | FT Address, Status, RoundTripTime
```  
```PowerShell  
1..100 | % { Test-NetConnection -ComputerName www.jesusninoc.com -RemotePort 80 } | FT -AutoSize
```  
->->->/usr/sbin/arp  
```PowerShell  
Get-NetAdapter | Select-Object Name,MacAddress
```  
```PowerShell  
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Select-Object Description,MACAddress
```  
```PowerShell  
Get-NetNeighbor
```  
->->->/usr/sbin/tcpdump  
->->->/usr/sbin/lsof  
```PowerShell  
Get-NetTCPConnection
```  
```PowerShell  
Get-NetTCPConnection | Group State, RemotePort | Sort Count | FT Count, Name –Autosize
```  
```PowerShell  
Get-NetTCPConnection | ? State -eq Established | FT –Autosize
```  
```PowerShell  
Get-NetTCPConnection | ? State -eq Established | ? RemoteAddress -notlike 127* | % { $_; Resolve-DnsName $_.RemoteAddress -type PTR -ErrorAction SilentlyContinue}
```  
```PowerShell  
Get-NetUDPEndpoint
```  
->->->/usr/bin/nc  
->->->/sbin/ip  
```PowerShell  
Get-NetIPv4Protocol
```  
```PowerShell  
Get-NetIPv6Protocol
```  
```PowerShell  
New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress 192.168.1.56 -PrefixLength 24 -DefaultGateway 192.168.1.1
```  
->->->nmap  
  
->Troubleshooting Network Issues  
->->Key Knowledge Areas:  
->->->Location and content of access restriction files  
->->->Utilities to configure and manipulate ethernet network interfaces  
->->->Utilities to manage routing tables  
->->->Utilities to list network states.  
->->->Utilities to gain information about the network configuration  
->->->Methods of information about the recognized and used hardware devices  
->->->System initialization files and their contents (SysV init process)  
->->->Awareness of NetworkManager and its impact on network configuration  
->->Terms and Utilities:  
->->->/sbin/ifconfig  
```PowerShell  
Get-NetIPv4Protocol
```  
```PowerShell  
Get-NetIPv6Protocol
```  
```PowerShell  
New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress 192.168.1.56 -PrefixLength 24 -DefaultGateway 192.168.1.1
```  
->->->/sbin/route  
```PowerShell  
Get-NetRoute
```  
->->->/bin/netstat  
```PowerShell  
Get-NetTCPConnection
```  
```PowerShell  
Get-NetTCPConnection | Group State, RemotePort | Sort Count | FT Count, Name –Autosize
```  
```PowerShell  
Get-NetTCPConnection | ? State -eq Established | FT –Autosize
```  
```PowerShell  
Get-NetTCPConnection | ? State -eq Established | ? RemoteAddress -notlike 127* | % { $_; Resolve-DnsName $_.RemoteAddress -type PTR -ErrorAction SilentlyContinue}
```  
```PowerShell  
Get-NetUDPEndpoint
```  
->->->/etc/network/, /etc/sysconfig/network-scripts/  
```PowerShell  
Get-NetIPv4Protocol
```  
```PowerShell  
Get-NetIPv6Protocol
```  
```PowerShell  
New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress 192.168.1.56 -PrefixLength 24 -DefaultGateway 192.168.1.1
```  
->->->/bin/ping  
```PowerShell  
Test-NetConnection
```  
```PowerShell  
Test-NetConnection www.jesusninoc.com
```  
```PowerShell  
Test-NetConnection -ComputerName www.jesusninoc.com -InformationLevel Detailed
```  
```PowerShell  
Test-NetConnection -ComputerName www.jesusninoc.com | Select -ExpandProperty PingReplyDetails | FT Address, Status, RoundTripTime
```  
```PowerShell  
1..100 | % { Test-NetConnection -ComputerName www.jesusninoc.com -RemotePort 80 } | FT -AutoSize
```  
->->->System log files such as /var/log/syslog & /var/log/messages  
```PowerShell  
Get-EventLog -LogName System -EntryType Error, Warning -After (Get-Date).AddDays(-1)
```  
->->->/etc/resolv.conf  
->->->/etc/hosts  
->->->/etc/hostname, /etc/HOSTNAME  
->->->/bin/hostname  
->->->/usr/sbin/traceroute  
```PowerShell  
Test-NetConnection –TraceRoute
```  
->->->/bin/dmesg  
->->->/etc/hosts.allow, /etc/hosts.deny  
  
---------------------------------------------------   
# System Maintenance
---------------------------------------------------  
->Make and install programs from source  
->->Key Knowledge Areas:  
->->->Unpack source code using common compression and archive utilities  
->->->Understand basics of invoking make to compile programs  
->->->Apply parameters to a configure script  
->->->Know where sources are stored by default  
->->Terms and Utilities:  
->->->/usr/src/  
->->->gunzip  
```PowerShell  
Compress-Archive -LiteralPath C:\powershell\example.txt –CompressionLevel Optimal -DestinationPath C:\powershell\comprimido.zip
```  
```PowerShell  
Expand-Archive -LiteralPath C:\powershell\comprimido.zip -DestinationPath C:\powershell\descomprimir
```  
->->->gzip  
```PowerShell  
Compress-Archive -LiteralPath C:\powershell\example.txt –CompressionLevel Optimal -DestinationPath C:\powershell\comprimido.zip
```  
```PowerShell  
Expand-Archive -LiteralPath C:\powershell\comprimido.zip -DestinationPath C:\powershell\descomprimir
```  
->->->bzip2  
```PowerShell  
Compress-Archive -LiteralPath C:\powershell\example.txt –CompressionLevel Optimal -DestinationPath C:\powershell\comprimido.zip
```  
```PowerShell  
Expand-Archive -LiteralPath C:\powershell\comprimido.zip -DestinationPath C:\powershell\descomprimir
```  
->->->tar  
```PowerShell  
Compress-Archive -LiteralPath C:\powershell\example.txt –CompressionLevel Optimal -DestinationPath C:\powershell\comprimido.zip
```  
```PowerShell  
Expand-Archive -LiteralPath C:\powershell\comprimido.zip -DestinationPath C:\powershell\descomprimir
```  
->->->configure  
->->->make  
->->->uname  
* http://www.jesusninoc.com/2012/12/10/useful-wmi-classes/

->->->install  
->->->patch  
  
->Backup operations  
->->Key Knowledge Areas:  
->->->Knowledge about directories that have to be include in backups  
->->->Awareness of network backup solutions such as Amanda, Bacula and BackupPC  
->->->Knowledge of the benefits and drawbacks of tapes, CDR, disk or other backup media  
->->->Perform partial and manual backups  
->->->Verify the integrity of backup files  
->->->Partially or fully restore backups  
->->Terms and Utilities:  
->->->/bin/sh  
->->->dd  
->->->tar  
->->->/dev/st* and /dev/nst*  
->->->mt  
->->->rsync  
  
->Notify users on system->related issues  
->->Key Knowledge Areas:  
->->->Automate communication with users through logon messages  
->->->Inform active users of system maintenance  
->->Terms and Utilities:  
->->->/etc/issue  
->->->/etc/issue.net  
->->->/etc/motd  
->->->wall  
->->->/sbin/shutdown  
```PowerShell  
$equipo='.'
```  
```PowerShell  
(get-wmiobject -class win32_operatingsystem -computername $equipo).win32shutdown(12)
```  
