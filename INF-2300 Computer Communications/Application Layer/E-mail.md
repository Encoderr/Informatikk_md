# Three major components:
- User Agents
- Mail Servers
- Simple Mail Transfer Protocol: SMTP
# User Agent
- aka Mail Reader
- Composing, editing, reading mail messages
- Outlook etc
# E-mail servers
- Mailbox
- Message queue
# SMTP Protocol
- Client: Sending mail server
- "server": receiving mail server
## SMTP RFC(5321)
**Uses TCP to reliably transfer email message from client to the server, port 25**
- Has direct transfer, where the sending server acts like a client to the receiving server.
### Three phases of transfer:
- Handshake
- Transfer of messages
- Closure
### Uses command/response interaction (like HTTP)
- commands: ASCII text
- response: status code and phrase
### SMTP: Observations
**Comparison with HTTP**:
- HTTP: Client Pull
- SMTP. Client Push
- Both have ASCII command/response interaction and status codes
- HTTP: Each object encapsulates in its own response message
- SMTP: Multiple objects sent in multipart messages
- SMTP uses persistent connections
- SMTP requires message to be in 7-bit ASCII
- SMTP servers uses CRLF.CRLF to determine end of messasge
# IMAP
