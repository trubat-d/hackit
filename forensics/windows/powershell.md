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
Get-ChildItem (-Path <PATH>)
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
```

{% hint style="info" %}
Patterns can use wildcards as \*
{% endhint %}

Filter output of objects

```powershell
Select-Object <PROPERTY1,PROPERTY2>
```

Filter by string (alias to grep or findstr)

```
Select-String -Path <PATH> -Pattern "<PATTERN>"
findstr
```

{% hint style="info" %}
It supports regex
{% endhint %}


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
Get-Process
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


{% endtab %}

{% tab title="Scripting" %}
Essential to execute commands on remote systems

```powershell
Invoke-Command

Get-Help Invoke-Command -examples
```


{% endtab %}
{% endtabs %}

