# SwissArmyKnife

This is just a cheatsheet with usefull programs or online services. Feel free to check!

- [Windows Utilities](#windows-utilities)
  * [Network Tools](#network-tools)
  * [Disk management](#disk-management)
  * [To sort](#to-sort)
- [Recovery & Diagnostics Live CDs](#recovery---diagnostics-live-cds)
- [Online Tools](#online-tools)
  * [Status pages](#status-pages)
- [Cheatcheets](#cheatcheets)
- [Linux basic commands](#linux-basic-commands)
  * [Network related](#network-related)
    + [Tracing](#tracing)
- [Android](#android)
- [More at theses links](#more-at-theses-links)


# Windows Utilities

## Network Tools

- [AdapterWatch (Nirsoft)](https://www.nirsoft.net/utils/awatch.html) 
  Utility to lookup the interfaces 
- [Advanced IP Scanner](https://www.advanced-ip-scanner.com/) 
- [Advanced Port Scanner](https://www.advanced-port-scanner.com/fr/) 
- [DHCP server](http://www.dhcpserver.de/cms/download/) 
  A DHCP & TFTP server 
- [Zenmap](https://nmap.org/download.html ) 
  Nmap with GUI (Graphical User Interface)
- [MobaXterm](https://mobaxterm.mobatek.net/download.html) 
  SSH client 
- [Wireless Key Viewer (Nirsoft)](https://www.nirsoft.net/utils/wireless_key.html) 
  Recover saved WiFi passwords
- [Wireshark](https://www.wireshark.org/#download) 
  Network packet capture
- [XShell](https://www.netsarang.com/en/xshell-download/) 
  SSH Client
- [Xftp](https://www.netsarang.com/en/xftp-download/)
  FTP/SFTP Client 



## Disk management

- [Macrium reflect](https://www.macrium.com/reflectfree) 

- [SD Card Formatter](https://www.sdcard.org/downloads/formatter/eula_windows/) 
- [Rufus](https://rufus.ie/) 
  A bootable USB flasher for your ISO/IMG files with advanced options for specific use cases. 
- [Etcher](https://www.balena.io/etcher/) 
  A one-click USB flasher.
- [WinToUSB](https://www.easyuefi.com/wintousb/) 
  Creation of Windows-To-Go drives
- [Windows 10 ISO downloader](https://www.microsoft.com/fr-fr/software-download/windows10) 


## To sort

- [Switch Off](https://www.clubic.com/telechargement-en-cours/9272-0-switch-off.html) 
  Sleep/shutdown/reboot timer for windows
- [Windows Grid](http://windowgrid.net/) 
- [HWInfo](https://www.hwinfo.com/download/) 
- [DigiCamControl](http://digicamcontrol.com/download) 
- [MP3Tag](https://www.mp3tag.de/en/download.html) 
- [OEM Info Tool](https://www.trishtech.com/oem-info-tool/)
- [MakeMkv](https://www.makemkv.com/) 
  Rip DVDs Into MKV files
- [Ninite](https://ninite.com/) 
- [WAMP](https://www.wampserver.com/#download-wrapper)
- [Folder Size](http://www.folder-size.com/) 
- [CCleaner](https://www.ccleaner.com/fr-fr/ccleaner/download) 
- [SpeedFan](http://www.speedfan.fr/) 
- [Outlook backup addin](https://github.com/HoffmannTom/outlookbackupaddin)

- [ID Photo Studio](https://www.kcsoftwares.com/?idps) 

- [Image resizer](https://www.bricelam.net/ImageResizer/) 



# Recovery & Diagnostics Live CDs 

- [Medicat](https://gbatemp.net/threads/medicat-usb-a-multiboot-linux-usb-for-pc-repair.361577/) 
- [MalwareByte](https://fr.malwarebytes.com/mwb-download/thankyou/) 
- 

# Online Tools

- [Cipher list](https://cipherlist.eu/) 
  Strong Ciphers for Apache, nginx and Lighttpd
- [Have I Been pwned ](https://haveibeenpwned.com/)
- [Deseat.me](https://www.deseat.me/) 
- [Draw.io](https://app.diagrams.net/)
- [EcoIndex](http://www.ecoindex.fr/) 
- [NginxConfig](https://www.digitalocean.com/community/tools/nginx)
- [Online JSON Viewer](https://jsonformatter.org/json-parser)
- [Online XML viewer ](https://codebeautify.org/xmlviewer)
- [Online PC Builder](https://pcpartpicker.com/list/) 
- [Email blacklist tester](https://unspam.email/) 
  A service that let you send a mail to their address and see the result of your mail infrastructure (Domain and mail body check)



## Status pages 

- [OVH Planned work](http://travaux.ovh.net/) 
- [Google Status](https://www.google.com/appsstatus#hl=fr&v=status) 
- [Apple Status](https://www.apple.com/support/systemstatus/)



# Cheatcheets

- [Devhints](https://devhints.io/) 
  Plenty of cheatsheets ([Bash](https://devhints.io/bash), [MySQL](https://devhints.io/mysql), ...)
- [Git](http://rogerdudler.github.io/git-guide/) 



# Linux basic commands

Know which service manager is installed 

```bash
ps -p 1
```

Example of what you get : 

```bash
    PID TTY          TIME CMD
      1 ?        00:16:16 systemd
```

Compress :

```bash
tar -czvf NEW_NAME.tar.gz FILE_OR_DIR
```

Uncompress : 

```bash
tar xvf mes0.tar	
```

How long a process has been running: 

```bash
ps -o etime= -p [PID]
```

## Network related

Get the public IP of a server:

Via Curl: 

```bash
curl ipecho.net/plain
```

When only DNS is authorized in the network:

```
dig TXT +short o-o.myaddr.l.google.com @ns1.google.com | awk -F'"' '{ print $2}'
```

Don't use traceroute, use mtr (A more beautifull traceroute via the mtr command)

```bash
mtr google.com
```



### Tracing

Cyclic trace that writes into 50 files of 64MB each, then starts rewriting in the first files

```bash
tcpdump -n -i eth0 -s 1500 -W 50 -C 64 -w '[Output Files]'
```







# Android	

- [Vanced](https://vancedapp.com/) 
  Youtube Vanced ([Git](https://github.com/YTVanced/))
- [Online SMS backup viewer](https://mattj.io/sms-backup-reader-2/main)
  An online tool to view backups made by [SMS Backup & Restore](https://play.google.com/store/apps/details?id=com.riteshsahu.SMSBackupRestore)



# More at theses links 

- [NirSoft Windows tools](https://www.nirsoft.net/)
- [Framasoft](https://framasoft.org/)
- [KC Software Windows tools](https://www.kcsoftwares.com/)
- [Portable apps.io](https://portapps.io/)

# TODO
MkvMake

Virtualbox

Typora

Unified remote



# Communication 
Whatsapp 

telegram 

signal
