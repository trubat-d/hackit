# Access Control, Authentication

### Four major concepts

* Identification - When a source claims to be someone using multiple possible values
* Authentication - Process of determining the claims of someones identity using 3 factors
  * Something you know : password, credit card pin, security question
  * Something you have : phone, hardware token, smart card
  * Something you are : fingerprint, retina pattern, face recognition
* Authorization - Process of verify what an individual can access to after it has been Authenticated
* Accounting or Auditing - Involves the tracking and logging of activities related to system resource access to monitor behavior, identify incidents and maintain compliance.

### Factor Authentication

Can be Single, or Multi (two or +)

* Single-factor: Requires only one of the 3 factors said above to generate authentication
* Multi-factor: Requires two or more of the combined factors as for example with a pin + a code on the phone (2FA)

## Authentication Protocols

* LDAP (Lighteweight Directory Access Protocol)
* Kerberos
* NTLanManager

### Kerberos Terminology

* **Ticket Granting Ticket (TGT)** - A ticket-granting ticket is an authentication ticket used to request service tickets from the TGS for specific resources from the domain.
* **Key Distribution Center (KDC)** - The Key Distribution Center is a service for issuing TGTs and service tickets that consist of the Authentication Service and the Ticket Granting Service.
* **Authentication Service (AS)** - The Authentication Service issues TGTs to be used by the TGS in the domain to request access to other machines and service tickets.
* **Ticket Granting Service (TGS)** - The Ticket Granting Service takes the TGT and returns a ticket to a machine on the domain.
* **Service Principal Name (SPN)** - A Service Principal Name is an identifier given to a service instance to associate a service instance with a domain service account. Windows requires that services have a domain service account which is why a service needs an SPN set.
* **KDC Long Term Secret Key (KDC LT Key)** The KDC key is based on the KRBTGT service account. It is used to encrypt the TGT and sign the PAC.
* **Client Long Term Secret Key (Client LT Key)** The client key is based on the computer or service account. It is used to check the encrypted timestamp and encrypt the session key.
* **Service Long Term Secret Key (Service LT Key)** The service key is based on the service account. It is used to encrypt the service portion of the service ticket and sign the PAC.
* **Session Key** - Issued by the KDC when a TGT is issued. The user will provide the session key to the KDC along with the TGT when requesting a service ticket.
* **Privilege Attribute Certificate (PAC)** - The PAC holds all of the user's relevant information, it is sent along with the TGT to the KDC to be signed by the Target LT Key and the KDC LT Key in order to validate the user.

### NTLM Network

What does a hash format looks like:

```powershell
Username::Domain:SERVER CHALLENGE:HMAC-MD5:NTML RESPONSE
```

In wireshark

* Server challenge is in NTLMSSP\_CHALLENGE packet
* HMAC-MD5 is in the NTLMSSP\_AUTH packet as NTProofStr
* Response need to be with the removed HMAC-MD5 at the start

```powershell
hashcat -m 5600 <file name> <wordlist path> --force
```
