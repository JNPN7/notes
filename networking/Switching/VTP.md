VTP: [VLAN](/networking/Switching/VLAN.md) Trunking Protocol
- Not a TRUNKING protocol
- Two trunking protocol : ISL(Inter Switch Link) and 802.1q
- VTP is CISCO proprietary protocol used to maintain consistency thoughout the network or user can say that synchronizing the VLAN information is same VTP domain.
- VTP allows us to add, delete and rename VLANs which is then propagated to other switches in the VTP domain.
- VTP advertisements can be sent over 802.1Q, and ISL trunks.

### Requirements:
1. The VTP version must be same on the switches user wants to configure.
2. VTP domain name must be same on the switches.
3. Authentication should match if applied.

### VTP modes:
1. Server
2. Client
3. Transparent

##### Server
• The switches are set to this mode by default. 
• This mode allows us to create, add and delete VLANs.
• Any changes that is done on this mode(on a particular switch) will be advertised to all the switches that are in same VTP domain.
• In this mode, the configuration are saved in NVRAM.

**Configuration:**
- Making switch VTP server
```terminal
Switch# config t
Switch(config)# vtp mode server
```
- Assigning a password for authentication in VTP domain
```terminal
Switch(config)# vtp domain mydomain
Switch(config)# vtp password pass
```
- Verify configuration
```terminal
Switch(config)# do show vtp password
Switch(config)# do show vtp ?
```


##### Client
- In this mode, the switches receives the updates and can also forward the updates to other switches(which are in same VTP domain).
- The updates received here is not saved in NVRAM so all the configuration will be deleted if the switch is reset or reloaded i.e. the switches will only learn and pass the VTP summary advertisements to other switches.

**Configuration:**
- Making switch VTP client
```terminal
Switch(config)# vtp mode client
```


##### Transparent
- This mode only forwards the VTP summary advertisements through trunk link.
- The transparent mode switches can make their own local database which keep secret from other switches.
- The whole purpose of transparent mode is to forward the VTP summary advertisements but not to take part in VLAN assignments.

**Configuration:**
- Changing mode to Transparent
```terminal
Switch(config)# vtp mode transparent
```


### Configuration Revision Number:
- The configuration revision number is a 32-bit number that indicates the level of revision for the VTP packet.
- This configuration number is tracked by each switch in order to find that the received information is more recent than the current version.
- Every time one modification is done on the VLANs by the server switch, the configuration revision number increases by one.
- %%This bring a great disadvantage.%%


### VTP Pruning:
VTP ensures that all switches in the VTP domain are aware of all VLANs. However there are occasions when VTP can create unnecessary traffics. All unknown unicasts are broadcasts in a VLAN are flooded over the entire VLAN. All switches in the network receives all broadcasts, even in situations in which few users are connected in that VLAN. VTP pruning is a feature that we use in order to eliminate or prune this unnecessary traffic.

Forwarding traffic related to specific VLANs only.
