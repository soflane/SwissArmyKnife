# Reach the UniFi management UI through port forwarding

> Document direct WAN access to a UniFi gateway management interface when a VPN
> or UniFi's supported remote-management options cannot be used.

## Prerequisites

- Administrative access to the UniFi Network application.
- A fixed external source IP or a source IP group that can be allow-listed.
- A tested recovery path in case the firewall change blocks management access.

> [!CAUTION]
> Publishing a gateway management interface on the Internet increases the risk
> of credential attacks and exploitation. Prefer a VPN or a supported UniFi
> remote-access method. If direct forwarding is unavoidable, restrict it to
> trusted source IP addresses and never expose it to the entire Internet.

Menu and rule names can vary between UniFi Network versions. Review the pending
changes before applying them.

## Steps

### 1. Define the destination

Create or adjust the destination rule for the gateway management service:

- **Destination type:** IP address
- **Address:** the gateway's internal IP address
- **Destination port:** `443`
- **Protocol:** `TCP`
- **Translated port:** `443`
- **Source:** the trusted external IP or source IP group

### 2. Add the port-forwarding rule

Open **Routing > Port Forwarding** and create a rule with these values:

- **WAN port:** a deliberately selected external port
- **Forward IP address:** the gateway's internal IP address
- **Forward port:** `443`
- **Protocol:** `TCP`
- **Source restriction:** the trusted external IP or source IP group

### 3. Review the firewall policy

Confirm that the applicable WAN-local firewall policy allows the selected
source to reach the forwarded service and denies other sources. Do not create a
broad allow rule for all WAN traffic.

## Verify

1. From an allow-listed external connection, open the selected WAN port and
   confirm that the expected UniFi login page appears.
2. From a different, non-allow-listed connection, confirm that the port is not
   reachable.
3. Review gateway logs for unexpected connection attempts.
4. Remove the forwarding and firewall rules when direct access is no longer
   required.

## References

- [Art of WiFi: access a UniFi controller by WAN IP or hostname](https://artofwifi.net/blog/how-to-access-the-unifi-controller-by-wan-ip-or-hostname-on-a-udm-pro)
