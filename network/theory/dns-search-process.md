---
description: Domain name system
---

# DNS Search Process

*   Phases of DNS Search on Windows:

    1. Hosts File: Windows checks the “hosts file”
    2. Local DNS Cache: If not found in the hosts file,it checks its local DNS cache for recent DNS queries.

    Sent to recursive DNS servers:

    1. Root Name Servers: If not found locally, the query is sent to root name servers.
    2. Top-Level Domain (TLD) Servers: Root servers redirect to TLD servers for the specific domain extension.
    3. Authoritative Name Servers: TLD servers direct to the authoritative name servers for the specific domain.
    4. DNS Resolution: The authoritative name server provides the IP address for the requested domain.
    5. Caching: The resolved IP address is cached locally for future use.
    6. Response: The IP address is returned to the client, allowing connection to the desired website or service.

### Dig

Dig (Domain Information Groper) is a command-line DNS query tool. It retrieves detailed information about DNS records, helping administrators and developers troubleshoot DNS issues and verify configurations.
