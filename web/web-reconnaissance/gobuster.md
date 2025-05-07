---
description: >-
  Enumartion tool for web directories, DNS subdomains, vhosts, Amazon s3 buckets
  and google cloud storage by brute-force. It is written in golang.
---

# Gobuster

{% tabs %}
{% tab title="Commands" %}
```
gobuster --help
```

* `-t , --threads`  - Configure the number of threads for the scan, with each thread sending requests with a delay. The default is 10 threads, which may be slow for large wordlists. Adjust the number based on system resources.
* `-w , --wordlist` - The flag configures a wordlist to use for iterating. Each wordlist entry is attached to the URL you included in the command.
* `--delay` -Specify the delay between requests. Increasing the delay can resemble normal web traffic, avoiding detection systems that flag
* `--debug` - This flag helps us to troubleshoot when our command gives unexpected errors.
* `-o , --output` - This flag writes the enumeration results to a file we choose.
* `-u` - gives URL to the command

\
\
Example:

{% code overflow="wrap" %}
```
gobuster dir -u "http://www.example.com" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r
```
{% endcode %}


{% endtab %}

{% tab title="Mods" %}
* `dir` - used for enumarting web directories
* `dns` - DNS subdomain enum mode
* `fuzz` - uses fuzzing mode replacing keyword FUZZ in url, header or body
* `gcs` - uses google cloud storage bucket enum mode
* `s3` - used for amazon web service bucket
* `tftp` - uses tftp enum mode
* `vhost` - use vhost enum mode
{% endtab %}

{% tab title="DIR" %}


<table data-view="cards"><thead><tr><th>Flag</th><th>Long Flag</th><th>Description</th></tr></thead><tbody><tr><td><code>-c</code></td><td><code>--cookies</code></td><td>This flag configures a cookie to pass along each request, such as a session ID.</td></tr><tr><td><code>-x</code></td><td><code>--extensions</code></td><td>This flag specifies which file extensions you want to scan for. E.g., .php, .js</td></tr><tr><td><code>-H</code></td><td><code>--headers</code></td><td>This flag configures an entire header to pass along with each request.</td></tr><tr><td><code>-k</code></td><td><code>--no-tls-validation</code></td><td>This flag  skips the process that checks the certificate when https is used. It often happens for CTF events or test rooms like the ones on THM a self-signed certificate is used. This causes an error during the TLS check.</td></tr><tr><td><code>-n</code></td><td><code>--no-status</code></td><td>You can set this flag when you don’t want to see status codes of each response received. This helps keep the output on the screen clear.</td></tr><tr><td><code>-P</code></td><td><code>password</code></td><td>You can set this flag together with the --username flag to execute authenticated requests. This is handy when you have obtained credentials from a user.</td></tr><tr><td><code>-s</code></td><td><code>--status-codes</code></td><td>With this flag, you can configure which status codes of the received responses you want to display, such as 200, or a range like 300-400.</td></tr><tr><td><code>-b</code></td><td><code>--status-codes-blacklist</code></td><td>This flag allows you to configure which status codes of the received responses you don’t want to display. Configuring this flag overrides the -s flag.</td></tr><tr><td><code>-U</code></td><td><code>--username</code></td><td>You can set this flag together with the <code>--password</code> flag to execute authenticated requests. This is handy when you have obtained credentials from a user.</td></tr><tr><td><code>-r</code></td><td><code>--followredirect</code></td><td>This flags configures Gobuster to follow the redirect that it received as a response to the sent request. A HTTP redirect status code (e.g., 301 or 302) is used to redirect the client to a different URL.</td></tr></tbody></table>
{% endtab %}

{% tab title="DNS" %}


<table data-view="cards"><thead><tr><th>Flag</th><th>Long Flag</th><th>Description</th></tr></thead><tbody><tr><td><code>-c</code></td><td><code>--show-cname</code></td><td>Show CNAME Records (cannot be used with the <code>-i</code> flag).</td></tr><tr><td><code>-i</code></td><td><code>--show-ips</code></td><td>Including this flag shows IP addresses that the domain and subdomains resolve to.</td></tr><tr><td><code>-r</code></td><td><code>--resolver</code></td><td>This flag configures a custom DNS server to use for resolving.</td></tr><tr><td><code>-d</code></td><td><code>--domain</code></td><td>This flag configures the domain you want to enumerate.</td></tr></tbody></table>

Example

```
gobuster dns -d example.com -w /path/to/wordlist
```


{% endtab %}

{% tab title="VHOST" %}


<table data-view="cards"><thead><tr><th>Shortflag</th><th>Long Flag</th><th>Description</th></tr></thead><tbody><tr><td><code>-u</code></td><td><code>--url</code></td><td>Specifies the base URL (target domain) for brute-forcing virtual hostnames.</td></tr><tr><td><br></td><td><code>--append-domain</code></td><td>Appends the base domain to each word in the wordlist (e.g., word.example.com).</td></tr><tr><td><code>-m</code></td><td><code>--method</code></td><td>Specifies the HTTP method to use for the requests (e.g., GET, POST).</td></tr><tr><td></td><td><code>--domain</code></td><td>Appends a domain to each wordlist entry to form a valid hostname (useful if not provided explicitly).</td></tr><tr><td><br></td><td><code>--exclude-length</code></td><td>Excludes results based on the length of the response body (useful to filter out unwanted responses).</td></tr><tr><td><code>-r</code></td><td><code>--follow-redirect</code></td><td>Follows HTTP redirects (useful for cases where subdomains may redirect).</td></tr></tbody></table>

Example

{% code overflow="wrap" %}
```shell
gobuster vhost -u "http://<IP>" --domain example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt --append-domain --exclude-length 250-320 
```
{% endcode %}
{% endtab %}
{% endtabs %}
