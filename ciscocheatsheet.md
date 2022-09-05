## 1. Cisco IOS Command Hierarchy

The commands in Cisco IOS are hierarchical structured. Knowing the  difference between the different modes (and how to move across) will  help you configure, monitor, or troubleshoot a router easier.

There are currently eight modes in Cisco IOS commands.

| **Prompt**             | **Abbreviation** | **Description**                                              |
| ---------------------- | ---------------- | ------------------------------------------------------------ |
| Router>                | U                | User EXEC mode, is the first level of access.                |
| Router#                | P                | Privileged EXEC mode. The second level of access, accessible with the “enable” command. |
| Router(config)#        | G                | Configuration mode. Accessible only via the privileged EXEC mode. |
| Router(config-if)#     | I                | Interface mode. Level accessible via configuration mode.     |
| Router(config-router)# | R                | Routing mode. Level within configuration mode.               |
| Router(config-line)#   | L                | Line level (vty, tty, async). Accessed via the configuration mode |
| Router(config-vlan)#   | V                | Config-vlan, accessible via the global configuration mode.   |
| Switch(vlan)#          | VD               | Vlan database, accessible from the privileged EXEC mode.     |

 

### Commands To Move Between These Six Modes:

| **Command**                       | **Mode**   | **Description**                            |
| --------------------------------- | ---------- | ------------------------------------------ |
| enable                            | U          | Moves from User to Privileged mode.        |
| logout                            | U          | Exit User mode.                            |
| configure <terminal>              | P          | Moves from Privileged to Configure mode.   |
| disable                           | P          | Exit user mode.                            |
| Interface <interface description> | G          | Enter interface configuration mode.        |
| vlan vlan-id                      | G          | Moves to configure vlan mode.              |
| Vlan database                     | P          | Enter vlan database from Privilege mode.   |
| line                              | G          | Enter line from Global configuration mode. |
| exit end                          | G, R, L, V | return to previous mode.                   |

 

## 2. Fundamentals — Basic Configuration

The following are the fundamental Cisco IOS commands. These commands  give you the necessary base to move to more advanced and specific  commands.

| **Command**                                           | **Mode** | **Description**                                              |
| ----------------------------------------------------- | -------- | ------------------------------------------------------------ |
| show version                                          | U,P      | Display information about IOS and router.                    |
| show interfaces                                       | U,P      | Display physical attributes of the router’s interfaces.      |
| show ip route                                         | U,P      | Display the current state of the routing table.              |
| show access-lists                                     | P        | Display current configured ACLs and their contents.          |
| show ip interface brief                               | P        | Displays a summary of the status for each interface.         |
| show running-config                                   | P        | Display the current configuration.                           |
| show startup-config                                   | P        | Display the configuration at startup.                        |
| enable                                                | U        | Acces Privilege mode                                         |
| config terminal                                       | P        | Access Configuration mode.                                   |
| interface <int>                                       | G        | Enter interface configuration.                               |
| ip address <ip address> <mask>                        | I        | Assign an IP address to the specified interface.             |
| shutdown no shutdown                                  | I        | Turn off or turn on an interface. Use both to reset.         |
| description <name-string>                             | I        | Set a description to the interface.                          |
| show ip interface <type number>                       | U,P      | Displays the usability status of the protocols for the interfaces. |
| show running-config interface interface <slot/number> | P        | Displays the running configuration for a specific interface. |
| hostname <name>                                       | G        | Set a hostname for the Cisco device.                         |
| enable secret <password>                              | G        | Set an “enable” secret password.                             |
| copy running-config startup-config                    | P        | Saves the current (running) configuration in the startup configuration into the NVRAM. The command saves the configuration so  when the device reloads, it loads the latest configuration file. |
| copy startup-config running-config                    | P        | It saves (overwrites) the startup configuration into the running configuration. |
| copy from-location to-location                        | P        | It copies a file (or set of files) from a location to another location. |
| erase nvram                                           | G        | Delete the current startup configuration files. The command returns the device to its factory default. |
| reload                                                | G        | Reboot the device. The NVRAM will take the latest configuration. |
| erase startup-config                                  | G        | Erase the NVRAM filesystem. The command achieves the similar outcome as “erase nvram” |

 

## 3. Network Access

This section covers all popular Cisco’s network access protocols.  From how to configure and verify VLANs, trunks, to Layer 2 discovery  protocols like CDP and LLDP. We’ll also cover simple Etherchannel, Rapid PVST+ Spanning Tree Protocol configuration.

| **Command**                                    | **Mode**  | **Description**                                              |
| ---------------------------------------------- | --------- | ------------------------------------------------------------ |
| cdp run no cdp run                             | P         | The “cdp run” command enables Cisco Discovery Protocol. The “no cdp run” disables it. |
| show cdp                                       | P         | Display global information for CDP.                          |
| show cdp neighbors                             | P         | Display all CDP neighbors.                                   |
| lldp run no lldp run                           | P         | The “lldp run” command enables the LLDP Protocol. The “no lldp run” disables it. |
| show lldp                                      | P         | Displays global information for LLDP                         |
| show lldp neighbors                            | P         | Show all LLDP neighbors.                                     |
| show mac address-table                         | P         | Display all the MAC address entries in a table.              |
| spanning-tree mode rapid-pvst                  | G         | A global configuration command that configures the device for Rapid Per VLAN Spanning Tree protocol. |
| spanning-tree vlan <1-4094> priority <0-61440> | G         | Manually set the bridge priority per vlan.                   |
| spanning-tree vlan <1-4094> root primary       | G         | Make the switch the root of the SP.                          |
| no spanning-tree vlan <1-4094>                 | G         | Disable SP on the specific VLAN.                             |
| show spanning-tree summary                     | P         | Show a summary of all SP instances and ports.                |
| show spanning-tree detail                      | P         | Show detailed information of each port in the spanning-tree process. |
| show vlan                                      | P         | Lists each VLAN and all interfaces assigned to that VLAN. The output does not include trunks. |
| show vlan brief                                | P         | Displays vlan information in brief                           |
| show interfaces switchport                     | P         | Display configuration settings about all the switch port interfaces. |
| show interfaces trunk                          | P         | Display information about the operational trunks along with their VLANs. |
| vlan <1-4094>                                  | G         | Enter VLAN configuration mode and create a VLAN with an associated number ID. |
| name <name>                                    | V         | Within the VLAN configuration mode, assign a name to the VLAN |
| switchport mode access                         | I         | In the interface configuration mode, the command assigns the interface link type as an access link. |
| switchport access vlan <>                      | I         | Assign this interface to specific VLAN.                      |
| interface range < >                            | I – range | Access interface range configuration mode from Interface Configuration. |
| channel-group <number>                         | I – range | Assign the Etherchannel. Set the interface range to a channel group. |
| no switchport access vlan <>                   | I         | Remove VLAN assignment from interface. It returns to default VLAN 1 |
| show vtp status                                | P         | Display all vtp status                                       |
| vtp mode <server \| client \| transparent>     | G         | In the global configuration mode, set the device as server, client, or transparent vtp mode. |
| switchport mode trunk                          | I         | An interface configuration mode. Set the interface link type as a trunk link. |
| switchport trunk native vlan <>                | I         | Set native VLAN to a specific number.                        |
| switchport trunk allowed vlan <>               | I         | Allow specific VLANs on this trunk.                          |
| switchport trunk encapsulation dot1q           | I         | Sets the 802.1Q encapsulation on the trunk link.             |

 

 

## 4. IP Connectivity

This section includes some of the most simple yet useful ip  connectivity IOS commands. From displaying a routing table, creating  static, to default route. We also include dynamic routes with OSPF.

| **Command**                             | **Mode** | **Description**                                              |
| --------------------------------------- | -------- | ------------------------------------------------------------ |
| Show ip route                           | P        | Show the routing table.                                      |
| Show ip route ospf                      | P        | Show routes created by the OSPF protocol.                    |
| ip default-gateway <ip_address>         | G        | Set the default gateway for the router.                      |
| ip route <network> <mask> <next hop>    | G        | Create a new static route                                    |
| no ip route <network> <mask> <next hop> | G        | Remove a specific static route.                              |
| ip route 0.0.0.0 0.0.0.0 <nex thop>     | G        | Configure a default route                                    |
| router ospf <process ID>                | G        | Enable OSPF with an ID. The command will open the router configuration mode. |
| show ip ospf interface                  | P        | Display all the active OSPF interfaces                       |

 

## 5. IP Services

This section shows the common commands for configuring NAT, DHCP, and DNS services. It also includes simple and useful SNMP and Syslog  commands for monitoring and logging.

| **Command**                                                  | **Mode** | **Description**                                              |
| ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| ip nat <inside \| outside>                                   | I        | Specific whether the interface is the inside or outside of NAT. |
| ip nat inside source <ACL No.> <pool \| static IP> <overload> | G        | Configure dynamic NAT. It instructs the router to  translate all addresses identified by the ACL on the pool. To configure  Port Address Translation (PAT) use the “overload” at the end. |
| ip nat inside source static <local IP> <global IP>           | G        | Create a static NAT from inside (local IP) to outside (global IP) |
| ip nat outside source static <ACL No.> <pool \| static IP>   | G        | Create a static NAT from outside (ACL) to inside (IP pool)   |
| ntp peer <ip-address>                                        | G        | Configure the time by synchronizing it from an NTP server.   |
| ip dhcp excluded-address <first-ip-address> <last-ip-address> | G        | The IP addresses that the DHCP server should not assign to the DHCP client. |
| ip dhcp pool <name>                                          | G        | Enters the DHCP pool configuration mode and creates a new DHCP pool. |
| network <network ID> <mask>                                  | G – DHCP | Inside the DHCP configuration mode. Define the address pool for the DHCP server. |
| default-router <IP address>                                  | G – DHCP | Set the default gateway IP address for the DHCP clients.     |
| dns-server <IP address>                                      | G – DHCP | Set the DNS server IP address for the DHCP clients.          |
| ip helper-address <ip address>                               | I        | Turns an interface into a DHCP bridge. The interface redirects DHCP broadcast packets to a specific IP. |
| show ip dhcp pool                                            | P        | Display information about the DHCP pool                      |
| show ip dhcp binding                                         | P        | Display information about all the current DHCP bindings.     |
| ip dns server                                                | G        | Enable DNS service.                                          |
| ip domain-lookup                                             | G        | Enable domain lookup service. DNS client                     |
| ip name-server <IP address \| domain name>                   | G        | Set a public DNS server.                                     |
| snmp-server community <community-string> ro                  | G        | Enable SNMP Read-Only public community strings.              |
| snmp-server community <community-string> rw                  | G        | Enable SNMP Read-Only private community strings.             |
| snmp-server host <ip-address> version <community-string>     | G        | Specific the hosts to receive the SNMP traps                 |
| logging <ip address>                                         | G        | Determines the Syslog server to send log messages.           |
| logging trap level                                           | G        | Limit Syslog messages based on severity level                |
| show logging                                                 | P        | Shows the state logging (syslog). Shows the errors, events, and host addresses. It also shows SNMP configuration and activity. |
| terminal monitor                                             | P        | Enables debug and system’s error messages for the current terminal. |
| sh ip ssh                                                    | P        | Verify SSH access into the device.                           |

 

## 6. Security

In this section, we include the most basic AAA configuration commands for Cisco IOS. We’ll also include basic standard and extended ACLs and  port security configuration commands.

| **Command**                                                  | **Mode** | **Description**                                              |
| ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| enable secret <password>                                     | G        | Set an “enable” secret password. Enable secret passwords are hashed via the MD5 algorithm. |
| line vty 0 4                                                 | G        | A global configuration command to access the virtual  terminal configuration. VTY is a virtual port used to access the device  via SSH and Telnet. 0 4 to allow five simultaneous virtual connections |
| line console 0                                               | G        | A global configuration command to access the console configuration. |
| password <password>                                          | L        | Once in line mode, set a password for those remote sessions with the “password” command. |
| Login local                                                  |          | The authentication uses only locally configured credentials. |
| username <username> privilege <level> secret <password>      | G        | Require a username with a specific password. Also configure different levels of privilege. |
| service password-encryption                                  | G        | Makes the device encrypt all passwords saved on the configuration file. |
| crypto key generate rsa                                      | G        | Generate a set of RSA key pairs for your device. These keys may be used for remote access via SSH. |
| access-list                                                  | G        | Defined a numbered ACL                                       |
| ip access-list                                               | G        | Defined an IPv4 ACL.                                         |
| access-list access-list-number <deny \| permit}> source <source> [log] | G        | Create a standard ACL.                                       |
| access-list access-list-number <deny \| permit}>  protocol <> source <source [ports]>destination  <destination [ports]> [Options] | G        | Create an extended ACL.                                      |
| ip access-class <access-list-name> <in \| out>  no ip access-group <access-list-name> <in \| out> | L        | A line configuration command mode. It restricts incoming and outgoing connections to a particular vty line. Use “no” to remove  the restriction. |
| show ip access-list                                          | P        | Show all IPv4 ACLs                                           |
| switchport mode access                                       | I        | From the interface configuration mode, this command assigns the interface link type as an access link. |
| switchport port-security                                     | I        | enable dynamic port security on the specific interface.      |
| switchport port-security maximum <max value>                 | I        | Specify the maximum number of secure MAC addresses on the specific interface. |
| switchport port-security mac-address <mac-address \| sticky [mac-address]> | I        | Force a specific mac-address to the interface. Also use  the “sticky” option to make the interface remember the first mac-address connected to the interface. |
| switchport port-security violation <shutdown \| restrict \| protect> | I        | Define the action to be taken when a violation is detected on the port. |
| show port security                                           | P        | Display the port security configuration on each interface.   |

 

## 7. Troubleshooting Commands

In the final section of this cheat sheet we’ll include basic  troubleshooting commands. We already included some of these commands on  previous sections, but they are also very useful when it comes to  troubleshooting.

| **Command**                                                  | **Mode** | **Description**                                              |
| ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| ping <target IP \| hostname> <repeat Count [5]> <source [IP \| interface] | P        | Diagnose connectivity with extended ping. Check reachability, RRTs, and packet loss. |
| traceroute <target IP \| hostname><source [IP \| interface]  | P        | Use traceroute to diagnose connectivity on a hop by hop basis. |
| telnet                                                       | P        | Use Telnet to check for listening ports (1 to 65535) on a remote device. |
| show interface                                               | P        | Use this command to discover the physical attributes;  find duplex, link types, and speed mismatches. Both ends must match.  Also use this command to find errors. |
| speed <10 \| 100 \| 1000 \| auto>                            | I        | Set the speed of an interface. Or configure it as auto.      |
| duplex <auto \| full \| half>                                | I        | Set the interface duplex.                                    |
| show interface \| include fastethernet \| input errors       | P        | This command searches across all interfaces and outputs the ones that include input errors. |
| show ip interface                                            | P        | Use this command to discover the status for all the protocols on that interface. |
| shutdown no shutdown                                         | I        | Interface configuration mode. Restart an interface           |
| show ip route                                                | P        | This command is useful for determining the route of ip packets. |
| show cdp neighbors                                           | P        | Discover basic information about neighboring Cisco’s routers and switches |
| show mac address-table                                       | P        | Display the contents of the mac-address table.               |
| Show vlan Show vlan brief                                    | P        | Find vlan status and interfaces assigned to the vlans.       |
| show vtp status                                              | P        | Use this command to discover the current VTP mode of the device. |
| show interfaces trunk                                        | P        | Check the allowed VLANs on both ends of the trunk.           |
| show ip flow top-talkers                                     | P        | If Netflow is enabled, this command is very useful to troubleshoot top talkers. |