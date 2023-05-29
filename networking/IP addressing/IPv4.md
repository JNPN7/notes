![](/assets/networking/ipv4-decimal.png)
![](/assets/networking/ipv4-binary.png)

- converted binary into decimal
- Gateway is also called as router sometimes
- Gateway is used for communicating with host in another network
- 8 bit, 4 times so, 32 bit address
- Can take no 0 - 255
- Subnet mask acts as filter for an IP address. For figuring out which part is network bits and which are host bits.
    - 1 → network bits
    - 0 → host bits
- IP address and Gateway should be in same network for it to be valid

### IPv4 Classes
**IPv4 Classes identified by the first octet** ??:xx:xx:xx
1. Class A ⇒     1 - 127   -> 0000 0001 - 0111 1111 
2. Class B ⇒ 128 - 191   -> 1000 0000 - 1011 1111
3. Class C ⇒ 192 - 223  -> 1100 0000 - 1101 1111
4. Class D ⇒ 224 - 239  -> 1110 0000 - 1110 1111
5. Class E ⇒ 240 - 255  ->  1111 0000 - 1111 1111

#### Class C:
Subnet mask → 255.255.255.0
also can be represented in IP form → 192.168.100.225 **/24**
/24 → means 24 ones in subnet mask : 11111111.11111111.11111111.00000000

For 192.168.100.0
- Network ID (First): 192.168.100.0
- Valid IP Address Start: 192.168.100.1
- Valid IP Address End: 192.168.100.254
- Broadcast ID (Last): 192.168.100.255
No of valid ip: (2^**8** - 2) → 254

#### Class B:
Subnet mask → 255.255.0.0
also can be represented in IP form → 172.123.100.255 **/16**
/16 → means 16 ones in subnet mask : 11111111.11111111.00000000.00000000

For 172.123.100.0
- Network ID (First): 172.123.0.0
- Valid IP Address Start: 172.123.0.1
- Valid IP Address End: 172.123.255.254
- Broadcast ID (Last): 172.123.255.255
No of valid ip: (2^**16** - 2) → 65,534

#### Class A:
Subnet mask → 255.0.0.0
also can be represented in IP form → 100.138.108.215 **/8**
/8 → means 8 ones in subnet mask : 11111111.00000000.00000000.00000000

For 100.238.101.215
- Network ID (First): 100.0.0.0
- Valid IP Address Start: 100.0.0.1
- Valid IP Address End: 100.255.255.254
- Broadcast ID (Last): 100.255.255.255
No of valid ip: (2^**24** - 2) → 2,097,150
