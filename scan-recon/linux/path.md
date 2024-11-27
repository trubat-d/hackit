---
description: Contains pathes to binaries used by scripts.
---

# PATH

We need to search for world-writable folders

```sh
find / -writable 2>/dev/null | cut -d "/" -f 2 | sort -u

find / -writable 2>/dev/null | grep <folder> | sort -u
```

then we can compare with the PATH folders and see matches\
alternative

```sh
find / -writable 2>/dev/null | cut -d "/" -f 2,3 | grep -v proc | sort -u
```



We can export our writable folder using export

```sh
export PATH=<folder>:$PATH
```

