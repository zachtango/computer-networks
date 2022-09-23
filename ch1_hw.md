
# Chapter 1 Review Questions

R1. Hosts and end systems are synonymous. Hosts host applications and end systems are located in the network edge, but they both refer to the same type of machine.

Some examples of end systems include laptops, desktops, web servers, phones, refrigerators, and cars.

R2. Wikipedia defines diplomatic protocol as a rule that describes how an activity should be performed. This is similar to the network definition for protocol. A network protocol defines the format of messages and actions taken when sending or receiving them or in response to other events.

R3. Standards are important for protocols because we need communicators to agree on what specific protocols do to be able to use them to communicate with each other effectively. This agreement about what the protocols specifically do are called standards. Network standards are created by the Internet Engineering Task Force and are documented in their Request for Comments (RFCs)

R4. DSL, Cable (HFC), FTTH, and 5G are home access technologies.
Ethernet LAN and Wireless LAN are enterprise access technologies (but they're also being increasingly used in homes).
4G and 5G are wide-area wireless access technologies.

R5. HFC transmission rate is shared among users because the users all transmit over the same coaxial cable, which is a broadcast cable. Collisions are possible in a downstream HFC channel because the channel is shared, so messages to different users can collide on the shared medium.

R7. The transmission rate of Ethernet LANs are ??

R8. Physical media Ethernet can run over coaxial cables and copper wires. ??

R9. HFC is a transmission rates are shared. DSL transmission rates are dedicated (dedicated phone line). FTTH transmission rates are dedicated (direct fiber). ??

R10. The most popular wireless Internet access technologies today are 4G and 5G. 4G transmits at a lower rate than 5G. ??

R11. L / R1 + L / R2

R12. Circuit-switched networks dedicate the resources needed for a communication between two or more end systems. As a result, the resources are reserved for the end systems communicating, so this leads to better performance and reliability compared to packet-switched networks (no packet loss). TDM has the advantage of allocating the full bandwidth for a connection over FDM, leading to higher transmission rates.

R13. 
a. 2
b. There will be no queuing delay because the users together transmit at most 2 Mbps in a 5 second time period.  ???

R14. Two ISPs at the same level of hierarchy peer with eachother to reduce traffic sent to their providers, the upper tier ISPs, by sharing it with the same level ISPs. Doing this will reduce the costs because they have to pay their providers based on their traffic amounts, but peering is often free. IXPs earn money by hosting an area where other ISPs can connect to to peer together. This area is usually a building full of switches.

R15. Google's network consists of large, powerful datacenters connected together by their private network, creating a CDN. They peer their CDN with other ISPs directly or at IXPs. They also connect their CDN to tier-1 ISPs. Content providers create their own CDN to restrict traffic in this network to traffic associated with their content. This allows them to provide content quicker and more efficiently. This also saves the company money because most of their traffic is traveling through their CDN rather than ISP providers they'd have to pay.

R16. The delays are processing delay, queuing delay, transmission delay, and propogation delay. Queuing delay is the only variable delay, while the other delays are constant.

R18. It takes a packet d / s seconds to propogate over a link. This delay don't depend on packet length or transmission rate. 10 ms

R19. 

a. R1 is the bottleneck, so the throughput is 500 kbps.
b. 4 * 10^6 * 8 / 500 / 10^3 = 64 seconds
c. R2 is the bottleneck now, so the throughput is 100 kbps. The time would be 320 seconds (64 * 5).

R20. The large file is divided into parts (bits) and packaged with headers specifying the packet's destination. end system A then sends these packets to the edge router to be sent to end system B. The information a router uses to determine an arriving packet's link is the packet's IP address. Packet switching is analogous to driving from one city to another and asking directions along the way because the packets are transmitted to packet switches, where are where the packets "ask" for directions to their destination. The packet switch forwards these packets to the next packet switch in their route, similar to giving instructions to the next place to drive.

R22. ??

R23. Application, Transport, Network, Link, Physical.

The application layer contains network applications and is responsible for allowing these network applications on different systems to communicate with each other using application layer protocols. The applications communicate using messages which are passed to the transport layer for transportation.

The transport layer is responsible for the logical connection between two network applications. It provides process-process communication and error checking. It takes the application messages, separates them, and encapsulates each separated item with header info to create segments. Then, the segments are passed to the network layer to be delivered to the host.

The network layer is responsible for routing and delivering the segments received from the transport layer to their destination. The packets are called datagrams.

The link layer is repsonsible for sending the datagrams from the beginning of a link to the end. The packets are called frames.

The physical layer is responsible for transmitting the bits of the datagrams.

R24. An application-layer message is used to communicate with other hosts. The application-layer protocol used decides the format of the message and the actions taken for sending and receiving them. A transport-layer segment contains the application-layer message encapsulated with transport-layer header information. A network-layer datagram contains the transport-layer segment encapsulated with network-layer header info. A link-layer frame contains the network-layer datagram encapsulated with link-layer header info.

R25. A router processes the network layer, link layer, and physical layer. A link-layer switch processes the link layer and physical layer. A host processes all 5 layers.

