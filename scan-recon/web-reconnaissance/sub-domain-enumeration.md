---
description: Finding subdomains on a host website
---

# Sub-domain enumeration

### SSL/TLS Certificates

they can be used to identify subdomains using Certificate transparency Logs

{% embed url="https://crt.sh/" %}

{% embed url="https://ui.ctsearch.entrust.com/ui/ctsearchui" %}

### Search engines

* Search engines allow to search for trillion of pages. Subdomain enumartion can be done using filtering with google dorking

> site:\*.domain.com -site:www.domain.com

### DNS Brute force

* Tools like `dnsrecon` can be used to bruteforce domains

```sh
dnsrecon -t brt -d <domainName>
```

* Tools like `sublist3r`

```sh
./sublist3r.py -d <domainName>
```

### Virtual Hosts

* Trying different values for Host header can also give indications about potential subdomains

{% code overflow="wrap" %}
```sh
ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.<domainName>" -u <URL> -f <filtersize>
```
{% endcode %}

