VLAN → Virtual LAN
- Logically Group
- Segment Broadcast
- Subnet Correlation

![](/assets/networking/vlan.png)

VLAN is _**sub-network**_ which can group together collections of devices on _**separate physical LANs**_(connected to different switch). VLAN is concept in which we can divide the devices logically on layer 2(data link layer). 
Generally, layer 3 devices divides broadcast domain from subnetting but broadcast domain can be divided by switches using the concept of VLAN.
A broadcast domain is a network segment in which if a device broadcast a packet then all the devices in the same broadcast domain will receive it.

#### Types of VLANs:
1. Static VLAN ⇒ Based on Port number
2. Dynamic VLAN ⇒ Based on MAC number

##### Static VLAN:
- Static VLAN are **based on port number**
- Need to **configure manually** i.e. Assign a port on a switch to a VLAN
- One port can be a member of only one VLAN
- It is also called **Port Based VLANs**
- Static VLANs is a group of ports designated by the switch as belonging to the same broadcast domain

##### Dynamic VLAN:
- Generally we don't use Dynamic VLAN
- Dynamic VLAN **are based on MAC address** of a PC
- Switch **automatically assign** the port to a VLAN
- Each port can be a member of multiple VLAN
- For Dynamic VLAN configuration, a software called **VMPS(VLAN Membership Policy Server)** is needed

##### Native VLAN:
- Default Native VLAN is VLAN 1
- If any packet is received without VLAN tagged then is assumed that it belongs to Native VLAN
- Untagged VLAN


# Configurations

![](/assets/networking/switch-conf-vlan.png)

- Show VLAN
```terminal
Switch# show vlan
```

- Creating VLAN
```terminal
Switch (config)# vlan 10
Switch (config-vlan)# name management  // assign name to vlan
Switch (config-vlan)# exit
```

- Assign ports to VLAN
```terminal
Switch (config)# int f0/1
Switch (config-if)# switchport ?
Switch (config-if)# switchport mode access  // set mode of port to access
Switch (config-if)# switchport access vlan 10  // set vlan to vlan 0
Switch (config-if)# exit
```

- Assign management IPs:
```terminal
Switch (config)# int vlan1
Switch (config-if)# ip add 10.1.1.1 255.255.255.0
Switch (config-if)# no sh
Switch (config-if)#
Switch (config-if)# int vlan 10
Switch (config-if)# ip add 192.168.1.10 255.255.255.0
Switch (config-if)# no sh
Switch (config-if)#
Switch (config-if)# int vlan 20
Switch (config-if)# ip add 192.168.2.10 255.255.255.0
Switch (config-if)# no sh
```

- Configure Trunks:
```terminal
Switch (config)# int f0/3
Switch (config-if)# switchport mode trunk
Switch (config-if)# exit
```