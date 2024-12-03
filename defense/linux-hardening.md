---
description: Security added to Linux systems
---

# Linux Hardening

### Setup a grub password

* `grub2-mkpasswd-pbkdf2` - Password-based derivation function 2

### Filesystem Partitioning and Encryption

Using Linux Unified Keys Setup in terminal (LUKS)

* `cryptsetup-luks` - Library for LUKS
* `fdisk -l , lsblk , blkid` - partition names
* `cryptsetup -y -v liksFormat <Partition>` - set up partition for luks
* `cryptsetup luksOpen <Partition> EDCdrive` - Create mapping to access the partition
* `ls -l /dev/mapper/EDCdrive` and `cryptsetup -v status EDCdrive` - confirm mapping details.
* `dd if=/dev/zero of=/dev/mapper/EDCdrive` - overwrite existing data with zero
* `mkfs.ext4 /dev/mapper/EDCdrive -L <NAME>` - Format partition
* &#x20;`mount /dev/mapper/EDCdrive /media/secure-USB` - Mount it and start using it like classic partition
* `cryptsetup luksDump /dev/sdb1` - checks LUKS settings



Open img and mount

{% code overflow="wrap" %}
```sh
sudo cryptsetup open --type luks <IMGFILE> <FOLDER> && sudo mount <MAPPER PATH> <FOLDER>
```
{% endcode %}

### Block Remote Root Login

* `/etc/ssh/sshd_config` - File to change
* `PermitRootLogin no` - add this line to block login as root in ssh

### Secure User Accounts

Instead of using root user, create a admin user with limited sudo commands added to sudoers.

```
usermod -aG sudo <USERNAME>
```

Disable root

* Change /etc/passwd root default shell to /sbin/nologin

Strong password Policy

* libpwquality can help change that
* `/etc/pam.d/common-password` - location of passwords rules in Debian and Ubuntu
* `/etc/security/pwquality.conf - same but on Redhat and fedora`
* `difok` allows you to specify the number of characters in the new password that were not present in the old password.
* `minlen` sets the minimum allowed length for new passwords.
* `minclass` specifies the minimum number of required classes of characters; a class can be uppercase, lowercase, and digits, among others.
* `badwords` provides a space-separated list of words that must not be contained in the chosen password.
* `retry=N` prompts the user `N` times before returning an error.

Disable Unused Accounts

* Add /sbin/nologin to the end in /etc/passwd

### Update and upgrade policies

Using APT manager

* `sudo apt update` - download package information from the configured sources
* `sudo apt upgrade` - install available upgrades for all packates from sources

Using Redhat manager

* dnf update (8 and later)
* yum update (on older ones)

### Log files

* `/var/log/messages` - a general log for Linux systems
* `/var/log/auth.log` - a log file that lists all authentication attempts (Debian-based systems)
* `/var/log/secure` - a log file that lists all authentication attempts (Red Hat and Fedora-based systems)
* `/var/log/utmp` - an access log that contains information regarding users that are currently logged into the system
* `/var/log/wtmp` - an access log that contains information for all users that have logged in and out of the system
* `/var/log/kern.log` - a log file containing messages from the kernel
* `/var/log/boot.log` - a log file that contains start-up messages and boot information
