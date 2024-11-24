---
description: Using libpcap library, it helps handle capture of packets over TCP
---

# TCPdump

{% tabs %}
{% tab title="Commands" %}
Basic command

```
tcpdump
```

* `-i <INTERFACE>` Specify the interface (you can use "any" as the interface)
* `-w <DEST>` Save the capture into a file (generaly a .pcap)
* `-r <SRC>` read the capture file
* `-c <COUNT>`  limit the number of captured packets
* `-n` dont resolve IP addresses and `-nn` PORT numbers
* `-v`  `-vv` `-vvv` produces more verbose output
* `host <HOSTNAME/IP>`  will allow to filter with a specific host
* `src <HOSTNAME/IP>`  will allow to filter with a specific src
* `port <HOSTNAME>`  will allow to filter with a specific port
* `ip, ip6, udp, tcp, icmp, arp`  can be added to filter by protocol
{% endtab %}

{% tab title="Filters" %}
* `and, or, not` can be used to use multiple filters&#x20;
* `greater, less <SIZE>` filter by packets by length (for filters checkout man pcap-filter)

Using pcap-filter, Tcpdump allows you to refer to the contents of any byte in the header using the following syntax `proto[expr:size]`, where:

* `proto` refers to the protocol. For example, `arp`, `ether`, `icmp`, `ip`, `ip6`, `tcp`, and `udp` refer to ARP, Ethernet, ICMP, IPv4, IPv6, TCP, and UDP respectively.
* `expr` indicates the byte offset, where `0` refers to the first byte.
* `size` indicates the number of bytes that interest us, which can be one, two, or four. It is optional and is one by default.



You can use `tcp[tcpflags]` to refer to the TCP flags field. The following TCP flags are available to compare with:

* `tcp-syn` TCP SYN (Synchronize)
* `tcp-ack` TCP ACK (Acknowledge)
* `tcp-fin` TCP FIN (Finish)
* `tcp-rst` TCP RST (Reset)
* `tcp-push` TCP Push
{% endtab %}

{% tab title="Output" %}
* `-q`: Quick output; print brief packet information
* `-e`: Print the link-level header
* `-A`: Show packet data in ASCII
* `-xx`: Show packet data in hexadecimal format, referred to as hex
* `-X`: Show packet headers and data in hex and ASCII
{% endtab %}
{% endtabs %}

