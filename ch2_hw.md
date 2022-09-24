## Chapter 2 Review Questions

R1. Web HTTP, Email SMTP, File transfer FTP, Domain name DNS

R2. Network architecture is fixed and provides a certain set of services while application architecture's structure and services are decided by the application developer.

R3. The process client is the one initiating the connection and sending a request. The process server is the one listening for a connection request.

R4. I don't agree with the statement. In a communication session in P2P file-sharing, one process will request a file from another and the other will server the file. This means that there still is a client server dynamic in the communication session; however, in P2P, anyone can be a client or server. There are no dedicated servers.

R5. The port number / socket id is used to identify a process running on another host (also IP of that host).

R6. I would use UDP because we want the transaction to occur as fast as possible. TCP has too much overhead and can even throttle your transmission rate while UDP does not do this. UDP packets are also more lightweight. All of this results in UDP being faster.

R7. An application that requires no data loss and is highly time-sensitive is real time analytics. Such an application could be an analyzer of the stock market. Correct data and time are crucial to the analyzer for making quick decisions on actions to apply in the stock market.

R8. The 4 broad classes are reliability, timing, throughput, and security. TCP provides reliability and security (with TLS). UDP provides none of these.

R9. TLS operates at the application layer. If the developer wants TCP to be enhanced with TLS, the developer has to configure TLS on the application layer of both the client and host.

R10. A handshaking protocol is a protocol that uses a handshake to establish a connection before exchanging information. TCP uses the 3 way handshake where the client sends a hello message first. The server responds to the hello message with an acknowledgement. The client then sends another acknowledgement with its request.

R11. HTTP SMTP and IMAP run on top of TCP because reliabiliy is crucial to the applications that use those protocols such as web apps and email.

R12. First, the customer's browser will send an HTTP request to the web server. In response to this, the web server will see that the request doesn't have a cookie. The web server will create a cookie id to associate subsequent requests from the browser with this id. It will save the cookie id in its database and send the cookie id to the browser in the set-cookie header of its HTTP response. The browser will see the set-cookie header in the response and will store the cookie id associated with the website in its cookie file. Every subsequent request that the browser makes will have the cookie id attached now because it will remember its cookie through the cookie file. The web server can see the cookie in every subsequent request and store information about the request in its database using the cookie id as the key to this request information. Particularly, we can see that the web server can store purchase records of a customer when they send an HTTP request, cookie id included, with those purchase records.

R13. Web caching can reduce delay in receiving a requested object by having the requested object stored in its cache. That way, the request doesn't have to go into the network core all the way to the original web server. It stays in the network edge where the web cache usually is and responded to quickly by the Web cache. Web caching will only reduce the delay for objects requested by the user that it has in its cache. If it doesn't have the requested object in the cache it will need to request that object from the original Web server which doesn't same any time. If it does have the requested object, it can return a response with the object to the host immediately, saving time.

R18. HOL blocking is when multiple objects need to be requested in a persistent TCP connection. If a significantly larger object is requested before the smaller objects, the packets of the larger object being transmitted back to the client will block the rest of the smaller objects from being transmitted for a significant period of time. HTTP/2 attempts to solve this by using packet weaving. It will send indivdual packets for each object requested in rounds, starting from object1 object2 object3 and so on until it wraps back to object1. This way, objects requested later won't have to wait on all the packets of objects requested before them to have their packets transmitted.

R26. 


R27.

# Problems

P1. 

a. Depends on the HTTP version you're using HTTP/2 supports server pushing and it's widely used, so True

b. True --> they're both from the same web server

c. False --> you need a TCP connection per HTTP request/response, so a TCP segment can't carry two distinct requests

d. False --> Date: header indiciates the date the response was sent; Last-Modified: header indicates when the object was last modified

e. False --> responses to HEAD requests are a counter example of this (only header is sent back in response)

P3. TCP

P4. 

a. URL = gaia.cs.umass.edu/cs453/index.html
    URL is the host + the file path
    the host is specified in the host: header
    the file path is the 2nd field in the request line (first line)

b. HTTP/1.1 is the version
    the HTTP version is specified in the third field of the request line

c. The browser requests a persistent connection.
    the Connection: header specifies that the connection should be kept alive (keep-alive value); in other words, the connection will be persistent.

d. The IP address of the host is not specified in the application layer message. It's specified in the TCP header to identify sockets (transport layer).

e. The browser type is Mozilla/5.0. The browser type is specified in the User-Agent: header. The browser type is needed so that web server can send different files based on the browser and their versions.

P5. 

a. The server was able to successfully because the response returned a 200 OK status in the request line. The time of the response was Tue, 07 Mar 2008 12:39:45 GMT which is found in the Date: header.

b. Sat, 10 Dec 2005 which is in the Last-Modified: header.

c. 3874 bytes were returned which is provided in the Content-length: header.

d. The first 5 bytes returned are <!doctype html public .......>.... . We know this because the document returned is going to be in the entity body which is after all the header lines. The server agreed to a persistent connection because the Connection: header value is keep-alive.


P6. 

a. Both can signal the close of a connection. The server can signal the close of a connection after a specified amount of time has passed without the client sending any requests. The client can close the connection ??

b. 

P7. 2RTT0 + RTT1 + RTT2 + RTT3 + RTT4 + RTT5 + ... + RTTn

P8. 

a. 2 RTT for every request/response pair (every object) = 16 RTT

b. 4 RTT

c. 4.5 RTT (pipelining ??)

P9.

a. d Internet = 3 sec 
total avr response time = avr access delay + d Internet

no of bits per object = 1,000,000
req rate = 16 req / sec
R = 15 Mbps

16,000,000 = La

avr time required to send an obj over acces link = 1,000,000 / (15 * 10^6) = 1/15 seconds

avr access delay = 1/15 sec / (1 - 1/15 sec * 16 obj / sec) = 1 / 15 sec / ()

P10. handshaking packets = 200 bits
    data packets = 100,000

    d = 10 m, R = 150 bits/sec
    N parallel connections each 1 / N bandwidth

    each downloaded obj is 100 kb long

    initial downloaded obj contains 10 referenced obj from the same sender

    Parallel downloads via parallel instances of non-persistent HTTP doesn't make sense because the initially downloaded objects have 10 referenced objects each from the same sender, resulting in more TCP connections to be initiated.

    I do expect significant gains with persistent HTTP because the client will be able to make pipelined requests over the same TCP connection for the 10 referenced objects.

P11.

a. Bob's parallel connections will help him get Web pages more quickly because he gets more bandwidth from parallel connections. The other users get less bandwidth because they do not download in parallel, resulting in one TCP connection at any time for them which causes them to get less bandwidth.

b. His parallel connections would still be beneficial so he maximizes the bandwidth he can get.

P13.

a. 2005

b. 18

P14. 3 until the second image begins to be sent

