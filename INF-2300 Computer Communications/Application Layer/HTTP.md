HTTP(Hyper Text Transfer Protocol)
- Web's application layer protocol.
- Uses TCP.
- Is a stateless protocol
	- Does not maintain information about the past client requests
	- Why? Because its a simple protocol built with simplicity.
# Connections
### Non Persistent HTTP
1. TCP connection opens
2. at most one object is sent
3. TCP connection closes
Downloading multiple objects requires multiple connections.
### Issues with non persistent HTTP
- Requires 2 RTTs per object
- OS Overhead for each [[TCP]] connection
- Browsers often open multiple parallel [[TCP]] Connections to fetch referenced objects in parallel.
### Persistent HTTP
- TCP connection opens to the server
- Does not require multiple connections to transfer multiple objects
# Messages
## Request
POST Method, PUT Method, HEAD method, GET Method.
## Receive

# Cookies
1. Cookie header line of HTTP response message
2. Cookie header line in next HTTP request message
3. Cookie file kept on users host

## What can cookies be used for?
- Authorization
- Shopping Carts
- Recommendations
- User Sessions State (Web e-mail)

Cookies permit sites to learn a lot about you on their site.
- They track users behavior on a given website (first party cookies)

Users now have access to control over whether or not cookies are allowed (EU General Data Protection Regulation).


