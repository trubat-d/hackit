---
description: >-
  PowerShell is a cross-platform task automation solution made up of a
  command-line shell, a scripting language, and a configuration management
  framework
---

# Powershell

{% tabs %}
{% tab title="Utility" %}
List command-lets and scripts

```powershell
Get-Command

#Can be filtered with options
Get-Command -CommandType "<TYPE>"
```

Show help related to a specific command-let

```powershell
Get-Help <CMDLET>
```

See the aliases of command-lets

```powershell
Get-Alias
```

Search for modules to add

```powershell
Find-Module -Name "<NAME>"
```

{% hint style="info" %}
Requires internet connection
{% endhint %}

Install a specific module

```powershell
Install-Module -Name "<NAME>"
```

{% hint style="info" %}
Requires internet connection
{% endhint %}

List Directory

```powershell
Get-ChildItem (-Path <PATH>) -Recurse
dir
ls
```

Change directory

```powershell
Set-Location (-Path <PATH>)
cd
```

Create a item (File or Dir)

```powershell
New-Item (-Path <PATH>) -ItemType "<File/Directory>"
```

Remove a item (File or Dir)

```powershell
Remove-Item -Path <PATH>
```

Copy an item

```powershell
Copy-Item -Path <PATH> -Destination <DESTPATH>
```

Print the content of a file

```powershell
Get-Content
type
cat
```

Convert from Base64

```powershell
[System.Text.Encoding]::Unicode.GetString([System.Convert]::FromBase64String($EncodedText))
```

Get hash

```powershell
Get-FileHash -Algorithm <ALG>
```

Download a file from a web server

```powershell
Invoke-WebRequest <URLonServer> -OutFile <fileOnLocal>
#OR
(New-Object System.Net.WebClient).Downloadfile(<URLonServer>,<fileOnLocal>)
```

Get the execution policy

```powershell
Get-ExecutionPolicy
```

can be bypassed spawning powershell with

```powershell
#if not already in powershell
powershell -ExecutionPolicy Bypass

#if already in powershell
Set-ExecutionPolicy Bypass
```

Save Output to a file

```powershell
Out-File <filename>
```


{% endtab %}

{% tab title="Piping Filtering and Sorting" %}
Pipe

```powershell
|
```

Sort Objects received

```powershell
Sort-Object <PROPERTY>
```

Filter objects by property

```powershell
Where-Object -Property <PROPERTY> -<eq/gt/ge/lt/le> "<VALUE>"

#With pattern Matching
Where-Object -Property <PROPERTY> -like "<PATTERN>"
Where-Object -Property <PROPERTY> -match "<PATTERN>"
```

{% hint style="info" %}
Patterns can use wildcards as \*
{% endhint %}

Filter output of objects

```powershell
Select-Object <PROPERTY1,PROPERTY2>
```

Filter by string (alias to grep or findstr)

```powershell
Select-String -Path <PATH> -Pattern "<PATTERN>"
findstr
```

{% hint style="info" %}
It supports regex
{% endhint %}

Show in a table format

```powershell
Format-Table <properties>
```

Show in a list

```powershell
Format-List
```
{% endtab %}

{% tab title="System and Network" %}
Retrieve comprehensive system info

```powershell
Get-ComputerInfo
```

List local users accounts

```powershell
Get-LocalUser
```

Show network config

```powershell
Get-NetIPConfiguration
```

Detailed configuration for network

```powershell
Get-NetIPAddress
```

Detailed view of all currently running processes including CPU and memory usage

```powershell
Get-Process (-name)
```

Start a specific Process

```powershell
Start-Process
```

Retrieve information about the status of services on the machines

```powershell
Get-Service
```

Display current TPC connections

```powershell
Get-NetTCPConnection
```

Get the hash of a file

```powershell
Get-FileHash -Path <PATH> (-Algorithm <ALGO>)
```

List patches installed

```powershell
Get-Hotfix
```

List Backup files

```powershell
Get-ChildItem -Path 'C:\' -Filter '*.bak*' -Recurse
```

Search for files with specific strings

```powershell
Select-String -Path "C:\Path\To\Directory\*" -Pattern "yourKeyword"
```

List Files containing a specific keyword

```powershell
Get-ChildItem -Path 'C:\'  -Recurse | Select-String -Pattern "keyword" 
```

This can be used to ping a range of ips

```powershell
<NUM>..<NUM> | %{echo "10.0.2.$_"; ping -n 1 10.0.2.$_ | Select-String ttl} 
```

Get the Owner of folder

```powershell
Get-Acl <file>
```
{% endtab %}

{% tab title="Scripting" %}
Essential to execute commands on remote systems

```powershell
Invoke-Command

Get-Help Invoke-Command -examples
```

### PowerView

Import the powerview.ps1 module

```powershell
Import-Module powerview.ps1
```

Collect infos about domain controller

```powershell
Get-NetDomainController
```

Get a list of domain Users

```powershell
Get-NetUser

(Get-NetUser).name
```

{% hint style="info" %}
You might consider output to .csv or out-gridview
{% endhint %}

you can also list for specific property

```powershell
Get-NetUser | select -ExpandProperty <protery>
#OR
Get-NetUser | select -ExpandProperty <lastlogon>
```

Enumerate systems connected to the domain

```powershell
Get-NetComputer -ping
```

List groups for domain

```powershell
Get-NetGroup
```

Enumerate members of a group

```powershell
Get-NetGroupMember "Domain Admins"
```

Find shares

```powershell
Find-DomainShare

#List readable Shares
Find-DomainShare -CheckShareAccess
```

Enumerate Group Policy

```powershell
Get-NetGPO
```

User enumeration

```powershell
Find-LocalAdminAccess
```

Disabled users in domain admins

```powershell
Get-NetUser -Filter "(userAccountControl:1.2.840.113556.1.4.803:=2)"
```


{% endtab %}
{% endtabs %}
