Network routing is the **process of selecting a path** across one or more networks. The principles of routing can apply to any type of network, from telephone networks to public transportation.

In [packet-switching networks](/networking/Switching/Switch.md), such as the Internet, routing selects the paths for Internet Protocol (IP) packets to travel from their origin to their destination. These Internet routing decisions are made by specialized pieces of network hardware called [routers](/networking/Routing/Router.md).

### How does Routing works?
Routers uses their routing table to route packets to their destination. A routing table records the paths that packets should take to reach every destination that the router is responsible for. 

Routers work in the following way: when a router receives a packet, it reads the headers* of the packet to see its intended destination. It then determines where to route the packet based on information in its routing tables.

### Types of Routing:
1. Static routing
2. Dynamic routing

##### Static routing
Static routing tables do not change. A network administrator manually sets up static routing tables. This essentially sets in stone the routes data packets take across the network, unless the administrator manually updates the tables.

##### Dynamic routing
Dynamic routing tables update automatically. Dynamic routers use various routing protocols (see below) to determine the shortest and fastest paths. They also make this determination based on how long it takes packets to reach their destination.
Dynamic routing requires more computing power, which is why smaller networks may rely on static routing. But for medium-sized and large networks, dynamic routing is much more efficient.
![](/assets/networking/routing-protocols.png)


### Types of Dynamic Routing
1. **Interior Gateway Protocol:** Protocol used for routing inside an Autonomous System
2. **Exterior Gateway Protocol:** Protocol used for routing between Autonomous System

### Distance Vector Routing vs Link State Routing

| Distance Vector Routing | Link State Routing | 
|-|-|
| Router send information about their directly connected networks only to the neighbor | Router send the information about their link to all other routers |
| Each router selects best routes from the perspective of the neighbors | Each router makes router selection decisions itself |
| Slow convergence | Fast convergence |
| Low CPU and memory usage | Higher CPU and memory usage |
| Best route is advertised | All known route are advertised |
| Neighbor aware routing only | Complete network aware |
| Neighbor topology table | Global topology table |
| Time based updates | Event triggered updates |
| Split horizon / route poisoning | native routing loop prevention |
| | Floods when link failure or added new link |


### Administrative Distance
- Trust worthiness of the information received by the router.
- The Number is between 0 and 255.
- Less value is more trusted.
- The packet takes most trusted path when multiple protocol yields multiple path i.e. with the lowest value.
- Default administrative distances:
	- Directly connected -> 0
	- Static Route -> 1
	- EIGRP -> 90
	- IGRP -> 100
	- OSPF -> 110
	- RIP -> 120

### Dynamic Routing Protocols
1. RIPv1
2. RIPv2
3. IGRP
4. EIGRP
5. IS-IS
6. OSPF
7. BGP

##### RIPv1 (Router Information Protocol)
- It is classful version i.e. Does not support [VLSM](/networking/IP%20addressing/IPv4%20subnetting) (Variable Length Subnet Mask).
- There is no authentication.
- It uses Broadcast.
- Metric: **Hop count**
- It has been **obsolete**.
- Exchange of routing table every 30 sec.
- If multiple route has same number of hop count then does **Load balancing**.
- RIP timers:
	- Invalid timer: (30 + 150 sec) waits until declares invalid i.e. link failure
	- Flush timer: (180 + 60 sec) flushes the failed link data from routing table
	- Hold down timer: (30 + 150 sec) until gets best route
 - Convergence time: 240 sec
	 - It is time when the a link gets down time required to sync again.

##### RIPv2
- It is classless version i.e. supports [VLSM](/networking/IP%20addressing/IPv4%20subnetting) (Variable Length Subnet Mask).
- There is authentication.
- It used Multicast.

##### OSPF
- Metric: **Link Cost**