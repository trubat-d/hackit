---
description: >-
  “CIA = Confidentiality, Integrity, Availability” It is a fundational framework
  guiding info security policies.
---

# CIA Triad, DID and Principles

#### Confidentiality:

* Infos are only available to those who have authorized permission.

Ex: Encryption

#### Integrity:

* Infos are in accurate, consistent, reliable, ensures arrival of unaltered and trustworthy data.

Ex: Checksums/Hash

#### Availability:

* Infos arrive in time and in uninterrupted access when needed.

Ex: Load balancing

***

## Defense in Depth: Protecting Your Digital Assets

Defense in Depth is a security strategy that uses multiple layers of protection to keep your digital information safe.

### Key Ideas

* Multiple Layers: Use different security measures together.
* Backup Plans: If one security measure fails, others are still working.
* Variety: Use different types of security to stop various kinds of attacks.

### Main Parts

1. **Physical** Security: Protect the actual computers and devices.
2. Network Security: Use firewalls and other tools to protect your internet connection.
3. Device Security: Use antivirus software and keep devices updated.
4. **Technical**: Keep important information encrypted and limit who can access it.
5. User Training: Teach people how to stay safe online.
6. **Administrative**: Organization’s policies and procedures for establishing a meeting security requirements and standards

### Why It's Good

* Better Protection: Stops many different types of threats.
* Early Warning: Helps catch attacks sooner.
* Flexible: Can be adjusted to fit different needs.

Defense in Depth helps keep your digital world safer by using many types of protection together.

***

### Privacy

* Involves protecting individual’s personal information from unauthorized access, use or disclosure.

Ex: Encryption, Access Controls, Data Masking

### Anonymity

* Allows individuals to interact online without revealing their true identity to prevent tracking.

Ex: VPN, Tor Network, Anonymous Browsing

### Pseudonimity

* Individual use of a fictitious or alternative identity (pseudonym) to interact online maintaining a consistent identifier

Ex: Usernames and Aliases, Unique Identifiers, Secure Hashing

***

> _“Paradigm that challenges the traditional notion of implicit trust within networks, the main principle is (Never Trust, Always Verify)”_

### Key components:

* Micro-Segmentation: Divide the network into segments with specific access controls
*   Enforce the principle of least privilege

    This principle ensures users and systems have only the minimum access rights necessary to perform their tasks. It helps limit potential damage from accidental or malicious actions.

### Network Visibility:

* Monitoring, logging and analysis of network activities
* Identify anomalies and potential threats

### Continuous Authentication:

* Users and devices must authenticate continuously
*   Multi-factor authentication and adaptive authentication

    Multi-factor authentication (MFA) requires users to provide two or more verification factors to gain access. For example:

    * Something you know (password)
    * Something you have (smartphone)
    * Something you are (fingerprint)

    Adaptive authentication adjusts security requirements based on context. For instance:

    * Requiring additional verification for unusual login locations
    * Increasing security measures for sensitive data access

### Least Privilege Access:

* Grant minimum access required for tasks
* Dynamically adjust access permissions based on circumstances

### Device Trustworthiness:

* Continuously evaluate the security posture of devices
* Restrict or deny access to non-compliant or compromised devices

### Secure Access Gateways:

* Act as intermediaries enforcing security policies
* Inspect traffic for malicious content and facilitate secure communication

### Encryption:

* Encrypt data in transit and at rest for enhanced protection

### Policy Automation and Orchestration:

* Automate security policies for agility
* Orchestrate consistent policy application across the network

### User and Entity Behavior Analytics (UEBA)

* Analyze user and entity behavior for anomalies
* Utilize machine learning for detecting potential security incidents
