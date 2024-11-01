




# subnetworks

IPv4 addresses consist of 4 bytes (32 bits) which are typically written as 4 decimal numbers separated by full stops. 

Each decimal number has a range from 0 to 255. e.g. `192.168.0.1` represents binary`11000000 10101000 00000000 00000001` or hex `0xC0A80001`

The 32 bits define an address range of 4.3 billion possible addresses.

The address range is divided into `sub networks` (or `subnets`) which define a range of IP addresses allocated to that subnetwork.

Subnets are specified using a 32 bit `network address` and an associated 32 bit `network mask` which determines how many sequential addresses are within the network.

Network masks are a sequential series of binary '1's (starting with the most significant bit) and which can be written like a network address. 

e.g. netmask `255.255.255.0` represents binary `11111111 11111111 11111111 00000000` or hex `0xFFFFFF00`

A network can also be defined in [CIDR Notation](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) by suffixing the count of '1' bits in a netmask to an IP address.

e.g  `192.168.0.0/24` represents a network address `192.168.0.0` and the 24 '1' bits in the netmask `255.255.255.0`

The network which an IP address occupies is determined by ANDing the netmask with the IP address.

If we are told that a device has an IP address of 192.168.0.8/24, we find it's subnetwork using AND

|               | IPv4 format  | Binary                             |
|:--------------|--------------|:-----------------------------------|
|Address        |192.168.0.8   |11000000 10101000 00000000 00000100 |
|Netmask  (/24) |255.255.255.0 |11111111 11111111 11111111 00000000 |
|               |AND           |                                    |                    
|Network Address|192.168.0.0   |11000000 10101000 00000000 00000000 |

The bottom address of this network is 192.168.0.0, and because we have 255 possible addresses in the 8 unmasked bits, the top address of this network will be `192.168.0.255`,
allowing us 256 possible addresses in this network definition.

Note however that the bottom address of this range is reserved the `network address` 192.168.0.0 and the top address of this range is reserved as the `broadcast address` 192.168.0.255 which leaves us 254 usable host addresses in this network.

THe `broadcast address` is used by a host in the subnet to send a message which will be received by all hosts in the subnet regardless of their ip address.

Lets take another example `192.168.10.1/30`

|               | IPv4 format    | Binary                             |
|:--------------|----------------|:-----------------------------------|
|Address        |192.168.10.1    |11000000 10101000 00001010 00000001 |
|Netmask  (/24) |255.255.255.252 |11111111 11111111 11111111 11111100 |
|               |AND             |                                    |                    
|Network Address|192.168.10.0    |11000000 10101000 00001010 00000000 |

In this case we only have 2 unmasked bits, so we can have 4 addresses in the subnet range `192.168.10.0 - 192.168.10.3`, with the broadcast address as `192.168.10.3`

We have 2 usable host addresses; `192.168.10.1` and `192.168.10.2`.

This very small subnet is typical of that defined for a user connecting to an ISP, where one of the host addresses will be the ISP's gateway router and the other host address the user's router.

Calculating the number range of hosts in a subnet using binary is tiresome. 

Fortunately a [subnet calculator](https://www.calculator.net/ip-subnet-calculator.html) can make this much easier.

## class A, B, C networks

in the past IANA alocated class netowrks now use CIDER as much more granualt

## netowrking using subnets

the following diagram shows how several routers form a network by routing between defined subnets.  

## public and private networks
A `public` IP address is an address which can be reached globally from anywhere on the Internet.

In order to avoid duplicate public addresses on the Internet, the [Internet Assigned Numbers Authority (IANA)](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority) coordinates with a hierarchy of `regional Internet registries (RIRs)` to allocate IP address ranges to Internet Service Providers, and end-user organisations in each country.















https://worldpopulationreview.com/country-rankings/ip-address-by-country


















notes - googe example https://www.lri.fr/~fmartignon/documenti/reseaux/3-RoutingForwarding-Martignon.pdf