---
description: Content Focusing on Windows Forensics and its tools
---

# Windows

***

### Registry

Its defined as a collection of databases containing system configurations.

### Hives

A database containing Registry Keys

### Keys

Keys are a set of Key-value pair that will provide a single information to programs and system inside of windows operating system.

#### Root Keys

They are the base keys that will hold multiple sub-keys. Here is the list of Root keys

1.  HKEY\_LOCAL\_MACHINE

    Contains configuration information particular to the computer (for any user). This key is sometimes abbreviated as HKLM.
2.  HKEY\_CURRENT\_USER

    Contains the root of the configuration information for the user who is currently logged on. The user's folders, screen colors, and Control Panel settings are stored here. This information is associated with the user's profile. This key is sometimes abbreviated as HKCU.
3.  HKEY\_USERS

    Contains all the actively loaded user profiles on the computer. HKEY\_CURRENT\_USER is a subkey of HKEY\_USERS. HKEY\_USERS is sometimes abbreviated as HKU.
4.  HKEY\_CURRENT\_CONFIG

    Contains information about the hardware profile that is used by the local computer at system startup.
5.  HKEY\_CLASSES\_ROOT

    Is a subkey of `HKEY_LOCAL_MACHINE\Software`. The information that is stored here makes sure that the correct program opens when you open a file by using Windows Explorer. This key is sometimes abbreviated as HKCR.

    Starting with Windows 2000, this information is stored under both the HKEY\_LOCAL\_MACHINE and HKEY\_CURRENT\_USER keys. The `HKEY_LOCAL_MACHINE\Software\Classes` key contains default settings that can apply to all users on the local computer. The `HKEY_CURRENT_USER\Software\Classes` key has settings that override the default settings and apply only to the interactive user.

    The HKEY\_CLASSES\_ROOT key provides a view of the registry that merges the information from these two sources. HKEY\_CLASSES\_ROOT also provides this merged view for programs that are designed for earlier versions of Windows. To change the settings for the interactive user, changes must be made under `HKEY_CURRENT_USER\Software\Classes` instead of under HKEY\_CLASSES\_ROOT.

    To change the default settings, changes must be made under `HKEY_LOCAL_MACHINE\Software\Classes` .If you write keys to a key under HKEY\_CLASSES\_ROOT, the system stores the information under `HKEY_LOCAL_MACHINE\Software\Classes`.

    If you write values to a key under HKEY\_CLASSES\_ROOT, and the key already exists under `HKEY_CURRENT_USER\Software\Classes`, the system will store the information there instead of under `HKEY_LOCAL_MACHINE\Software\Classes`.



* Amcache Hive - save info on programs recently run on system - `C:\Windows\AppCompat\Programs\Amcache.hve`
*   NTUSER.DAT - infos about user profile directory

    `C:\Users\<username>\`
* Logs for chantges in Registry Hives - `C:\Windows\System32\Config` files as `.LOG` extension
* Backups of hives are made every 10 days - `C:\Windows\System32\Config\RegBack`



### Transaction Logs

Logs containing the data about the modified values and keys inside of Hives



***



#### OS Version

```
SOFTWARE\Microsoft\Windows NT\CurrentVersion
```

#### Control set

machine’s configuration data used for controlling system startup are called Control Set

```
SYSTEM\ControlSet001 - commonly the control set that machine booted with
SYSTEM\ControlSet002 - last known good configuration
SYSTEM\Select\LastKnownGood
```

#### Volatile Control Set

control set when machine is live

```
HKLM\SYSTEM\CurrentControlSet
SYSTEM\Select\Current
```

#### Computer Name

```
SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName
```

#### Time Zone Info

```
SYSTEM\CurrentControlSet\Control\TimeZoneInformation
```

#### Network Interfaces and Past Networks

```
SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces
```

Each Interface is represented with a unique identifier (GUID) subkey, which contains values relating to the interface’s TCP/IP configuration.

This key will provide us with information like IP addresses, DHCP IP address and Subnet Mask, DNS Servers, and more.

The past networks a given machine was connected to can be found in the following locations:

```
SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Unmanaged
SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Managed
```

These registry keys contain past networks as well as the last time they were connected. The last write time of the registry key points to the last time these networks were connected.

#### Autostart Programs

programs that run on user logon

```
NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run
NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce
SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer\Run
SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

#### Services

```
SYSTEM\CurrentControlSet\Services
```

#### Same Hive and User info

The SAM hive contains user account information, login information, and group information.

```
SAM\Domains\Account\Users
```

The information contained here includes the relative identifier (RID) of the user, number of times the user logged in, last login time, last failed login, last password change, password expiry, password policy and password hint, and any groups that the user is a part of.



***

#### Recently Opened Files

```
NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs
```

In Registry explorer : looking for last used PDF files:

```
NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.pdf
```

Replace extension with the one you are interested in

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
