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



<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

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

### _Content of /etc/passwd_

1. **Username**: It is used when user logs in. It should be between 1 and 32 characters in length.
2. **Password**: An x character indicates that encrypted password is stored in /etc/shadow file. Please note that you need to use the passwd command to compute the hash of a password typed at the CLI or to store/update the hash of the password in /etc/shadow file, in this case, the password hash is stored as an "x".\

3. **User ID (UID)**: Each user must be assigned a user ID (UID). UID 0 (zero) is reserved for root and UIDs 1-99 are reserved for other predefined accounts. Further UID 100-999 are reserved by system for administrative and system accounts/groups.
4. **Group ID (GID)**: The primary group ID (stored in /etc/group file)
5. **User ID Info**: The comment field. It allow you to add extra information about the users such as user’s full name, phone number etc. This field use by finger command.
6. **Home directory**: The absolute path to the directory the user will be in when they log in. If this directory does not exists then users directory becomes /
7. **Command/shell**: The absolute path of a command or shell (/bin/bash). Typically, this is a shell. Please note that it does not have to be a shell.
