Network devices or networking hardware are physical devices that are required for communication and interaction between hardware on a computer network.

**Types of network devices:**
1. Hub
2. [Switch](/networking/Switching/Switch.md)
3. [Router](/networking/Routing/Router.md)
4. Bridge
5. Gateway
6. Modem
7. Repeater
8. Access Point

##### Repeater:
A repeater operates at the **physical layer**. Its job is to regenerate the signal over the same network before the signal becomes too weak and corrupts so as to extend the length to which the signal can be transmitted over the same network. The repeaters do **not amplify the** **signal**. They copy the signal bit by bit and regenerates it at original strength. It is **2 port device**.

##### Hub:
A hub is basically a multiport repeater. A hub connects multiple wires coming from different branches. It is a center device in which devices are connected. It forms **star topology**.

Hubs cannot filter data, so data packets are sent to all connected devices. The **collision domain of all hosts connected through Hub remains one.**

They do not have intelligence to find out the best path for the data packets which leads to inefficiencies and wastage.

Types of Hub
1. **Active Hub:** There are hubs that have their own power supply and can clean, boost and relay the signal in the network. It serves both as a repeater as well as a wiring center. These are used to extend the maximum distance between nodes.
2. **Passive Hub:** These are hub that doesn't have. These hubs relay signals onto the network without cleaning and boosting them and can't be used to extend the distance between nodes.
3. **Intelligent Hub:** It works like active hubs and includes remote management capabilities. It also enables an administrator to monitor the traffic passing through the hub and to configure each port in the hub.

##### Bridge:
A bridge operates at the **data link layer**
- A bridge is a repeater with add on the functionality of filtering content by reading the MAC address of source and destination. It keeps record of connected devices and create separate route for each devices.
- They cannot control broadcast
- Bridges manage collision by software that slows down overall network performance
- Bridges have port limitation

##### [Switch](/networking/Switching/Switch.md):
A switch is a multiport bridge with a buffer and a design that can boost it's efficiency and performance. A switch is a **data link layer device**. They control collision at hardware level that improves overall network performance.

The switch can perform error checking before forwarding data, which makes it very efficient as it does not forward packets that have errors and forward good packet selectively.

The switch **divides the collision domain of hosts, but broadcast domain remains the same.**

##### [Router](/networking/Routing/Router):
Router can **control both collision and broadcast**. A router is a device like a switch that routes data packets based on their IP addresses. The router is mainly a **Network Layer device**. Routers normally connect LAN and WAN together and have a dynamically updating routing table based on which they make decisions on routing the data packets.

Four ways a router functions in network:    
1. Packet switching
2. Packet filtering
3. Inter-network communication
4. Path selection

##### Gateway:
Gateway is a **passage to connect two networks together** that may work upon different networking models. They basically work as the messenger agents that take data from one system, interprets it and transfer it to another system. Gateways are also called protocol converters and can operate at any network layer. Gateways are generally more complex than switches or routers. Gateway is called a **protocol converter**.


## Collision and Broadcast of devices:

| Device | Collision Domain | Broadcast Domain |
|--------|------------------|------------------|
|Hub|Single|Single|
|Bridge|Per port|Single|
|Switch|Per port|Single|
|Router|Per port|Per port|


# Terminology

### Broadcast domain:
Broadcast is a destination less message. It never carries user data. It is used by computer for network functionality. Domain is the group of computers sharing same characteristics.

A broadcast domain is logical division of a computer network in which all nodes reach each other by broadcast as the data link layer.

In broadcasting, a computer broadcasts and sends data, and all the computers in the networks gets the data


### Collision domain:
Collision domain is, as the name implies, the part of a network where packet collisions can occur. A collision occurs when two devices send a packet at the same time on the shared network segment. The packets collide and both devices must send the packets again, which reduces network efficiency.

Collision are often in hub environment, because each port on a hub is in the same collision domain. By contrast, each port on a bridge, a switch or a router is in a separate collision domain.
![](/assets/networking/collision-domain.png)

### CSMA/CD:
Carrier Sense Multiple Access/ Collision Detection (CSMA/CD) is a process that is used to send the data in shared environment.
- This process is used in HUB.
- All devices have equal priority.
- In this process only one device can send data at a time.
- Before a device sends data, it will first send the wire to ensure that no other device is currently sending data. If other device is currently using the media, it will have to wait till that transmission is over. If no device is currently using wire it can send the data.
- If two devices simultaneously sense wire and see no data in it, they could place their data on the wire at same time. In this situation collision will occur.
- When collision occurs, a special jam signal is created in the wire.
- Jam signal has a waiting time period. All devices have to wait till jam signal time period is over.
- Once this time period is over, devices can sense the wire again. Data lost in the collision have to be resend again.
