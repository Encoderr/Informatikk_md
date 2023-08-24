The goal for HTTP 2 is to decrease delay in multi-object HTTP requests.

HTTP 2 Increases flexibility at the server in sending objects to the client.
- Methods, status codes, and most header files are the same as in HTTP 1.1
- Push non-requested objects to the client

## Mitigating HOL blocking
HTTP 1.1: Client requests 1 large object and 3 smaller objects.
HTTP 2: Large objects are divided into frames, and the frame transmission is interleaved. This improves performance substantially.  