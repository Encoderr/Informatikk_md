Goals: Understand principles behind transport layer services:
- Multiplexing & demultiplexing
- Reliable data transfer
- Flow control
- Congestion control

Also we're gonna learn about internet transport layer protocols (UDP & TCP).

Communication between processes.

**Transport Layer Actions**
*Sender:
- Is passed an application-layer message
- determines segment header fields values
- creates segment
- passes segment to IP

**Receiver**:
- Receives segment from IP
- Checks Header Values (|T_h|app.msg|)
- Extracts application layer message
- demultiplexes message uplink

# Transport Layer Services and Protocols
- Provide logical communication between application processes running on different hosts
- Transport protocols actions in end systems
	- sender: breaks application messages into segments, passes to network layer
	- Receiver: Reassembles segments into messages

## Logical Communication
- Sender and receiver logically connected to each other by a direct link
- Reality: host may be on different sides of the planet
- Logical Perspective: sender and receiver directly connected

**Channel abstraction**
- Abstract away what is in between communicating processes

**Focus on**:
	- Properties of the channel
	- How services are implemented given the channel

## Transport vs network layer services and protocols
**Household analogy:**
12 kids in Ann's house sending letters to 12 kids in Bill's house:
- hosts = houses
- processes = kids
- app messages = letters in envelopes
- Transport Protocol = Ann & Bill who demux to in-house siblings

**[[Transport Layer]]**: Communication between processes.
**[[Network Layer]]**: Communication between hosts.

# [[Multiplexing]] and [[Demultiplexing]]
**Multiplexing as sender**:
- Handle data from multiple sockets, add transport header (later used for demultiplexing)
**Demultiplexing as receiver**:
- uses header info to deliver received data(?)

**Summary**:
- Multiplexing, demultiplexing: based on segment, datagram header field values
- [[UDP]]: Demultiplexing using destination port number (only)
- [[TCP]]: demultiplexing using 4-tuple: source and detination IP addresses, and port numbers
- Multiplexing/demultiplexing happens at all layers

[[UDP#UDP Transport Layer Actions|UDP Transport Layer Actions]]
[[UDP#UDP Checksum|UDP Checksum]]
