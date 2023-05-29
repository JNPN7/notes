Subnetting is:
- Network within a network
- Logically division of IP address
- Saves IP addresses

Subnetting allows to create multiple logical networks that exists within a single Class A, B or C network.

Each data link on a network must have a unique network ID, with every node on that link being a member of the same network. If you break a major network [(Class A, B or C)](/networking/IP%20addressing/IPV4.md) into smaller sub-networks, it allows you to create a network of interconnecting sub-networks. Each data link on this network would then have a unique network/sub-network ID. Any device, or gateway, that connects n networks/sub-network has n distinct IP addresses.
![](/assets/networking/subnetting.png)

#### Class C Subnetting:
![](/assets/networking/subnetting-class-c.png)

![](/assets/networking/subnet-before-after.png)

![](/assets/networking/subnet-wheel.png)

| | | |
|-|-|-|
| 204.17.5.0 | 255.255.255.224 | host address range 1 to 30 |
| 204.17.5.32 | 255.255.255.224 | host address range 33 to 62 |
|204.17.5.64 | 255.255.255.224 | host address range 65 to 94 |
|204.17.5.96 | 255.255.255.224 | host address range 97 to 126
|204.17.5.128 | 255.255.255.224 | host address range 129 to 158 |
|204.17.5.160 | 255.255.255.224 | host address range 161 to 190 |
|204.17.5.192 | 255.255.255.224 | host address range 193 to 222 |
|204.17.5.224 | 255.255.255.224 | host address range 225 to 254 |

>                       128  64  32  16  8  4  2  1
> 255.255.255.    1     1     1    1   1  1  1  1

#### Class A Subnetting:
![](/assets/networking/subnetting-class-a.png)


#### Class B Subnetting:
![](/assets/networking/subnetting-class-b.png)
