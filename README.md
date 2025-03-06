# Network Switches for Electric Petrol site.

This readme provides an overview of the configuration of the network switches in the Switch listings and the gns3 project. The switches are part of a network infrastructure designed to support multiple VLANs, provide DHCP services, ensure network security, and facilitate communication between different network segments.

## Switches Overview
### Switch1
- **Functionality**:
  - **DHCP Services**: Excludes specific IP addresses from the DHCP pool and defines DHCP pools for VLANs 2-16.
  - **Spanning Tree Protocol (STP)**: Configured with Rapid PVST mode and a priority of 4096 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to other switches (Switch2, Switch3, Switch4, FloorDistributer1A, and FloorDistributer1B).
  - **VLAN Interfaces**: IP addresses are assigned to VLAN interfaces to act as gateways for end devices.
  - **OSPF**: Configured for routing between VLANs.
  - **SSH**: Enabled for secure remote access.

### Switch2
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with PVST mode and a priority of 8192 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1, Switch3, and Switch4.
  - **VLAN Interface**: IP address assigned to VLAN16 for remote connectivity.
  - **SSH**: Enabled for secure remote access.

### Switch3
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with PVST mode and a priority of 12288 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1, Switch2, and Switch4.
  - **VLAN Interface**: IP address assigned to VLAN16 for remote connectivity.
  - **SSH**: Enabled for secure remote access.

### Switch4
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with PVST mode and a priority of 16384 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1, Switch2, and Switch3.
  - **VLAN Interface**: IP address assigned to VLAN16 for remote connectivity.
  - **SSH**: Enabled for secure remote access.

### FloorDistributer1A
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with Rapid PVST mode and a priority of 32768 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1 and FloorDistributer1B.
  - **Access Ports**: Configured for specific VLANs (e.g., VLAN 3 for hosts, VLAN 6 for technical clients, VLAN 13 for wireless APs to show as examples.).
  - **Port Security**: Implemented on certain ports to restrict access based on MAC addresses.
  - **SSH**: Enabled for secure remote access.

### FloorDistributer1B
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with Rapid PVST mode and a priority of 32768 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1 and FloorDistributer1A.
  - **Access Ports**: Configured for specific VLANs (e.g., VLAN 3 for hosts, VLAN 6 for technical clients, VLAN 12 for security cameras to show as examples.).
  - **Port Security**: Implemented on certain ports to restrict access based on MAC addresses.
  - **SSH**: Enabled for secure remote access.

## Commonality between switches.
- **VLAN Configuration**: All switches are configured to support multiple VLANs, with VLAN 999 as the native VLAN for trunk ports.
- **Spanning Tree Protocol**: Each switch is configured with STP to prevent network loops, with varying priorities to ensure a stable network topology.
- **Port Channels**: Used to aggregate bandwidth and provide redundancy between switches.
- **SSH Access**: All switches have SSH enabled for remote management.
- **Port Security**: Implemented on access ports to enhance network security by restricting access based on MAC addresses.

## Extra notes.
 - The one thing that is not set up on this network yet are ACLs or access control lists. These would be implemented to filter network traffic between vlans (i.e vlan 3 can't communicate with vlan 5 but can with 6, etc).
 - This network was configured without an ISP in mind or internet connectivity.
 - This site was configured with four main distriubtion layer switches, one core switch (which doubles as a distribution layer switch for cost saving measures, and two access layer switches (no ip addressing). The switches are all connected via etherchannel for redundancy. These are shown in the forms of port channels 1,2,20,25,30,35, and 40.
 - Spanning tree is also enabled on each switch and its access ports to allow for redundancy.
 - DHCP was configured on a network switch instead of a router (which was the initial idea until it was pointed out that the switches for gns3 were layer 3 capable) to allow for ip address assignment.
 - port-security was configured on the access ports so any new device connecting to a pre-existing connection has the protect command applied upon violation.
 - a simple VTP domain has been set up (cisco is the domain and password if needed for demonstration purposes). the vlans were then allowed across the trunk ports to allow each network switch to see each vlan.
 - A new natvie vlan was set up, 999. This is done so as to deter any potential attackers to the network and stopping them from guessing vlan 1 as being the native vlan.
 - A discard VLAN was set up., 1000. This was done to put unused ports into so that they are not in the native vlan by default which could compromise the security aspect of the network.
 - An attempt was made to remove vlan 1 completely but the default could not be removed from the switch network.
 - FloorDistributer1A and FloorDistributer1B, while they have been configured with spanning tree redundancy like the distribution layer switches, they will only apply when all four other main switches (1,2,3,4) are offline. Access layer switches should not be the root bridge where possible.
 - All 6 switches have been configured with Secure Shell (SSH) to allow remote management from the office or anywhere in the network by the IT department.
 - 
