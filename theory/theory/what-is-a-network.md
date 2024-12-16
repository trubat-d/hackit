---
description: >-
  Networking refers to the ability to connect multiple devices, enabling data
  exchange between them.
---

# What is a network ?

These devices can range from computers and smartphones to routers and servers. The network infrastructure allows for seamless communication and resource sharing between connected devices. This interconnectivity forms the backbone of modern digital communication and information exchange.

#### Components of network identification system

The dynamic one:

* IP Address (Internet Protocol)
  * Built with 4 octets: 0.0.0.0 - 255.255.255.255
  * Defines a device identification in public or private networks
  * Some ranges are assigned for private and public ip
  * Is used in layer 3

The static one:

* MAC address (Media access Control)
  * Unique identifier assigned to network interface cards (NICs)
  * Consists of 48 bits, typically represented as 12 hexadecimal digits
  * Used in layer 2 of the OSI model for device-to-device communication within a local network

#### Ping

* Uses ICMP (Internet Control Message Protocol)
* Measures time for data packets sent between devices
* Helps diagnose network connectivity issues and latency problems
* Can be used to determine if a remote host is reachable and responsive

## Network Administration

It involves organization, installation and troubleshooting of devices in a network Some of the task it involves are:

* Network configuration: Setting up and configuring network devices such as routers, switches, and firewalls.
* User management: Creating and managing user accounts, permissions, and access controls.
* Security implementation: Implementing and maintaining network security measures to protect against threats and vulnerabilities.
* Detecting and Preventing Exploits for network protection

### What does a Network administrator do in a Network?

*   Design

    Network design is a crucial responsibility of a network administrator. It involves planning the overall structure and topology of the network to ensure optimal performance, scalability, and security. This includes determining the appropriate hardware and software components, network architecture, and protocols to meet the organization's current and future needs.
*   Set up (Hardware) and Configuration (Software)

    This involves the physical setup of network hardware components such as routers, switches, and servers, as well as the software configuration of these devices. Key aspects include:

    * Installing and connecting network devices
    * Configuring network protocols and services
    * Setting up network security measures
*   Expansion

    This involves adding new components or expanding the network's capabilities to meet growing demands. Some examples include:

    * Adding new network segments or subnets
    * Integrating new technologies or protocols
    * Scaling up infrastructure to accommodate more users or devices
    * Create new VLANs
* Maintaining the Network
  * Troubleshooting issues
  * Managing Hosts
  * Services management - emails, printer, sys-admin
  * Implementing and managing secure access controls

## Troubleshooting

Act of identifying and resolving a problem linked to communications in a network

Example of a network problem:

A user reports that they cannot access the company's internal website from their workstation. Upon investigation, it is discovered that:

* The user's computer has a valid IP address
* Other network resources (like shared drives) are accessible
* The internal website is functioning correctly for other users
* The problem persists after restarting the user's computer

This scenario could indicate issues such as:

* Misconfigured DNS settings on the user's machine
* A problem with the network switch port the user is connected to
* Firewall rules blocking access for this specific user

Troubleshooting steps would involve checking these potential causes systematically to identify and resolve the issue.

Idea of troubleshooting is testing failure points from the easiest to check:

* Hardware and cables

to more advanced ones:

* Tools like ipconfig for checking gateways, router’s IP, network connection between computers and to routers
* Tools like ping and tracert for verifying reachability of host on IP network.
* DNS checks with nslookup for checking Time outs and Server failures
* Contacting ISP (Internet service provider) or checking outages
* Check for malware and Viruses protection
* Examine the logs of network activity

### Network troubleshooting steps

* Check for network Issues
* Install hardware and apps
* Tracks and improve network efficiency
* Planning of the growth of the network
* Managing Documentation for network
* Ensure compliance with the policies and legal regulations
* Secure network against threats

## Local Area Network (LAN) Topologies, Subnetting, ARP, and DHCP

### 1. LAN Topologies

Local Area Networks (LANs) can be arranged in various topologies, each with its own advantages and disadvantages:

*   **Bus Topology:** All devices are connected to a single cable, called the bus or backbone.

    In this topology, data is transmitted along the main cable and received by all devices on the network. However, only the intended recipient processes the data. While simple and cost-effective, bus topologies can suffer from performance issues in high-traffic scenarios and are vulnerable to cable failures.
*   **Star Topology:** All devices are connected to a central hub or switch.

    In this topology, each device has a dedicated connection to the central hub or switch. This arrangement offers improved performance and easier troubleshooting compared to bus topology. If one connection fails, it doesn't affect the entire network. However, star topologies can be more expensive to implement due to the need for more cable and the central device.
*   **Ring Topology:** Devices are connected in a closed loop configuration.

    In this topology, data travels in one direction around the ring, passing through each device. Each device acts as a repeater, boosting the signal before passing it on. Ring topologies offer fair access to all devices and perform well under heavy network loads. However, a single device or connection failure can disrupt the entire network, unless a redundant ring is implemented.
*   **Mesh Topology:** Every device is connected to every other device in the network.

    This topology offers high redundancy and fault tolerance, as data can take multiple paths to reach its destination. It's extremely reliable but can be complex and expensive to implement, especially in large networks. Mesh topologies are often used in critical environments where network uptime is crucial.

### 2. Subnetting

Subnetting is the practice of dividing a network into two or more networks. Key points include:

* Allows for more efficient use of IP addresses
* Improves network performance by reducing traffic
* Enhances security by isolating network segments
* Subnet mask determines the network and host portions of an IP address

### 3. Address Resolution Protocol (ARP)

ARP is a protocol used to map IP addresses to MAC addresses in a LAN:

* Essential for communication between devices on the same network
* Maintains an ARP cache to store recent mappings
* Uses broadcast messages to find unknown MAC addresses
* **ARP Request Example:**
  1. Device A (IP: 192.168.1.5) wants to communicate with Device B (IP: 192.168.1.10).
  2. Device A checks its ARP cache for Device B's MAC address but doesn't find it.
  3. Device A broadcasts an ARP request: "Who has IP 192.168.1.10? Tell 192.168.1.5"
  4. Device B receives the request and responds with its MAC address.
  5. Device A updates its ARP cache with Device B's IP-MAC mapping.
  6. Communication can now proceed using the resolved MAC address.

### 4. Dynamic Host Configuration Protocol (DHCP)

DHCP automates the assignment of IP addresses and other network configuration parameters:

* Reduces administrative overhead in large networks
* Prevents IP address conflicts
* Can be configured to assign static IP addresses to specific devices
*   **DHCP DORA Process Example:**

    The DHCP DORA process consists of four steps: Discover, Offer, Request, and Acknowledge. Here's a simple example:

    1. Discover: A new device joins the network and broadcasts a DHCP Discover message.
    2. Offer: The DHCP server responds with a DHCP Offer, suggesting an IP address and other network parameters.
    3. Request: The device sends a DHCP Request, accepting the offered IP address.
    4. Acknowledge: The DHCP server sends a DHCP Acknowledge, confirming the IP address assignment.

    This process ensures that devices can automatically obtain network configuration without manual intervention.

Understanding these concepts is crucial for effective network administration and troubleshooting in LAN environments.
