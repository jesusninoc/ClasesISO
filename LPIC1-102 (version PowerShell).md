---------------------------------------------------  
# Shells, Scripting and Data Management
---------------------------------------------------  
->Customize and use the shell environment  
->->Key Knowledge Areas:  
->->->Set environment variables (e.g. PATH) at login or when spawning a new shell  
```PowerShell  
$Env:Path
```  
->->->Write Bash functions for frequently used sequences of commands  
->->->Maintain skeleton directories for new user accounts  
->->->Set command search path with the proper directory  
->->The following is a partial list of the used files, terms and utilities:  
->->->.  
```PowerShell  
Set-Location .
```  
```PowerShell  
Set-Location ..
```  
```PowerShell  
Set-Location \
```  
->->->source  
->->->/etc/bash.bashrc  
```PowerShell  
Get-Location
```  
->->->/etc/profile  
```PowerShell  
Get-Location
```  
->->->env  
```PowerShell  
$Env:Path
```  
->->->export  
```PowerShell  
$Env:Path | Out-File
```  
->->->set  
```PowerShell  
$Env:Path
```  
->->->unset  
```PowerShell  
$Env:Path
```  
->->->~/.bash_profile  
```PowerShell  
Get-Location
```  
->->->~/.bash_login  
```PowerShell  
Get-Location
```  
->->->~/.profile  
```PowerShell  
Get-Location
```  
->->->~/.bashrc  
```PowerShell  
Get-Location
```  
->->->~/.bash_logout  
```PowerShell  
Get-Location
```  
->->->function  
->->->alias  
```PowerShell  
Get-Alias
```  
->->->lists  
  
->Customize or write simple scripts  
->->Key Knowledge Areas:  
->->->Use standard sh syntax (loops, tests)  
* http://www.jesusninoc.com/2015/09/29/bucles/

->->->Use command substitution  
```PowerShell  
"hola" -replace "h","j"
```  
->->->Test return values for success or failure or other information provided by a command  
->->->Perform conditional mailing to the superuser  
->->->Correctly select the script interpreter through the shebang (#!) line  
->->->Manage the location, ownership, execution and suid-rights of scripts  
->->Terms and Utilities:  
->->->for  
* http://www.jesusninoc.com/2015/09/29/bucles/

->->->while  
->->->test  
```PowerShell  
New-Item -Name fichero -WhatIf
```  
->->->if  
* http://www.jesusninoc.com/2015/04/26/sentencia-condicional-if-else/

->->->read  
```PowerShell  
Read-Host
```  
->->->seq  
```PowerShell  
1..100
```  
->->->exec  
```PowerShell  
1..100 | New-Item -Name $_ -WhatIf
```  
  
->SQL data management  
* http://www.jesusninoc.com/2015/12/13/select-into-mysql-database/
* http://www.jesusninoc.com/2015/12/14/insert-into-mysql-database/

->->Key Knowledge Areas:  
->->->Use of basic SQL commands  
->->->Perform basic data manipulation  
->->Terms and Utilities:  
->->->insert  
->->->update  
->->->select  
->->->delete  
->->->from  
->->->where  
->->->group by  
->->->order by  
->->->join  
  
---------------------------------------------------  
# Interfaces and Desktops
---------------------------------------------------  
->Install and configure X11  
->->Key Knowledge Areas:  
->->->Verify that the video card and monitor are supported by an X server  
->->->Awareness of the X font server  
->->->Basic understanding and knowledge of the X Window configuration file  
->->Terms and Utilities:  
->->->/etc/X11/xorg.conf  
->->->xhost  
->->->DISPLAY  
->->->xwininfo  
* http://www.jesusninoc.com/2016/03/23/mover-notepad-de-una-posicion-de-la-pantalla-a-otra-y-escribir-un-texto-dentro-del-proceso/

```PowerShell  
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(502,222)
```  
->->->xdpyinfo  
->->->X  
  
->Setup a display manager  
->->Key Knowledge Areas:  
->->->Basic configuration of LightDM  
->->->Turn the display manager on or off  
->->->Change the display manager greeting  
->->->Awareness of XDM, KDM and GDM  
->->Terms and Utilities:  
->->->lightdm  
->->->/etc/lightdm/  
  
->Accessibility  
->->Key Knowledge Areas:  
->->->Basic knowledge of keyboard accessibility settings (AccessX)  
->->->Basic knowledge of visual settings and themes  
->->->Basic knowledge of assistive technology (ATs)  
->->Terms and Utilities:  
->->->Sticky/Repeat Keys  
```PowerShell  
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")
```  
->->->Slow/Bounce/Toggle Keys  
->->->Mouse Keys  
```PowerShell  
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(502,222)
```  
->->->High Contrast/Large Print Desktop Themes  
->->->Screen Reader  
```PowerShell  
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(502,222)
```  
->->->Braille Display  
->->->Screen Magnifier  
->->->On-Screen Keyboard  
->->->Gestures (used at login, for example GDM)  
->->->Orca  
->->->GOK  
->->->emacspeak  
  
---------------------------------------------------  
# Administrative Tasks
---------------------------------------------------  
->Manage user and group accounts and related system files  
* https://github.com/jesusninoc/PowerShell/blob/master/Usuarios/

->->Key Knowledge Areas:  
->->->Add, modify and remove users and groups  
->->->Manage user/group info in password/group databases  
->->->Create and manage special purpose and limited accounts  
->->Terms and Utilities:  
->->->/etc/passwd  
->->->/etc/shadow  
->->->/etc/group  
->->->/etc/skel/  
->->->chage  
->->->getent  
->->->groupadd  
->->->groupdel  
->->->groupmod  
->->->passwd  
->->->useradd  
->->->userdel  
->->->usermod  
  
->Automate system administration tasks by scheduling jobs  
* https://github.com/jesusninoc/PowerShell/tree/master/TareasProgramadas

->->Key Knowledge Areas:  
->->->Manage cron and at jobs  
->->->Configure user access to cron and at services  
->->->Configure anacron  
->->Terms and Utilities:  
->->->/etc/cron.{d,daily,hourly,monthly,weekly}/  
->->->/etc/at.deny  
->->->/etc/at.allow  
->->->/etc/crontab  
->->->/etc/cron.allow  
->->->/etc/cron.deny  
->->->/var/spool/cron/  
->->->crontab  
->->->at  
->->->atq  
->->->atrm  
->->->anacron  
->->->/etc/anacrontab  
  
->Localisation and internationalisation  
->->Key Knowledge Areas:  
->->->Configure locale settings and environment variables  
->->->Configure timezone settings and environment variables  
->->Terms and Utilities:  
->->->/etc/timezone  
```PowerShell  
Set-Date
```  
```PowerShell  
Get-Date
```  
->->->/etc/localtime  
->->->/usr/share/zoneinfo/  
->->->LC_*  
->->->LC_ALL  
->->->LANG  
->->->TZ  
->->->/usr/bin/locale  
->->->tzselect  
->->->timedatectl  
->->->date  
->->->iconv  
->->->UTF-8  
->->->ISO-8859  
->->->ASCII  
->->->Unicode  
  
---------------------------------------------------  
# Essential System Services
---------------------------------------------------  
->Maintain system time  
->->Key Knowledge Areas:  
->->->Set the system date and time  
->->->Set the hardware clock to the correct time in UTC  
->->->Configure the correct timezone  
->->->Basic NTP configuration  
->->->Knowledge of using the pool.ntp.org service  
->->->Awareness of the ntpq command  
->->Terms and Utilities:  
->->->/usr/share/zoneinfo/  
->->->/etc/timezone  
```PowerShell  
Set-Date
```  
```PowerShell  
Get-Date
```  
->->->/etc/localtime  
->->->/etc/ntp.conf  
->->->date  
->->->hwclock  
->->->ntpd  
->->->ntpdate  
->->->pool.ntp.org  
  
->System logging  
->->Key Knowledge Areas:  
->->->Configuration of the syslog daemon  
->->->Understanding of standard facilities, priorities and actions  
->->->Configuration of logrotate  
->->->Awareness of rsyslog and syslog-ng  
->->Terms and Utilities:  
->->->syslog.conf  
->->->syslogd  
->->->klogd  
->->->/var/log/  
->->->logger  
->->->logrotate  
->->->/etc/logrotate.conf  
->->->/etc/logrotate.d/  
->->->journalctl  
->->->/etc/systemd/journald.conf  
->->->/var/log/journal/  
  
->Mail Transfer Agent (MTA) basics  
->->Key Knowledge Areas:  
->->->Create e-mail aliases  
->->->Configure e-mail forwarding  
->->->Knowledge of commonly available MTA programs (postfix, sendmail, qmail, exim) (no configuration)  
->->Terms and Utilities:  
->->->~/.forward  
->->->sendmail emulation layer commands  
->->->newaliases  
->->->mail  
```PowerShell  
Send-MailMessage
```  
->->->mailq  
```PowerShell  
Get-Mailbox
```  
->->->postfix  
->->->sendmail  
->->->exim  
->->->qmail  
->->->~/.forward  
->->->sendmail emulation layer commands  
->->->newaliases  
  
->Manage printers and printing  
```PowerShell  
Out-Printer
```  
->->Key Knowledge Areas:  
->->->Basic CUPS configuration (for local and remote printers)  
->->->Manage user print queues  
->->->Troubleshoot general printing problems  
->->->Add and remove jobs from configured printer queues  
->->Terms and Utilities:  
->->->CUPS configuration files, tools and utilities  
->->->/etc/cups/  
->->->lpd legacy interface (lpr, lprm, lpq)  
  
---------------------------------------------------  
# Networking Fundamentals
---------------------------------------------------  
->Fundamentals of internet protocols  
* http://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/

->->Key Knowledge Areas:  
->->->Demonstrate an understanding of network masks and CIDR notation  
->->->Knowledge of the differences between private and public “dotted quad” IP addresses  
->->->Knowledge about common TCP and UDP ports and services (20, 21, 22, 23, 25, 53, 80, 110, 123, 139, 143, 161, 162, 389, 443, 465, 514, 636, 993, 995)  
->->->Knowledge about the differences and major features of UDP, TCP and ICMP  
->->->Knowledge of the major differences between IPv4 and IPv6  
->->->Knowledge of the basic features of IPv6  
->->Terms and Utilities:  
->->->/etc/services  
```PowerShell  
Get-Service
```  
->->->IPv4, IPv6  
->->->Subnetting  
->->->TCP, UDP, ICMP  
  
->Basic network configuration  
* http://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/

->->Key Knowledge Areas:  
->->->Manually and automatically configure network interfaces  
->->->Basic TCP/IP host configuration  
->->->Setting a default route  
->->Terms and Utilities:  
->->->/etc/hostname  
->->->/etc/hosts  
->->->/etc/nsswitch.conf  
->->->ifconfig  
->->->ifup  
->->->ifdown  
->->->ip  
->->->route  
->->->ping  
  
->Basic network troubleshooting  
* http://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/

->->Key Knowledge Areas:  
->->->Manually and automatically configure network interfaces and routing tables to include adding, starting, stopping, restarting, deleting or reconfiguring network interfaces  
->->->Change, view, or configure the routing table and correct an improperly set default route manually  
->->->Debug problems associated with the network configuration  
->->Terms and Utilities:  
->->->ifconfig  
->->->ip  
->->->ifup  
->->->ifdown  
->->->route  
->->->host  
->->->hostname  
->->->dig  
->->->netstat  
->->->ping  
->->->ping6  
->->->traceroute  
->->->traceroute6  
->->->tracepath  
->->->tracepath6  
->->->netcat  
  
->Configure client side DNS  
* http://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/

->->Key Knowledge Areas:  
->->->Query remote DNS servers  
->->->Configure local name resolution and use remote DNS servers  
->->->Modify the order in which name resolution is done  
->->Terms and Utilities:  
->->->/etc/hosts  
->->->/etc/resolv.conf  
->->->/etc/nsswitch.conf  
->->->host  
->->->dig  
```PowerShell  
Resolve-DnsName
```  
->->->getent  
  
---------------------------------------------------  
# Security
---------------------------------------------------  
->Perform security administration tasks  
->->Key Knowledge Areas:  
->->->Audit a system to find files with the suid/sgid bit set  
->->->Set or change user passwords and password aging information  
->->->Being able to use nmap and netstat to discover open ports on a system  
->->->Set up limits on user logins, processes and memory usage  
->->->Determine which users have logged in to the system or are currently logged in  
->->->Basic sudo configuration and usage  
->->Terms and Utilities:  
->->->find  
->->->passwd  
->->->fuser  
->->->lsof  
->->->nmap  
->->->chage  
->->->netstat  
```PowerShell  
Get-NetTCPConnection
```  
```PowerShell  
Get-NetUDPEndpoint
```  
->->->sudo  
->->->/etc/sudoers  
->->->su  
->->->usermod  
->->->ulimit  
->->->who, w, last  
  
->Setup host security  
->->Key Knowledge Areas:  
->->->Awareness of shadow passwords and how they work  
->->->Turn off network services not in use  
->->->Understand the role of TCP wrappers  
->->Terms and Utilities:  
->->->/etc/nologin  
->->->/etc/passwd  
->->->/etc/shadow  
->->->/etc/xinetd.d/  
->->->/etc/xinetd.conf  
->->->/etc/inetd.d/  
->->->/etc/inetd.conf  
->->->/etc/inittab  
->->->/etc/init.d/  
->->->/etc/hosts.allow  
->->->/etc/hosts.deny  
  
->Securing data with encryption  
* https://www.jesusninoc.com/02/28/seguridad-informatica-con-powershell/

->->Key Knowledge Areas:  
->->->Perform basic OpenSSH 2 client configuration and usage  
->->->Understand the role of OpenSSH 2 server host keys  
->->->Perform basic GnuPG configuration, usage and revocation  
->->->Understand SSH port tunnels (including X11 tunnels)  
->->Terms and Utilities:  
->->->ssh  
->->->ssh-keygen  
->->->ssh-agent  
->->->ssh-add  
->->->~/.ssh/id_rsa and id_rsa.pub  
->->->~/.ssh/id_dsa and id_dsa.pub  
->->->/etc/ssh/ssh_host_rsa_key and ssh_host_rsa_key.pub  
->->->/etc/ssh/ssh_host_dsa_key and ssh_host_dsa_key.pub  
->->->~/.ssh/authorized_keys  
->->->ssh_known_hosts  
->->->gpg  
->->->~/.gnupg/  
