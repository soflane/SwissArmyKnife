## Enable Port Forwarding on UniFi Management Web UI

### Overview

This guide explains how to enable port forwarding on the UniFi Management Web UI while ensuring secure access. The original method is detailed in [this tutorial](https://artofwifi.net/blog/how-to-access-the-unifi-controller-by-wan-ip-or-hostname-on-a-udm-pro). However, we will modify the destination rule to improve security and reliability.

### Step 1: Modify the Destination Rule

To allow remote access to the UniFi Controller, follow these steps:

1. **Log in to your UniFi device** via SSH.

2. **Modify firewall settings** to allow connections from external IPs.

3. Create a destination NAT rule

    in the UniFi web UI:

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

### Step 3 (Optional but Strongly Recommended): Restrict Access to Specific IPs

For enhanced security, restrict access to specific trusted IPs:

1. **Edit the Destination NAT rule** created in Step 1.
2. **Set the Source IP Group** (if Destination Type is set to "Object").
3. **Add a new group of authorized public IPs** that are allowed to access the management interface.

### Step 4: Security Considerations

Exposing the gateway management interface can be a security risk. It is **strongly recommended** to:

- Restrict access to specific trusted IPs using firewall rules.
- Use a VPN instead of direct port forwarding whenever possible.
- Regularly monitor logs for unauthorized access attempts.

By following this guide, you will enable external access to the UniFi Management UI while minimizing security risks.