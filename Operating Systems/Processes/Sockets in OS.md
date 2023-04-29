### Used for communication in Client-Server Systems
- A socket is defined as an endpoint for communication.
- A pair of processes communicating over a network employ a pair of sockets-one for each process.
- A socket is identified by an IP address concatenated with a port number.
- The server waits for incoming client requests by listening to a specified port. Once a request is received, the server accepts a connection from the client socket to complete the connection.
- Server implementing specific services (telnet, ftp, http) listen to well-known ports.
	- (A telnet server listens to port 23, an ftp server listens to port 21, and a web, or http, server listens to port 80.)
- All ports below 1024 are considered well-known; we can use them to implement standard services.