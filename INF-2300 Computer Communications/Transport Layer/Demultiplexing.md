De-multiplexing: Being split, being directed to a certain class of service.

**Host receiver IP Datagrams**:
- each datagram has source IP address, destination IP address
- each datagram carries one transport-layer segment
- each sgement has source, destination port number

Host then uses IP addresses & port numbers to direct segment to appropriate socket.
## Datagram
- Header
	- Contains info i.e addresses, protocol types, etc
- Payload
	- Contains actual data
	- Bound for different applications or to different protocols

## Connectionless demultiplexing
Recall:
- When creating socket, must specify host-local port number:
	```
	DatagramSocket mySocket1 
	= new DatagramSocket(12534);
	```

**Example**:
(Legg inn eksempel fra powerpoint)

## Connection oriented demultiplexing
- TCP socket identified by 4-tuple:
	- Source IP address
	- Source port number
	- etc... (mer står i powerpoint, legg til senere!!!)

**Example**:
(Legg inn fra powerpoint)