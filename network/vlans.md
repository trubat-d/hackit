---
description: Virtual Local area network
---

# VLANs

Allows to divide a network access into multiple independent networks without having implement more hardware switches, dividing a switch into multiple mini-switches “virtually”

This technology is particularly useful in large organizations or educational institutions where different departments or groups require separate network segments for security or management purposes. VLANs offer several benefits, including improved network performance, enhanced security, and greater flexibility in network design and management.

#### VLAN Usage

* Separation: Divides network traffic
* Restriction: prevents access to data even in the same company for example in a separate department.
* Provision: Using only one physical switch, you can manage multiple services in Internet service providers / Data center or other facility.
* Isolation: Separates network segments, enhancing security and reducing congestion.

#### Subnets

* Definition: A subnet is a logical subdivision of an IP network.
* Purpose: Subnets organize and manage network traffic within each VLAN.
* Benefits:
  * Efficient use of IP addresses
  * Better control over network resources
* Relationship with VLANs:
  * Subnets work in conjunction with VLANs for improved network structure and security
  * VLANs operate at Layer 2 of the OSI model
  * Subnets function at Layer 3 of the OSI model
* Complementary benefits: Enhance network segmentation and management

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

#### Subnets, IP Addresses, Masks, and CIDR

Subnets are closely related to IP addresses, subnet masks, and CIDR notation. Understanding these concepts is crucial for effective network management:

* **IP Addresses:** Unique identifiers for devices on a network, consisting of 32 bits (IPv4) or 128 bits (IPv6).
* **Subnet Masks:** Used to determine which portion of an IP address belongs to the network and which to the host.
* **CIDR (Classless Inter-Domain Routing):** A compact method of representing subnet masks using a forward slash and a number (e.g., /24).

How they work together:

* IP addresses are divided into network and host portions using subnet masks.
* CIDR notation simplifies subnet representation (e.g., 192.168.1.0/24 represents a subnet with 256 possible addresses).
* Subnetting allows for efficient use of IP address space and improved network organization.

Example: A subnet with mask 255.255.255.0 (or /24 in CIDR) applied to the IP 192.168.1.0 creates a network with addresses ranging from 192.168.1.1 to 192.168.1.254, with 192.168.1.0 as the network address and 192.168.1.255 as the broadcast address.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
