https://docs.python.org/3/howto/sockets.html

# sockets

IPv4 Sockets and STREAM (TCP) sockets.

client application (your browser) uses client sockets only.
The web server it's talking to uses both server sockets and client sockets

Client side creating a socket:
```
# create an INET, STREAMing socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# now connect to the web server on port 80 - the normal http port
s.connect(("www.python.org", 80))
```
when socket s is connected, it can be used to send in a request for a page.
The socket will then read the reply and get destroyed. Client sockets are normally only used for one exchange or a small set of sequential exchanges.

On the web server side:
```
# create an INET, STREAMing socket
serversocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# bind the socket to a public host, and a well-known port
serversocket.bind((socket.gethostname(), 80))
# become a server socket
serversocket.listen(5)
```
- `gethostname()` makes the socket visible to the public
- `bind(('', 80))` specifies that the socket is reachable by any address the machine has.
- `listen(5)` tells the socket library to queue up as many as 5 connect requests before refusing outside connections

main loop:
```
while True:
    # accept connections from outside
    (clientsocket, address) = serversocket.accept()
    # now do something with the clientsocket
    # in this case, we'll pretend this is a threaded server
    ct = client_thread(clientsocket)
    ct.run()
```
- server socket just produces client sockets
- server socket does not receive any data
- server socket does not send any data
- each clientsocket is created in response to a "client" socket doing a connect() to the host and port the server is bound to
- as soon as the clientsocket is created, the server goes back to listening for more connections

This is the equivalent of the welcome socket dicussed in connection-oriented multiplexing in class. When the client app wants to initiate a 
connection, the client app sends a request to the welcome socket. The welcome socket on the server demultiplexes the request and creates a new 
socket for that client. It responds with the new socket info; now every subsequent request the client app makes is sent to the new socket (not the 
welcome socket).

Using a socket:
We design the rules of the conversation between the sockets connected. Normally, the connecting socket starts the convo by sending a request.