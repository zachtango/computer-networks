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

R5. Voice and video traffic are often sent over TCP for the reliability because the transmission rates are high enough using TCP.

R6. It is possible for the application to enjoy reliable data transfer using UDP if they employ mechanisms to enforce reliability on the application layer.

R7. Both of these segments will be directed to the same socket because UDP sockets are only identified by the destination port number. The process at host C can differentiate the two segments by comparing the source IPs and source ports of the segment.

R8. All initial requests go to a welcoming socket at Host C. This welcoming socket creates different sockets for each request, so in the future, subsequent requests directed to those sockets will go straight to those sockets. Both of the sockets share the same port 80 but are differentiated by their source IP and port.


## Problems

P1.
a. source A, destination S
b. source B, destination S
c. source S, destination A
d. source S, destination B
e. It's possible that the source port number is the same, but then they're differentiated by the source IP addresses.
f. It's impossible that they're the same ports because they're from different processes on the same host. Processes can't share port numbers.

P2. The source and destination values are flipped for segments flowing from the server back to the clients' processes.

P3. 
    01010011
    01100110
   +01110100
    
   100101101 --> wrap around --> 00101110

   check sum = 1s complement = 11010001

   UDP takes the 1s complement so adding up the bits on the receiving side and adding the checksum will yield all 1s in the final sum. If the final sum are all 1s, then it doesn't detect an error. It's possible a 1-bit error will go undetected. For example, if 1 of the bits in the same place value was swapped with another 1 of the bits in the same place value in another number, the sum would be the same. The same logic applies for a two bit error.

P4.
a. 01011100
  +01100101

   11000001 --> checksum --> 00111110

b. 11011010
  +01100101
  
  101111111 --> wrap around --> 10000000 --> checksum --> 01111111

c. if the rightmost bits were flipped

P5. The receiver can't be absolutely certain no bit errors have occurred because a bit error could occur that would yield the same checksum.
