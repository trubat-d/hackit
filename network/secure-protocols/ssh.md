---
description: Secure Shell
---

# SSH

{% hint style="info" %}
SSH server listens on port 22
{% endhint %}



OpenSSH offers several benefits. We will list a few key points:

* **Secure authentication**: Besides password-based authentication, SSH supports public key and two-factor authentication.
* **Confidentiality**: OpenSSH provides end-to-end encryption, protecting against eavesdropping. Furthermore, it notifies you of new server keys to protect against man-in-the-middle attacks.
* **Integrity**: In addition to protecting the confidentiality of the exchanged data, cryptography also protects the integrity of the traffic.
* **Tunneling**: SSH can create a secure “tunnel” to route other protocols through SSH. This setup leads to a VPN-like connection.
* **X11 Forwarding**: If you connect to a Unix-like system with a graphical user interface, SSH allows you to use the graphical application over the network.



Command to connect

```
ssh <username>@<hostname>

#For graphical interface use
ssh <username>@<hostname> -X
```

