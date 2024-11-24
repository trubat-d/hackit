---
description: Pretty Good Privacy and Gnu Privacy Guard
---

# PGP and GPG

It’s software that implements encryption for encrypting files, performing digital signing, and more. [GnuPG or GPG](https://gnupg.org/) is an open-source implementation of the OpenPGP standard.

GPG is commonly used in email to protect the confidentiality of the email messages. Furthermore, it can be used to sign an email message and confirm its integrity



Generate GPG

```
gpg --full-gen-key
```

Import a key

```
gpg --import <KEYFILE.key>
```

Decrypt a message

```
gpg --decrypt <FILE.gpg>
```





You can try to crack gpg messages using&#x20;

```
gpg2john
```

