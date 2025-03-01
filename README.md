# Network Switch Configuration Overview

This document provides an overview of the configuration and functionality of the network switches in the provided files. The switches are part of a network infrastructure designed to support multiple VLANs, provide DHCP services, ensure network security, and facilitate communication between different network segments.

## Switches Overview

### Switch1
- **Hostname**: Switch1
- **Functionality**:
  - **DHCP Services**: Excludes specific IP addresses from the DHCP pool and defines DHCP pools for VLANs 2-16.
  - **Spanning Tree Protocol (STP)**: Configured with Rapid PVST mode and a priority of 4096 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to other switches (Switch2, Switch3, Switch4, FloorDistributer1A, and FloorDistributer1B).
  - **VLAN Interfaces**: IP addresses are assigned to VLAN interfaces to act as gateways for end devices.
  - **OSPF**: Configured for routing between VLANs.
  - **SSH**: Enabled for secure remote access.

### Switch2
- **Hostname**: Switch2
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with PVST mode and a priority of 8192 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1, Switch3, and Switch4.
  - **VLAN Interface**: IP address assigned to VLAN16 for remote connectivity.
  - **SSH**: Enabled for secure remote access.

### Switch3
- **Hostname**: Switch3
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with PVST mode and a priority of 12288 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1, Switch2, and Switch4.
  - **VLAN Interface**: IP address assigned to VLAN16 for remote connectivity.
  - **SSH**: Enabled for secure remote access.

### Switch4
- **Hostname**: Switch4
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with PVST mode and a priority of 16384 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1, Switch2, and Switch3.
  - **VLAN Interface**: IP address assigned to VLAN16 for remote connectivity.
  - **SSH**: Enabled for secure remote access.

### FloorDistributer1A
- **Hostname**: FloorDistributer1A
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with Rapid PVST mode and a priority of 32768 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1 and FloorDistributer1B.
  - **Access Ports**: Configured for specific VLANs (e.g., VLAN 3 for hosts, VLAN 6 for technical clients, VLAN 13 for wireless APs).
  - **Port Security**: Implemented on certain ports to restrict access based on MAC addresses.
  - **SSH**: Enabled for secure remote access.

### FloorDistributer1B
- **Hostname**: FloorDistributer1B
- **Functionality**:
  - **Spanning Tree Protocol (STP)**: Configured with Rapid PVST mode and a priority of 32768 for VLANs 1-4094.
  - **Port Channels**: Configured for trunking with VLANs 2-16 and native VLAN 999. Port channels are set up for connections to Switch1 and FloorDistributer1A.
  - **Access Ports**: Configured for specific VLANs (e.g., VLAN 3 for hosts, VLAN 6 for technical clients, VLAN 12 for security cameras).
  - **Port Security**: Implemented on certain ports to restrict access based on MAC addresses.
  - **SSH**: Enabled for secure remote access.

## Common Features Across Switches
- **VLAN Configuration**: All switches are configured to support multiple VLANs, with VLAN 999 as the native VLAN for trunk ports.
- **Spanning Tree Protocol**: Each switch is configured with STP to prevent network loops, with varying priorities to ensure a stable network topology.
- **Port Channels**: Used to aggregate bandwidth and provide redundancy between switches.
- **SSH Access**: Enabled on all switches for secure remote management.
- **Port Security**: Implemented on access ports to enhance network security by restricting access based on MAC addresses.
