## REST - Representational State Transfer
- Set of design principles for making network communication more scalable and flexible. 
- These principles answer a number of questions. 
    - What are the components of the system? 
    - How should they communicate with each other? 
    - How do we ensure we can swap out different parts of the system at any time? 
    - How can the system be scaled up to serve billions of users?

### Fielding Constraints
System must satisfy the following to be considered RESTful.
#### Client-server
- One-to-one communication
#### Stateless
- Each request is standalone
- Client and server don't track each other's state
#### Uniform Interface
- Identification of resources
- Manipulation of resources through representations
- Self-descriptive messages
- Hypermedia - data sent from the server to the client that contains information about what the client can do next–in other words, what further requests it can make.
#### Caching
#### Layered System
#### Code on Demand (opt.)

#### Reference
[What RESTful actually means](https://codewords.recurse.com/issues/five/what-restful-actually-means)

### HTTP
- Safe method - Does not modify resources
      - GET
- Idempotent method - Can be called many times without different outcomes

HTTP Method | Idempotent| Safe
----------- | --------- | ---- 
OPTIONS |	yes  |	yes
GET	| yes |	yes
HEAD |	yes	| yes
PUT	| yes	 | no
POST |	no |	no
DELETE	| yes |	no
PATCH	| no	| no

#### PUT vs PATCH
- PUT is idempotent while PATCH is not
- PUT - send entire entity over and replace entire entity
- PATCH - only need to send what you want updated. Can send PATCH requests without ID, in which case, the server will create new objects.

## What happens when you type a url in the browser and hit enter?
1. Type in www.google.com.
2. Browser checks four caches for DNS (domain name system) record to find IP.
    - Browser
    - If not found, browser checks OS cache 
    - Then browser checks router cache 
    - Then ISP cache
3. If URL is not found in cache, ISP's DNS server issues a DNS query to find IP of server host.
    - Contacts root name server "."
    - Root name server redirects to top-level domain ".com"
    - Top-level domain redirects to second-level domain "google.com" and so on.
4. Once browser gets IP address, initiates a TCP connection with server.
    - TCP/IP three way handshake. Send SYN/ACK/ACK messages to establish a connection.
5. Browser sends HTTP request to web server.
    - GET, POST, etc.
    - Also pass cookies from browser with request.
6. Server handles request.
    - Web server (Apache, IIS) receives request and passes it to request handler to read and generate response.
    - Request handler (written in ruby, php, asp.net) reads the request, updates info on server if needed, then creates response (JSON, XML, HTML)
7. Server sends out HTTP response.
    - Response contains webpage, status code, compression type (content-encoding), cache control, cookies, privacy info, etc
    - 1xx indicates an informational message only
    - 2xx indicates success of some kind
    - 3xx redirects the client to another URL
    - 4xx indicates an error on the client’s part
    - 5xx indicates an error on the server’s part
8. Browser displays HTML content (for HTML responses)
    - Content displayed in stages:
        - HTML skeleton
        - Then checks HTML tags and sends out GET request for add'l elements like images, CSS stylesheets, JS files, etc 
        
#### Reference
[What happens when you type a url in the browser and hit enter?](https://medium.com/@maneesha.wijesinghe1/what-happens-when-you-type-an-url-in-the-browser-and-press-enter-bb0aa2449c1a)

## TCP/IP Internet Protocol Suite
- Applicaton Layer (HTTP port 80, SMTP, FTP, POP)
- Transport Layer (TCP, UDP)
- Network/Internet Layer (IP, ICMP)
- Physical Layer (Ethernet, ARP)

### TCP Transmission Control Protocol
- Connection-oriented - handshake to set up
- Reliable  - manages acknowledgement, retransmission, timeout
- Ordered data transfer 
    - Each packet has a header that contains order and error checking
- Heavyweight - require three packets to set up socket connection
- Retransmission of lost packets
- Error free data transfer
- Flow control
- Congestion control
- Used by HTTP, HTTPs, FTP, SMTP, Telnet

### UDP User Datagram Protocol
- Connectionless
- Unreliable - no acknowledgment, retranmission, or timeout
- Unordered packets
- Lightweight
- Datagrams - packets sent individually and checked for integrity only if they arrival
- No congestion control
- Broadcasts - connectionless allows for broadcasting
- Lack of retransmisson delays - Good for real-time steaming apps like VoIP, games
- Transaction Oriented - Good for simple query response protocols like DNS, Network Time Protocol
- Used by DNS, DHCP, TFTP, SNMP, RIP, VoIP



  
