An internet is a switched network in which a switch connects at least two links together. The two common types of switched networks are circuit switched and packet switched networks.
1. **Circuit-Switched Network**
	In circuit switched Network, dedicated connection called a circuit is always available (point to point connection). The work of switch is to make it active or inactive as par need.
	Circuit switching was very common in telephone network in the past, although part of telephone network today is packet switched network.
    There is no storing of data and transmission is continuous.
	
2. **Packet-Switched Network**
	In a computer network, the communication between the two ends is done in blocks of data called packets. In circuit the switching functions for both storing and forwarding the packets because a packet is an independent entity that can be stored and send later. The is a queue system while forwarding the packets.


Three method by which a switch can forward frames:
1. Store and forward: Checks all
2. Cut-through: Doesn't check any
3. Fragment free: Checks 64 bytes

# Port Modes and functions
![](/assets/networking/switch-port-modes.png)

### Dynamic Trunking protocol
It is only used by Cisco.
This protocol is a Cisco proprietary protocol
![](/assets/networking/switch-dtp.png)
No negotiable -> disable DTP

##### DTP configuration
1. **Switchport mode dynamic auto:** will form a trunk if the neighbor switch port is set to trunk or desirable. Trunk will not be formed if both sides are set to auto. Default on newer switches.
2. **Switchport mode dynamic desirable:** will from a trunk if the neighbor switch port is set to trunk, desirable or auto. Default on older switches.
3. **Switchport mode no-negotiate:** disables DTP

##### Switch functions:
1. Address Learning
2. Forwarding Decisions
3. Loop Avoidance ⇒ Spanning Tree Protocol (STP)


# Configurations

- Check all the ports
```terminal
Switch#show ip interface brief
Switch#sh ip int br
```

- Change Host name
```terminal
Switch(config)# hostname anyname
```

- Change Banner [It is the text that appears when logged in to the switch]
```
Switch(config)# banner motd &
```

- Add or change console password
```terminal
Switch (config)#line con 0
Switch (config-line)#password pass
Switch (config-line)#login
```

- Telnet password
```terminal
Switch (config)# line vty ? // vty ⇒ virtual telnet
	<0-15> first line number
Switch (config)# line vty 0 ?
	<1-15> last line number
Switch (config)# line vty 0 15
Switch (config-line)# password pass
Switch (config-line)# login
```

- Change enable password
```terminal
Switch (config)# en secret pass
```

- Change default gateway
```teminal
Switch (config)# ip default-gateway 10.0.0.254
```

- Saving Configuration
```terminal
Switch# write
Switch# copy running-config startup-config
Switch# copy run start
```

- Configure single port
```terminal
Switch (config)# int f0/1
```

- SSH
![](/assets/networking/switch-conf-ssh.png)
```terminal
Switch (config)# hostname sw1
sw1 (config)# ip domain-name ahsoka.org
sw1 (config)# crypto key generate rsa
sw1 (config)# ip ssh version 2
sw1 (config)# username ahsoka secret iamnojedi

sw1 (config)# line vty 0 15
sw1 (config-line)# transport input ssh
sw1 (config-line)# login local
```
