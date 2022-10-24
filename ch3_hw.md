## Chapter 3 Review Questions

R1. 

a.
Protocol on client side
The protocol requires the application layer to provide the destination IP address and destination port number. It takes the message with this information from the socket interface and creates a segment with the destination IP address and port number in the header. It passes it down to the network layer to be delivered to the transport layer at the destination

Protocol on server side
The segment is passed to the transport layer from the network layer. The protocol reads the port number from the header info and sends the message to the process running on that port.

b. Protocol on client side
In addition, the protocol will include the source IP and port in the header.

c. The transport layer doesn't have to do anything in the core of the computer network

R2.

a.

Protocol on client side
Require the senders to include the name of the person and their address. Take the message and add the destination name to the message. Wrap the message in an envelope and write the destination address on the envelope. Give the envelope to the mail service to be delivered.

Protocol on server side
Receive an envelope from the mail service. Open it and read the name the message is addressed to. Give the message to the person with that name.

b. The mail service never has to open the envelope.

R3. The source port number is y and the destination port number is x.

R4. An application developer may choose to run an application over UDP rather than TCP for speed. If they can tolerate dataloss but require low latency, UDP is a good option because there's less overhead in the protocol and its packets are lightweight.

R5. Voice and video traffic are often sent over TCP because many firewalls block UDP traffic.

R6. It is possible for the application to enjoy reliable data transfer using UDP if they employ mechanisms to enforce reliability on the application layer.

R7. Both of these segments will be directed to the same socket because UDP sockets are only identified by the destination port number. The process at host C can differentiate the two segments by comparing the source IPs and source ports of the segment.

R8. All initial requests go to a welcoming socket at Host C. This welcoming socket creates different sockets for each request, so in the future, subsequent requests directed to those sockets will go straight to those sockets. Both of the sockets share the same port 80 but are differentiated by their source IP and port.

Unlike UDP, TCP connections don't need to get the source IP address from the OS to differentiate messages from different sources because the source IP address is in the socket id.

R9. We introduced sequence numbers in our rdt protocols to handle duplicate packets. The problem of duplicate packets arose when we had the sender retransmit packets on receipt of corrupted packets/ACKs. Sequence numbers allow the receiver to distinguish between new packets and old, retransmitted packets. The problem of duplicate packets also arose when we implemented timers, but we had already introduced sequence numbers to handle that.

R10. We introduced timers to handle packet loss, or over-delayed packets. If packets took too long to get to the receiver or were lost, we would never know because we would receive ACKs too late or not receive ACKs at all. Because of this, we introduced timers to have the packets retransmitted after a certain amount of elapsed time so the sender doesn't get stuck waiting for lost or over delayed packets.

R11. A timer is still required in our protocol even if we know the RTT delay because packets can still get lost. Even if we know the RTT delay, if we don't have a timer, we won't be able to retransmit the packets that get lost. We need the timer because packets that are lost will never have their acknowledgement sent to the sender, so the sender will be stuck waiting for the acknowledgement forever unless we have a timer to interrupt its waiting.

R12. Interactive animation

R13. Interactive Animation

R14.
a. F
b. F
c. T
d. F, sequence number is not determined by segment but by the byte stream --> sequence number prev + payload data size in bytes
e. T
f. F, TimeoutInterval = EstimatedRTT (new) + 4 * DevRTT
    EstimatedRTT (new) = (1 - alpha) EstimatedRTT (old) + alpha * SampleRTT (new) = (1 - alpha) EstimatedRTT (old) + alpha * 1
    EstimatedRTT (old) could be really small and we could put less weight on the recent SampleRTT by changing alpha, so it's not guaranteed that the current value of TimeoutInterval will be >= 1 sec.
g. F, The acknowledgement number in this same segment is not related to the sequence number in the segment at all. The acknowledgement number is related to the next sequence number the host is expecting to be sent from the other side of the connection.

R15.
a. 110 - 90 = 20 bytes
b. The ack number will be 90 because the first segment was lost.

R16. After the user types 'C', the host ACKs the 'C' and echoes it back. The user's machine then ACKs the receipt of the echoed 'C'. After the user types the letter 'R', two things could happen: the machine piggybacks the ACK of the echoed 'C' onto the datasegment containing 'R' to be sent together to the host, or the machine already sent the ACK of the echoed 'C' so it doesn't get piggybacked onto the datasegment containing 'R'. In the first case, the data segment 'R' gets seq number 43 and ack number 80. In the second case, the ack has already been sent with a seq number 43, so the data segment 'R' gets seq number 44 and ack number 80.


## Problems

P1.
a. source A, destination S
b. source B, destination S
c. source S, destination A
d. source S, destination B
e. It's possible that the source port number is the same, but then they're differentiated by the source IP addresses.
f. It's impossible that they're the same ports because they're from different processes on the same host. Processes can't share port numbers on the same host.

P2. The source and destination values are flipped for segments flowing from the server back to the clients' processes.

P3. 
    01010011
    01100110
   +01110100
    
   100101101 --> wrap around --> 00101110

   check sum = 1s complement = 11010001

   UDP takes the 1s complement so adding up the bits on the receiving side and adding the checksum will yield all 1s in the final sum. If the final sum are all 1s, then it doesn't detect an error. All 1 bit errors will be detected. Some 2 bit errors will go undetected. For example, if 1 of the bits in the same place value was swapped with another 1 of the bits in the same place value in another number, the sum would be the same.

P4.
a. 01011100
  +01100101

   11000001 --> checksum --> 00111110

b. 11011010
  +01100101
  
  100111111 --> wrap around --> 01000000 --> checksum --> 10111111

c. if the rightmost bits were flipped

P5. The receiver can't be absolutely certain no bit errors have occurred because a bit error could occur that would yield the same checksum.

P6. Say the sender sends a packet with sequence number 0 to the receiver. The receiver receives this packet correctly and acknowledges it, moving to the next state where it waits for a packet with sequence number 1; however, the acknowledgement is corrupted when the sender receives it. The sender then retransmits the segment with sequence number 0. The receiver receives it but is waiting on sequence number 1, so it sends a NAK packet back. The sender receives the NAK and retransmits the segment with sequence number 0 again. Now, the sender and the receiver are stuck in this loop.

P7. The ACK packets don't require sequence numbers because they do not contain any application data; they're just used as confirmation for the sender to know that its segments were received. If the sender receives duplicate ACKs, it isn't a problem because the duplicate ACKs just let the sender its segments were received.