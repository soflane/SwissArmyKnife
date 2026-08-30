# Configure Dynamic DNS on a UniFi gateway behind NAT

> Configure `inadyn` to discover the externally visible address when a UniFi
> UDM or UDR does not receive the public IP directly on its WAN interface.

## Prerequisites

- SSH access to the UniFi gateway.
- Dynamic DNS credentials from a provider such as OVH, DynDNS, or No-IP.
- A double-NAT or similar setup in which the gateway cannot read its public IP
  from the WAN interface.
- A backup of the current gateway configuration.

> [!WARNING]
> This method edits system files outside the UniFi interface. Firmware updates
> may overwrite the configuration or change service behavior. Recheck the file
> and service after every gateway update.

## Steps

### 1. Remove the UI-managed Dynamic DNS entry

Delete any Dynamic DNS service configured in the UniFi interface. A UI-managed
entry can regenerate `inadyn.conf` and overwrite the custom configuration.

### 2. Configure `inadyn`

Connect to the gateway over SSH and edit `/etc/inadyn.conf`. The following OVH
example asks the default check-IP service for the public address:

```text
period = 300
custom www.ovh.com:1 {
    hostname = "YOUR_DYDNS_HOSTNAME"
    username = "YOUR_USERNAME"
    password = "YOUR_PASSWORD"
    ssl = true
    ddns-server = "www.ovh.com"
    ddns-path = "/nic/update?system=dyndns&hostname=%h&myip=%i"
    checkip-server = default
}
```

Replace every placeholder with the provider values. Do not commit the populated
file or paste its credentials into an issue.

`period = 300` checks every five minutes. `checkip-server = default` prevents
the update from relying on the address assigned directly to WAN1 or WAN2.

### 3. Enable and restart the service

```bash
sudo systemctl enable inadyn.service
sudo systemctl restart inadyn.service
```

Do not recreate the Dynamic DNS entry in the UniFi interface afterward.

### 4. Optional custom IP check

For explicit control over the external-IP service, replace
`checkip-server = default` with:

```text
checkip-command = /run/getwanip.sh
```

The script must output only the public IP address:

```sh
#!/bin/sh
wget -qO- https://api.ipify.org
```

Make the script executable before restarting `inadyn`:

```bash
sudo chmod +x /run/getwanip.sh
```

The `/run` directory is normally volatile. If this alternative is used, add a
supported boot-time mechanism that recreates the script after each restart.

## Verify

Run `inadyn` once in the foreground with debug output:

```bash
sudo /usr/sbin/inadyn -n -s -f -1 -l debug --foreground
```

Then confirm that:

- the detected address matches the external public IP;
- the Dynamic DNS record resolves to that address;
- the service is active after a reboot;
- `/etc/inadyn.conf` still contains the custom configuration.

With WAN load balancing, the reported address may alternate according to the
interface used to reach the check-IP service and trigger repeated updates.

## References

- [Community discussion: `inadyn` parameters for double NAT](https://community.ui.com/questions/INADYN-additional-configuration-parameters-double-NAT-support-for-failover-support-for-external-IP-/071d86de-e6d6-4561-b6b7-fe7bd253df76)
- [Community discussion: OVH Dynamic DNS with `inadyn`](https://community.ui.com/questions/OVH-dyndns-with-inadyn-on-udm-pro/0d02954c-318a-42ef-a9b5-6afa3e5b8df2)
