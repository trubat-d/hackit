---
description: >-
  Internet Mesage Access Protocol allows synchronizing read, moved, and deleted
  messages
---

# IMAP

{% hint style="info" %}
IMAP server listens on TCP port 143 by default
{% endhint %}

Commands

{% code overflow="wrap" %}
```
LOGIN <username> <password> - authenticates the user

SELECT <mailbox> - selects the mailbox folder to work with

FETCH <mail_number> <data_item_name> - Example fetch 3 body[] to fetch message number 3, header and body.

MOVE <sequence_set> <mailbox> - moves the specified messages to another mailbox

COPY <sequence_set> <data_item_name> - copies the specified messages to another mailbox

LOGOUT logs out
```
{% endcode %}
