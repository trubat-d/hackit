---
description: >-
  Executable programs that have "s" bit in the permissions /4000 what doing ls
  -la
---

# SUID

```sh
find / -type f -perm -04000 -ls 2>/dev/null
```

{% embed url="https://gtfobins.github.io/#+suid" %}

With tools such as John the Ripper we can use both&#x20;

* /etc/passwd
* /etc/shadow

to unshadow and get the wanted passwords

```sh
unshadow passwd.txt shadow.txt > password.txt
```

We can create a hash for the new user we want to have

```sh
openssl passwd -1 -salt <salt> <password>
```

