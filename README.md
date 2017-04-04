# Invoke-HostRecon
Invoke-HostRecon runs a number of checks on a system to help provide situational awareness to a penetration tester during the reconnaissance phase of an engagement. It gathers information about the local system, users, and domain information. It does not use any 'net', 'ipconfig', 'whoami', 'netstat', or other system commands to help avoid detection. 

For more info check out this blog post: http://www.blackhillsinfosec.com/?p=5824

## Situational Awareness
### Invoke-HostRecon gets the following information from the system without running system tools like 'net', 'ipconfig', etc.
```
Current Hostname
IP Information
Current Username
Current Domain Name
All Local Users
Local Admins Group
Netstat Information
DNS Cache Information
Shares
Scheduled Tasks
Web Proxy Information
Process Listing
AntiVirus Information
Firewall Status
Local Admin Password Solution (LAPS)
Domain Password Policy
Domain Admins Group Members
Domain Controllers
Checks for Common Security Products
```
## Common Security Product Detection
Invoke-HostRecon attempts to enumerate common security products on the system including AV, IDS, AppWhitelisting, Behavioral Analysis, etc.

## Egress Filter Check
Invoke-HostRecon also includes a functionality for assessing egress filtering from the system. The -Portscan flag can be passed to initiate an outbound portscan against allports.exposed to help determine open ports allowed through an egress firewall. (Credit for the Portscan module goes to Joff Thyer)

### Usage Example
This command will run a number of checks on the local system including the retrieval of local system information (netstat, common security products, scheduled tasks, local admins group, LAPS, etc), and domain information (Domain Admins group, DC's, password policy). Additionally, it will perform an outbound portscan on the top 128 ports to allports.exposed to assist in determining any ports that might be allowed outbound for C2 communications.
``` PowerShell
Invoke-HostRecon -Portscan -TopPorts 128
```
