---
description: >-
  Packets and frames are fundamental units of data transmission in computer
  networks, each serving a specific purpose in different layers of the network
  model.
---

# Packets and Frames

### Packets

Packets are units of data at the network layer (Layer 3) of the OSI model. They contain:

* Source and destination IP addresses
* Protocol information
* Payload data

### Frames

Frames are units of data at the data link layer (Layer 2) of the OSI model. They include:

* Source and destination MAC addresses
* Error checking information (Checksums)
* The encapsulated packet data

## TCP/IP 3-Way Handshake

The TCP/IP 3-way handshake is a method used to establish a reliable connection between two devices before data transmission begins.

Example of TCP/IP communication:

* Step 1: Client sends SYN packet to server (Sequence number: 100)
* Step 2: Server responds with SYN-ACK packet (Acknowledgment: 101, Sequence number: 300)
* Step 3: Client sends ACK packet to server (Acknowledgment: 301)
* Step 4: Connection established, data transfer begins
* Step 5: Client sends data packet (Sequence number: 101, Length: 100)
* Step 6: Server sends ACK (Acknowledgment: 201)

This process ensures reliable, ordered data transmission.

## UDP/IP

UDP (User Datagram Protocol) is a connectionless protocol that doesn't require a handshake before data transmission. It's faster but less reliable than TCP.

Example of UDP/IP communication:

Step 1: Client sends UDP datagram to server (Source port: 12345, Destination port: 53)

Step 2: Server receives the datagram but does not send a response

Step 3: Client continues sending datagrams without confirmation of receipt

This process is faster but doesn't guarantee delivery or order of packets.

## Ports

Ports are virtual endpoints for communication in a network. They allow multiple applications on a single device to use network resources simultaneously.

Ports range from 0 to 65535, with numbers below 1024 typically reserved for well-known services.

\<aside> 💡

[Link of common ports](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

\</aside>
