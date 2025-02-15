---
description: How to extract data from a binary file
---

# Data Extraction

## Readelf

```
readelf -S <binary>
```

Used to get an overview of the position in the program and in the file of each sections.

* 1 is the section
* 2 is the `Offset` in the file
* 3 is the VMA offset (See in references)

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## DD

```
dd if=<file in> bs=1 skip=<offset> count=<Number of Bytes> of=<file out>
```

* Numerical values are in base 10 by default. To use hex, use this:&#x20;

```
$((value))
```

Example:

```
 dd if=myfile.bin bs=1 skip=$((0x404020)) count=40 of=outfile.dat
```



References:\
[VMA Offset](https://embeddedartistry.com/fieldmanual-terms/virtual-memory-address/)
