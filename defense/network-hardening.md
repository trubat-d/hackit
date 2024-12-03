---
description: >-
  techniques for securing and protecting network devices from potential threats
  and attacks
---

# Network Hardening

### VPN Config

* `/etc/openvpn/server/server.conf` - File containing config

```sh
sudo openvpn --genkey --secret <KEYNAME>.key
```

* cypher - specify cipher option
* auth - specify algorithm
* tls-crypt - specify key

```sh
sudo systemctl restart openvpn-server@server.service
```

### Routers, Switches & Firewalls

Use of GUI OpenWrt

### Important tools for network monitoring

[Nagios](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/quickstart.html)\
A popular open-source software for monitoring systems, networks, and infrastructure. It provides real-time monitoring and alerting for various services and applications.\
\
[SolarWinds Network Performance Monitor](https://documentation.solarwinds.com/en/success_center/npm/content/npm_installation_guide.htm)\
A comprehensive network monitoring tool that provides real-time visibility into network performance and availability. It includes network mapping, automated network discovery, and customisable dashboards.\
\
[PRTG](https://www.paessler.com/manuals/prtg/installation)\
An all-in-one network monitoring tool that provides comprehensive performance and availability monitoring. It includes real-time traffic analysis, custom dashboards, and customisable alerts.\
\
[Zabbix](https://www.zabbix.com/download)\
A powerful open-source network monitoring tool that provides real-time network performance and availability monitoring. It includes features such as customisable dashboards, network mapping, and alerting.\
