---
description: Tool for RAM analysis and forensics
---

# Volatility3

syntax: `python3 vol.py -f <file> <os>.<plugin>`

It has no profiles like vol2, it uses profiles automaticaly based on plugins

* windows.info
* linux.info
* mac.info

OS not known plugin:

* imageinfo

Process Listing:

* pslist
* psscan - Uses \_EPROCESS to find process uncaught processes from pslist
* pstree - gets processes based on parent ID

Network Connections:

* netstat

if unstable on old windows machines, use tools like bulk\_extractor to get PCAP file from the mem file

#### List DLLs associated with process:

* dlllist

#### Code Injection Hunting:

* malfind

scan the heap for executables with bit set to RWE or RX

#### Compare against yara rules

* yarascan

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
