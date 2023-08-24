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