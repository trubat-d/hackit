---
description: Tools to crack hashes
---

# Cracking Hashes

{% hint style="info" %}
Fastest if run on Host instead of VM since in VM it cannot use GPU if not set up
{% endhint %}

## Rainbow Tables

{% embed url="https://hashes.com/en/decrypt/hash" %}

{% embed url="https://crackstation.net/" %}

## Identify Hashe types

```
john --list=formats
```

```
hashid file
```

## Wordlists Locations

```
/usr/share/wordlists/
```

## Hashcat

```
hashcat -m <hash_type> -a <attack mode> <file> <wordlist>
```

* `-m <hash_type>` specifies the hash-type in numeric format. For example, `-m 1000` is for NTLM. Check the official documentation (`man hashcat`) and [example page](https://hashcat.net/wiki/doku.php?id=example_hashes) to find the hash type code to use.
* `-a <attack_mode>` specifies the attack-mode. For example, `-a 0` is for straight, i.e., trying one password from the wordlist after the other.
* `hashfile` is the file containing the hash you want to crack.
* `wordlist` is the security word list you want to use in your attack.
* -w 3 for cracking longer passwords but more ressource intensive

## JohnTheRipper

```
john <options> <file path>
```

* `john`: Invokes the John the Ripper program
* `options`: Specifies the options you want to use
* `file path`: The file containing the hash you’re trying to crack; if it’s in the same directory, you won’t need to name a path, just the file.

```
john --wordlist=<WORDLIST> <path to file>
```

```
john --format=<format> --wordlist=<WORDLIST> <path to file>
```

#### To crack /etc/shadow passwords

you need to use tool for john called unshadow

```
unshadow <PWDPATH> <SHADOWPATH> > <OUTFILE>
```

```
john --wordlist=<WORDLIST> --format=sha512crypt <UNSHADOWEDFILE>
```

### Single Crack Mode

```
john --single --format=<FORMAT> hashes.txt
```

**For Single Crack Mode you need to add the username to the hash**

**From** `1efee03cdcb96d90ad48ccc7b8666033`

**To** `mike:1efee03cdcb96d90ad48ccc7b8666033`

### How to create Custom Rules

Folder : /etc/john/john.conf

\[List.Rules:\<RULENAME>]

* `Az`: Takes the word and appends it with the characters you define
* `A0`: Takes the word and prepends it with the characters you define
* `c`: Capitalises the character positionally
* `[0-9]`: Will include numbers 0-9\

* `[0]`: Will include only the number 0
* `[A-z]`: Will include both upper and lowercase\

* `[A-Z]`: Will include only uppercase letters
* `[a-z]`: Will include only lowercase letters

To call the Rule you can use

```
john --wordlist=<WORDLIST> --rule=<RULENAME> <FILE>
```

### Zip password protected&#x20;

```
zip2john <options> <ZIPFILE> > <OUTFILE>
```

* `options`: Allows you to pass specific checksum options to `zip2john`; this shouldn’t often be necessary

### Rar archives

```
rar2john <RARFILE> > <OUTFILE>
```

### SSH key cracking

Using the id\_rsa private key

```
ssh2john <ID_RSAFILE> > <OUTFILE>
```
