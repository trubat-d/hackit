---
description: >-
  Used to run scripts or binaries at specific times. Normaly uses owners
  privileges. They can provide privesc vector in some conditions
---

# Cronjobs

Jobs are stored in Cron tables (crontabs)

Any user can read /etc/crontab



You can search for scripts that have been removed from system but not from cronjobs using

```sh
locate <scriptname>
```



You could then create a reverse shell with privileges if you manage to create a script that is run by cronjobs so that it is run with root privileges
