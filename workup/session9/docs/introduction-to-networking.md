[Main Menu](../../README.md) | [session9](../../session9/) | [Introduction to Networking](../docs/introduction-to-networking.md)

# Introduction to Networking

In this section we will give a basic introduction to `networking`.
That is, how computers and devices communicate with each other over the Internet.

![alt text](../docs/images/simplifiedNetworkLayers.drawio.png "simplifiedNetworkLayers.drawio.png")


physical layer - Mac addresses
IP layer - Ip addresses

TCP/UDP  ports
NAT

finding other devices on the netowrk -ARP

routing tables
routing protocols

DNS - translating IP addresses to

# notes

on windows terminal try arp -a

```
PS C:\Users\cg02r> arp -a

Interface: 192.168.10.101 --- 0x12
  Internet Address      Physical Address      Type
  192.168.10.1          00-14-d1-57-11-ad     dynamic
  192.168.10.102        b8-27-eb-5b-24-76     dynamic
  192.168.10.255        ff-ff-ff-ff-ff-ff     static
  224.0.0.22            01-00-5e-00-00-16     static
  224.0.0.251           01-00-5e-00-00-fb     static
  224.0.0.252           01-00-5e-00-00-fc     static
  239.192.152.143       01-00-5e-40-98-8f     static
  239.255.255.250       01-00-5e-7f-ff-fa     static
  255.255.255.255       ff-ff-ff-ff-ff-ff     static
```

On pi try `arp -a` or `arp`

```
admin@raspberrypi01:~ $ arp -a
wstaff-79-128-1.solent.ac.uk (10.79.128.1) at b4:0c:25:e2:80:10 [ether] on wlan0
192-168-x-x.solent.ac.uk (192.168.10.1) at 00:14:d1:57:11:ad [ether] on eth0
192-168-x-x.solent.ac.uk (192.168.10.101) at 34:48:ed:03:cc:73 [ether] on eth0
admin@raspberrypi01:~ $ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
wstaff-79-128-1.solent.  ether   b4:0c:25:e2:80:10   C                     wlan0
192-168-x-x.solent.ac.u  ether   00:14:d1:57:11:ad   C                     eth0
192-168-x-x.solent.ac.u  ether   34:48:ed:03:cc:73   C                     eth0
admin@raspberrypi01:~ $ ^C
admin@raspberrypi01:~ $ 

```

https://superuser.com/questions/29640/inverse-arp-lookup

https://www.networkworld.com/article/969445/checking-network-connections-with-arp-and-ip-neigh.html
