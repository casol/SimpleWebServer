# SimpleWebServer

The Web server creates a listening socket and starts accepting new connections in a loop.
The client initiates a TCP connection and, after successfully establishing it,
the client sends an HTTP request to the server and the server responds with an HTTP response that gets displayed to the user.
To establish a TCP connection both clients and servers use sockets.


```
listen_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```
Create a new socket using the given address family, socket type and protocol number. The address family should be AF_INET (the default), AF_INET6, AF_UNIX, AF_CAN or AF_RDS. The socket type should be SOCK_STREAM (the default), SOCK_DGRAM, SOCK_RAW or perhaps one of the other SOCK_ constants.

AF_INET is an address family that is used to designate the type of addresses that your socket can communicate with (in this case, Internet Protocol v4 addresses). When you create a socket, you have to specify its address family, and then you can only use addresses of that type with the socket.

SOCK_STREAM is a constant indicating the type of socket (TCP), as opposed to SOCK_DGRAM (UDP).

```
listen_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
```
Set the value of the given socket option (Unix manual page setsockopt(2)- getsockopt() and setsockopt() manipulate options for the socket referred to by the file descriptor sockfd. Options may exist at multiple protocol levels; they are always present at the uppermost socket level.). The needed symbolic constants are defined in the socket module (SO_* etc.). The value can be an integer, None or a bytes-like object representing a buffer.

```
listen_socket.bind((HOST, PORT))
``` 
Bind the socket to address. The socket must not already be bound

```
listen_socket.listen(1)
```
Enable a server to accept connections. The backlog (1) parameter is now optional, it specifies the number of unaccepted connections that the system will allow before refusing new connections.
