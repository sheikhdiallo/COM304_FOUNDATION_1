## Algorithm Used with Routing Table

The following steps are used by the router to forward packets.

### 1. Check Direct Routing

Determine if this packet is destined for a directly connected network.

To perform this check, the router performs a cross check and computes the 

Bitwise AND between the interface address and the interface netmask,

Bitwise AND between the destination address and the interface netmask.

If the two outcomes coincide, direct forwarding is performed on that interface.

For example, given the following interfaces

| interface | IP address  | Netmask       |Network (bitwise AND) |
|:----------|:------------|:--------------|:---------------------|
| eth0      |131.17.123.1 | 255.255.255.0 |131.17.123.0 |
| eth1      |131.17.78.1  | 255.255.255.0 |131.17.78.0 |
| eth2      |131.17.15.12 | 255.255.255.0 |131.17.15.0 |

Incoming packet 131.17.123.10 forwards to eth0.

|                        | IPv4 format  | Binary                             |
|:-----------------------|--------------|:-----------------------------------|
|Incoming packet Address |131.17.123.10 |10000011 00010001 01111011 00001010 |
|Netmask  (/24)          |255.255.255.0 |11111111 11111111 11111111 00000000 |
|                        |AND           |                                    |                    
|Network Address         |131.17.123.0  |10000011 00010001 01111011 00000000 |

|                        | IPv4 format  | Binary                             |
|:-----------------------|--------------|:-----------------------------------|
|eth0 interface address  |131.17.123.1  |10000011 00010001 01111011 00000001 |
|Netmask  (/24)          |255.255.255.0 |11111111 11111111 11111111 00000000 |
|                        |AND           |                                    |                    
|Network Address         |131.17.123.0  |10000011 00010001 01111011 00000000 |

Similarly incoming packet 131.17.78.30 forwards to eth1.

### 2. Check Indirect routing

If the direct routing crosscheck is negative for all the interfaces, indirect forwarding is performed using the routing table.

The very same crosscheck is performed for all the rows of the routing table using the corresponding netmask.

If the crosscheck is positive for multiple rows, the one with the highest number of 1s in its netmask is chosen (longest match). 
This means that we can specify an overlapping wide address range and a narrow address range.
The more specific narrow address range will be chosen in preference to the larger range.

This rule allows us to define a `default route` which will always be chosen if none of the other routes match.

`0.0.0.0` corresponds to the `default route` because the crosscheck is always positive but netmask length = 0

## Example Routes

Try working through the following examples.
In each case find where to route an IP address coming from the Test Router.

![alt text](../docs/images/routing2.drawio.png "routing2.drawio.png")

### Example 1

Where to route 131.175.21.86

| Network     | Netmask      | first hop |   |
|:------------|:-------------|:----------|---|
|131.175.15.0 |255.255.255.0 |131.175.21.1| X  |
|131.175.16.0 |255.255.255.0 |131.175.21.2| X  |
|131.175.17.0 |255.255.255.0 |131.175.21.3| X  |
|131.180.23.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.18.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.21.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.0.0  |255.255.0.0   |131.175.21.5| X  |
|0.0.0.0      |0.0.0.0       |131.175.12.254| X  |


| Interface     | IP Address   |  Netmask     |   |
|:--------------|:-------------|:-------------|---|
|interface 1:   |131.175.21.254| 255.255.255.0| X  |
|interface 2:   |131.175.12.253| 255.255.255.0|YES |

### Example 2

Where to route 131.175.16.65

| Network     | Netmask      | first hop |   |
|:------------|:-------------|:----------|---|
|131.175.15.0 |255.255.255.0 |131.175.21.1| X  |
|131.175.16.0 |255.255.255.0 |131.175.21.2| OK - THIS ONE |
|131.175.17.0 |255.255.255.0 |131.175.21.3| X  |
|131.180.23.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.18.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.21.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.0.0  |255.255.0.0   |131.175.21.5| X  |
|0.0.0.0      |0.0.0.0       |131.175.12.254| OK |


| Interface     | IP Address   |  Netmask     |   |
|:--------------|:-------------|:-------------|---|
|interface 1:   |131.175.21.254| 255.255.255.0|   |
|interface 2:   |131.175.12.253| 255.255.255.0|   |

### Example 3

Where to route 131.180.21.78

| Network     | Netmask      | first hop |   |
|:------------|:-------------|:----------|---|
|131.175.15.0 |255.255.255.0 |131.175.21.1| X  |
|131.175.16.0 |255.255.255.0 |131.175.21.2| X |
|131.175.17.0 |255.255.255.0 |131.175.21.3| X  |
|131.180.23.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.18.0 |255.255.255.0 |131.175.21.4| X  |
|131.180.21.0 |255.255.255.0 |131.175.21.4| OK - THIS ONE |
|131.180.0.0  |255.255.0.0   |131.175.21.5| OK  |
|0.0.0.0      |0.0.0.0       |131.175.12.254| OK |


| Interface     | IP Address   | Netmask      |   |
|:--------------|:-------------|:-------------|---|
|interface 1:   |131.175.21.254| 255.255.255.0|   |
|interface 2:   |131.175.12.253| 255.255.255.0|   |

examples taken from (https://www.lri.fr/~fmartignon/documenti/reseaux/3-RoutingForwarding-Martignon.pdf)
