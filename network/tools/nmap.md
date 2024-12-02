---
description: >-
  Tool which helps discover live hosts, find open ports, and detect service
  versions
---

# NMAP

Main Command

```
nmap
```

Well Known Ports: 1024

Ways to specify targets:

* `-` is used to define a range : 192.168.0.1-10
* `/` is used to define a subnet : 192.168.0.1/24 is equivalent to 192.168.0.0-255
* Hostname is used to define a target by his hostname: `example.com`&#x20;

{% tabs %}
{% tab title="Types of Scans" %}
- `-sn`  Ping Scan
- `-PS <portlist>` does a TCP syn scan
- `-PA <portlist>` does a TCP ACK scan
- `-PU <portlist>` does a UDP scan
- `-sL` will list the target that will be scaned in the case of more than 1 target
- `-sT` does a connect scan, it tries to complete TCP three-way handshake with every port
- `-sS` does a SYN scan, it only does the first step of TCP handshake which is stealthier
- `-sU` does a UDP scan
- `-Pn` will force nmap to scan every port even if they the host don't reply to ICMP request during discovery phase
- `-sN` does a TCP Null Scan
- `-sF` does a TCP FIN scan
- `-sX` does a TCP Xmas Scan
{% endtab %}

{% tab title="Utilities" %}
Limiting number of ports to scan

* `-F` is the fast mode, which scans the 100 most common ports instead of default 1000
* `-f` will fragment packets making them less likely to be detected by IDS or firewalls (size fragemented to 8bytes)
* `--mtu <num>` will be a multiple of 8 to fragment packets in size specific
* `-g` - Use give source port
* `--scan-delay <time>ms` will add a delay between packets sent
* `--badsum` will generate invalid checksum packets
* `-p <range>` allows to specify a range of ports to scan
* `-p-<maxport>` allows to specify a maximum port so it scans from 1 to max
* `-p-` scans for every port and is equivalent to `-p1-65535`
* `--data-length <num>` will add random data to sent packets
* `--min-parallelism, --max-parallelism` Minimum and maximum number of parallel probes
* `--min-rate <num>, --max-rate <num>` Minimum and maximum rate (packets/second)
* `--host-timeout <time>` Maximum amount of time to wait for a target host
* `--top-ports <numbers>`&#x20;
* `-T<VALUE>`  will offer the possiblity to select a specific timing between requests

100 Ports scan example (will not be always the same depending on the networks) :

| Timing          | Total Duration |
| --------------- | -------------- |
| T0 (paranoid)   | 9.8 hours      |
| T1 (sneaky)     | 27.53 minutes  |
| T2 (polite)     | 40.56 seconds  |
| T3 (normal)     | 0.15 seconds   |
| T4 (aggressive) | 0.13 seconds   |
{% endtab %}

{% tab title="Version Detection" %}
* `-O` enables OS Detection
* `-sV` service and version detection
* `-A` enables all previous detections&#x20;
{% endtab %}

{% tab title="Output" %}
* `-v` increased the verbosity (can use `-vv` , `-vvv`  or even `-vvvv` for more)
* `-d` if its not enough verbosity, (can go up to `-d9`)
* `-oN <filename>` stores as Normal Output
* `-oX <filename>` stores as XML Output
* `-oG <filename>` stores as grep-able output
* `-oA <basename>` output in all major formats
{% endtab %}

{% tab title="Scripting" %}
* `--script=<SCRIPT>` enables a specific script or a catageory of scripts
* `--script-args=<scriptname>.<arg>="<value>"`
* `-sC` will run all the scripts&#x20;

Scripts are located at : /usr/share/nmap/scripts

after install of a new script

```
nmap --script-updatedb
```



### Scripts categories

Written in LUA

* `safe`:- Won't affect the target
* `intrusive`:- Not safe: likely to affect the target
* `vuln`:- Scan for vulnerabilities
* `exploit`:- Attempt to exploit a vulnerability
* `auth`:- Attempt to bypass authentication for running services (e.g. Log into an FTP server anonymously)
* `brute`:- Attempt to bruteforce credentials for running services
* `discovery`:- Attempt to query running services for further information about the network (e.g. query an SNMP server).
{% endtab %}
{% endtabs %}

### TCP Connect Scan

* If port closed, server sends RST flag
* appropriate behavior for TCP protocol defined by RFC 9293

### SYN Scan

* also known as Half-Open, Stealth
* Cannot be used without Sudo permissions

### UDP Scan

* When a packet is sent to an open UDP port, there should be no response
* The port is considered then open|filtered
* When port is closed it is marked as "port unreachable"

### NULL Scan

* TCP request sent with no flags
* Target host should respond with RST if port closed

### FIN Scan

* Request Sent with FIN Flags
* Expects RST if port closed

### XMAS Scan

* TCP request sent malformed
* Sets PSH, URG and FIN flags
* If port closed expects RST
* In Miscrosoft Windows OS, it respondes to NULL, FIN or Xmas scan

{% hint style="info" %}
If port is filtered, packets might be droped leading to no response and ports being marked as open even when they aren't
{% endhint %}

### Libraries

{% embed url="https://nmap.org/nsedoc/scripts/" %}
