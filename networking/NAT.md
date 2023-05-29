NAT: Network Address Translation
PAT: Port Address Translation

| **NAT** | **PAT** |
|----------|--------|
| Network Address Translation | Port Address Translation |
|NAT implies translation of an IP address to another IP address. | PAT implies translation of IP address and port to another IP address and port.|
| NAT affect only L3 header (IPv4 header) | PAT affects both L3 and L4 header (IPv4 header and either TCP or UDP header) |
|   | One can consider PAT as a subset of NAT (i.e. Network address translation along with a Port translation) |

Private IPv4 Addresses:
1. 10.0.0.0        /8    - any IP address in the range of 10  .      #      .   #   .   #
2. 172.16.0.0    /12   - any IP address in the range of 172 . |16-31| .   #   .   #
3. 192.168.0.0  /16   - any IP address in the range of 192 .    168   .   #   .   #

Static translation
- Explicit mapping between pre-translation and post-translation
- Example: Translate 10.0.0.2 to 171.23.42.4
- Administrator explicitly defines pre and post mapping
- Permanently mapped

Dynamic translation
- pre-translation attributes are defined by admin
- post-translation attributes are selected by translation device
- Example: Translate anything in 10.6.6.0/24 to 72.9.4.22, 72.9.4.23 or  72.9.4.24
- Translation device choose post-translation attributes
- Temporarily mapped
- Dynamic mapping is sometimes referred as One to Many or Many to One translation

Static NAT
- Explicit mapping of an IP address to another IP address
- Static NAT makes internal resources externally accessible
- Inbound packet: destination gets translated
- Outbound packet: source gets translated
- Packet are translated whether initiated by internal or external host (i.e. static NAT is bidirectional)
- Static NAT does not conserve IP address

Static PAT
- Explicit mapping of an IP:Port to another IP:Port
- Static PAT makes internal ports externally accessible
- Facilitates using Non-Standard ports
- Port forwarding / Hole punching
- Bidirectional
- Multiple Servers can use same IP address (i.e. it conserve IP address)

Dynamic PAT
- Router keeps track using Router's translation table
- Unidirectional (Traffic must be initiated form inside)
- Allows many hosts with Private IP to share one Public IP
- Greatest potential for IP Address conservation
- Each shared Public IP allow more than ~65000 connections

Dynamic NAT
- Ports are not translated
- Multiple device cannot share IP addresses
- Bidirectional while connection is active
	- Useful of protocols which require secondary inbound connections to the client (FTP)
- Use-case: Lazy Static NAT 
	 - but only if number of hosts is equal to IP address in translation
	 - Exact mapping of Private IP to Public IP is irrelevant
- Disadvantage
	- Non Deterministic IP assignments
	- Inconsistent connectivity


Policy NAT
- In above only source was used.
- In Policy NAT, translation decision based on matching both source and destination
- Example: Dynamic PAT Configuration
	- If source is 10.6.6.0/24 and destination is 45.5.4.9 -> Dynamic PAT source to 32.6.2.77
	- If source is 10.6.6.0/24                                              -> Dynamic PAT source to 32.6.2.78

Twice NAT
- Translates both Source and Destination of the packet
- Packets are still translated using: 
	- Static NAT, Static PAT, Dynamic NAT, Dynamic PAT
- Example: 
	- If source is 10.6.6.0/24 and destination is 8.8.8.8 (Google DNS server) -> Dynamic PAT source to 32.6.2.77 and Static NAT destination to 32.9.1.8 (corporate DNS server)
- It is a policy NAT