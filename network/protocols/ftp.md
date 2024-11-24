---
description: File transfer Protocol
---

# FTP

{% hint style="info" %}
FTP server listens on TCP port 21 by default
{% endhint %}



Example commands defined by the FTP protocol are:

* `USER` \<name> - is used to input the username
* `PASS <pass>` - is used to enter the password
* `RETR` \<ressource> - (retrieve) is used to download a file from the FTP server to the client.
* `STOR` \<ressource> - (store) is used to upload a file from the client to the FTP server.
* TYPE A - switch to ascii



Commands through FTP can be

```
anonymous - username without password
ls - list directory and files
type ascii - switch to ascii
get <file> - retrieve the file
```

