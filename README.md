# Assignment 4 Overview

This repository contains configuration files for six network switches. Below is a brief overview of the setup:

## Switch Configurations

### Switch1
- **Hostname**: Switch1  
- **Description**: Acts as a core switch with multiple VLANs configured for different network segments.  
- **Key Features**:  
  - Multiple DHCP pools for VLANs 2-14 and 16.  
  - OSPF routing for VLAN networks.  
  - Port-channels configured for trunking with VLANs 2-14 and 16.  

### Switch2
- **Hostname**: Switch2  
- **Description**: A distribution switch with trunking enabled for VLANs 2-14 and 16.  
- **Key Features**:  
  - Port-channels configured for trunking.  
  - Spanning-tree mode set to PVST.  

### Switch3
- **Hostname**: Switch3  
- **Description**: Another distribution switch with similar trunking configurations.  
- **Key Features**:  
  - Port-channels for trunking with VLANs 2-14 and 16.  
  - Spanning-tree mode set to PVST.  

### Switch4
- **Hostname**: Switch4  
- **Description**: A distribution switch with trunking configurations.  
- **Key Features**:  
  - Port-channels for trunking with VLANs 2-14 and 16.  
  - Spanning-tree mode set to PVST.  

### FloorDistributer1A
- **Hostname**: FloorDistributer1A  
- **Description**: A floor distribution switch with access and trunk ports.  
- **Key Features**:  
  - Access ports for hosts, wireless APs, and technical clients.  
  - Port-channels for trunking with VLANs 2-14 and 16.  
  - Spanning-tree guard root enabled on access ports.  

### FloorDistributer1B
- **Hostname**: FloorDistributer1B  
- **Description**: Another floor distribution switch with similar configurations.  
- **Key Features**:  
  - Access ports for hosts, infrastructure services, and technical clients.  
  - Port-channels for trunking with VLANs 2-14 and 16.  
  - Port-security enabled on access ports. 

## Summary
This setup represents a typical enterprise network with core, distribution, and access layers. The core switch (Switch1) handles inter-VLAN routing and DHCP, while the distribution and floor switches manage access and trunking for various network segments. The image helps visualize the physical connections between these switches.