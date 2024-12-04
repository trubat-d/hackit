---
description: >-
  Key attack vectors used by hackers and how to protect yourself using different
  hardening techniques
---

# Windows Hardening

### Important Concepts

* services.msc - Access infos about services running on a system
* regedit - Registry key database editor
* Event Viewer - show log details about all events occuring on your computer&#x20;
* Telemetry - data collection system to enhance user experience that shares data with microsoft that runs using (diagtrack.dll) and stores encrypted in a local folder %ProgramData%\Microsoft\Diagnosis (This feature can be access through services)

### Standard vs Admin Account

* Control Panel > User accounts
* Windows hello feature -> (Settings > Accounts > Sign-in Options)
* User Account Control (UAC) -> (Control Panel > User Accounts) -> Change User Account Control Setting

LPGPE-

* Local Policy and Group Policies Editor - Built-in interactive tool that allows to configure and implement local and group policies.
* Password Policy Hardening -> (Security settings > Account Policies > Password policy)
* Lockout Policy -> (Local Security Policy > Windows Settings > Account Policies > Account Lockout Policy)

### Windows defender Firewall

* WF.msc
* Domain, Public and Private profiles should all have \`Blocked Incoming Connections"
* Disable Unused Networking Devices -> (Control panel > System and Security Setting > System > Device Manager)
* Disable SMB Protocol - it is used in the wild by hackers

```powershell
Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
```

* Protect Local Domain Name System - Host file located at `C:\Windows\System32\Drivers\etc\hosts`&#x20;
* Mitigating address Resolution Protocol attack

```sh
#Check the entries
arp -a

#Clear cach and prevent attack
arp -d
```

* Prevent Remote access to Machine -> (settings > Remote Desktop)

### Application Management

* Download trusted application from windows store -> ms-windows-store in the run dialague
* Only allow install of apps from store on computer -> (Setting > Select Apps and Features) -> The Microsoft Store Only&#x20;
* Malware Removal through Windows Defender Anti virus that provides Real-time protection, Browser Integration, Application Guad, Controlled Folder Acces
* Microsoft Office Hardening - Things like macros are used by some people in specific jobs which makes it not always a good idea to just block in all scenarios

{% embed url="https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference?view=o365-worldwide" %}

* AppLocker is a feature that allows users to block specific executables, scripts, and installers from execution through a set of rules (In the Local Group Policy Editor > Widnwos Settings > Security settings > Application Control Policies > AppLocker)
* Browser (MS Edge) - It is one of the first vectors on entry in a system so it needs to have specific locked features to mitigate chances of trojan, ransomware, ads , unsigned apps downloads.
* Protecting the browser through Microsoft Smart Screen - System that protects from phishing/malware sites and software when using Microsoft Edge -> (Settings > Windows Security > App and Browser Control > Reputation-based Protection)

### Storage management

* Data Encryption through BitLocker - (Start > Control Panel > System and Security > BitLocker Drive Encryption)
* Windows Sandbox - (Click Start > Search for 'Windows Features' and turn it on > Select Sandbox > Click OK to restart)
* Windows Secure Boot- msinfo32 in the run window (already the case if running UEFI)
* File Backups -> (Settings > Update and Security > Backup)

### Updating Windows

* Click Start > Settings > Update & Security > Window Updates
