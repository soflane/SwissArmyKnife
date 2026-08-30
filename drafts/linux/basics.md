# Linux basics

> Draft: working notes that require review before publication.

## Host configuration

- Find and review a current method for automatic APT updates with email
  notifications; the original reference is no longer available.

## Package updates

Update a Debian-based system:

```bash
sudo apt update
sudo apt upgrade -y
sudo apt dist-upgrade
sudo do-release-upgrade
sudo apt autoremove
```

Update a Raspberry Pi OS system:

```bash
sudo apt update
sudo apt full-upgrade -y
```

## Process and service information

Identify the process running as PID 1, which usually reveals the service
manager:

```bash
ps -p 1
```

Check how long a process has been running:

```bash
ps -o etime= -p PID
```

## Archives

Create a compressed tar archive:

```bash
tar -czvf archive-name.tar.gz file-or-directory
```

Extract an archive:

```bash
tar -xvf archive-name.tar
```

## Network notes

Get the public IP address with curl:

```bash
curl https://ipecho.net/plain
```

Query the public IP through DNS when only DNS traffic is allowed:

```bash
dig TXT +short o-o.myaddr.l.google.com @ns1.google.com | awk -F'"' '{ print $2 }'
```

Use `mtr` for a continuously updated route and latency view:

```bash
mtr google.com
```

Capture packets into 50 rotating files of 64 MB each:

```bash
sudo tcpdump -n -i eth0 -s 1500 -W 50 -C 64 -w 'capture-file'
```
