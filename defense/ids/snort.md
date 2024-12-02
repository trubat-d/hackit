---
description: Packet sniffer, Packet logging or Network Intrusion detection system.
---

# Snort

### Important files

* `/etc/snort` - gather main config
* `/etc/snort/snort.conf` - specify which rules files to enable and network range to monitor
* `/etc/snort/rules/` - folder containing snort rules
* `/etc/snort/rules/local.rules` - file containing rules to add

### Rule format:

```
Action Protocol SourceIP SourcePort Direction DestIP DestPort (Rule Metadata)
```

Example

{% code overflow="wrap" %}
```
alert any any -> 127.0.0.1 80 (msg:"Web Server incoming Detected"; sid:1000001; rev:1;)
```
{% endcode %}

{% hint style="info" %}
Note that Direction can be - > or "< - >"&#x20;
{% endhint %}

### Start snort in listening mode example

```sh
sudo snort -q -l /var/log/snort -i lo -A console -c /etc/snort/snort.conf
```

For help menu -&#x20;

```sh
snort -?
snort -h
```

### Start snort in packet logging mode example (on a pcap file)

```bash
sudo snort -q -l /var/log/snort -r <PCAPFILE> -A console -c /etc/snort/snort.conf
```

