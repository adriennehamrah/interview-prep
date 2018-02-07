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
