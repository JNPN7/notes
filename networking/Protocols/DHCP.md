DHCP: Dynamic Host Configuration Protocol
The DHCP is a network management protocol used on Internet Protocol(IP) networks for automatically assigning IP addresses and other communication parameters like subnet mask, default gateway and DNS server information on the device.

### Operation
The DHCP employs a connection less service model using the UDP.
DHCP consists of four phases:
1. Discovery
2. Offer
3. Request
4. Acknowledge
![](/assets/networking/dhcp.png)
>**UDP port**
>client: 68
>Server: 67

#### Discovery
The client broadcasts a DHCP-DISCOVER message on the network subnet using the destination address 255.255.255.255 (limited broadcast) or the specific subnet broadcast address (directed broadcast).
A DHCP client may also request its last known IP address.
![](/assets/networking/dhcp-discovery.png)

#### Offer:
When a DHCP server receives DHCP-DISCOVER message from the client, which is an IP address lease request. Then, the DHCP server reserves an IP address for the client and makes a offer by sending DHCP-OFFER message to the client.

The offer message consists of client MAC address, the IP address that the server is offering, the subnet mask, the lease duration, DNS servers and IP address of the DHCP server making the offer.
![](/assets/networking/dhcp-offer.png)

#### Request
In response to DHCP offer, the client replies with DHCP-REQUEST message, broadcast to the server, requesting the offered address. A client may receive DHCP offer from multiple servers, but it will accept only one DHCP offer.
![](/assets/networking/dhcp-request.png)

#### Acknowledgement
When the DHCP server receives the DHCP-REQUEST message form the client, the configuration process enters its final phase. The acknowledgement phase involves sending a DHCP-ACK packet to the client from server.

This packet includes the lease duration, subnet mask, router address, DHCP server, DNS servers, and any other configuration information that the client might have requested.
![](/assets/networking/dhcp-acknowledge.png)

#### Information
A DHCP client may request more information than the server has provided with the original DHCP-OFFER. The client may also request repeat data for a particular application.

Browsers use DHCP inform to obtain web proxy settings via WPAD (Web Proxy Auto-Discovery Protocol)

#### Releaseing
The client sends a request to the DHCP server to release the DHCP information and the client deactivates its IP address. As client devices usually do not know when users may unplug them from the network, the protocol does not mandate the sending of DHCP-RELEASE.


# Terminology

### Broadcast:
Broadcast is a frame or packet destined to everyone
- Layer 2 Header with Destination MAC Address:
    - FF:FF:FF:FF:FF:FF
- Layer 3 Header has two options Destination IP Address.
    1. Local Broadcast: 255.255.255.255
    2. Directed Broadcast: [Broadcast IP of each Subnet]
	    -> Disabled by default on all modern Routers and OS's

##### Local Broadcast:
- Sends packet to every host on local IP network
- 255.255.255.255

##### Directed Broadcast:
- Sends packet to every host on local IP network
- Sends packet to every host on foreign IP network
- [Broadcast IP of each Subnet] 24.10.1.255

