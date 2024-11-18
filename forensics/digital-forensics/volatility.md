---
description: Tool for RAM analysis and forensics
---

# Volatility

Install:

With sufficient access rights:

{% tabs %}
{% tab title="V3" %}
```
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3
python3 setup.py install
python3 vol.py —h
```
{% endtab %}

{% tab title="V3 Symbols" %}
Install at volatility3/volatility/symbols

* [https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip)
* [https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip)
* [  https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip)
{% endtab %}

{% tab title="V2" %}
```
git clone https://github.com/volatilityfoundation/volatility.git
cd volatility
python setup.py install
```
{% endtab %}
{% endtabs %}

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
PID, process, base, size, name, path, loadtime, file output

<pre><code><strong>vol -f “/path/to/file” windows.dlllist ‑‑pid &#x3C;PID>
</strong></code></pre>
{% endtab %}

{% tab title="V2" %}
PID, command line, base, size, loadcount, loadtime, path

```
vol.py -f “/path/to/file” ‑‑profile <profile> dlllist -p <PID>
```
{% endtab %}
{% endtabs %}

### CMDLine

{% tabs %}
{% tab title="V3" %}
&#x20;PID, process name, args

```
vol -f “/path/to/file” windows.cmdline.CmdLine
```
{% endtab %}

{% tab title="V2" %}
process name, PID, commandline; cmdscan includes application, flags, process handle; consoles contains C:\ listing, original titles, screen position and command history information

```
vol.py -f “/path/to/file” ‑‑profile <profile> cmdline
vol.py -f “/path/to/file” ‑‑profile <profile> cmdscan
vol.py -f “/path/to/file” ‑‑profile <profile> consoles
```
{% endtab %}
{% endtabs %}

If searching for history of closed cmd sessions, its in `conhost.exe` and can be searched by dumping the process and reading it with strings

### Network Information

{% tabs %}
{% tab title="V3" %}
```
vol -f “/path/to/file” windows.netscan
vol -f “/path/to/file” windows.netstat
```
{% endtab %}

{% tab title="V2" %}
<pre><code><strong>vol.py -f “/path/to/file” ‑‑profile &#x3C;profile> netscan
</strong>vol.py -f “/path/to/file” ‑‑profile &#x3C;profile> netstat
</code></pre>

Note: The XP/2003 specific plugins are deprecated and therefore not available in Volatility 3

```
vol.py -f “/path/to/file” ‑‑profile <profile> connscan
vol.py -f “/path/to/file” ‑‑profile <profile> connections
vol.py -f “/path/to/file” ‑‑profile <profile> sockscan
vol.py -f “/path/to/file” ‑‑profile <profile> sockets
```
{% endtab %}
{% endtabs %}

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

{% tabs %}
{% tab title="V3" %}
```sh
#Get enabled privileges of some processes
vol -f file.dmp windows.privileges.Privs [--pid <pid>]

#Get all processes with interesting privileges
vol -f file.dmp windows.privileges.Privs | grep "SeImpersonatePrivilege\|SeAssignPrimaryPrivilege\|SeTcbPrivilege\|SeBackupPrivilege\|SeRestorePrivilege\|SeCreateTokenPrivilege\|SeLoadDriverPrivilege\|SeTakeOwnershipPrivilege\|SeDebugPrivilege"
```
{% endtab %}

{% tab title="V2" %}
<pre><code><strong>#Get enabled privileges of some processes
</strong>volatility --profile=Win7SP1x86_23418 privs --pid=3152 -f file.dmp | grep Enabled

#Get all processes with interesting privileges
volatility --profile=Win7SP1x86_23418 privs -f file.dmp | grep "SeImpersonatePrivilege\|SeAssignPrimaryPrivilege\|SeTcbPrivilege\|SeBackupPrivilege\|SeRestorePrivilege\|SeCreateTokenPrivilege\|SeLoadDriverPrivilege\|SeTakeOwnershipPrivilege\|SeDebugPrivilege"
</code></pre>
{% endtab %}
{% endtabs %}

### SIDs

{% tabs %}
{% tab title="V3" %}
```sh
vol -f file.dmp windows.getsids.GetSIDs [--pid <pid>] #Get SIDs of processes
vol -f file.dmp windows.getservicesids.GetServiceSIDs #Get the SID of services
```
{% endtab %}

{% tab title="V2" %}
```sh
volatility --profile=Win7SP1x86_23418 getsids -f file.dmp 
#Get the SID owned by each process

volatility --profile=Win7SP1x86_23418 getservicesids -f file.dmp 
#Get the SID of each service
```
{% endtab %}
{% endtabs %}

## Hivelist

{% tabs %}
{% tab title="V3" %}
```sh
vol -f “/path/to/file” windows.registry.hivescan
vol -f “/path/to/file” windows.registry.hivelist
```
{% endtab %}

{% tab title="V2" %}
<pre><code><strong>vol.py -f “/path/to/file” ‑‑profile &#x3C;profile> hivescan
</strong>vol.py -f “/path/to/file” ‑‑profile &#x3C;profile> hivelist
</code></pre>
{% endtab %}
{% endtabs %}

### Printkey

{% tabs %}
{% tab title="V3" %}
```sh
vol -f “/path/to/file” windows.registry.printkey <--key "Key path">
```
{% endtab %}

{% tab title="V2" %}
```
vol.py -f “/path/to/file” ‑‑profile <profile> printkey <-K "Key Path">
```
{% endtab %}
{% endtabs %}

### HiveDump

{% tabs %}
{% tab title="V2" %}
```sh
vol.py -f “/path/to/file” ‑‑profile hivedump -o <offset>
```
{% endtab %}
{% endtabs %}

## Files

### Filescan

{% tabs %}
{% tab title="V3" %}
```sh
vol -f “/path/to/file” windows.filescan
```
{% endtab %}

{% tab title="V2" %}
```
vol.py -f “/path/to/file” ‑‑profile <profile> filescan
```
{% endtab %}
{% endtabs %}

### Filedump

{% tabs %}
{% tab title="V3" %}
```sh
vol -f “/path/to/file” -o “/path/to/dir” windows.dumpfiles
<‑‑virtaddr <offset>> <‑‑physaddr <offset>>
```
{% endtab %}

{% tab title="V2" %}
<pre><code>vol.py -f “/path/to/file” ‑‑profile &#x3C;profile> dumpfiles ‑‑dump-dir=“/path/to/dir”
<strong>&#x3C;-Q &#x3C;offset>> &#x3C;-p &#x3C;PID>>
</strong></code></pre>
{% endtab %}
{% endtabs %}

## Miscellaneous

Output differences:

{% tabs %}
{% tab title="First Tab" %}
PID, process name, process start, protection, commit charge, privatememory, file output, hexdump disassembly

```
vol -f “/path/to/file” windows.malfind
```
{% endtab %}

{% tab title="Second Tab" %}
PID, process name, address, VAD tags, hexdump, and shellcode

```
vol.py -f “/path/to/file” ‑‑profile <profile> malfind
```
{% endtab %}
{% endtabs %}

### Yarascan

{% tabs %}
{% tab title="V3" %}
```
vol.py -f “/path/to/file” windows.vadyarascan 
<‑‑yara-rules <string>>
<‑‑yara-file “/path/to/file.yar”>
<‑‑yara-file “/path/to/file.yar”>
```
{% endtab %}

{% tab title="V2" %}
```
vol.py -f “/path/to/file” yarascan -y “/path/to/file.yar”
```
{% endtab %}
{% endtabs %}

## References

* [https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet)
* [https://blog.onfvp.com/post/volatility-cheatsheet/](https://blog.onfvp.com/post/volatility-cheatsheet/)

