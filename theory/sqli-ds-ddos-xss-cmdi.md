# SQLi, DS, DDoS, XSS, CMDi

## SQLi

Uses SQL commands in a vulnerable website to delete, modify or enumerate a database server

### Classic SQL Injection:

```sql
<http://url.com/file.ext?id=1> AND SELECT * FROM users WHERE username = 'input' OR '1=1;
```

### Blind :

Boolean Based:

> Not possible to have an active view of the database error/query response

```sql
<http://url.com/file.ext?id=1> UNION SELECT * FROM users WHERE username like 'a%';
```

% is a wildcard for 0+ char

\_ is a wildcard for 1 char

Time based:

```sql
<http://url.com/file.ext?id=1> SELECT SLEEP(5),2 FROM users WHERE username like 'a%';
```

Where we have a 2 column base response and SLEEP(5) is the first column and 2 is the second one

SQL accessible database information file-

```jsx
information_schema

information_schema.tables
information_schema.columns
```

SQL injections Can lead to

* Data disclosure
* Ahthentication Bypass
* Database Manipulation

#### Prevention

Using Parametrized Statements

***

## DoS

> “Denial of Service / Distributed Denial of Service”

Techniques used -

* Flooding attacks - Overwelm target with ICMP requests with **ping** or SYN/ACK using **tcp handshake** process sending large number of connection requests without completing the handshake
* Resouce Depletion - **Bandwith** overconsuming or **CPU and Memory** depletion exausting processing power and memory
* Application-layer Attacks - **HTTP/HTTPS** Request flooding or **DNS** Spoofing redirecting traffic or cause service dissruption

### DDOS

* Botnets → 1 Server (C2) Commanding a lot of infected Systems to participate in a focused attack
* Amplification → Exploit DNS servers to amplify volume of traffic or Abuse Network Time Protocole (NTP)
* Layered Attacks → Target multiple osi layers to overwhelm defenses
* Spoofing → Falsifies the source IP to make tracking difficult

#### How to mitigate

* Traffic Filtering → Anomaly Based Filtering or using Rate Limiting single sources
* Load Balancing → distribute traffic in efficient way to prevent overwelming situations
* Content Delivery Networks (CDNs) → Using Geographically distributed servers to cache and deliver content
* Intrusion Prevension Systems (IPS)
* Firewalls

## Cross-site Scripting

> Using javascript vulnerability to execute code on a system that is not originaly coming from the website

Types -

* Stored XSS → Malicious Script is injected into the webserver which makes it persistant
* Reflected XSS → Embeded URL with malicious Script that gets embeded in the servers response
* DOM-Based XSS → Code that will run due to the javascript of the site running with client-side content

***

## Command Injection

> _Imagine that the website/server you are trying to connect uses scripts to generate http responses_

You can use Command injection to retrieve infos about the server where the script is running if it not sanitised enough

List of command examples: [https://github.com/payloadbox/command-injection-payload-list](https://github.com/payloadbox/command-injection-payload-list)
