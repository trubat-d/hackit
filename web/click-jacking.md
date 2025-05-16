---
description: >-
  Clickjacking is an interface-based attack in which a user is tricked into
  clicking on actionable content on a hidden website by clicking on some other
  content in a decoy website.
---

# Click Jacking

## This is a Personal document based on the content of PortSwigger

{% embed url="https://portswigger.net/web-security/learning-paths/clickjacking" %}

## Basic HTML script for Clickjacking

```html
<head>
	<style>
		#target_website {
			position:relative;
			width:(VALUE);
			height:(VALUE);
			opacity:0.00001;
			z-index:2;
			}
		#decoy_website {
			position:absolute;
			top:(VALUE);
			left:(VALUE);
			z-index:1;
			}
	</style>
</head>
...
<body>
	<div id="decoy_website">
	(CONTENT)
	</div>
	<iframe id="target_website" src="https://vulnerable-website.com">
	</iframe>
</body>
```

## Burp suite clickbandit

clickbandit is a burp suite resource that enables to make quick proof of concepts of clickjacking specific pages giving the ability to save the HTML page used in the testing context.

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Copy the code to clipboard and copy it in the developer's tool window of the page you want to use it on.

{% hint style="info" %}
Some browsers are asking to allow the console pasting:\
Example: chrome -> Write "allow pasting" in the console before pasting the code.
{% endhint %}

## Prefilled Input Forms

Some Forms can be prefilled we adding the id of the field as a parameter of the URL in a GET command

This allows your clickjacking to have a frame containing a website with a pre-filled form so that the only action required is clicking the decoy button.



## Frame busting

It is the act of running a script via an add-on/extension to verify and prevent clickjacking and iframes being used in this context.

Bypass methods for those scripts consist in using HTML5 iframe `sandbox` attribute that when set with a value of `allow-forms` or `allow-scripts` omitting `allow-top-navigation` will neutralize the scripts that cannot check if the window is on top or not.



## DOM Based XSS with Clickjacking

If you find a DOM based XSS vulnerability on a website and have the possibility to use it in a frame, then you can make people execute arbitrary JavaScript code by making them for example:\
\- click on a submit form that will reflect the name that was inputted in the form to the page and will then execute the code that was prefilled in the name field, all of that overlapped with Clickjacking window.



## Multi-step clickjacking

Sometimes the user need to do multiple clicks to do an action:

* Clicking on a payment form and then validating it
* Clicking on delete account button and then on validation button

In this case it it possible to build more complex HTML to trick the user into clicking at different parts of the window.



## Clickjacking prevention

#### X-Frame-Options

We have already seen that Frame busters scripts can be bypassed using `sandbox` tag in the iframe.\
There was a new header introduced: `X-Frame-Options`&#x20;

Here are the possible values:

| Directives            | Effect                                                                                    |
| --------------------- | ----------------------------------------------------------------------------------------- |
| deny                  | The page cannot be displayed in a frame, regardless of the site attempting to do so.      |
| sameorigin            | The page can only be displayed if all ancestor frames are same origin to the page itself. |
| allow-from (OBSELETE) | Use Content-Security-Policity HTTP header with frame-ancestors instead.                   |

{% embed url="https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Frame-Options" %}

#### Content Security Policy

Detection and prevention mechanism used to provide mitigation against XSS and clickjacking

Implemented server-side as:

```
Content-Security-Policy: <policy>
```

policy is a semicolon separated string of directives that browsers will use to detect and mitigate possible attacks.

The directive used relative to clickjacking is : `frame-ancestors` and here is the possible values:

| Value       | effect                                                     |
| ----------- | ---------------------------------------------------------- |
| 'none'      | Similar to X-Frame-Options: deny                           |
| 'self'      | Similar to X-Frame-Options: sameorigin                     |
| website.com | Possibility to restrict the embedding to specific websites |

{% embed url="https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/frame-ancestors" %}
