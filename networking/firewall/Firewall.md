- Network security device
- First Line of Defence
- Monitors incoming and outgoing network traffic
- Decides whether to allow of block specific traffic based on defined set of security rules
- Firewall prevents unauthorized access to networks through software of firmware
- Firewall can be hardware or software unit
- Firewall employs set of rules to spot and prevent cyberattacks
- Firewall is installed in the perimeter of the internal network
	
### Key Uses of Firewall
- Incorporate a security information and event management strategy (SIEM) into cybersecurity devices concerning modern organizations
- Perform logging and auditing the packets identifying patterns and improving the rules to defend the immediate thread

### Function of Firewall
- The most important function of a firewall is that it **creates a border** between an **external network and the guarded (internal) network** where the firewall inspects all packets (pieces of data for internet transfer) entering and leaving the guarded (internal) network
- Firewall inspect the packet and label the packet as benign or malicious letting the benign packet pass and dropping the malicious packet
- Firewall checks if the packet follows the defined rules or not and **filters the traffic**


### Types of Firewall
1. Packet Filtering
2. Proxy Service
3. Circuit Monitoring
4. Stateful inspection
5. [Next Generation Firewall (NGFW)](/networking/firewall/NGFW.md)
6. Unified Threat Management (UTM) Firewall *
7. Thread Focused NGFW *


##### Packet Filtering
- Controls data flow to and from the networks
- Allows or block packet based on **source address, source port, destination address, destination port, protocol, and so on**
- If rule matched then forward or discard i.e. drop
- If none rule matched then use default action which can be forward of discard (good to discard)
- It **doesn't check data / payload**
- Network Layer
- Example kinda: ACL (Access Control Lists)

##### Proxy Service
- Also known as **Application Firewall** or **Gateway Firewall**
- Uses proxy server to check whether the packet is benign or malicious
- It **checks data / payload**
- It has processing overhead
- Application Layer
- Limits the applications that a network can support, which increases security levels but can affect functionality and speed
- It determines which traffic should be allowed and denied and analyzes incoming traffic to detect signs of a potential cyberattacks or malware
- A proxy server firewall **caches, filters, logs, and controls requests** from devices to keep networks secure
- It has its own [Internet Protocol (IP) address](/networking/IP%20addressing/IPv4), which means an external network connection cannot receive packets directly from the network
- Proxy firewall **provides single point** to implement attack detection
- Examples: [Fortiproxy](https://www.fortinet.com/products/secure-web-gateway/fortiproxy)

##### Stateful Inspection
- A stateful firewall is a kind of firewall that **keeps track and monitors the state of active network connections** while analyzing incoming traffic and looking for potential traffic and data risks.
- Firewall is situated at Layer 3 and 4
- **State** is the most recent or immediate status of a process or application. In a firewall, the state of connections is stored, providing a list of connections against which to compare the connection a user is attempting to make. Devices that track state ascertain which states are safe and which pose threats.
- **Context** refers to Internet Protocol (IP) addresses, packets, and other kinds of data that can be used to provide evidence of repeated patterns. In the context of a connection, a stateful firewall can, for example, examine the contents of data packets that came through the firewall and into the network. If these packets contain unsafe data, they can be blocked by a stateful firewall in the future.

##### Circuit Monitoring


##### Next Generation Firewall (NGFW)
- Combines
	- Packet inspection
	- Stateful inspection
	- Deep packet inspection
	- Intrusion detection and prevention
	- Malware filtering
	- Antivirus
- Has multiple control points unlike traditional firewall which deploy firewall at perimeter (i.e. check only inflow and outflow packets).
- Example: [Fordigate](https://docs.fortinet.com/product/fortigate/7.4)
