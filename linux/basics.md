# Linux basics

## Host configurations

[Automatic APT updates (with mail notifications)](https://gist.github.com/roybotnik/b0ec2eda2bc625e19eaf)



## Commands

Update all, Debian based 

```shell
sudo apt update ; sudo apt upgrade -y ; sudo apt dist-upgrade ; sudo do-release-upgrade ; sudo apt autoremove
```

Update RPI

```shell
sudo apt update ; sudo apt -y dist-upgrade ; sudo apt full-upgrade 

```

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



