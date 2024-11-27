---
description: Used in password verification and file integrity checking
---

# Hashing

They are different from encryption, there is no key

* A hash function takes some input data of any size and creates a summary or **digest** of that data.&#x20;
* The output has a fixed size.
* It’s hard to predict the output for any input and vice versa.
* Good hashing algorithms will be relatively fast to compute and prohibitively slow to reverse, i.e., go from the output and determine the input.
* Any slight change in the input data, even a single bit, should cause a significant change in the output.

### Hash identification

```
haiti

gem install haiti
```



Tools like Hashcat can give more infos about Hash types

{% embed url="https://hashcat.net/wiki/doku.php?id=example_hashes" %}

You can search about Unix hashes using

```
man 5 crypt
```

Commands to hash

{% tabs %}
{% tab title="Unix" %}
```
md5sum <file>
sha256sum <file>
sha512sum <file>
sha1sum <file>
```
{% endtab %}

{% tab title="Windows" %}
```
Get-FileHash -Algorithm <HASHTYPE> <FILE>

CertUtil -hashFile <FILE> <HASHTYPE>
```
{% endtab %}
{% endtabs %}



Some algorithms are considered unsafe nowadays because of "Hash Collison" which is the fact of two input giving the same hash since you are using a hashfunction that transforms any size input into a fixed size one



## Salting

To protect against Rainbow Tables (list of unsalted password to hash)

You can use a random value before salting a password so that if two passwords are the same, the hash will be different. \
Salts don't need to be kept private

## Linux Passwords

They are located in the /etc/shadow file encrypted

Saved in the format `$prefix$options$salt$hash`&#x20;

| Prefix                         | Algorithm                                                                                                                                                                                        |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `$y$`                          | yescrypt is a scalable hashing scheme and is the default and recommended choice in new systems                                                                                                   |
| `$gy$`                         | gost-yescrypt uses the GOST R 34.11-2012 hash function and the yescrypt hashing method                                                                                                           |
| `$7$`                          | scrypt is a password-based key derivation function                                                                                                                                               |
| `$2b$`, `$2y$`, `$2a$`, `$2x$` | bcrypt is a hash based on the Blowfish block cipher originally developed for OpenBSD but supported on a recent version of FreeBSD, NetBSD, Solaris 10 and newer, and several Linux distributions |
| `$6$`                          | sha512crypt is a hash based on SHA-2 with 512-bit output originally developed for GNU libc and commonly used on (older) Linux systems                                                            |
| `$md5`                         | SunMD5 is a hash based on the MD5 algorithm originally developed for Solaris                                                                                                                     |
| `$1$`                          | md5crypt is a hash based on the MD5 algorithm originally developed for FreeBSD                                                                                                                   |



## Windows Passwords

Generaly hashed using NTLM, variant of MD4. Visually identical to MD4 and MD5 hashes.\
\
In MS Windows, generaly stored in Security Accounts Manager (SAM).&#x20;

Tools like Mimikatz are used to dump them and circumvent MS Windows security&#x20;

Hashes found are split into NT Hashes and LM Hashes



## John rules

* Border mutation - commonly used combinations of digits and special symbols can be added at the end or at the beginning, or both
* Freak mutation - letters are replaced with similarly looking special symbols
* Case mutation - the program checks all variations of uppercase/lowercase letters for any character
* Order mutation - character order is reversed
* Repetition mutation - the same group of characters are repeated several times
* Vowels mutation - vowels are omitted or capitalized
* Strip mutation - one or several characters are removed
* Swap mutation - some characters are swapped and change places
* Duplicate mutation - some characters are duplicated
* Delimiter mutation - delimiters are added between characters

{% embed url="https://www.openwall.com/john/doc/RULES.shtml" %}

## Wordlist modification

{% embed url="https://github.com/sc0tfree/mentalist/releases" %}

web crawler for wordlist generation

{% embed url="https://github.com/digininja/CeWL" %}

example

```
cewl -d 2 -w $(pwd)/example.txt https://example.org
```

{% embed url="https://github.com/tp7309/TTPassGen" %}
