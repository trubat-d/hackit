---
description: Process of collection of informations about a system
---

# Enumeration

{% tabs %}
{% tab title="Host information" %}
```sh
hostname
```

```sh
uname -a
```

```sh
cat /proc/version
```

```sh
cat /etc/issue
```

```sh
cat /etc/passwd
cat /etc/passwd | cut -d ":" -f 1
cat /etc/passwd | grep home
```
{% endtab %}

{% tab title="Processes" %}
```sh
ps

#All running services
ps -A

#Process tree
ps axjf

#Processes for all users with user info and processes not attached to terminal
ps aux
```

Get infos about commands history

```sh
history
```
{% endtab %}

{% tab title="Environement" %}
```sh
env
```

```sh
export
```
{% endtab %}

{% tab title="Privileges" %}
```sh
sudo -l
```

Site to get infos about programs that have sudo access and the usage

{% embed url="https://gtfobins.github.io/" %}

General overview of the user's privilege level and group memberships

```sh
id
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Network" %}
Check for interfaces

```sh
ifconfig
```

Show Routes

```sh
ip route
```

Active connections

```sh
netstat

#All listening ports and established connections
netstat -a 

#Lists TCP or UDP ports
netstat <-at> or <-au>

#Lists ports that are in "listening" mode
netstat -l

#List network usage statistics by protocol
netstat -s

#List connections with service name + PID info
netstat -tp

#List connections with service name, PID info, listening ports
# PID/Program name - Empty owned by another user
netstat -ltp

#Show interface statistics
netstat -i

#Most common command, Display all sockets, does not resolve names, 
#display timers 
netstat -ano
```
{% endtab %}

{% tab title="File System" %}
```sh
ls -la
```

Find files or filders&#x20;

```sh
#Search in specific dir for a file
find <folder> -name <filename>

#Search by type
find <folder> -type d -name <filename>

#Search files with specific perms (files readable, writeable, executable)
find <folder> -type f -perm 0777

#Find all executable files
find <folder> -user <user>

#Find files that were modified in last N days
find <folder> -mtime <N>

#Find files that are last accessed in last N days
find <folder> -atime <N>

#Find files changed in the last <N> minutes
find <folder> -cmin -<minutes>

#Find files changed in the last <N> minutes
find <folder> -amin -<minutes>

#Find files with specific size (G,M,K) with + or - ex: +50M
find <folder> -size <size>

#Redirect error Output to see
find <folder> -name <filename> 2>/dev/null

#Find world-writable folders
find / -writable -type d 2>/dev/null
find / -perm -222 -type d 2>/dev/null
find / -perm -o w -type d 2>/dev/null

#Find world-writable
find / -perm -o x -type d 2>/dev/null

#Find dev tools for specicic supportated languages
find / -name perl*
find / -name python*
find / -name gcc*

#Find file with SUID bit set
find / -perm -u=s -type f 2>/dev/null
```

Enumerate Shares

```sh
showmount -e <ip>
```

Mount a share

```sh
mount -o rw <ip>:/<folder or remote> <folder on attacker machine>
```


{% endtab %}
{% endtabs %}

## Tools For Automated Enumeration

* LinPeas: [https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)
* LinEnum: \
  [https://github.com/rebootuser/LinEnum](https://github.com/rebootuser/LinEnum)
* LES (Linux Exploit Suggester): \
  [https://github.com/mzet-/linux-exploit-suggester](https://github.com/mzet-/linux-exploit-suggester)
* Linux Smart Enumeration: \
  [https://github.com/diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)
* Linux Priv Checker: \
  [https://github.com/linted/linuxprivchecker](https://github.com/linted/linuxprivchecker)

