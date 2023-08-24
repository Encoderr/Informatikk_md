## Protocols are everywhere
- Controls sending, receiving of messages
- HTTP (web), [[TCP]], IP, WiFi, 4/5G etc

## Internet Standards
- RFC : Request For Command

## What the Infrastructure provides
- Web, streaming video, multimedia, email, games etc..

## Protocols
We humans use protocols all the time, like communicating by saying hi to each other, or by asking each other the time. 
### Rules for protocols
- Specific messages sent
- Specific actions taken after receiving the message

# Network Edge
- Hosts = end systems: clients and servers
- Servers often in Data Centers

# Access networks, physical medias
- Wired, wireless communication links
- Physically connects the end-system to the [[first hop router]]

How to connect end systems to edge router?
- Residental access nets
- Institutional access networks (schools, companies)
- Mobile access networks (4/5G)

[[Frequency Division Multiplexing (FDM)]]: Different channels transmitted in different frequency bands

## Digital Subscriber Line (DSL)
- Use existing telephone line to central office DSLAM
	- Data over DSL phone line goes to Internet
	- Voice over DSL phone line goes to ...

## Host: sends packets of data
Hosts sending function:
- takes application message
- break into smaller chunks, known as [[packets]], of length L bits
- Transmits packet into access network at transmission rate R
	- Link transmission rate, aka link capacity, aka link bandwidth
# Network core
- A mesh of Interconnected routers
- [[Packet-switching]]
- Network of networks

Packet Switching vs Circuit Switching
- Packet Switching is great for "bursty data"

## Two key network core functions
### Forwarding
- aka "switching"
- local action: move arriving packets from router's input link to appropriate router output link
### Routing
- Global action: determine source.destination paths taken by packets
- Routing algorithms

# Performance

## Packet Delay: Four sources
### $d_proc$: nodal processing
- check bit errors
- determine output link
- typically < microseconds

### $d_queue$: queuing delays
- time waiting at output link for transmission
- depends on congestion levels

### $d_trans$: transmission delay:
- L: Packet length (bits)
- R: Link transmission rate (bps)
- $d_trans$: = $L/R$

### $d_prop$: propagation delay:

## Packet queuing delay 
- a: average packet arrival rate
- L: packet length (bits)
- R: link bandwidth (bit transmission rate)
$$ L * \frac{A}{R}: \frac{Arrival\space Rate \space of\space  bits} {Service\space Rate\space of\space bits} $$
- La/R - 0: avg. queuing delay small
- La/R -> 1: avg queuing delay large
- La/R ->1:

# Security
## TraceRoute
- Command line utility
- Finds out the exact path a data packet has used from a host to receiver
- Helps find bottlenecks
- Does not only ping the server, but each router the data packet has "touched".
- Gives information of how long time it used to ping between each router until it reaches its destination

## Throughput
Rate (bits/time unit) at which bits are being sent from sender to receiver
- instantaneous: rate at given point in time
- average: rate over longer period of time

$R_s < R_c$ What is average end-end throughput?
$R_s > R_c$ What is average end-end throughput?

[[Bottleneck Link]]

## Network Scenario
- Per connection end-end throughput: min($R_c$, $R_s$, $R/10$)
- In practice: $R_c$ or $R_s$ is often smaller than $R/N$
	- Bottleneck links tend to be at the network edge

# Protocol Layers, Service models
### Example: Organization of air travel:
|--end-to-end transfer of person plus baggage-->|
|ticket(purchase) ---> ticketing service --->ticket (complain)|
|baggage(check) ---> baggage service---> baggage (claim)|
|gates(load) ---> gate service --->gates(unload)|
|runway takeoff ---> runway service --->runway landing|
|airplane routing ---> airplane service --->airplane routing|

### Why layering?
Approach to designing/discussing complex systems:
- explicit structure allows identification, relationship of systems pieces
	- layered reference model for discussion
- modularization eases maintenance, updating of system
	- change in layers service implementation:transparent to rest of system
	- e.g., change in gate
## Layered Internet Protocol Stack
- Application: supporting network applications
	- HTTP, IMAP, SMTP, DNS
- Transport: process-process data transfer
	- TCP, UDP
- Network: Routing of datagrams from source to destination
	- IP, Routing protocols
- Link: data transfer between neighboring network elements
- Physical: bits on the wire

