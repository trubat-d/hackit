---
description: Basic concepts regarding Active Directory attacks and mitigation measures.
---

# Active Directory Hardening

* Server Manager > Tools > Active Directory Domains and Trust

Lan Manager Hash

* Group Policy Management Editor > Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options > double click Network security - Do not store LM hash value on next password change policy > select "Define policy setting"

SMB Signing

* Group Policy Management Editor > Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options > double click Microsoft network server: Digitally sign communication (always) > select Enable Digitally Sign Communications

LDAP Signing

* Group Policy Management Editor > Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options > Domain controller: LDAP server signing requirements > select Require signing from the dropdown

Password policies

* Group Policy Management Editor > Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy

Understanding Password Policy Settings

* Enforce password history: Prevent at least 10 to 15 old passwords from being set as new ones.&#x20;
* Minimum password length: The minimum password length should be set between 10 to 14.
* Complexity requirements: Must not contain the name of the user account and ensure the password has uppercase letters, lowercase letters, digits, or special characters.

### Implement policies of Least Privilege

Use different accounts types:

* **User accounts**: for regular users
* **Privilege accounts**: with elevated privileges (first and second privilege accounts)
* **Shared accounts**: with limited access for specific times (not recommended)

Change access controls

* **Role-Based Access Control**: grants rights to resources while keeping the principle of Least Privilege in mind
* **Tiered Access Model (TAM)**: separates Active Directory's assets into three tiers (Tier 0, 1, and 2) to reduce privilege escalation risks
* **Auditing Accounts**: involves setting up correct accounts, assigning privileges, and applying restrictions to monitor account usage, privileges, and changes
