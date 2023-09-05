User Datagram Protocol is used to establish low-latency and loss-tolerating connections between applications. It also speeds up transmissions by enabling the transfer of data before an agreement is provided by the receiving party.

Uses unreliable unordered delivery, and has no-frills extension of "best effort" IP. If services are not available, delay will be guaranteed, though bandwidth is also guaranteed.

- No frills, bare bones internet transport protocol
- Best effort service, UDP segments may be either lost or delivered out-of-order to app
- Is connectionless
	- Means it has no handshaking between UDP sender and receiver
	- Each UDP segment handled independently of others

**Why is there a UDP?**
- No connection establishment (which can add RTT delay)
- Simple. no connection state at sender, receiver
- Small header size
- No congestion control
	- UDP can blast away as fast as desired
	- Can function in the face of congestion

**UDP Uses**:
- Streaming multimedia apps
- [[DNS]]
- SNMP
- [[HTTP 3|HTTP/3]]
If a reliable transfer is needed over UDP (e.g., [[HTTP 3|HTTP/3]]):
- Add needed reliability at application layer
- Add congestion control at application layer

## UDP: Transport Layer Actions
**UDP Sender Actions**:
- Is passed an application layer message
- Determines UDP segment header fields values
- Creates UDP segment
- Passes segment to IP
**UDP Receiver Actions**:
- Receives segment from IP
- Checks UDP checksum header values
- Extracts application layer message
- Demultiplexes message up to application via...

# UDP Checksum
**Goal**: detect errors (i.e, flipped bits) in transmitted segments.

**Example**:
Transmitted: 5 - 6 = 11
Received: 4 - 6 = 11 (something is wrong)

## Summary
- No frills protocol
	- Segments may be lost, delivered out of order
	- best effort service: "send and hope for the best"
- UDP has it plusses:
	- No setup/handshaking needed(no RTT incurred)
	- can function when entwork service is compromised
	- helps with reliability(checksum)
- Build additional functionality on top of UDP in application layer (e.g., HTTP/3)