# Dynamic DNS on UniFi UDM/UDR When the Device Doesn't Know Its Public IP

## Overview

This tutorial explains how to configure Dynamic DNS (DDNS) on a UniFi UDM/UDR when the device does not automatically detect its public IP. This is particularly useful in scenarios where double NAT is present or the WAN interface does not directly obtain a public IP. 

## Prerequisites

- SSH access to your UniFi device.
- A Dynamic DNS provider (e.g., OVH, DynDNS, No-IP, etc.).
- Basic familiarity with Linux commands and system configuration.

## Steps

### Step 1: Remove Any Existing Dynamic DNS Configuration

If you have already defined a DDNS service through the UniFi UI, delete it. Any configuration made via the UI will automatically overwrite the custom `inadyn` configuration file.

### Step 2: Create a Custom `inadyn` Configuration File

Modify the default `inadyn` configuration file found in `/etc/inadyn.conf`.

Example configuration for an OVH DDNS service:

```sh
period   = 300
custom www.ovh.com:1 {
    hostname = "YOUR_DYDNS_URL"
    username = "YOUR_USERNAME"
    password = "YOUR_PASSWORD"
    ssl = true
    ddns-server = "www.ovh.com"
    ddns-path = "/nic/update?system=dyndns&hostname=%h&myip=%i"
    checkip-server = default
}
```

#### Explanation:

- `period = 300`: Checks the public IP every 300 seconds (5 minutes).
- `checkip-server = default`: Instructs `inadyn` to determine the public IP from a default online checkip service.
- If using another public service for IP checking, replace `checkip-server` accordingly.

### Step 3: Enable `inadyn` to Start on Boot

Run the following command to ensure the DDNS service starts on boot:

```sh
sudo systemctl enable inadyn.service
```

This creates a systemd service symlink, ensuring the service persists across reboots.

### Step 4: Reboot Your UniFi Device

```sh
sudo reboot
```

**Important:** Never redefine the DDNS service in the UniFi UI after this configuration, as it will overwrite `inadyn.conf`.

## How It Works

Once configured, `inadyn` follows this logic:

- It checks the public IP every 5 minutes using the `checkip-server`.
- If the detected IP differs from the previously cached IP, an update request is sent to the DDNS provider.
- No reliance on `eth0`, `WAN1`, or `WAN2`, ensuring compatibility with double NAT scenarios.

### Load Balancing Considerations

If load balancing is in place, `inadyn` will report the IP of the WAN interface used to access the checkip service. This could lead to frequent updates depending on WAN selection.

## Testing the Configuration

To manually test the DDNS update process:

```sh
/usr/sbin/inadyn -n -s -f -1 -l debug --foreground
```

This command runs `inadyn` in the foreground with verbose debugging enabled.

## Alternative Method: Custom IP Check Script

For greater control over IP detection, an alternative method involves using a custom script:

### Modified `inadyn.conf`:

```sh
period   = 300
custom www.ovh.com:1 {
    hostname = "YOUR_DYDNS_URL"
    username = "YOUR_USERNAME"
    password = "YOUR_PASSWORD"
    ssl = true
    ddns-server = "www.ovh.com"
    ddns-path = "/nic/update?system=dyndns&hostname=%h&myip=%i"
    checkip-command = /run/getwanip.sh
}
```

### Custom Script (`/run/getwanip.sh`):

Create the file `/run/getwanip.sh` and make it executable:

```sh
echo '#!/bin/sh
wget -qO- http://api.ipify.org' | sudo tee /run/getwanip.sh > /dev/null
sudo chmod +x /run/getwanip.sh
```

This script retrieves the public IP using `api.ipify.org` and returns it to `inadyn`.

## Conclusion

By following this guide, you can successfully configure Dynamic DNS on a UniFi UDM/UDR device even when it does not automatically detect its public IP. This approach ensures stable DDNS updates regardless of the network topology, avoiding issues caused by double NAT or dynamic WAN configurations.

## Credits

Thanks [enderwap](https://community.ui.com/user/enderwap/94a5ef6b-8861-40ed-9494-5750dc318e8c) for his [indadyn service trick](https://community.ui.com/questions/INADYN-additional-configuration-parameters-double-NAT-support-for-failover-support-for-external-IP-/071d86de-e6d6-4561-b6b7-fe7bd253df76) and [mrflop](https://community.ui.com/user/mrflop/ea332d33-428f-4ff2-a106-311b86ab531c) for its [alternate public IP check method and OVH config](https://community.ui.com/questions/OVH-dyndns-with-inadyn-on-udm-pro/0d02954c-318a-42ef-a9b5-6afa3e5b8df2) 