---
description: >-
  Consists of 7 Layers - Application, Presentation, Session, Transport, Network,
  Data-link and Physical
---

# OSI Model

*   Application Layer

    Definition: Provides network services directly to end-users or applications.

    Application: Web browsers, email clients, file transfer protocols (FTP).

    Name for Data: Data
*   Presentation Layer

    Definition: Translates data between the application layer and the network format.

    Application: Data encryption, compression, and format conversion.

    Name for Data: Data
*   Session Layer

    Definition: Establishes, manages, and terminates sessions between applications.

    Application: Authentication, authorization, and session restoration.

    Name for Data: Data
*   Transport Layer

    Definition: Provides reliable data transfer between end systems.

    Application: TCP (connection-oriented) and UDP (connectionless) protocols.

    Names for Data: Segment (TCP), Datagram (UDP)
*   Network Layer

    Definition: Handles routing and forwarding of data packets between different networks.

    Application: IP addressing, routing protocols (e.g., OSPF, BGP).

    Name for Data: Packets
*   Data Link Layer

    Definition: Provides reliable data transfer between two directly connected nodes.

    Application: Ethernet, Wi-Fi, error detection and correction.

    Name for Data: Frames
*   Physical Layer

    Definition: Defines the physical and electrical characteristics of the network.

    Application: Network cables, connectors, signal transmission, and hardware specifications.

## Layer 1 - Physical

#### What Physical Layer does:

* Defines a physically connected medium (ex: two computer connected via a copper cable, wifi, fibre) or more computer connected to a HUB
* Defines Standards for transmitting onto the medium
* Defines Standards for receiving from the medium (ex: For wifi, what antennas to use)

#### What Physical Layer doesn’t do:

* Doesn’t provide access control (every device processes the same data sent)
* No uniquely identified devices
* No method to “device to device” communication in case of more that 2 devices
* Prone to errors and collision (two devices communicating at the same time on a copper cable)

## Layer 2 - Data-link

* Identifiable devices (MAC Address)
* Device to device communication
* Media access control (CSMA/CD Carrier sense multiple access and Collision detection)
* Unicast 1→1 communication
* Broadcast 1→All communication
* Switches - Like Hubs with capability of understanding Frames and has a MAC address table that populates over time to redirect to the right destination

### Frame:

Preamble (56 bits) and Start frame delimiter (SFD) - 8 bits Destination Mac address

Source MAC address

EtherType (16 bits) (ex: IP)

Payload - 46-1500 Bytes

FCS (Checksum) - 32 bits

## L1/2

### Equipment and tagging

* Hub - Layer 1 - broadcast every message to every connected device
* Switch - Layer 2/3 - Has the ability to connect multiple devices implementing Routing

### VLAN -

Access ports and trunk ports are crucial for efficient network segmentation: • Access ports or Untagged ports: Connect end devices to a single VLAN • Trunk ports or Tagged ports: Carry multiple VLANs between switches, allowing for network scalability and efficient use of physical connections adding a “802.1Q” tag to the frame that has the infos about the VLAN it comes from (Default or Native VLAN is the default tag)

### Static vs Dynamic VLAN

Static VLAN:

* Manually configured by network administrators
* Port-based: Each switch port is assigned to a specific VLAN
* More secure and predictable
* Less flexible for network changes

Dynamic VLAN:

* Automatically assigns devices to VLANs based on criteria like MAC address
* More flexible for mobile devices and changing network environments
* Requires more complex setup and management

### Layer 3 - Network

> _“Routing is the dynamic process of finding the optimal path for transmitting data across a network.”_

#### How does it work ?

* When a router receives a packet, it accesses its routing table and searches for the best path.
* The router forwards the packet along the optimal route identified.
* A metric called "hops" counts the number of routers a packet passes through across the network.
* Routing occurs either statically (manually configured) or dynamically (automatically learned through routing protocols).

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

#### Types of Routing

#### 1. Default Routing

* **Advantages:** Simple configuration, low resource usage
* **Disadvantages:** Limited path options, potential for routing loops

#### 2. Static Routing

* **Advantages:** Increased security, reduced bandwidth usage
* **Disadvantages:** Manual configuration, doesn't adapt to changes

#### 3. Dynamic Routing

* **Advantages:** Automatic adaptation, scalability
* **Disadvantages:** Higher resource consumption, potential security risks

Networks often combine these methods to balance efficiency, security, and adaptability.

### Common Metrics used

*   Bandwidth

    Bandwidth in routing decisions:

    * Maximum data transfer rate of a network link/path
    * Higher bandwidth often preferred for efficient data transmission
    * Used by routers to choose high-capacity paths
    * Not the sole factor; latency and reliability also matter
*   Delay

    Time for a packet to travel from source to destination. Critical for real-time applications. Affected by distance, congestion, and processing time.
*   Hop Count

    Number of intermediate devices data passes through. Lower count often means a more direct route. Simple to calculate but doesn't account for link quality.
*   Cost

    Abstract value combining factors like bandwidth, delay, and reliability. Lower cost preferred. Can be adjusted by admins and change dynamically.

### Routing Protocols

#### Interior Gateway Protocols -

*   Distance Vector Protocols

    Simpler routing approach:

    * Routers share entire routing tables with neighbors
    * Best path calculated based on hop count
    * Examples: RIP (update every 30 seconds), EIGRP
    * Simpler but slower convergence in large networks
*   Link State Protocols

    Link State protocols build a complete map of the network topology:

    * Routers exchange information about their direct connections
    * Each router independently calculates the best path to all destinations
    * Examples include OSPF (Open Shortest Path First) and IS-IS
    * More efficient than Distance Vector, but require more processing power
*   Hybrid Routing Protocols

    Combines Link State and Distance Vector features:

    * Balances advantages of both approaches
    * Uses different methods for near and far routes
    * Example: BGP (Border Gateway Protocol), EIGRP
    * Offers flexibility for complex networks

#### Exterior Gateway Protocols -

*   Exterior Gateway Protocols

    Used for routing between different autonomous systems:

    * Designed for large-scale internet routing
    * Handle routing policies and decisions between ISPs
    * Main example: BGP (Border Gateway Protocol)
    * Focus on path selection based on policies rather than just metrics
*   What is an Autonomous System?

    An Autonomous System (AS) is like a big chunk of the internet:

    * It's a large network run by one company or organization
    * Think of it as a country on the internet, with its own rules
    * It has a special number to identify it, like a phone number for the network
    * It connects to other big networks to form the whole internet
    * Examples are networks owned by big internet providers or large companies

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
