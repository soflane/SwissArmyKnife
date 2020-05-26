# SwissArmyKnife

This is just a cheatsheet.

[TOC]

# Utilities

## Network Tools

AdapterWatch (Interface lookup) : https://www.nirsoft.net/utils/awatch.html

Advanced IP Scanner : https://www.advanced-ip-scanner.com/

DHCP server : http://www.dhcpserver.de/cms/download/

Nmap with GUI (Graphical User Interface) : https://nmap.org/download.html

MobaXterm : 

Wireless Key Viewer : https://www.nirsoft.net/utils/wireless_key.html

Wireshark : https://www.wireshark.org/#download

XShell : https://www.netsarang.com/en/xshell-download/

Xftp : https://www.netsarang.com/en/xftp-download/











# Telephony related old shit

## Converting IVR prompts

3CX offers a tool that converts your audio prompts into this format :

- **Format**: WAV
- **Channel**: Mono
- **Bit rate**: 8 kHz
- **Sampling**: 16 bit

Windows : 

https://www.3cx.com/docs/converting-wav-file/

```bash
.\3CXConvertPrompts.exe [input-Folder] .\ffmpeg.exe
```

# Linux basic commands

Compress :

```bash
tar -czvf NEW_NAME.tar.gz FILE_OR_DIR
```

Uncompress : 

```bash
tar xvf mes0.tar	
```

How long a process has been running: 

```
ps -o etime= -p [PID]
```

## Network related

Get the public IP of a server:

Via Curl: 

```
curl ipecho.net/plain
```

When only DNS is authorized in the network:

```
dig TXT +short o-o.myaddr.l.google.com @ns1.google.com | awk -F'"' '{ print $2}'
```

Don't use traceroute, use mtr (A more beautifull traceroute via the mtr command)

```
mtr google.com
```



### Tracing

Cyclic trace that writes into 50 files of 64MB each, then starts rewriting in the first files

```
tcpdump -n -i eth0 -s 1500 -W 50 -C 64 -w '[Output Files]'
```





##### To sort : 

https://github.com/HoffmannTom/outlookbackupaddin

https://haveibeenpwned.com/



#### More: 

https://www.nirsoft.net/

https://framasoft.org/

https://www.kcsoftwares.com/