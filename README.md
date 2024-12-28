# SwissArmyKnife

**Your personal cheat sheet of useful programs, online services, and all-around geeky goodies!**

Hey there, fellow geeks (and the geek-curious)! 
This repository is a living collection of the most practical (and sometimes downright lifesaving) tools I’ve stumbled upon during my tech adventures. 
It’s split into categories so you can quickly find what you need—whether it’s a Windows disk utility, a Docker container, or a random online JSON viewer.

If you find this helpful, give it a star or share it around. If you have suggestions for new additions or better ways to structure it, feel free to open an issue or submit a pull request!

This is my carefully curated list of handy utilities, Docker containers, Proxmox tips, and more, all in one convenient place. If you find something new and awesome, feel free to add it (PRs welcome!).

------

## Table of Contents

- Windows Utilities
  - [Office 365 & Windows Tools](#office-365--windows-tools)
  - [Network Tools](#network-tools)
  - [Disk Management & USB Bootable Tools](#disk-management--usb-bootable-tools)
  - [System Utilities](#system-utilities)
  - [Windows Customization Tools](#windows-customization-tools)
  - [Development Tools](#development-tools)
  - [Media Tools](#media-tools)
  - [Text & Diagram Editors](#text--diagram-editors)
- [Mac Utilities](#mac-utilities)
- [Recovery & Diagnostics Live CDs](#recovery--diagnostics-live-cds)
- Online Tools
  - [Web Server Tools](#web-server-tools)
  - [Mailing Tools](#mailing-tools)
  - [Image Tools](#image-tools)
  - [Online Viewer Tools](#online-viewer-tools)
  - [Other Online Services](#other-online-services)
  - [Status Pages](#status-pages)
- [Cheatsheets](#cheatsheets)
- [Open Self-Hosted Projects](#open-self-hosted-projects)
- [Docker Projects](#docker-projects)
- [Proxmox Goodies](#proxmox-goodies)
- [Android](#android)
- [More at These Links](#more-at-these-links)
- [TODO](#todo)

---
---

## Windows Utilities

### Office 365 & Windows Tools

- **[NK2Edit](https://www.nirsoft.net/utils/outlook_nk2_edit.html)**
   Handy for recovering Outlook’s AutoComplete list.
- **[Import PST File to O365](https://www.youtube.com/watch?v=8DhOTQPzFyU)**
   Tutorial for Microsoft’s network upload method.
- **[Outlook Backup Add-in](https://github.com/HoffmannTom/outlookbackupaddin)**
   Automates Outlook PST backups.

### Network Tools

- **[AdapterWatch (Nirsoft)](https://www.nirsoft.net/utils/awatch.html)**
   Shows network interface details.
- **[SMTP Test Tool](https://github.com/georgjf/SMTPtool)**
   SMTP server tester app.
- **[Advanced IP Scanner](https://www.advanced-ip-scanner.com/)**
   Fast and simple IP scanner.
- **[Advanced Port Scanner](https://www.advanced-port-scanner.com/fr/)**
   Scan open ports on your network.
- **[DHCP Server](http://www.dhcpserver.de/cms/download/)**
   DHCP & TFTP server in one.
- **[Zenmap (Nmap GUI)](https://nmap.org/download.html)**
   Nmap with a friendly UI.
- **[MobaXterm](https://mobaxterm.mobatek.net/download.html)**
   All-in-one remote computing toolbox (SSH, SFTP, X11, etc.).
- **[Wireless Key Viewer (Nirsoft)](https://www.nirsoft.net/utils/wireless_key.html)**
   Recovers saved Wi-Fi credentials.
- **[Wireshark](https://www.wireshark.org/#download)**
   Network protocol analyzer for sniffing traffic.
- **[XShell](https://www.netsarang.com/en/xshell-download/)**
   Feature-rich SSH client.
- **[Xftp](https://www.netsarang.com/en/xftp-download/)**
   FTP/SFTP client from the XShell suite.
- **[Homedale](https://www.the-sz.com/products/homedale/)**
   Wi-Fi analyzer and monitoring tool.

### Disk Management & USB Bootable Tools

- **[Macrium Reflect](https://www.macrium.com/reflectfree)**
   Reliable backup and cloning tool (free version available).
- **[SD Card Formatter](https://www.sdcard.org/downloads/formatter/eula_windows/)**
   Official SD Association formatting utility.
- **[Rufus](https://rufus.ie/)**
   Versatile USB flasher for ISO/IMG files.
- **[BalenaEtcher](https://www.balena.io/etcher/)**
   A simple and user-friendly USB flasher for creating bootable USBs from ISO, IMG, or ZIP files.
- **[WinToUSB](https://www.easyuefi.com/wintousb/)**
   Create Windows-To-Go drives in a snap.
- **[Windows 10 ISO Downloader](https://www.microsoft.com/fr-fr/software-download/windows10)**
   Official Microsoft Windows ISO page.
- **[Minitool Partition Wizard](https://www.partitionwizard.com/download.html)**
   Manage partitions with an easy interface.

### Hardware diagnostic & Testing tools

- **[HWInfo](https://www.hwinfo.com/download/)**
  Hardware info and diagnostics.
- **[CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/)**
  Monitors HDD/SSD health by tracking SMART values, temperatures, and more.
- **[CrystalDiskMark](https://crystalmark.info/en/software/crystaldiskmark/)**
  Benchmarking tool to measure the sequential and random read/write speeds of storage drives.
- **[System Examiner](https://systemexaminer.com/)**
  Generates detailed system reports on Windows, useful for diagnostics and tech support.

### System Utilities

- **[Ninite](https://ninite.com/)**
   Auto-install multiple popular applications at once.
- ~~**[CCleaner](https://www.ccleaner.com/fr-fr/ccleaner/download)**
   Cleanup and optimization.~~
- **[BleachBit](https://www.bleachbit.org/download)**
   A free and open-source system cleaner that safely removes unnecessary files and frees up disk space (great CCleaner alternative).
   It has custom cleaners that you can enable into settings
- [**Bulk Crap Uninstaller**](https://www.bcuninstaller.com/)
   A powerful, bulk uninstaller tool that helps you remove multiple programs (and all their remnants) in one go.
- **[SpeedFan](http://www.speedfan.fr/)**
   Monitor and adjust fan speeds/temps.
- **[Folder Size](http://www.folder-size.com/)**
   Visualize and manage folder sizes on Windows.
- **[WindowGrid](http://windowgrid.net/)**
   Advanced window management tool.
- **[SimpleWall](https://github.com/henrypp/simplewall)**
   Lightweight firewall control tool that helps manage and block unwanted outgoing or incoming connections.
- [**Windows Privacy for Dashboard (WPD)**](https://wpd.app/)
   Although not recently updated, its a good start to disable some telemetry settings of Windows 
- **[Switch Off](https://www.clubic.com/telechargement-en-cours/9272-0-switch-off.html)**
   Scheduled shutdown/reboot/sleep.

### Windows Customization Tools

- **[OEM Info Tool](https://www.trishtech.com/oem-info-tool/)**
   Easily change or view OEM branding info on Windows.

### Development Tools

- **[WAMP](https://www.wampserver.com/#download-wrapper)**
   Local server environment (Windows, Apache, MySQL, PHP).

### Media Tools

- **[Converseen](https://converseen.fasterland.net/)**
   A cross platform Batch Image Converter and Resizer Tool
- **[DigiCamControl](http://digicamcontrol.com/download)**
   Control and automate DSLR cameras from Windows.
- **[MP3Tag](https://www.mp3tag.de/en/download.html)**
   Tag editor for music files.
- **[MakeMKV](https://www.makemkv.com/)**
   Rip DVDs/Blu-rays to MKV files.
- **[ID Photo Studio](https://www.kcsoftwares.com/?idps)**
   Easy ID-photo creation.
- **[Image Resizer](https://www.bricelam.net/ImageResizer/)**
   Batch resize images with Explorer integration.

### Text & Diagram Editors

- **[Diagrams.net (formerly Draw.io)](https://app.diagrams.net/)**
   Create flowcharts, diagrams, and more in your browser.
- **[Typora](https://typora.io/)**
  A clean Markdown editor with live preview (not free, but great UX).

---
---

## Mac Utilities

- **[EtreCheck](https://www.etrecheck.com/fr/index.html)**
   Comprehensive diagnostic and troubleshooting tool for macOS.
   
- **[Silent Knight](https://eclecticlight.co/lockrattler-systhist/)**    
  A macOS security and system integrity checker from Eclectic Light. 
  
- **[Coconut Battery](https://www.coconut-flavour.com/coconutbattery/)**    
  Monitors the health of your Mac’s battery (and iOS devices when plugged in).
  
- **[Homebrew](https://brew.sh/)** 
  Homebrew installs [the stuff you need](https://formulae.brew.sh/formula/) that Apple (or your Linux system) didn’t.
  
   

---
---

## Recovery & Diagnostics Live CDs

When your system is on the brink, these might just save your day!

- **[MediCat](https://gbatemp.net/threads/medicat-usb-a-multiboot-linux-usb-for-pc-repair.361577/)**
   A multiboot USB solution.
- **[Malwarebytes](https://fr.malwarebytes.com/mwb-download/thankyou/)**
   Detect and remove malware.
- **[Hiren’s BootCD PE (UEFI)](https://www.hirensbootcd.org/)**
- **[Hiren’s BootCD 15.2 (Legacy BIOS)](https://www.hirensbootcd.org/hbcd-v152/)**
- **[WinPE 11-10 Sergei Strelec](https://sergeistrelec.name/)**

---
---


## Online Tools

### Web Server Tools

- **[Cipher List](https://cipherlist.eu/)**
   Best practices for SSL/TLS ciphers on Apache/Nginx/Lighttpd.
- **[EcoIndex](http://www.ecoindex.fr/)**
   Measures the eco-score of a webpage (environmental impact).
- **[NginxConfig](https://www.digitalocean.com/community/tools/nginx)**
   Easily generate an Nginx configuration.

### Mailing Tools

- **[Email Blacklist Tester (Unspam mail)](https://unspam.email/)**
  A service that let you send a mail to their address and see the result of your mail infrastructure (Domain and mail body check)
- **[Email Blacklist Tester (Mail Tester)](https://www.mail-tester.com/)**
   Check your domain/mail reputation.

### Image Tools

- **[BRIAA's AI-Powered Background Removal](https://huggingface.co/spaces/briaai/BRIA-RMBG-1.4)**
   Drop in an image, get a crisp cut-out.

### Online Viewer Tools

- **[Online JSON Viewer](https://jsonformatter.org/json-parser)**
- **[Online XML Viewer](https://codebeautify.org/xmlviewer)**

### Other Online Services

- **[Have I Been Pwned](https://haveibeenpwned.com/)**
- **[Deseat.me](https://www.deseat.me/)**
   Helps clean up old accounts you might’ve forgotten.
- **[Draw.io (again, it’s that good)](https://app.diagrams.net/)**
- **[Online PC Builder (PCPartPicker)](https://pcpartpicker.com/list/)**

### Status Pages

- **[OVH Planned Work](http://travaux.ovh.net/)**
- **[Google Apps Status](https://www.google.com/appsstatus#hl=fr&v=status)**
- **[Apple System Status](https://www.apple.com/support/systemstatus/)**

------

## Cheatsheets

- **[Devhints](https://devhints.io/)**
   Massive collection of quick references ([Bash](https://devhints.io/bash), [MySQL](https://devhints.io/mysql), etc.).
- **[Git Guide](http://rogerdudler.github.io/git-guide/)**

------

## Open Self-Hosted Projects

- **[Wolweb (Wake-on-LAN)](https://github.com/unikiteam/wolweb)**
   Turn your devices on remotely using a web interface.

------

## Docker Projects

- **[Wolweb Docker Image](https://github.com/unikiteam/wolweb)**
   Run Wolweb in a container.

*(More Docker ideas coming soon!)*

------

## Proxmox Goodies

- **[Proxmox VE Community Scripts](https://community-scripts.github.io/ProxmoxVE/)**
   An awesome collection of scripts to enhance your Proxmox workflow.

*(Stay tuned for more Proxmox tips!)*

------

## Android

- **[Vanced](https://vancedapp.com/)**
   A modded YouTube client with extra features ([GitHub](https://github.com/YTVanced/)).
- **[Online SMS Backup Viewer](https://mattj.io/sms-backup-reader-2/main)**
   View backups from [SMS Backup & Restore](https://play.google.com/store/apps/details?id=com.riteshsahu.SMSBackupRestore) online.

------

## More at These Links

- **[NirSoft Windows Tools](https://www.nirsoft.net/)**
- **[Framasoft](https://framasoft.org/)**
- **[KC Software Windows Tools](https://www.kcsoftwares.com/)**
- **[Portable Apps.io](https://portapps.io/)**

------

## TO Add

- Install Kali on WSL using [Win-Kex](https://www.kali.org/docs/wsl/win-kex/)
- **MkvMake**
- [**System Examiner**](https://systemexaminer.com/)
- **VirtualBox**
- marktext
- **Unified Remote**
- **Mi Home Toolkit**
  A companion tool for Xiaomi’s Mi Home ecosystem—used to manage and automate smart home devices, firmware updates, and some Tweaking.
- **winget-autoupdate**
  A utility to automatically update packages installed via Windows Package Manager (winget). Can be scheduled to run via Task Scheduler.
- **UpdateHub**
  A centralized update solution that helps manage and deploy software updates across Windows systems.
- **uniGet**
  A universal package manager for Windows that supports winget, Chocolatey, and Scoop repositories in one place.
- Feel free to suggest any additions or open issues/PRs for improvements!

**Happy exploring!**
