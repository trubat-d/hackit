---
description: Active directory
---

# Windows AD

### Active Directory Env

Infos about Domain and Os Config:

```powershell
systeminfo | findstr Domain
```

get all active directory users

```powershell
Get-ADUser  -Filter *
```

Search for specific Users based on Distinguished Names

```powershell
Get-ADUser -Filter * -SearchBase ("OU=(field),CN=(field),DC=(field)")
```

### Windows

search for anti-viruses

```powershell
wmic /namespace:\\root\securitycenter2 path antivirusproduct

OR

Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntivirusProduct
```

print windows defender status

```powershell
Get-Service WinDefend
```

show RealTimeProtection status

```powershell
Get-MpComputerStatus | select RealTimeProtectionEnabled
```

show status of firewall profile:

```powershell
Get-NetFirewallProfile | Format-Table Name, Enabled
```

Modify firewall profiles status

```powershell
Set-NetFirewallProfile -Profile Domain, Public, Private -Enabled False
```

Test some port status

```powershell
Test-NetConnection -ComputerName 127.0.0.1 -Port 80
```

Show list of available logs

```powershell
Get-EventLog -List
```

Find exact name processes

```powershell
 Get-Process | Where-Object { $_.ProcessName -eq "(process name field)" }
 
 
 
 Get-CimInstance win32_service -Filter "Description = 'System Monitor service'"
 or
 Get-Service | where-object {$_.DisplayName -like "*sysm*"}
 
 # Registry query
 reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\WINEVT\Channels\Microsoft-Windows-Sysmon/Operational
```

show Sysmon config files

```powershell
findstr /si '<ProcessCreate onmatch="exclude">' C:\\tools\\*
```

Installed apps:

```powershell
wmic product get name,version
```

Searching particular text strings, hidden directoris, backup files with Get-ChildItem

```powershell
Get-ChildItem -Hidden -Path C:\Users\kkidd\Desktop\
```

see interesting running services:

```powershell
Net start
```

get more service info:

```powershell
wmic service where "name like '(Process name field)'" get Name,PathName

Get-Process -Name "(process executable file name field)"

netstat -noa |findstr "LISTENING" |findstr "(process PID field)"
```

get dns server ip

```powershell
nslookup -type=ns (dns server name field) (127.0.0.1)
```

DNS zone transfer

```powershell
nslookup.exe

> server (target ip field)
```



## Enumerating Active directory

for ssh access

```powershell
ssh <domain>\\<AD Username>@<IP>
```

Windows built-in tool : runas.exe

```powershell
runas.exe /netonly /user:<domain>\<username> cmd.exe
```

setup dns on windows shell

```powershell
$dnsip = "10.200.56.101"
$index = Get-NetAdapter -Name 'Ethernet 4' | Select-Object -ExpandProperty 'ifIndex'
Set-DnsClientServerAddress -InterfaceIndex $index -ServerAddresses $dnsip
```

### enumerate infos about local system

list users in ad domain

```powershell
net user /domain

#precise infos about 1 user
net user (user name field) /domain
```

list groups

```powershell
net group /domain

net group (group name field) /domain
```

enumerate password policy

```powershell
net accounts /domain
```

enumerate a specific user in **powershell**

```powershell
Get-ADUser -Identity (user name field) -Server (Server domain field) -Properties *

Get-ADUser -Filter 'Name -like "*(name field)"' -Server (domain field) | Format-Table Name,SamAccountName -A
```

enumerate specific groups

```powershell
Get-ADGroup -Identity (group name field) -Server (domain field) -Properties *

#Memberships
Get-ADGroupMember -Identity (group name field) -Server (domain field) -Properties *
```

AD objects changed after a specific date

```powershell
$ChangeDate = New-Object DateTime(2022, 02, 28, 12, 00, 00)
Get-ADObject -Filter 'whenChanged -gt $ChangeDate' -includeDeletedObjects -Server (domain field)
```

Password spraying , not zero tries password avoidance

```powershell
Get-ADObject -Filter 'badPwdCount -gt 0' -Server (Domain field)
```

infos about a specific domain

```powershell
Get-ADDomain -Server (domain field)
```

force changing the password of our AD user

```powershell
Set-ADAccountPassword -Identity (user name field) -Server (domain field) -OldPassword (ConvertTo-SecureString -AsPlaintext "(old password field)" -force) -NewPassword (ConvertTo-SecureString -AsPlainText "(new password field)" -Force)
```

Sharphound command

```powershell
Sharphound.exe --CollectionMethods <Methods> --Domain (domain field) --ExcludeDCs
#Methods can be All, Default, Session
```
