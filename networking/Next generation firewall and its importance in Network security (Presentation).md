
 ---
### Content
- Network Security
- Challenges faced by Organization
---
## Agenda
- Next generation Firewall 
- Features of Next Generation Firewall
- Importance of Next Generation Firewall in Network security
---
## Firewall [Introduction]
- Increase in use of internet by every organization
- Every organization is going digital
- So, need of network security
- Network security given by firewall
##### What is a firewall?
- It is first Line of defense
- It monitors incoming and outgoing network traffic and decides whether to block them or allow them
- Firewall prevents unauthorized access to the network
- Firewall employs set of rules to spot and prevent cyberattacks
- Firewall is deployed at the perimeter of internal network
---
## Types of Firewall
- Packet filtering firewall
	- Allows or block packet based on **source address, source port, destination address, destination port, protocol, and so on**
	- Doesn't check data / payload
	- Works in Layer 3 i.e. Network layer
	- Example: ACL (Access Control List)
- Stateful inspection firewall
	- A stateful firewall is a kind of firewall that **keeps track and monitors the state of active network connections** while analyzing incoming traffic and looking for potential traffic and data risks.
	- Works in Layer 3 and 4
	- They can verify that incoming packets belong to existing, legitimate connections and can identify and block unauthorized or suspicious connections.
- Proxy Service firewall
	- Also Known as **Application firewall**
	- It checks data / payload
	- Works in application layer
	- They can verify that incoming packets belong to existing, legitimate connections and can identify and block unauthorized or suspicious connections.
	 - Example: Fortiproxy
- **Next Generation firewall**
	- Added functionalities to Traditional firewall
	- Has better security and one console to control
	- Example: Fortigate
---
### What is Next Generation Firewall
- It is a network security device
- Provides capabilities beyond a traditional, stateful firewall
##### Traditional firewall
- Inspection of incoming and outgoing network traffic
- Checks the source address, source port, destination address, destination port, protocol
- NAT/PAT
##### Additional features given by NGFW
- Application Awareness and control
	- Application layer Inspection
	- SSL / TLS decryption
	- Deep packet inspection
- Reputation based filtering (URL filtering)
- User Awareness
- Security Intelligence
- Advance Malware protection
- Single Console access
---
### Application Awareness and control
- Application Layer inspection
- Contextual awareness
- SSL / TLS decryption (Man in the middle session management)
- Deep packet Inspection
---
### Reputation based Filtering (URL filtering)
- Examines the URL
- Scores is given to the URL
- Cisco Talos security intellectual group updates the score
- Filters the rate limit
---
### User awareness (Implementation of Role based Access)
- Access according to user and group/role of the user
- Policy based on user and group/role
- Use of active directory
	- Use of LDAP (Lightweight directory access protocol)
---
### Security Intelligence
- Get information to the firewall from the cloud
- NGFWs can receive frequent updates from security vendors to stay current with the latest threat intelligence and security enhancements.
- NGFWs can subscribe to external threat intelligence feeds provided by reputable sources such as security vendors, research organizations, or global threat intelligence networks. These feeds deliver up-to-date information about known malicious IP addresses, domains, URLs, malware signatures, and other indicators of compromise.
---
### Advance malware protection
- Network based anti-malware function
	- Traffic scanning
	- Url filtering
- Sandboxing
- Blocking files transfer installing malware
- Save copies for later analysis
---
### Single console access
- Capability of managing and monitoring multiple NGFW devices from centralized management console
- Scalability and ease of administration
- Administrators can monitor network traffic, track security incidents, view real-time alerts, and generate comprehensive reports from a central location.
- Administrators can deploy configurations and policy updates to multiple NGFW devices simultaneously through the single console