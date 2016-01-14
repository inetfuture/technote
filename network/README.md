# References

- [High Performance Browser Networking](http://chimera.labs.oreilly.com/books/1230000000545/index.html)

# Misc

## Subnets

**No computer is directly connected to every other computer on the internet.** Instead, each computer is a member of one or more subnets. Subnets, in turn, **are connected to each other by machines called routers or gateways**, which belong to multiple subnets, forwarding internet traffic from one subnet to the other and reverse.

In order to successfully communicate with other computers throughout the internet, your computer must know what subnet it is part of, so that it knows what IP addresses are outside your local subnet and must be relayed through the gateway. In addition, your computer must of course also know the IP address of the gateway.

**Typically, a subnet is a group of consecutive IP addresses**, such as all IP addresses from 11.22.33.0 to 11.22.33.255. This is commonly expressed in either of two formats:

- **The subnet mask format. Here.** The subnet is expressed as 11.22.33.0 with subnet mask 255.255.255.0. **The subnet mask indicates what bits of the subnet IP address indicate the actual subnet, and what bits are variable, indicating individual computers in the subnet.** A byte consists of 8 bits, and 255 is 1111 1111 in binary. Therefore, 255.255.255.0 means that the first 3 bytes of the subnet IP address (11.22.33) indicate the actual subnet, and the last byte can be variable (and indicates computers in the subnet). If the subnet mask were 255.255.0.0, that would mean that the last two bytes are variable.
- **The significant bits format.** Here, the subnet is expressed as 11.22.33.0/24, which means subnet 11.22.33.0 with 24 significant bits. The 24 means that the first 24 bits of the subnet mask are 1, and all the following bits are 0. Thus, /24 is equivalent to a subnet mask of 255.255.255.0. /16 is equivalent to a subnet mask of 255.255.0.0. And because there are just 32 bits in an IP address, **/32 indicates an IP address with no variable part: a fixed, constant IP address.**

## Types of IP addresses and subnets

There are three major types of IP addresses (or subnets) that you need to be aware of.

- **Public IP addresses.** Most IP addresses in the 32-bit address range have the purpose of uniquely identifying a computer on the internet. The IP address 207.155.248.18, for example, is a public IP address that uniquely identifies one of the servers hosting the www.bitvise.com website (and others). This is the type of IP address through which a server must be reachable in order to be accessible to computers throughout the internet.
- **Private subnets.** Special ranges of the 32-bit IP address range have been set aside for use in private networks, where the computers in such a network do not need to be directly accessible from the internet as servers (but may nevertheless access the internet through a gateway, as clients). These ranges include:
10.0.0.0/8 (addresses from 10.0.0.0 to 10.255.255.255)
172.16.0.0/12 (addresses from 172.16.0.0 to 172.31.255.255)
192.168.0.0/16 (addresses from 192.168.0.0 to 192.168.255.255)
- **Special IP ranges.** There are several special purpose IP ranges, but the one you need to know about is 127.0.0.0/8 (addresses from 127.0.0.0 to 127.255.255.255). This is the local loopback range and is used to connect two programs running on the same machine. Any address in this range can be used for this kind of purpose, but the most commonly used are 127.0.0.1 and 127.0.0.2. The special DNS name 'localhost' translates to 127.0.0.1.
