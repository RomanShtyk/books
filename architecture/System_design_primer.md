# The System Design Primer

Summaries of various system design topics, including pros and cons. Everything is a trade-off.

---

## Scalability

- **Horizontal scaling**
- **Load balancing & caching**
- **Shared session state**
- **RAID**
- **Shared storage tech**
- **Database replication**
- **Load balancing tech**
- **Session affinity**
- **In-memory caching**
- **Data replication**: Active:Passive
- **Partitioning**
- **Data center redundancy**
- **Security**

---

### Clones

Requires management of deployment to ensure there is no outdated code running.

---

## Cache

### 2 Types of Cache:

1. **Cached Database Queries**:
    - Store the result dataset of a database query in the cache.

2. **Class or Dataset Cache**:
    - Let a class assemble a dataset from the database, then store the complete instance of the class or the assembled
      dataset in the cache.

**Redis**: Best for complex data, persistent cache.  
**Memcached**: Best for raw speed.

---

## Asynchronism

### 2 Types of Asynchronism:

1. **Do heavy work in advance**:
    - Best for static, predictable data.

2. **Not blocking the user**:
    - Notify the user that the work is done later.
    - Best for custom data.
    - **RabbitMQ**: Open-source message broker often used for communication between microservices in the cloud.

---

## Performance vs Scalability

- A service is **scalable** if it results in increased **performance** in proportion to resources added.
- **Performance Problem**: The system is slow for a single user.
- **Scalability Problem**: The system is fast for a single user but slow under heavy load.

---

## Latency vs Throughput

- **Latency**: Time to perform an action or produce a result.
- **Throughput**: Number of actions or results per unit of time.

**Goal**: Maximize throughput while maintaining acceptable latency.

---

## Availability vs Consistency

In a distributed computer system, you can only support two of the following guarantees:

- **Consistency**: Every read receives the most recent write or an error.
- **Availability**: Every request receives a response, without guaranteeing it contains the most recent version.
- **Partition Tolerance**: The system operates despite network failures.

### Trade-offs:

- **CP (Consistency and Partition Tolerance)**:  
  Wait for a response from the partitioned node (might result in a timeout error).  
  Best for atomic reads and writes.

- **AP (Availability and Partition Tolerance)**:  
  Returns the most readily available version of the data. Writes might take time to propagate.  
  Best for eventual consistency or when the system needs to continue despite external errors.

---

## CDN (Content Delivery Network)

### Push CDN:

- **Content**: Pre-uploaded to CDN servers, distributed across locations in advance.
- **Best for**: Static assets (e.g., images, large media files).
- **Pros**: Control over caching; reduces load on origin.
- **Cons**: Manual uploads; higher storage costs.

### Pull CDN:

- **Content**: Fetched from the origin when first requested, cached for future use.
- **Best for**: Dynamic or frequently updated content.
- **Pros**: No manual uploads; cost-effective for low-demand content.
- **Cons**: Higher latency on first request; increased load on origin.

**Summary**: Use push for static, high-demand content and pull for dynamic, unpredictable requests.

---

## Load Balancing

### Layer 4 Load Balancing:

- Operates at the transport layer (TCP/UDP).
- Directs traffic based on IP address and port without inspecting content.

**Pros**: Low latency; handles large traffic volumes.  
**Cons**: Limited routing options; cannot inspect HTTP headers or content.

### Layer 7 Load Balancing:

- Operates at the application layer.
- Routes traffic based on HTTP content, headers, or URLs.

**Pros**: Content-based routing; useful for complex apps.  
**Cons**: Higher latency; more resource-intensive.

---

# The Seven Layers of the OSI Model

Each layer has a specific role in handling network communication.

### Physical Layer (Layer 1):

- **Purpose**: Handles the physical connection between devices.
- **Functions**:
    - Transmission of raw binary data (bits) over the medium (e.g., cables, wireless).
    - Defines hardware specifications (e.g., cables, connectors, voltage levels).
- **Examples**: Ethernet cables, Wi-Fi frequencies, USB.

### Data Link Layer (Layer 2):

- **Purpose**: Ensures error-free transmission of data between adjacent nodes.
- **Functions**:
    - Framing, error detection/correction, and flow control.
    - Organizes data into frames for physical transmission.
- **Examples**: MAC addresses, switches, ARP, PPP.

### Network Layer (Layer 3):

- **Purpose**: Handles data routing, forwarding, and addressing.
- **Functions**:
    - Logical addressing (IP addresses).
    - Routing packets across networks.
- **Examples**: IP (IPv4/IPv6), routers, ICMP.

### Transport Layer (Layer 4):

- **Purpose**: Provides reliable or unreliable delivery of data between devices.
- **Functions**:
    - Ensures error recovery, segmentation, and flow control.
    - Handles end-to-end communication.
- **Examples**: TCP (reliable), UDP (unreliable).

### Session Layer (Layer 5):

- **Purpose**: Manages sessions or connections between applications.
- **Functions**:
    - Establishes, maintains, and terminates communication sessions.
- **Examples**: NetBIOS, RPC.

### Presentation Layer (Layer 6):

- **Purpose**: Translates data between the application and network.
- **Functions**:
    - Data encoding/decoding, encryption/decryption, compression.
    - Ensures the data is in a usable format.
- **Examples**: SSL/TLS, JPEG, MPEG.

### Application Layer (Layer 7):

- **Purpose**: Interfaces directly with the user and applications.
- **Functions**:
    - Provides services for file transfers, email, remote access, and web browsing.
- **Examples**: HTTP, FTP, SMTP, DNS.

In information security, computer science, and other fields, the **principle of least privilege (PoLP)**, also known as
the
principle of minimal privilege (PoMP) or the principle of least authority (PoLA), requires that in a particular
abstraction layer of a computing environment, every module (such as a process, a user, or a program, depending on the
subject) must be able to access only the information and resources that are necessary for its legitimate purpose.

### Latency numbers every programmer should know

    L1 cache reference ......................... 0.5 ns
    Branch mispredict ............................ 5 ns
    L2 cache reference ........................... 7 ns
    Mutex lock/unlock ........................... 25 ns
    Main memory reference ...................... 100 ns             
    Compress 1K bytes with Zippy ............. 3,000 ns  =   3 µs
    Send 2K bytes over 1 Gbps network ....... 20,000 ns  =  20 µs
    SSD random read ........................ 150,000 ns  = 150 µs
    Read 1 MB sequentially from memory ..... 250,000 ns  = 250 µs
    Round trip within same datacenter ...... 500,000 ns  = 0.5 ms
    Read 1 MB sequentially from SSD* ..... 1,000,000 ns  =   1 ms
    Disk seek ........................... 10,000,000 ns  =  10 ms
    Read 1 MB sequentially from disk .... 20,000,000 ns  =  20 ms
    Send packet CA->Netherlands->CA .... 150,000,000 ns  = 150 ms

Assuming ~1GB/sec SSD