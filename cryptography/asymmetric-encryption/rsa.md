---
description: Rivent-Shamir-Adleman
---

# RSA

RSA is a public-key encryption algorithm that enables secure data transmission over insecure channels. With an insecure channel, we expect adversaries to eavesdrop on it.



* Based on the math problem of factoring large numbers

Its easy to multiply but hard to factor huge numbers

* Prime number 1: $$982451653031$$
* Prime number 2: $$169743212279$$
* Their product: $$982451653031 × 169743212279 = 166764499494295486767649$$





## For CTF

You need to know the main variables for RSA in CTFs: p, q, m, n, e, d, and c:

* p and q are large prime numbers
* n is the product of p and q
* The public key is n and e
* The private key is n and d
* m is used to represent the original message, i.e., plaintext
* c represents the encrypted text, i.e., ciphertext

Tool for breaking RSA

{% embed url="https://github.com/RsaCtfTool/RsaCtfTool" %}

{% embed url="https://github.com/ius/rsatool" %}
