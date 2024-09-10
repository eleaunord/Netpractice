NB : ex06 to ex10 at the exam

## How TCP addressing works

TCP = Transmission Control Protocol. Used so that application programs and devices can exchange messages over a network. Send "packets" (small segment of larger messages) across the internet.
Using TCP, we can make sure that the entire data is being communicated over a network. Before any data transmission, TCP first establishes a connection between a source and its destination. This connection remains active until communication begins. 

## How IP addressing works

IP = Internet Protocol. Part of the internet protocol suite that also includes TCP. Usually known together as TCP/IP. Governs rules for packetizing, adressing, etc. 
Used to assign addresses to devices on a network. Each device connected to the internet requires a unique IP address. 

Two parts of the IP adress : 1/ host 2/ network it belongs to.

These two parts are distingues by a subnet mask.

## Subnet mask

A 32 bits/4 bytes address. Calculated using bitwise AND. 

IP address | 01101000.11000110.11110001.01111101
Mask       | 11111111.11111111.11111111.10000000

Network address | 01101000.11000110.11110001.00000000
Which translates to a network address of 104.198.241.0.

NB : Bitwise AND
Compares each bit in the corresponding pos of 2 binary nums.
- Input 1: 1010
- Input 2: 1100
- Result: 1000
Because :
- The leftmost bits: 1 AND 1 = 1
- The second bits: 0 AND 1 = 0
- The third bits: 1 AND 0 = 0
- The fourth bits: 0 AND 0 = 0

## Range of host addresses

IP address | 01101000.11000110.11110001.01111101
Mask       | 11111111.11111111.11111111.1**0000000**

Possible range = **last** bits of the mask

BINARY  | 0000000 - 1111111
DECIMAL | 0 - 127

BUT range extremities reserved for specific uses

104.198.241.0   | Reserved to represent the network address.
104.198.241.127 | Reserved as the broadcast address; used to send packets to all hosts of a network.

So our range of possible IP addresses becomes 104.198.241.0 - 104.198.241.126

CIDR notation (using /)
255.255.255.128 in binary is:
11111111.11111111.11111111.10000000
In this binary representation:
- The 1s represent the network portion of the address.
- The 0s represent the host portion of the address.
In this case, there are 25 ones (1s) followed by 7 zeros (0s). so /25 in CIDR notation

## Switch

Connects mult devices together in a single network. ONly distributes packets to its local network. Cannot talk directly to a network outside of its own.

## Router

Connects mult devices together like a switch but can connect mutiplie networks together. Has an interface for each network it connects to. 
CAREFUL : Ip addresses range on one interface must not overlapp on the other ow it will mean that they're on the same network. 

### Routing table 

Declares the routes to network destinations. Destination to (default 0.0.0.0/0, when no other route is available for an IP destination address) -> next hop (IP adress of the next router on the packet's way)
For eg, destination default is equivalent to 0.0.0.0/0, which will send the packets indiscriminately to the first network address it encounters. A destination address of 122.3.5.3/24 would send the packets to the network 122.3.5.0.
The **next hop** is the IP address of the next router (or internet) interface to which the interface of the current machine must send its packets. 

## Exo notes

/24 subnet mask is equivalent to 255.255.255.0.
