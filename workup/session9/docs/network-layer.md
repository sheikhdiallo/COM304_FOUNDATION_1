[Main Menu](../../README.md) | [session9](../../session9/) | [Network Layer](../docs/network-layer.md)

# Network Layer (OSI layer 3)

The Internet Packet frame format is shown below

![alt text](../docs/images/IPv4_Packet-en.svg.png "Ethernet_Type_II_Frame_format.svg.png")

#### Internet Addresses

The Internet V4 protocol defines a 32 bit IP address for each device in the network. 
Each network layer frame has a `source IP address` and a `destination IP address` which is used by the network layer to deliver the frame to the correct device. 

IPv4 addresses consist of 4 bytes which are typically written as 4 decimal numbers separated by full stops. 

Each number has a range from 0 to 255. e.g. `192.168.0.1` represents binary`11000000 10101000 00000000 00000001` or hex `0xC0A80001`

The original Internet design (IPv4) assumed 32 bits were enough to cover the projected number of computers in the world (4.3 billion addresses available).
Internet addresses are allocated globally by the Internet Assigned Numbers Authority (IANA) which announced that the available address allocations began to be exhausted on 31 January 2011 (see [IPv4_address_exhaustion](https://en.wikipedia.org/wiki/IPv4_address_exhaustion))

Fortunately, IPv6 is being introduced which has a much larger address range.
An IPv6 address has 128-bits and is usually written in hex e.g. `2001:db8:3333:4444:5555:6666:7777:8888`

There are 340 undecillion (2128 or 3.4×1038) possible IPv6 addresses, which is more than 100 times the number of atoms on Earth. 
This means that there is enough space for trillions of Internet devices for the foreseeable future.

(We will just look at IPv4 for now).

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

In the past (prior to 1993) IANA allocated ranges of ip addresses to networks in large chunks or [network classes](https://en.wikipedia.org/wiki/Classful_network).
There were 128 Class A networks with 16,777,216 addresses per class A,  
16,384 Class B networks with 1,073,741,824  addresses per class B and
2,097,152 Class C networks with 536,870,912  addresses per class C.

Class A networks were assigned to [large organisations and regional Internet registers](https://en.wikipedia.org/wiki/List_of_assigned_/8_IPv4_address_blocks) and some of these allocations still remain in place.

This classification of sub networks proved to be inefficient and resulted in a mismatch between the allocated address ranges and the actual needs of organisations. 
Classful networks gave way to [Classless Inter-Domain Routing (CIDER)](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) in 1993.

## public and private networks
A `public` IP address is an address which can be reached globally from anywhere on the Internet.

In order to avoid duplicate public addresses on the Internet, the [Internet Assigned Numbers Authority (IANA)](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority) coordinates with a hierarchy of `regional Internet registries (RIRs)` to allocate IP address ranges to Internet Service Providers, and end-user organisations in each country.

Several ranges of addresses have been reserved as [private IP addresses](https://en.wikipedia.org/wiki/Private_network).
These addresses are for internal use only and not for routing across the Internet.

Most Internet service providers (ISPs) allocate only a single publicly routable IPv4 address to each residential customer, but many homes have more than one computer, smartphone, or other Internet-connected device. In this situation, a network address translator (NAT) gateway is usually used to provide Internet connectivity to multiple hosts.

## network routing using subnets

`Routers` are network devices which relay IP packets from router to router across a network towards their destination. 
A router can have many interfaces, each connected to different subnetworks.

A router (or computer) will also have an internal `loopback` interface which it uses to originate or consume traffic destined for itself.
The `loopback` interface is given the IP address of the device itself and is the address other devices use to communicate with the device itself.
The `loopback` interface usually also has a local IP address of `127.0.0.1` with a DNS name of `localhost`.

IP networks operate using `next hop routing` which means that routers are basically very simple.
When they receive an IP packet, they can only forward it to one of the attached subnetworks or to the `loopback` interface (to be consumed as a message sent to the device itself).
So a packet hops between routers from subnetwork to subnetwork until it reaches its final destination.

When a router receives a packet, it must decide which interface to forward it to.

A `routing table` is used by each router to determine the most optimal next hop (or subnetwork) a packet must be forwarded to to reach its final destination.

`Direct Forwarding` happens when the destination is within a directly attached subnetwork.

`Indirect Forwarding` happens when the destination is elsewhere and the router must decide which is the best port to forward the packet to move it closer to its destination.

A `static route` is a route which has been manually entered in the routing table. 

Networks can be fully described using manually assigned static routes but this is complex and error prone.
Instead, in large networks, [routing protocols](https://en.wikipedia.org/wiki/Routing_protocol) are used by routers to discover optimal routes and set up the routing tables automatically using `dynamic routes`.

In this unit we will only look at simple static routing.