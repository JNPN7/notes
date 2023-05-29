Ethernet is a collection of network protocols/standards.
Ethernet is a network protocol that controls how data is transmitted over a LAN and is referred to as the IEEE 802.3 protocol.

Ethernet Standards
- Defined in the IEEE 802.3 standard in 1983
- IEEE ⇒ Institute of Electrical and Electronics Engineers

Ethernet Standards (copper)

|Speed | Common Name| IEEE Standards | Informal Name | Maximum Length | No of cables |
|-|-|-|-|-|-|
|10 Mbps | Ethernet | 802.3i | 10 BASE-T | 100 m | 2 pairs (4 wires) |
|100 Mbps | Fast Ethernet | 802.3u | 100 BASE-T | 100 m | 2 pairs (4 wires) |
|1 Gbps | Gigabit Ethernet | 802.3ab | 1000 BASE-T | 100 m | 4 pairs (8 wires) |
|10 Gbps | 10 Gig Ethernet | 802.3an | 10 GBASE-T | 100 m | 4 pairs (8 wires) |

BASE → baseband signaling
T → twisted pair

UTP cables ⇒ Unshielded Twisted Pair

#### 10 BASE-T and 100 BASE-T cables:
![](/assets/networking/cables-utp-fullduplex.png)
![](/assets/networking/cables-utp-straight-through.png)
![](/assets/networking/cables-utp-crossover.png)

| Device Type | Transmit (Tx) pins | Receive (Rx) pins |
|-|-|-|
| Router | 1 and 2 | 3 and 6 |
| Firewall | 1 and 2 | 3 and 6 |
| PC | 1 and 2 | 3 and 6 |
| Switch | 3 and 6 | 1 and 2 |

#### Auto MDI-X
Detects the Transmittion and receiving and changes pins functionally accordingly.
This helps to remove the conflict and we can use straight-through or crossover cable for any devices.
![](cables-auto-mdi-x.png)

#### 1000 BASE-T and 10 GBASE-T:
![](/assets/networking/cables-utp-bidirectional.png)
Bidirectional so fast.

#### Fiber-Optic Connection:
SFP Transceiver → Small Form-Factor Pluggable
![](/assets/networking/cables-fiber-optics.png)

| Information Name | IEEE standard | Speed | Cable Types | Maximum Length |
|-|-|-|-|-|
| 1000 BASE-LX | 802.3z | 1 Gbps | Multimode or Single-Mode | 550m (MM) 5km (SM) |
| 10 GBASE-SR | 802.3ae | 10 Gbps | Multimode | 400m |
| 10 GBASE-LR | 802.3ae | 10 Gbps | Single-Mode | 400m |
| 10 GBASE-ER | 802.3ae | 10 Gbps | Single-Mode | 400m |


### UTP vs Fiber Optics

| UTP | Fiber Optic |
|-|-|
|Lower cost than fiber optic | Higher cost than UTP|
| Shorter maximum distance than fiber optic (~100 m) | Longer Maximum distance than UTP |
| Can be vulnerable to EMI (Electromagnetic Interference) | No vulnerability to EMI |
| RJ45 ports used with UTP are cheaper than SFP ports | SFP ports are more expansive than RJ45 ports (single-mode is more expensive than multimode) |
| Emit (leak) a faint signal outside of the cable, which can be copied (security risk) | Does not emit any signal outside of the cable (no security risk) |
