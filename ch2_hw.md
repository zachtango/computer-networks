## Chapter 2 Review Questions

R1. Web HTTP, Email SMTP, File transfer FTP, Domain name DNS

R2. Network architecture is fixed and provides a certain set of services (5 layer Internet architecture) while application architecture's structure and services are decided by the application developer.

R3. The process client is the one initiating the connection and sending a request. The process server is the one listening for a connection request.

R4. I don't agree with the statement. In a communication session in P2P file-sharing, one process will request a file from another and the other will server the file. This means that there still is a client server dynamic in the communication session; however, in P2P, anyone can be a client or server. There are no dedicated servers.

R5. The port number / socket id is used to identify a process running on another host (also IP of that host).

R6. I would use UDP because we want the transaction to occur as fast as possible. UDP completes in one RTT while TCP takes 2 RTT per request/response. TCP has too much overhead and can even throttle your transmission rate while UDP does not do this. UDP packets are also more lightweight. All of this results in UDP being faster.

R7. An application that requires no data loss and is highly time-sensitive is real time analytics. Such an application could be an analyzer of the stock market. Correct data and time are crucial to the analyzer for making quick decisions on actions to apply in the stock market.

R8. The 4 broad classes are reliability, timing, throughput, and security. TCP provides reliability and security (with TLS). UDP provides none of these.

R9. TLS operates at the application layer. If the developer wants TCP to be enhanced with TLS, the developer has to configure TLS on the application layer of both the client and host.

R10. A handshaking protocol is a protocol that uses a handshake to establish a connection before exchanging information. The 2 communicators exchange control packets before sending data to each other. TCP uses the 3 way handshake where the client sends a hello message first. The server responds to the hello message with an acknowledgement. The client then sends another acknowledgement with its request.

R11. HTTP SMTP and IMAP run on top of TCP because reliabiliy of the data sent is crucial to the applications that use those protocols such as web apps and email.

R12. When a user first visits a site, the web server of the site creates a unique id, creates an entry in its backend database associated w/ that id, and returns that id as a cookie number. This cookie id is then stored on the cookie file of the user's host that the browser accesses to remember the cookie id for a particular site. Subsequent HTTP requests to the web server are sent with the cookie id, so the browser can store information about the HTTP requests in its backend entry associated with the cookie id to remember things about the user.

R13. Web caching can reduce delay in receiving a requested object by having the requested object stored in its cache. That way, the request doesn't have to go into the network core all the way to the original web server. It stays in the network edge where the web cache usually is and responded to quickly by the Web cache. Web caching reduces the delay of all objects, even those not cached, because caching reduces traffic on the Internet/network.

R18. HOL blocking is when multiple objects need to be requested in a persistent TCP connection. If a significantly larger object is requested before the smaller objects, the packets of the larger object being transmitted back to the client will block the rest of the smaller objects from being transmitted for a significant period of time. HTTP/2 attempts to solve this by using packet weaving. It will send indivdual packets for each object requested in rounds, starting from object1 object2 object3 and so on until it wraps back to object1. This way, objects requested later won't have to wait on all the packets of objects requested before them to have their packets transmitted.

# Problems

P1. 

a. Depends on the HTTP version you're using HTTP/2 supports server pushing and it's widely used
False

b. True --> they're both from the same web server

c. False --> you need a TCP connection per HTTP request/response, so a TCP segment can't carry two distinct requests

d. False --> Date: header indiciates the date the response was sent; Last-Modified: header indicates when the object was last modified

e. False --> responses to HEAD requests are a counter example of this (only header is sent back in response)

P3. DNS over UDP and HTTP over TCP

P4. 

a. URL = http://gaia.cs.umass.edu/cs453/index.html
    URL is the host + the file path
    the host is specified in the host: header
    the file path is the 2nd field in the request line (first line)

b. HTTP/1.1 is the version
    the HTTP version is specified in the third field of the request line

c. The browser requests a persistent connection.
    the Connection: header specifies that the connection should be kept alive (keep-alive value); in other words, the connection will be persistent.

d. The IP address of the host is not specified in the application layer message. It's specified in the IP datagrams from the network layer.

e. The browser type is Mozilla/5.0. The browser type is specified in the User-Agent: header. The browser type is needed so that web server can send different versions of files based on the browser and their versions.

P5. 

a. The server was able to successfully because the response returned a 200 OK status in the request line. The time of the response was Tue, 07 Mar 2008 12:39:45 GMT which is found in the Date: header.

b. Sat, 10 Dec 2005 which is in the Last-Modified: header.

c. 3874 bytes were returned which is provided in the Content-length: header.

d. The first 5 bytes returned are <!doc. We know this because the document returned is going to be in the entity body which is after all the header lines and an ASCII char is 1 byte (ASCII used for req/res). The server agreed to a persistent connection because the Connection: header value is keep-alive.


P6. 

a. Both client and server can close the signal. They do so by inserting close as the Connection: header value of the HTTP req/res.

b. HTTP isn't an encryption service

c. Clients that use persistent connections should limit the number of simultaneous connections they maintain to a given server. A single-user client should not maintain more than 2 connections with any server or proxy.

d. Yes. The one that closes it by sending the message w/ Connection: close views the connection as closed immediately after sending the message. Therefore, a server or client could be sending a message before receiving the close message.

P7. 2RTT0 + RTT1 + RTT2 + RTT3 + RTT4 + RTT5 + ... + RTTn

P8. 

a. 2 RTT for every request/response pair (every object) = 16 RTT0 + P7 ans

b. 4 RTT0 + P7 ans

c. with pipelining: RTT0 + P7 ans
    w/o pipelining: 8TT0 + P7 ans

P9.

a. you get a traffic intensity of over 1 ... this problem has a typo or something

b. cache installed on the LAN --> miss rate = 0.4

    0.6 of requests are satisfied within the LAN --> traffic intensity on access link reduced by 60%. New traffic intensity = old * 0.4

    avr response time = internet delay + 0.4(delay w/ cache miss) + 0.6(delay w/ cache hit) = internet delay + 0.4(delay w/ cache miss) because delay w/ cache hit is 0

P10. handshaking packets = 200 bits
    data packets = 100,000

    each obj = 100kbits --> each obj can fit in a data packet

    need 10 parallel connections to transmit 10 objects

    bandwidth / connection = 15 bps

    parallel delay = 3 control packets + 1 obj + 4 d prop
    + 3 control packets (using 1/15th bandwidth) + 1 obj (using 1/15th bandwidth) + 4 d prop)

    = 3 * 200 / 150 + 100,000 / 150 + 4 d prop + 3 * (200 / 15) + 100,000 / 15 + 4 d prop = 7377.33 + 8 d prop sec 

    persistent delay = 3 control packets + 10 control packets + 11 obj + 24 d prop = 13 * 200 / 150 + 11 * 100,000 / 150 = 7350.67 + 24 d prop sec

    d prop is negligible because the short distance the information is transferred over, which leaves us to compare the transmission delay. As shown, persistent HTTP is not significantly better than using non-persistent HTTP w/ parallel TCP connections.

P11.

a. Bob's parallel connections will help him get Web pages more quickly because he gets more bandwidth from parallel connections. The other users get less bandwidth because they do not download in parallel, resulting in one TCP connection at any time for them which causes them to get less bandwidth.

b. His parallel connections would still be beneficial so he maximizes the bandwidth he can get.

P13.

a. 2005

b. 18

P14. 3 until the second image begins to be sent

