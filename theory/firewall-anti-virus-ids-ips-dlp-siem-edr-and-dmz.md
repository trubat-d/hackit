# Firewall, Anti-virus, IDS, IPS, DLP, SIEM, EDR and DMZ

### Firewalls

First line of defense of a network capable of filtering traffic

> _“Protects data by blocking packets destined for specific software ports, filtering traffic based on IP Addresses or blocking packets for specific apps”_

They can be :

* Network-Based: Operates at network level filtering data as it goes from the internet to the computer network, it regulates the data flow across the entier network
* Host-based: Installed on a single device, it provides personalized defense and is configured for the individual machine

Firewalls work based on rule sets specifying what to accept and what to drop.

* Stateless Firewalls or (Packet-filtering Firewalls): Layer 3/4 - most basic type, it it inspects protocol, soure and destination ip, and ports. Efficient for high-speed networks.
* Circuit-Level Gateway: Layer 5 - They can provide capabilities such as verifying three-way-handshakes
* Stateful Firewalls - Layer 3/4 - Keeps track of established TCP sessions, can drop packets outside TCP sessions already established.
* Proxy Firewall/ Application Firewall/Web App Firewall: Layer 7- Able to read the data inside of the packets which makes it capable to analyse payloads and injections. It does not work for every protocol. Can decrypt SSL/TLS data
* Next-Generation Firewall (NGFW) - Layer 2-7 - Has app awarness and control., can decrypt SSL/TLS data, comes with an IPS
* Cloud Firewall or Firewall as a Service (FWaaS) - Similar to NGFW but in the cloudl.

### Linux Firewalls:

* iptables : based on Netfilter, its the first and most widely used in linux distributions.
* nftables : successor to iptables, enhanced packet filtering and NAT capabilities
* firewalld : comes with predefined rule sets , it works differently from the others.
* ufw (uncomplicated firewall): Layer over iptables that facilitates the usage by giving the possibility to generate rules in an easier way

### Anti-virus

Types:

* Signature-Based: Detects malware by its hash/checksum, taking appropriate actions as removing and blocking it.
* Behavior-Based: Monitors the unusual user behavior to identify threats based on patterns defending against new Threats

### IDS (Intrusion Detection System)

* Can be Signature or Anomaly-Based monitoring and analyzing network events for incidents and breaches
* Is located inside the network receiving mirrored copies of traffic.
* Does not take action to prevent threat only used for detection

### IPS (Intrusion Prevention System)

* Detects and stops detected Incidents, Reports and Logs to SoC (Security Operation Center)

### DLP (Data Loss Prevention)

* Its a set of technologies used to monitor, identify and block unwanted transfers via various channels likes mail, text messaging, file-sharing.

### SIEM (Security information and Event Management)

* Collects and Logs data from various IT systems
* Detect, centralize and report network and security events
* Alert based on rules and signatures for potential threats

### EDR (Enpoint detection and Response)

* Real time monitoring of Systems Endpoints tracking lifecycle of attacks enabling organizations to respond promptly

### DMZ (Demilitarized Zone)

* Located between local and private networks
* Contain services fully exposed to the internet
* Is isolated using firewall
* enable untrusted networks to access resources while keeping the private network secure

### Honeypot

* Security mechanism, virtual trap to attackers. Allows analysts to study the patterns of attacks.

Types:

Email, Spam, malware, crawler

***

## Secure network Architecture

#### Network Segmentation

BYOD - Bring your Own Device

#### Common Secure Network Architecture

Zones:

* External - All devices and entities outside of our network
* DMZ - Separate untrusted networks or devices from internal resources
* Trusted - Internal networks or devices. A device may be placed in the trusted zone if there is no confidential or sensitive info
* Restricted - Any high-risk servers or databases
* Management - Any devices or services dedicated to network or other device management
* Audit - Devices dedicated to security or monitoring

#### Network Security Policies and Controls

QoS (Quality of Service) - 802.11e

ACE - Access Control Entry

Zone-pair are direction-based and stateful policy that will enforce the traffic in sigle direction per vlan

Solutions to some attacks: DHCP Snooping

* adds a database in the switch, DHCP Binding database to validate the link between mac and ip address

Dynamic ARP Inspection

* Uses the database to validate a arp packet verifying if it has a spoofed mac address
