# Memory Forensics

Jhon password:

```
vol -f <vmem file> windows.hashdump.Hashdump
```

grab the nthash of john

use john

```
john --wordlist <path to rockyou> --format=nt <file with nthash>
```

***

