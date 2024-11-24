---
description: Command line interface for windows
---

# CMD.exe

Basic commands

{% hint style="info" %}
It is possible to use /? after the commands to see the help menu
{% endhint %}

{% tabs %}
{% tab title="System" %}
Get the version of the system

```
ver
```

Enumerate system infos

```
systeminfo
```

Get a list of drivers

```
driverquery
```

Show a list of Env Variables

```
set
```

Show a list of current tasks

```
tasklist
```

Kill process

```
taskkill /PID <PID>
```

Check the file system and disk volumes for errors and bad sectors

```
chkdsk
```

Scans the system files for corruption and repairs them if possible

```
sfc /scannow
```

Shudown or restart a sytem

```
shutdown /<TASK>
```


{% endtab %}

{% tab title="Utilities" %}
Give ability to scroll the output up and down (less for up and down, more for only down)

<pre><code><strong>&#x3C;COMMAND> | less
</strong><strong>&#x3C;COMMAND> | more
</strong></code></pre>

Clear the terminal

```
cls
```

Help Utility

```
help
```


{% endtab %}

{% tab title="Network" %}
The terminal output below shows our IP address, subnet mask, and default gateway

```powershell
ipconfig

#More Infos
ipconfig /all
```

ICMP packet network troubleshoot

```
ping <TARGET_NAME>
```

List routes to reach a specific target using TTL

```
tracert <TARGET_NAME>
```

Get infos about a domain and returns the IP searching in DNS servers

```
nslookup <DOMAIN> (<SERVER>)
```

Show a list of current established connections

```
netstat

#For help on extras
netstat -h

#For more infos
netstat -abon
```

File&#x20;
{% endtab %}

{% tab title="File and Disk" %}
Switch directory

```
cd <DIR>

#To come back to previous dir
cd ..
```

List directory and files

```
dir

#List hiden
dir /a

#List recursively
dir /s
```

Show directories in a tree structure

```
tree
```

Create a Directory

```
mkdir <DIR>
```

Remove a Directory

```
rmdir <DIR>
```

View Text files

```
type <FILE>
```

Copy a file

```
copy <FILE> <OUTFILE>
```

Move files

```
move <FILE> <DIR>
```

Delete file

```
del <FILE>
erase <FILE>
```

{% hint style="info" %}
You can refer to multiple files using the wildcard \*
{% endhint %}
{% endtab %}
{% endtabs %}
