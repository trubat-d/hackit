---
description: Tool for RAM analysis and forensics
---

# Volatility

Install:

With sufficient access rights:

Vol3

```
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3
python3 setup.py install
python3 vol.py —h
```

Vol2

```
git clone https://github.com/volatilityfoundation/volatility.git
cd volatility
python setup.py install
```



Profiles in Vol3

* windows.info
* linux.info
* mac.info

Profiles in Vol2:

* imageinfo
* Kdbgscan - Kernel Debugger

### Typers of Hooks for malware evasion:

* SSDT Hooks - System Service Descriptor Table
* IRP Hooks
* IAT Hooks
* EAT Hooks
* In line Hooks

#### SSDT plugin:

* ssdt

#### List of loaded kernel modules:

* modules

### Other intersting modules for searching for malwares in memory:

* `modscan`
* `driverirp`
* `callbacks`
* `idt`
* `apihooks`
* `moddump`
* `handle`

Most important thing is getting the profile of the dump file

### Get Infos about profiles

{% tabs %}
{% tab title="V3" %}
```sh
vol -f <dmpfile> <windows.info/linux.info/mac.info>
```
{% endtab %}

{% tab title="V2" %}
```sh
vol.py -f <dmpfile> <imageinfo/kdbgscan>
```
{% endtab %}
{% endtabs %}

### **Dump Hashes from a windows image**

{% tabs %}
{% tab title="V3" %}
<pre class="language-sh"><code class="lang-sh"><strong>vol -f &#x3C;vmem file> windows.hashdump.Hashdump
</strong>#Grab common windows hashes (SAM+SYSTEM)

vol -f &#x3C;vmem file> windows.cachedump.Cachedump
#Grab domain cache hashes inside the registry

vol -f file.dmp windows.lsadump.Lsadump
#Grab lsa secrets
</code></pre>
{% endtab %}

{% tab title="V2" %}
```sh
volatility --profile=<profile> hashdump -f file.dmp 
#Grab common windows hashes (SAM+SYSTEM)

volatility --profile=<profile> cachedump -f file.dmp
#Grab domain cache hashes inside the registry

volatility --profile=<profile> lsadump -f file.dmp 
#Grab lsa secrets
```
{% endtab %}
{% endtabs %}

### List Processes

{% tabs %}
{% tab title="V3" %}
{% code overflow="wrap" %}
```sh
vol -f <file.dmp> windows.pstree.PsTree # Get processes tree (not hidden)
vol -f <file.dmp> windows.pslist.PsList # Get process list (EPROCESS)
vol -f <file.dmp> windows.psscan.PsScan # Get hidden process list(malware)
```
{% endcode %}
{% endtab %}

{% tab title="V2" %}
{% code overflow="wrap" %}
```sh
volatility --profile=PROFILE pstree -f file.dmp # Get process tree (not hidden)
volatility --profile=PROFILE pslist -f file.dmp # Get process list (EPROCESS)
volatility --profile=PROFILE psscan -f file.dmp # Get hidden process list(malware)
volatility --profile=PROFILE psxview -f file.dmp # Get hidden process list
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Proc dump

{% tabs %}
{% tab title="V3" %}
&#x20;Dumps exe and associated DLLs

<pre class="language-sh" data-overflow="wrap"><code class="lang-sh"><strong>vol -f “/path/to/file” -o “/path/to/dir” windows.dumpfiles ‑‑pid &#x3C;PID>
</strong></code></pre>
{% endtab %}

{% tab title="V2" %}
Just outputs specified PID (or all if not specified)

{% code overflow="wrap" %}
```sh
vol.py -f “/path/to/file” ‑‑profile <profile> procdump -p <PID> ‑‑dump-dir=“/path/to/dir”
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Memdump

{% tabs %}
{% tab title="V3" %}
{% code overflow="wrap" %}
```sh
vol -f “/path/to/file” -o “/path/to/dir” windows.memmap ‑‑dump ‑‑pid <PID>
```
{% endcode %}
{% endtab %}

{% tab title="V2" %}
{% code overflow="wrap" %}
```sh
vol.py -f “/path/to/file” ‑‑profile <profile> memdump -p <PID> ‑‑dump-dir=“/path/to/dir”
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Handles

{% tabs %}
{% tab title="V3" %}
PID, process, offset, handlevalue, type, grantedaccess, name

{% code overflow="wrap" %}
```sh
vol -f “/path/to/file” windows.handles ‑‑pid <PID>
```
{% endcode %}
{% endtab %}

{% tab title="V2" %}
&#x20;Offset(V), PID, handle, access, type, details

<pre class="language-sh" data-overflow="wrap"><code class="lang-sh"><strong>vol.py -f “/path/to/file” ‑‑profile &#x3C;profile> handles -p &#x3C;PID>
</strong></code></pre>
{% endtab %}
{% endtabs %}

### DLLS

{% tabs %}
{% tab title="V3" %}
<pre><code><strong>vol -f “/path/to/file” windows.dlllist ‑‑pid &#x3C;PID>v
</strong></code></pre>
{% endtab %}

{% tab title="V2" %}
PID, command line, base, size, loadcount, loadtime, path

```
vol.py -f “/path/to/file” ‑‑profile <profile> dlllist -p <PID>
```
{% endtab %}
{% endtabs %}



Output differences:

*

```
vol.py -f “/path/to/file” ‑‑profile <profile> dlllist -p <PID>
```

* Volatility 3: PID, process, base, size, name, path, loadtime, file output

```
vol -f “/path/to/file” windows.dlllist ‑‑pid <PID>
```

### CMDLine

Output differences:

* Volatility 2: process name, PID, commandline; cmdscan includes application, flags, process handle; consoles contains C:\ listing, original titles, screen position and command history information

```
vol.py -f “/path/to/file” ‑‑profile <profile> <cmdline/cmdscan/consoles>
```

* Volatility 3: PID, process name, args

```
vol -f “/path/to/file” windows.cmdline.CmdLine
```

If searching for history of closed cmd sessions, its in `conhost.exe` and can be searched by dumping the process and reading it with strings

### Network Information

{% tabs %}
{% tab title="V3" %}
```
vol --f    
```
{% endtab %}

{% tab title="V2" %}

{% endtab %}
{% endtabs %}



V2

```
vol.py -f “/path/to/file” ‑‑profile <profile> <netscan/netstat>
```

Note: The XP/2003 specific plugins are deprecated and therefore not available in Volatility 3

```
vol.py -f “/path/to/file” ‑‑profile <profile> <connscan/connections/sockscan/sockets>
```

V3

```
vol -f “/path/to/file” windows.<netscan/netstat>
```

### Env variables per process

{% tabs %}
{% tab title="V3" %}
{% code overflow="wrap" %}
```sh
vol -f file.dmp windows.envars.Envars [--pid <pid>] 
#Display process environment variables
```
{% endcode %}
{% endtab %}

{% tab title="V2" %}
{% code overflow="wrap" %}
```sh
volatility --profile=PROFILE envars -f file.dmp [--pid <pid>] 
#Display process environment variables

volatility --profile=PROFILE -f file.dmp linux_psenv [-p <pid>] 
#Get env of process. runlevel var means the runlevel where the proc is initated 
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Token Privileges

```
V2
#Get enabled privileges of some processes
volatility --profile=Win7SP1x86_23418 privs --pid=3152 -f file.dmp | grep Enabled

#Get all processes with interesting privileges
volatility --profile=Win7SP1x86_23418 privs -f file.dmp | grep "SeImpersonatePrivilege\|SeAssignPrimaryPrivilege\|SeTcbPrivilege\|SeBackupPrivilege\|SeRestorePrivilege\|SeCreateTokenPrivilege\|SeLoadDriverPrivilege\|SeTakeOwnershipPrivilege\|SeDebugPrivilege"

V3
#Get enabled privileges of some processes
python3 vol.py -f file.dmp windows.privileges.Privs [--pid <pid>]

#Get all processes with interesting privileges
python3 vol.py -f file.dmp windows.privileges.Privs | grep "SeImpersonatePrivilege\|SeAssignPrimaryPrivilege\|SeTcbPrivilege\|SeBackupPrivilege\|SeRestorePrivilege\|SeCreateTokenPrivilege\|SeLoadDriverPrivilege\|SeTakeOwnershipPrivilege\|SeDebugPrivilege"
```

### SIDs

```
V2
V3
volatility --profile=Win7SP1x86_23418 getsids -f file.dmp 
#Get the SID owned by each process

volatility --profile=Win7SP1x86_23418 getservicesids -f file.dmp 
#Get the SID of each service
```

{% tabs %}
{% tab title="V3" %}
<pre class="language-shell"><code class="lang-shell"><strong>volatility --profile=PROFILE getsids -f file.dmp 
</strong>#Get the SID owned by each process

volatility --profile=PROFILE getservicesids -f file.dmp 
#Get the SID of each servicezs
</code></pre>
{% endtab %}

{% tab title="V2" %}

{% endtab %}
{% endtabs %}



## Hivelist

<pre><code><strong>V2
</strong><strong>vol.py -f “/path/to/file” ‑‑profile &#x3C;profile> &#x3C;hivescan/hivelist>
</strong>V3
vol -f “/path/to/file” windows.registry.&#x3C;hivescan/hivelist>
</code></pre>

### Printkey

```
V2
vol.py -f “/path/to/file” ‑‑profile <profile> printkey <-K "Key Path">
V3
vol -f “/path/to/file” windows.registry.printkey <--key "Key path">
```

### HiveDump

```
V2
vol.py -f “/path/to/file” ‑‑profile hivedump -o <offset>
```

## Files

### Filescan

```
V2
vol.py -f “/path/to/file” ‑‑profile <profile> filescan
V3
vol -f “/path/to/file” windows.filescan
```

### Filedump

```
V2
vol.py -f “/path/to/file” ‑‑profile <profile> dumpfiles ‑‑dump-dir=“/path/to/dir”
<-Q <offset>> <-p <PID>>
V3
vol -f “/path/to/file” -o “/path/to/dir” windows.dumpfiles
<‑‑virtaddr <offset>> <‑‑physaddr <offset>>
```

## Miscellaneous

Output differences:

* Volatility 2: PID, process name, address, VAD tags, hexdump, and shellcode

```
vol.py -f “/path/to/file” ‑‑profile <profile> malfind
```

* Volatility 3: PID, process name, process start, protection, commit charge, privatememory, file output, hexdump disassembly

```
vol -f “/path/to/file” windows.malfind
```

### Yarascan

```
V2
vol.py -f “/path/to/file” yarascan -y “/path/to/file.yar”
V3
vol.py -f “/path/to/file” windows.vadyarascan 
<‑‑yara-rules <string>>
<‑‑yara-file “/path/to/file.yar”>
<‑‑yara-file “/path/to/file.yar”>
```



## References

* [https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet)
* [https://blog.onfvp.com/post/volatility-cheatsheet/](https://blog.onfvp.com/post/volatility-cheatsheet/)

