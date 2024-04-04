# Cradlepoint Router Setup and Security Guide

This comprehensive guide outlines the steps for configuring a Cradlepoint router, including IP configuration, disabling WAN pings, managing remote access, setting up port forwarding, changing DNS settings, and managing user accounts.

## Initial Setup

### Setting the IP Address

1. **Access the Cradlepoint Interface**:
   - Connect to the router and open a web browser.
   - Enter the default IP address to access the Cradlepoint configuration page.
2. **Configure the IP Address**:
   - Navigate to the network settings.
   - Set the IP address to `192.client.project.site`.
   - Example: For project number 123-0001 at Plant 2, set IP to `192.123.1.2`.

## Securing the Router

1. Navigate to  `System > Administration > Remote Admin`:

   - Disable WAN Pings

   - Allow Remote Web Administration
   - Set up Remote Access Firewall using the following information

### Restricting Remote Access

1. Navigate to `Security > Zone Firewall > Remote Access Restriction`:
   - Specify which IPs are allowed to access the router remotely.
   - At a minimum, allow access from `45.32.196.108`, `104.225.141.163`.

### Configuring Port Forwarding

1. Navigate to Port Forwarding Settings:
   - Access `Security > Zone Firewall > Port Forward`.
2. Add New Port Forward Rule:
   - Click to add a new port forward rule.
   - Enter port `502` for Modbus devices and `102` for Siemens devices.
   - Specify the local computer address (e.g., PLC or HMI).

### Restricting Port Forwarding

1. Set Up Filter Policies:
   - Navigate to `Security > Zone Firewall > Filter Policies`.
   - Add a new policy named "Server Access".
2. Add Allow Rule:
   - Within "Server Access", add a new allow rule.
   - Allow IPv4 addresses from `45.32.192.108`, `104.225.141.163`, and any static IPs associated with the project.
3. Add Deny Rule:
   - Add a rule to deny all other IPs.
4. Configure Zone Forwarding:
   - Go to `Security > Zone Firewall > Zone Forwarding`.
   - Change the policy on `Primary LAN Zone` to `WAN Zone` to the "Server Access" policy that was just created.

### Changing DNS Settings

1. Navigate to DNS Settings:
   - Go to `Networking > DNS Servers`.
2. Set DNS Servers:
   - Set the primary DNS to `45.32.196.108`.
   - Set the secondary DNS to `94.140.14.15`.
3. Force DNS Requests to Router:
   - Enable an option to force all DNS requests through the router, if available.

## User Account Management

### Creating a New User Account

1. Add New User Account:
   - Go to the user management section.
   - Create a new user account named `bgdscada`.
2. Generate and Save Password:
   - Use KeePassXC to generate a strong password.
   - Save this password securely in KeePassXC.

### Changing the Default Admin Password

1. Change or Remove Default Admin Account:
   - After confirming the `bgdscada` account is working, change the default admin password.
   - If possible, remove or disable the default admin account for enhanced security.

## Final Steps

- Ensure all settings are correctly applied.
- Test the configurations to confirm functionality.
- Document any changes and configurations for future reference.

------

Regularly review and update the router settings to maintain security and functionality. Ensure that these configurations align with your organization's security policies and network requirements.