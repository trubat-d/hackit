# Traffic Monitoring

### Benefits of Traffic monitoring

* Improve operational efficiency and reduce costs
* Enhance time-to-resolution and reduce downtime
* Enable more efficient use of ressources

### Tools

* Traffic analysis: Wireshark
* Network monitoring : Zeek
* Intrusion Detection and Prevention: Snort
* Network forensics: NetworkMiner
* Threat Hunting: Brim

### Strategy

* Relevance and Installation
  * Assess tool's relevance to network needs Example: Determining if Wireshark is suitable for a small office network
  * Consider ease of installation process Example: Evaluating if Snort can be easily installed on existing servers
*   Configuration

    * Evaluate complexity of setup

    Example: Checking if Zeek requires extensive configuration for basic monitoring

    * Check for customization options

    Example: Assessing if NetworkMiner allows custom rule creation for specific threats
*   Cost to Purchase

    * Compare initial licensing fees

    Example: Comparing the cost of Brim's enterprise version to open-source alternatives

    * Consider hardware requirements

    Example: Determining if current servers can run Snort or if upgrades are needed
*   Ongoing Maintenance Cost

    * Factor in regular updates

    Example: Estimating monthly costs for keeping Wireshark updated on all workstations

    * Include potential upgrade costs

    Example: Budgeting for potential Zeek sensor upgrades as network traffic increases
*   Support Requirements

    * Assess vendor support availability

    Example: Checking if NetworkMiner offers 24/7 support for critical issues

    * Consider in-house expertise needed

    Example: Evaluating if current IT staff can effectively use and maintain Brim

### Access Control

* Firewall, Network Access Control, IAM (Identity and Access Management), Load Balancing, Network Segmentation, VPNs, Zero Trust Model

### Threat Control

* Intrusion Detection and Prevention (IDS/IPS), Data loss Prevention (DLP), Endpoint Protection, Cloud Security, Security Information and Event Management (SIEM), Security Orchestration Automation (SOAR), Network Traffic Analysis & Network Detection and Response

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

### Management

### SNMP (Simple Network Management Protocol)

#### Components:

* Manager - Controls and monitors network agents with SNMP, its a computer/server itself
* Agent - A **software** running on a network device ex: (router, switches)
* MIB (Management Information Database) - A hierarchical database that defines the structure and content of management information for network devices

#### Interactions:

* Get: **Server** requests data from **Agent**, who responds
* Set - set a value on **Agent**
* Trap: Sent by **Agent** when fault occurs (ex: interface going down, hardware failure)
