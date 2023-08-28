# Principles of network applications
Network apps in general, like social networks, voice over IP and games.
# Creating a network app
Has to run on different end systems, and has to communicate over networks.
We do not need to create software for the network-core devices.

## Different models
[[Client Server Model]] & [[P2P]].

## Process Communicating
*A process* is a program which runs within a host. Within the same host, two process communicate using [[IPC]]. Processes in different hosts communicate by exchanging messages.
## Sockets
Process sends/receives messages to/from its socket.

The Socket is analogous to the door.
	This means that sending a process shoves the message out of the door. It also relies on transport infrastructure on the other side of the door to deliver message to socket at the receiving end. If we have two sockets they will communicate more easier.
## [[Addressing processes]]
To receive messages, a process MUST have an identifier.
## An Application-layer protocol defines
Types of messages exchanged, message syntaxes, message semantics and rules for when and how processes send & respond to messages.

Open Protocols are defined in RFCs, which means everyone has access to the protocol definition (HTTP, SMTP).

## What kind of transport service does an app need?
[[Data Integrity]], [[timing]], [[throughput]] and [[security]].

## Internet Transport Protocol Services
[[TCP]] and [[UDP]].

### [[Securing TCP]]

# Web and HTTP
## Overview
Web pages consists of objects, which can be stored on different web servers. The object CAN be an HTML file, JPEG, audio file etc. The web page consists of base HTML-file which has several referenced objects, which is addressed by the URL.
## [[HTTP]] 
### [[HTTP#Connections|Connections]]
[[HTTP|Non Persistent HTTP]], [[HTTP|Persistent HTTP]]
### [[HTTP#Messages|Messages]]
Two types of HTTP Messages: Request and receive. 
### [[HTTP#Cookies|Cookies]]
## Latency
[[Web Caching]], [[Browser Caching]],
## [[HTTP 2]] and [[HTTP 3]]

# E-mail, SMTP, IMAP
## [[E-mail ]]

## [[E-mail#SMTP Protocol|SMTP]]
## [[E-mail#IMAP|IMAP]]

# [[DNS]](Domain Name System)
## DNS Services & structure
### Services
- Hostname-to-IP-address translation
- Host aliasing
	- Canonical, alias names
- Mail Server aliasing
- Load Distribution
*Why not centralize the DNS?*
- Single point of failure
- Traffic volume
- Distant centralized database
- Maintenance

**Each ms counts in regards for resolving loaded traffic!**

We do not centralize it because it would get too many queries at the same time. 

DNS is physically decentralized, which means it is reliable and secure.
### Structure
**Example of a DNS Hierarchy:** Root -> Top Level Domain -> Authoritative

DNS root name servers:
- Official, contact-of-last-resort by name servers that can not resolve name
- *Very important function* for the internet
	- Internet couldn't function without DNS
	- DNSSEC - provides security (message integrity and authentication)

**Top level Domain (TLD) Servers:**
- Responsible for .com, .org, .net and all top level country domains like .no, .dk etc...
**Authorative DNS Servers:**
- Organization's own DNS server(s), providing authoritative hostname to the IP Addresses.
**Local DNS name servers:**
- When host makes DNS query, it is sent to its local DNS server
	- Local DNS server returns a reply, answering:
		- from its local cache of recent name-to-address translation pairs
		- forwarding request into DNS hierarchy for resolution

**DNS Iterated Query:**
Requesting host -> local DNS server -> root DNS server - local DNS server -> TLD DNS server -> local DNS server -> authoritative DNS server -> local DNS server -> requesting host.

**DNS Recursive Query:**
Requesting host -> local DNS server -> Root DNS Server -> TLD DNS Server -> Authoritative DNS server -> TLD DNS server -> Root DNS server -> local DNS server -> Requesting host.

**Caching DNS Info**
- Once (any) name server learns mapping, it caches mapping, and immediately returns a cached mapping in response to a query
	- Caching improves response time
	- Cache entries timeout (disappear) after some time (TTL)
	- TLD Servers typically cached in local name servers
- Cached entries may be *out of date*
	- if named host changes IP-address, it may not be known Internet-wide until all TTLs expire
	- **Best-effort name-to-address translation!**

## DNS records
- Has a resource record (RR) where the format is: (name, value, type, ttl).
- Different types are:
	- Type A
		- name is hostname
		- value is ip address
	- Type NS
		- name is domain
		- value is hostname of authorative name server for this domain
	- Type CNAME
	- Type MX

DNS query and reply messages have **both** the same format.
- Message header:
	- ID has 16 bit # for query and reply uses same #

**Getting your info into the DNS**
- Register the(your) network at the DNS registrar
	- Provide names, IP addresses of authoritative name server (primary and secondary)
	- Registrar inserts NS, A RRs into .com TLD Server
- Create authoritative server locally with IP Address 212.212.212.1

## DNS Security
Certain types of attacks: [[DDoS]] and Spoofing attacks

# P2P Applications
## The Architecture 
- No always-on server
- Arbitrary end systems directly communicate
- Peers request service from other peers, provide service in return to other peers
- Peers are intermittently connected and share IP Addresses
	- Complex management

- Server transmission: must sequentially send(upload) N file copies
	- time to send one copy: F/u_s
	- time to send N copies: NF/u_s
- Client: each client must download file copy
	- d_min = min client download rate
	- min client download time: F/d_min

$$D_{c-s} >_{max}{NF/u_s, F/d_[min]}$$
$$D_p2p >_ {max}{F/u_s,\space F/d_min,\space NF/(u_s + \sum u_i)}$$
# Video Streaming and content distribution networks
## Video Streaming
- Video characteristics
- Streaming stored video
	- Buffering
	- Playout
- DASH - Dynamic Client-Driven Streaming
- CDNs example

### Context
- Stream video traffic: major consumer of internet bandwidth
- *challenge*: scale- how to reach 1 Billion users?
- *challenge*: heterogeneity
	- different users have different capabilities
- *solution*: distributed, application based infrastructure
### Multimedia: Video
- Video: Sequence of images display at constant rate (24 images/sec)
- Digital image: array of pixels where each pixel is represented by bits
- Coding: use redundancy within and between images to decrease the number of bits used to encode image
	- Spacial (within image)
	- Temporal (from one image to the next)
- CBR (constant bit rate): Video encoding rate fixed
- VBR (Variable Bit Rate): video encoding rate changes as amount of spatial, temporal coding changes
- examples:
	- MPEG 1 (CD-ROM)
	- MPEG 2 (DVD) 3-6 Mbps
	- MPEG 4 (often used in Internet, 64Kbps - 12Mbps)

### Streaming stored video
**Main-challenges**:
- Bandwidth varies over time
- Packet loss due to congestion (low quality or output delay)

**Steps in streaming a stored video**:
1. Video is recorded
2. Video is being sent by the server
3. Video is being played out at the client

**Challenges**:
- Continuous play-out constraint: during client video play-out, play-out timing must match original timing.
- Client interactivity: pause, fast-forward, rewind etc...
- Video packets may be lost, re-transmitted
- [[Variable network delays]]

**Playout buffering** will help compensate for the network-added delay and it will delay [[jitter]].

### Streaming multimedia: DASH (Dynamic Adaptive Streaming over HTTP)
**Server**:
- Divides video file into multiple chunks
- Each chunk encoded at multiple different rates
- Different rates of encoding which is stored in different files
- Files replicated in various nodes
- **Manifest file**: provides URLs for different chunks

**Client**:
- Periodically estimates server-to-client bandwidth
- Consulting manifest, requests one chunk at a time
	- Client chooses the maximum sustainable coding rate given.

## CDNs 
To stream content for hundreds of thousands of simultaneous users, we can create a mega server, or we can store/serve multiple copies of videos at multiple geographically distributed sites.
# Socket programming with UDP and TCP