---
description: Try to find what a website hides
---

# Website Content Discovery

### Possibilities

* Robots.txt - contains information of website for crawlers
* Favicon - if default can be curled to find infos about the framework used

{% embed url="https://wiki.owasp.org/index.php/OWASP_favicon_database" %}

* Sitemap.xml - Contains infos about the website structure (generaly for SEO usage)
* Comments, credits or copyright notices can give infos about framework
* Google dorking - filter google outputs

{% embed url="https://www.boxpiper.com/posts/google-dork-list" %}

* Wappalyzer - tool that identify technologies on websites

{% embed url="https://www.wappalyzer.com/" %}

* Wayback machine - Tool that allow retrieving snapshots of websites at different time frames

{% embed url="https://web.archive.org/" %}

* Github - Can have infos about tracked files on project inside commits
* S3 buckets from amazon - try links and common terms such as \<NAME>-assets, \<NAME>-www, \<NAME>-public, \<NAME>-private, etc on a link like \
  http(s)://**{name}.s3.amazonaws.com**
* Automated Discovery using tools like ffuf, dirb or gobuster

{% content-ref url="../web/web-reconnaissance/gobuster.md" %}
[gobuster.md](../web/web-reconnaissance/gobuster.md)
{% endcontent-ref %}

