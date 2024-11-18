---
description: Tools that can be used to receive connections
---

# Shell Listeners

### Rlwrap

Provides editing keyboard and history allowing the use of arrow keys

```sh
rlwrap nc -lvnp <port>
```

### Ncat

improved version of netcat distributed by NMAP project. I provides extra features such as ssl encryption.

```sh
ncat -lvnp <port>

ncat --ssl -lvnp <port>
```

### Socat

Allows creation of socket connections between two data sources like two different hosts

```sh
socat -d -d TCP-LISTEN:<port> STDOUT
```

* `-d` adds verbosity
* `-d -d` adds even more verbosity
* `TCP-LISTEN:<port>` option creates a TCP listener on port \<port>&#x20;
