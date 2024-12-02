---
description: Generate certificates
---

# Openssl

{% code overflow="wrap" %}
```sh
openssl req -x509 -newkey rsa:4096 -days 365 -subj '/CN=www.example.com/O=RedTeam/C=UK' -nodes -keyout key-reverse.key -out key-reverse.crt
```
{% endcode %}

* `req` indicates that this is a certificate signing request. Obviously, we won’t submit our certificate for signing.
* `-x509` specifies that we want an X.509 certificate
* `-newkey rsa:4096` creates a new certificate request and a new private key using RSA, with the key size being 4096 bits. (You can use other options for RSA key size, such as `-newkey rsa:2048`.)
* `-days 365` shows that the validity of our certificate will be one year
* `-subj` sets data, such as organization and country, via the command-line.
* `-nodes` simplifies our command and does not encrypt the private key
* `-keyout PRIVATE_KEY` specifies the filename where we want to save our private key
* `-out CERTIFICATE` specifies the filename to which we want to write the certificate request
