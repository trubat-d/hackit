---
description: >-
  Post office Protocol v3 allow the client to communicate with a mail server and
  retrieve email messages
---

# POP3

{% hint style="info" %}
POP3 server listens on TCP port 110 by default
{% endhint %}



Common Commands

```
USER <username> - identifies the user
PASS <password> - provides the user’s password
STAT - requests the number of messages and total size
LIST - lists all messages and their sizes
RETR <message_number> - retrieves the specified message
DELE <message_number> - marks a message for deletion
QUIT - ends the POP3 session applying changes, such as deletions
```

