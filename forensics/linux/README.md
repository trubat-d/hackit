---
description: Aggregate of Linux Tools for Forensics
---

# Linux

***

### Important Files:

* /etc/ os-release - os release infos
*   /etc/passwd - contains infos about existing users

    `username : password info : user id : groud ip : description : home directory : defaut shell exec on login`

    command to parse: `column -t -s :`

    non-system generated users start with id 1000+
* /etc/shadow - contains hashed passwords
*   /etc/group - contains user group infos

    `group name : group password (x if in shadow) : group id : users in group`
* /etc/sudoers  - contains infos about users that are allowed to use sudo commands
* /var/log - aggregates log files of services
  * /var/log/auth.log - logs all the authentication of users
    * contains the sudo commands logs
  * /var/log/wtmp- historical data of logins (read with `last` command since they are binaries)
  * /var/log/btmp - failedl ogins (read with `last` command)
  * /var/log/syslog - Infos about system logs activity
* /etc/hostname - Linux host info
* /etc/timezone - timezone information
* /etc/network/interfaces - infos about network interfaces
* /etc/hosts - contains DNS name assignment
* /etc/resolv.conf - DNS servers that a Linux host talks to
* /etc/crontab - contains infos about persistant cron jobs
* /etc/init.d - directory with the list of services on startup
* \~/.bashrc - config file for the spawned bash shells from the user
* /etc/bash.bashrc - system wide settings for shells
* /etc/profile - system wide settings for shells
* \~/.bash\_history - history of the commands that aren't sudo
* \~/.viminfo - logs about vim tool uses

### Useful commands

* ip address show - retrieves infos about interfaces
* netstat  - active network connections (can add -natp for more info)
* ps - running processes (-aux for more info)
* hostname - get host name



<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

***

### Memory Extraction programs

* FTK Imager
* Redline
* DumpIt.exe
* win32dd.exe / win64dd.exe
* Memoryze
* FastDump

#### VM files for analysis

* VMWare - .vmem
* Hyper-V - .bin
* Parallels - .mem
* VirtualBox - .sav file \*_this is only a partial memory file_
