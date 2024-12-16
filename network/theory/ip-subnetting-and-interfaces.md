---
description: Division of ip into segments and entry points
---

# IP Subnetting and interfaces

* **IP Subnetting Basics**
  * **Network ID:** Identifies the network portion of an IP address
  * **Host ID:** Identifies the device within a network
  * **Default Subnetting:** Standard division using default subnet masks
  * **Classful Subnetting:** Based on traditional IP address classes (A, B, C)
  * **Broadcast IP:** Special address for network-wide communication
*   **Classless Subnetting Concepts**

    * **VLSM:** Variable Length Subnet Mask for efficient IP space use

    Supports /8, /16, /24 Masks (A,B,C)

    * **CIDR:** Classless Inter-Domain Routing for flexible IP allocation

    Support range from /0-32 masks
*   **Interfaces and Subinterfaces**

    * **Interface:** A connection point between a device and a network. It's like a door that allows data to enter or exit a network device.
    * **Subinterface:** A virtual interface created within a physical interface. It's like having multiple doors within one main door, each leading to a different room (or in this case, network segment).

    Interfaces and subinterfaces help in:

    * Organizing network traffic
    * Separating different types of data
    * Creating virtual networks within a single physical connection

    They are crucial for efficient network management and segmentation.

    Examples of interfaces and subinterfaces:

    * **Physical Interfaces:**
      * Ethernet ports (e.g., FastEthernet0/0, GigabitEthernet1/0)
      * Serial ports (e.g., Serial0/0/0)
      * Wireless interfaces (e.g., Wireless0/0/0)
    * **Logical Interfaces:**
      * Loopback interfaces (e.g., Loopback0)
      * Tunnel interfaces (e.g., Tunnel0)
    * **Subinterfaces:**
      * Ethernet subinterfaces (e.g., FastEthernet0/0.10, where .10 is the subinterface number)
      * VLAN interfaces (e.g., VLAN10)

    These examples showcase how interfaces and subinterfaces are named and utilized in network devices. This naming convention enables flexible network configuration and effective segmentation.
