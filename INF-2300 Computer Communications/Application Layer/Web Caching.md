Is used to satisfy client requests without involving origin server. 

- User configures browser to point to a local cache
- The browser sends all HTTP requests to the cache:
	If object is in the cache, the cache returns the object to the client, else the cache requests objects from the origin server, caches the received object and then returns the object to the client.

- Web cache acts as both the client and server
	- Server for original requesting client
	- Client to origin server
- Server tells cache about objects allowable caching in the response header.

## Why do web cache?
- It reduces the response time for the client request, and it reduces traffic on the access link. 
