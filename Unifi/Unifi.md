## Enable port forward on management web UI 

Follow [this](https://artofwifi.net/blog/how-to-access-the-unifi-controller-by-wan-ip-or-hostname-on-a-udm-pro)

But change the destination rule with the following : 

- destination type : ip address
- address : [address of the gateway]
- port : 443 (web gateway management port)

then add a normal port forwarding rule in "routing" -> "port forwarding" -> then create a new entry 

wan port : chosen forwarded port

forward IP address : the ip of the gateway

fowrard port : 443

recommandation to restrict ip to the one you want to permit, as exposing the gateway management is not very secure 



## Enable Port Forwarding on UniFi Management Web UI

### Overview

This guide explains how to enable port forwarding on the UniFi Management Web UI while ensuring secure access. The original method is detailed in [this tutorial](https://artofwifi.net/blog/how-to-access-the-unifi-controller-by-wan-ip-or-hostname-on-a-udm-pro). However, we will modify the destination rule to improve security and reliability.

### Step 1: Modify the Destination Rule

To allow remote access to the UniFi Controller, follow these steps:

1. **Modify firewall settings** to allow connections from external IPs.
2. **Create a destination NAT rule** in the UniFi web UI:
   - **Destination Type**: IP Address
   - **Address**: [Your Gateway’s IP Address]
   - **Port**: 443 (Web Gateway Management Port)
   - **Protocol**: TCP
   - **Translate Port**: 443

### Step 2: Add a Port Forwarding Rule

Navigate to **Routing** → **Port Forwarding**, then create a new entry with the following values:

- **WAN Port**: Choose a port to forward (e.g., 8443 or any preferred port).
- **Forward IP Address**: The IP address of the gateway.
- **Forward Port**: 443
- **Protocol**: TCP
- **Restrict Source IP**: Only allow access from trusted IPs for security reasons.

### Step 3: Update Firewall Rules

To restrict access and improve security, add a firewall rule:

1. **Go to Settings → Security → Firewall.**
2. **Create a new rule under WAN LOCAL.**
3. **Set Rule Action**: Allow.
4. **Set Protocol**: TCP/UDP.
5. **Set Source IP Restriction**: Enter allowed IPs.
6. **Set Destination Port**: 443 (or the port used in Step 2).
7. **Apply the rule.**

### Step 4: Security Considerations

Exposing the gateway management interface can be a security risk. It is **strongly recommended** to:

- Restrict access to specific trusted IPs using firewall rules.
- Use a VPN instead of direct port forwarding whenever possible.
- Regularly monitor logs for unauthorized access attempts.

By following this guide, you will enable external access to the UniFi Management UI while minimizing security risks.





























## Use Dynamic DNS behind NAT 

To use Dynamic DNS on unify UDM/UDR/... when the device doesn't know his public IP : 



SSH into the device thanks to [enderwap](https://community.ui.com/user/enderwap/94a5ef6b-8861-40ed-9494-5750dc318e8c) for his [trick](https://community.ui.com/questions/INADYN-additional-configuration-parameters-double-NAT-support-for-failover-support-for-external-IP-/071d86de-e6d6-4561-b6b7-fe7bd253df76): 

Step 1 - delete any dynamic dns from Unifi UI. Nothing should be defined, since if is defined, it generates a new inadyn conf file.

Step 2 - create your own config file - by altering original inadyn config file from /etc: Use something similar - in my case ddns provider - dyndns:

root@UniFiNeXt-GenGatewayPRO:/etc# cat inadyn.conf



```
period   = 300
custom www.ovh.com:1 {
    hostname = "YOUR_DYDNS_URL"
    username = "YOUR_USERNAME"
    password = "YOUR_PASSWORD"
    ssl = true
    ddns-server = "www.ovh.com"
    ddns-path = "/nic/update?system=dyndns&hostname=%h&myip=%i""
    checkip-server = default
}
```





Pay attention to have checkip-server = default - this will instruct inadyn to ignore allocate ip's on your eth (wan1 or wan 2) and check what is your ip reported by the default site/service of inadyn. here you can use any other public service that reports back your ip for standard dyndns clients.



Step 3 - enable the native service to run on boot:

root@UniFiNeXt-GenGatewayPRO:/etc/init.d# sudo systemctl enable inadyn.service

Created symlink /etc/systemd/system/multi-user.target.wants/inadyn.service → /lib/systemd/system/inadyn.service.

Step 4 - reboot :) NEVER define any service in GUI. in that case inadyn.conf will be overwritten.



Now you will have a dynamic dns service that will not care about interface, about double NAT, about anything. Logic will be always:

inadyn checks every 300 seconds (the interval defined in conf file -> period = 300 the response from checkip server. If is different then the ip cached by inadyn in its cache will trigger update of your provider. Else, nothing will happen. Simple. No eth0 WAN 1 or WAN 2, plain real exit ip.

In case of load balancing, will report the ip of the WAN used to access checkip site. So.... this will trigger multiple updates. In that case, most probably, you are not interested about this functionality,

To test it easyly:

```
/usr/sbin/inadyn -n -s -f -1 -l debug --foreground
```



Alternate [method](https://community.ui.com/questions/OVH-dyndns-with-inadyn-on-udm-pro/0d02954c-318a-42ef-a9b5-6afa3e5b8df2) for IP checking : 


```
period   = 300
custom www.ovh.com:1 {
    hostname = "YOUR_DYDNS_URL"
    username = "YOUR_USERNAME"
    password = "YOUR_PASSWORD"
    ssl = true
    ddns-server = "www.ovh.com"
    ddns-path = "/nic/update?system=dyndns&hostname=%h&myip=%i""
    checkip-command = /run/getwanip.sh
}
```



This script at `/run/getwanip.sh` must return the IP that your want to record.

```
# cat /run/getwanip.sh
#!/bin/sh
wget -qO- http://api.ipify.org
```