
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

## Problems

P2. given P packets, it will take the Pth packet (P - 1) L / R + N * L / R

P3. N bits per k seconds at a steady rate.

a. A circuit-switched network would be more appropriate for this application because the application transmits at a steady rate for a long period of time, so dedicated resources for this transmission would increase performance and reliability. The application will also transmit for a long period of time, so it will fully utilize the circuit-switched network's resources because it will be transmitting all of that period.

b. No form of congestion control is needed because the application data rates are less than the capacities of every link, so every link will be able to store and forward the data without the queue ever overflowing given that the application's traffic is the only one in the network.

P4.
a. 16

b. 8

c. Yes

P5.
a. 10 cars / 1 car per 12 seconds = 120 seconds at a toll booth

175 km / 100 km per hour = 1.75 hours

end-to-end delay = 1.75 hours + 1.75 hours + 3 * 120 seconds = 3.5 hours + 6 minutes = 216 minutes

b. 8 / 1 car per 12 seconds = 96 seconds at toll booth

end-to-end delay = 3.5 hours * 2 * 96 seconds = 210 minutes and 192 seconds = 213 minutes + 12 seconds

P6.
a. d prop = m / s

b. d trans = L / R

c. d end-end = d prop + d trans

d. The last bit of the packet is at the start of the link. 

e. The first bit of the packet is at the start of the link.

f. The first bit of the packet is at the start of the link.

g. 600000

P7. R = 10 Mbps, d prop = 10 msec, 56-byte packet
    56 * 8 / (10 * 1000 * 1000) + 10 msec = 10.0448 msec

P8. R = 10 Mbps, each user requires 200 kbps, each user transmits 10 percent of the time

a. 50 users can be supported using circuit switching

b. 10%

c. P(n) = 120! / [ (120 - n)! * n! ] * (0.1)^n * (0.9)^(120 - n)

d. The probability is vero close to 0 --> 0.

P9.

a. 1 * 10^3 * 10^3 / 100 = 10000

P10.

d end-end = (L / Ri + di / si) sum over i in (1, 2, 3) * 2 d proc

d end-end = 3 (1500 * 8 / 2.5 / 1000 / 1000) s + 10000 * 10^3 / (2.5 * 10^8) s + 2 * 3msec = 57.4 msec

P11. d end-end = L / R + 0.04 sec

P12. 4 packets in q, 1 packet halfway done being transmitted

all packets = 1500 bytes and R = 2.5 Mbps

delay q = [ (6750 * 8) / (2.5 * 1000 * 1000) ] = 0.0216 s

delay q = n * L / R + (L - x) / R

P13.

a. packet n has q delay = (n - 1) * L / R

total q delay = (1 + 2 + 3 + ... + N - 1) * L / R
              = N(N - 1) * L / R

avr q delay = total q delay / n = (n - 1) * L / R

b. N packets arrive every N * L/R seconds -->

total q delay every N * L/R is N(N - 1) * L / R

avr q delay = N - 1 seconds


P14.

a. total delay = I (L/R) (1 - I) + L / R
b. straight line going through 0 w/ positive slope

P15. total delay = (La/u) (L/u) (1 - La/u) + L/u

P16. N is avr number of packets in buffer + packet being transmitted

a is rate of packets arriving at link

d is avr total delay (q delay plus trans delay) experienced by a packet

N = a * d

101 = a * (20msec + 1 packet / 100 packets per sec)
a = 3.36666 packet / msec

P17.

a. heterogeneous processing rates

b. no avr queueing delay of dqueue at each node --> repeat

P19. v = k * users^2

n = users

n * (n - 1) messages will be sent

P20. throughput = min(Rs, Rc, R / M)

P21. max = maximum of all the minimum rates of each path
max = sum of all minimum rates of each path

P22. Probability = (1 - p)^N
server will retransmit the packet 1 - (1 - p)^n of the time

P23.
a. inter-arrival time = (L / Rs)

b. It's possible that the second packet queues at the input queue of the second link because the first link has a higher transmission rate, which could lead to the second packet arriving at the input queue of the second link when the first packet is still being transmitted on the second link. T must be L / Rc - L / Rs to allow the second link to finish transmitting before the second packet arrives.

P24. Transmitting alone would take 4 * 10^6 seconds which is about 1111 hours. I would use overnight delivery because 1111 hours way longer than a night (12 hours).

P30. The equivalent of header information added to passengers and baggage as they move down the airline protocol stack are tickets and checking bag receipts to specify their destinations or passports to provide id.

P31. 

a. first packet switch time = 10^6 / (5 * 10^6) = 0.2 sec
total time = 3 * 0.2 sec = 0.6 sec

b. first packet switch time = 10^4 / (5 * 10^6) = 0.002 sec
second packet first packet switch time = 0.004 sec

c. 100 packets --> 100th packet arrives at first packet switch at 100 * 0.002 sec 

total time = 0.2 sec + 0.004 sec = 0.204 sec compared to 0.6 sec (almost 3 times as fast)

d. Message segmentation is also used to transport a message more reliably. If we transport a whole message in a packet, it can easily be lost; while if we transmit multiple packets for a single message, it's unlikely that all or most of the packets will be lost.

e. Some drawbacks of message segmentation include increased overhead to keep track of the segments (disassembling and reassembling them) and more complicated systems to manage them.

P33. F bits, 3 links, 2 packet switches between A and B
no queueing delays bc 0 congestion
F segmented into S bits each + 80 bits for header

L = 80 + S

R bps

S such that minimizes delay of moving the file from host A to B

delay = (F / S + 1) (80 + S) / R




