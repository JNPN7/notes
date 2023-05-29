ARP: Address Resolution Protocol
The Address Resolution Protocol (ARP) is a communication protocol used for discovering the link layer address, such as MAC address, associated with a given internal layer address. This mapping is critical function in the internal protocol suite.

The Address Resolution Protocol is a request-response protocol whose messages are encapsulated by a link layer protocol. It is communicated within the boundaries of a single network, **never routed across inter-networking nodes**.

IP → MAC
Logical → Physical

Request ⇒ Broadcast
Response ⇒ Uni-cast

The ARP's main task is to convert the 32-bit IP address (for IPv4) to 48-bit MAC address. It is used when one device wants to communicate with some other device on a local network.

### How ARP works?
All OS in an IPv4 networks keep an ARP cache. When the host request a MAC address to send packets to another host in the LAN, it checks its ARP cache to check that the MAC address translation already presents. If it isn't present in the cache then, the host does ARP request. The arp request is broadcasting. In request header there consists protocol, self IP address, self MAC address, destination IP address, broadcast MAC address which is usually (ff:ff:ff:ff:ff:ff). Then the respective device responses uni-casts with its MAC address. The source host then saves MAC address in the ARP cache for future use and sends packet dedicated to the MAC address.

### Important ARP terms:
1. **ARP Cache:** After resolving the MAC address, the ARP sends it to the cache stored in a table for future reference. The subsequent communication can use the MAC address form the table.
2. **ARP Cache Timeout:** It is the time for which the MAC address in the ARP cache can reside.
3. **ARP request:** Broadcasting a packet over the network to validate whether we came across the destination MAC address or not.
4. **ARP response:** The MAC address response that the source receives from the destination, aids in further communication of the data.

### Address Resolution Methods:
Association between a protocol address and a hardware address is known as binding.
There are three techniques used for this purpose:
1. **Table lookup:** Binding stored in memory with protocol address as the key. It uses the protocol address to find the hardware address by mapping protocol address with mac address and storing in memory.
2. **Dynamic:** This type of network messaging method is type of network messaging method is used for “just-in-time” resolution. Data link layer sends message request in a hardware address. destination responds.
3. **Closed-form computation:** In this method, a protocol address is based on a hardware address. Data link layer calculates/derives hardware address form the protocol address.

### Types of ARP
1. Simple ARP [Above]
2. Proxy ARP
3. Gratuitous ARP
4. Reverse ARP
5. Inverse ARP

##### Proxy ARP
This ARP occurs for inter-networking. Routers do not forward Broadcasts, so they will send their own MAC address to the host in another network. This process is called proxy ARP.
![](/assets/networking/arp-proxy.png)

##### Gratuitous ARP (GARP):
Gratuitous is type of ARP request of the host which helps network to identify the duplicate IP address. Therefore, when an ARP request is send by a router or switch to get its IP address, no ARP responses are received. So that no other nodes can use the IP address allocated to that switch or router.
It is something performed by computer while booting up. When the computer booted up (Network Interface Card is powered) for the first time, it automatically broadcast its MAC address to the entire network. After Gratuitous ARP MAC address of the computer is known to every switch and allow DHCP servers to know where to send the IP address if requested. Gratuitous ARP could mean both Gratuitous ARP request and Gratuitous ARP reply, but not needed in all cases. Gratuitous ARP request is a packet where source and destination IP are both set to IP of the machine issuing the packet and the destination MAC is the broadcast address ff:ff:ff:ff:ff:ff ; no reply packet will occur.

##### Reverse ARP (RARP):
RARP is a type of arp which maps a known MAC address to an IP address. Hosts such as diskless workstations (also known as thin clients) know their MAC address when they boot. They use RARP to discover their IP address from a server on the network.

##### Inverse ARP (InARP):
Layer 2 address to layer 3 address. Frame relay uses inverse arp. Inverse arp is to associate a **DLCI** with an ip address. InARP is widely used for ATM networks frame relays where Layer 2 virtual circuit addressing acquired from Layer 2 signaling.

### ARP header
![](/assets/networking/arp-header.png)
1. Hardware Type: It is 1 for Ethernet.
2. Protocol Type: It is protocol used in the network layer.
3. Hardware Address Length: It is length in bytes so that it would be for Ethernet.
4. Protocol Address Length: Its value is 4 bytes.
5. Operation Code: indicates that packet is an ARP Request (1) or an ARP Response (2).
6. Senders Hardware Address: It is hardware address of source node.
7. Senders Protocol Address: It is layer 3 address of source node.
8. Target Hardware Address: It is used in a RARP request, which response impact both the destination's hardware and layer 3 addresses.
9. Target Protocol Address: It is used in an ARP request when the response carried both layer 3 addresses and the destination's hardware.


### What is ARP poisoning (ARP spoofing)
ARP spoofing is a type of network attack in which the attacker sends the falsified ARP request over the LAN (say to the default gateway), which results connecting attacker’s MAC address to the legitimate server on that victim network. Now, the attacker will start receiving the data which was intended for that IP address. With the help of ARP Poisoning (or ARP Spoofing) attacker is able to intercept data frames, modify traffic or even stop data in-transit.
![](/assets/networking/arp-poisoning.png)
