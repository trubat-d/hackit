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



## Cryptography

* Protocol based on RSA keys

Generate a Key

```
ssh-keygen
```

It can use theses algos using `-t`

* **DSA (Digital Signature Algorithm)** is a public-key cryptography algorithm specifically designed for digital signatures.
* **ECDSA (Elliptic Curve Digital Signature Algorithm)** is a variant of DSA that uses elliptic curve cryptography to provide smaller key sizes for equivalent security.
* **ECDSA-SK (ECDSA with Security Key)** is an extension of ECDSA. It incorporates hardware-based security keys for enhanced private key protection.
* **Ed25519** is a public-key signature system using EdDSA (Edwards-curve Digital Signature Algorithm) with Curve25519.
* **Ed25519-SK (Ed25519 with Security Key)** is a variant of Ed25519. Similar to ECDSA-SK, it uses a hardware-based security key for improved private key protection.



You can copy your public key using

```
ssh-copy-id
```

You can define a specific key to a user using:

```
ssh -i <privateKeyFileName> <user>@<host>
```



