# Computer Networks Interview Preparation - TCS Prime

## 1. Network Basics (Must-Know)

### What is a computer network?
A computer network is a collection of interconnected devices (computers, servers, routers, switches) that can communicate and share resources with each other. These devices are connected through communication channels like cables, wireless signals, or fiber optics.

### Why do we need computer networks?
- **Resource Sharing**: Share files, printers, internet connection
- **Communication**: Email, messaging, video calls
- **Data Storage**: Centralized data storage and backup
- **Cost Efficiency**: Share expensive resources among multiple users
- **Reliability**: Redundancy and fault tolerance
- **Scalability**: Easy to add new devices and expand

### Types of networks (LAN, MAN, WAN, PAN)
- **PAN (Personal Area Network)**: 1-10 meters (Bluetooth, USB)
- **LAN (Local Area Network)**: Within a building or campus (Ethernet, Wi-Fi)
- **MAN (Metropolitan Area Network)**: City-wide coverage (Cable TV networks)
- **WAN (Wide Area Network)**: Country/continent-wide (Internet, satellite)

### Client-server vs peer-to-peer model
**Client-Server Model:**
- Centralized architecture
- Server provides services, clients request services
- Better security and resource management
- Examples: Web browsing, email systems

**Peer-to-Peer Model:**
- Decentralized architecture
- Each node can act as both client and server
- Better fault tolerance
- Examples: BitTorrent, blockchain networks

### Network topology types
- **Bus Topology**: All devices connected to a single cable
- **Star Topology**: All devices connected to a central hub/switch
- **Ring Topology**: Devices connected in a circular fashion
- **Mesh Topology**: Every device connected to every other device
- **Tree Topology**: Hierarchical structure like a tree
- **Hybrid Topology**: Combination of multiple topologies

### Bus vs star vs ring topology
**Bus Topology:**
- Single cable backbone
- Easy to install, cost-effective
- Single point of failure
- Performance degrades with more devices

**Star Topology:**
- Central hub/switch
- Easy to troubleshoot and expand
- Hub failure affects entire network
- Most commonly used today

**Ring Topology:**
- Circular connection
- Equal access for all devices
- Difficult to troubleshoot
- One device failure can affect entire network

### What is bandwidth?
Bandwidth is the maximum amount of data that can be transmitted over a network connection in a given time period, typically measured in bits per second (bps), kilobits per second (Kbps), megabits per second (Mbps), or gigabits per second (Gbps).

### Bandwidth vs throughput
**Bandwidth:**
- Theoretical maximum capacity
- Like the width of a highway
- Measured in bps

**Throughput:**
- Actual data transfer rate achieved
- Like actual traffic flow on highway
- Always less than or equal to bandwidth
- Affected by network congestion, latency, protocol overhead

### Latency vs delay
**Latency:**
- Time taken for a packet to travel from source to destination
- Measured in milliseconds (ms)
- Also called round-trip time (RTT)

**Delay:**
- General term for any time lag in network communication
- Includes propagation delay, transmission delay, processing delay, queuing delay

### What is packet switching?
Packet switching is a method of data transmission where data is broken into small packets, each packet is sent independently through the network, and packets are reassembled at the destination. Each packet contains source/destination addresses and sequence numbers.

### Circuit switching vs packet switching
**Circuit Switching:**
- Dedicated communication path established
- Constant bandwidth allocation
- Used in traditional telephone systems
- No sharing of resources during call

**Packet Switching:**
- No dedicated path
- Dynamic resource allocation
- Better resource utilization
- Used in internet and data networks
- Packets can take different routes

### What is protocol?
A protocol is a set of rules and standards that define how devices communicate over a network. It specifies the format, timing, sequencing, and error control of data exchange between network devices.

### Examples of network protocols
- **HTTP/HTTPS**: Web browsing
- **FTP**: File transfer
- **SMTP**: Email sending
- **POP3/IMAP**: Email receiving
- **TCP**: Reliable data transmission
- **UDP**: Fast, unreliable data transmission
- **IP**: Internet addressing and routing
- **DNS**: Domain name resolution
- **DHCP**: Automatic IP address assignment

## 2. OSI & TCP/IP Models (Very Common)

### What is the OSI model?
The OSI (Open Systems Interconnection) model is a conceptual framework that standardizes network communication into 7 layers. It helps understand how data flows through different network components and protocols.

### Layers of OSI model
1. **Physical Layer**: Hardware transmission (cables, signals)
2. **Data Link Layer**: Frame formatting, error detection (Ethernet, Wi-Fi)
3. **Network Layer**: Routing, logical addressing (IP)
4. **Transport Layer**: End-to-end delivery, reliability (TCP, UDP)
5. **Session Layer**: Session management, dialog control
6. **Presentation Layer**: Data encryption, compression, translation
7. **Application Layer**: User interface, network services (HTTP, FTP)

### Functions of each OSI layer
**Physical Layer:**
- Bit transmission over physical medium
- Electrical, mechanical, and procedural specifications
- Examples: Ethernet cables, fiber optics, radio waves

**Data Link Layer:**
- Frame formatting and error detection
- MAC addressing
- Flow control between adjacent nodes
- Examples: Ethernet, Wi-Fi, PPP

**Network Layer:**
- Logical addressing (IP addresses)
- Routing between different networks
- Path determination
- Examples: IP, ICMP, ARP

**Transport Layer:**
- End-to-end reliable delivery
- Segmentation and reassembly
- Flow control and error recovery
- Examples: TCP, UDP

**Session Layer:**
- Establishes, manages, and terminates sessions
- Dialog control (full-duplex, half-duplex)
- Session checkpointing and recovery

**Presentation Layer:**
- Data encryption and decryption
- Data compression
- Data format translation
- Examples: SSL/TLS, JPEG, MPEG

**Application Layer:**
- Network services to applications
- User interface
- Examples: HTTP, FTP, SMTP, DNS

### Which OSI layer is responsible for encryption?
The **Presentation Layer (Layer 6)** is responsible for encryption and decryption of data. However, in practice, encryption can occur at multiple layers (e.g., SSL/TLS at transport layer, VPN at network layer).

### Which OSI layer is responsible for routing?
The **Network Layer (Layer 3)** is responsible for routing packets between different networks using logical addresses (IP addresses).

### What is TCP/IP model?
The TCP/IP model is a practical 4-layer networking model used in the internet. It's simpler than OSI and focuses on actual implementation rather than theoretical concepts.

### Layers of TCP/IP model
1. **Network Access Layer**: Physical and data link (Ethernet, Wi-Fi)
2. **Internet Layer**: Routing and logical addressing (IP, ICMP)
3. **Transport Layer**: End-to-end communication (TCP, UDP)
4. **Application Layer**: Network applications (HTTP, FTP, SMTP)

### OSI vs TCP/IP differences
| OSI Model | TCP/IP Model |
|-----------|--------------|
| 7 layers | 4 layers |
| Theoretical model | Practical implementation |
| Protocol independent | Protocol specific |
| Clear separation of layers | Some layer functions overlap |
| Developed before protocols | Developed with protocols |
| Less widely used | Widely used in internet |

### Where does HTTP fit in OSI?
HTTP operates at the **Application Layer (Layer 7)** in the OSI model and the **Application Layer** in the TCP/IP model.

### Where does TCP/UDP fit?
TCP and UDP operate at the **Transport Layer (Layer 4)** in both OSI and TCP/IP models.

### Where does IP fit?
IP operates at the **Network Layer (Layer 3)** in OSI model and **Internet Layer** in TCP/IP model.

### Why OSI has 7 layers?
The OSI model has 7 layers to:
- Provide clear separation of concerns
- Enable modular design and development
- Allow different vendors to develop compatible products
- Simplify troubleshooting by isolating problems to specific layers
- Enable standardization across different technologies

## 3. Physical & Data Link Layer

### What is transmission media?
Transmission media is the physical path through which data travels from sender to receiver. It carries electromagnetic signals that represent data.

### Guided vs unguided media
**Guided Media (Wired):**
- Physical path for signal transmission
- Examples: Twisted pair cable, coaxial cable, fiber optic cable
- More secure and reliable
- Higher bandwidth capacity

**Unguided Media (Wireless):**
- No physical path, signals travel through air/space
- Examples: Radio waves, microwaves, infrared, satellite
- More flexible and mobile
- Susceptible to interference

### What is MAC address?
MAC (Media Access Control) address is a unique 48-bit identifier assigned to network interface cards (NICs). It's written in hexadecimal format (e.g., 00:1B:44:11:3A:B7) and used for communication within the same network segment.

### MAC address vs IP address
| MAC Address | IP Address |
|-------------|------------|
| Physical address | Logical address |
| 48 bits (6 bytes) | 32 bits (IPv4) or 128 bits (IPv6) |
| Assigned by manufacturer | Assigned by network administrator |
| Works at Data Link Layer | Works at Network Layer |
| Used for local network communication | Used for internet communication |
| Cannot be changed easily | Can be changed |
| Example: 00:1B:44:11:3A:B7 | Example: 192.168.1.1 |

### What is framing?
Framing is the process of adding headers and trailers to data to create frames at the Data Link Layer. It helps identify the beginning and end of each frame and provides error detection capabilities.

### What is error detection?
Error detection is the process of identifying errors that occur during data transmission. Common methods include:
- **Parity Check**: Adding an extra bit to make total 1s even or odd
- **Checksum**: Mathematical calculation on data bits
- **CRC (Cyclic Redundancy Check)**: Polynomial division method

### What is error correction?
Error correction is the process of not only detecting errors but also correcting them without retransmission. Methods include:
- **Hamming Code**: Can detect and correct single-bit errors
- **Reed-Solomon Code**: Used in CDs and DVDs
- **Forward Error Correction (FEC)**: Adds redundant data for correction

### CRC vs parity check
**CRC (Cyclic Redundancy Check):**
- More sophisticated error detection
- Can detect burst errors and multiple bit errors
- Uses polynomial division
- More reliable but complex

**Parity Check:**
- Simple error detection method
- Can only detect odd number of bit errors
- Adds one extra bit
- Less reliable but simple to implement

### What is ARP?
ARP (Address Resolution Protocol) is used to find the MAC address of a device when only its IP address is known. It broadcasts an ARP request on the local network, and the target device responds with its MAC address.

### What is Ethernet?
Ethernet is a widely used LAN technology that defines wiring and signaling standards for the Physical and Data Link layers. It uses CSMA/CD (Carrier Sense Multiple Access with Collision Detection) for media access control.

### What is switch?
A switch is a Data Link Layer device that connects multiple devices in a LAN. It maintains a MAC address table to forward frames only to the intended recipient, creating separate collision domains for each port.

### Hub vs switch
| Hub | Switch |
|-----|--------|
| Physical Layer device | Data Link Layer device |
| Single collision domain | Separate collision domain per port |
| Half-duplex communication | Full-duplex communication |
| Broadcasts to all ports | Sends to specific port |
| Shared bandwidth | Dedicated bandwidth per port |
| Cheaper | More expensive |
| Largely obsolete | Widely used |

### What is VLAN?
VLAN (Virtual Local Area Network) is a logical grouping of devices in different physical locations into the same broadcast domain. It provides network segmentation, improved security, and better traffic management without changing physical infrastructure.

### CSMA/CD
CSMA/CD (Carrier Sense Multiple Access with Collision Detection) is a media access control method used in Ethernet networks:
- **Carrier Sense**: Listen before transmitting
- **Multiple Access**: Multiple devices can access the medium
- **Collision Detection**: Detect when two devices transmit simultaneously
- When collision detected, devices stop transmission and wait random time before retrying

### CSMA/CA
CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance) is used in wireless networks:
- **Collision Avoidance**: Try to avoid collisions rather than detect them
- Uses RTS/CTS (Request to Send/Clear to Send) mechanism
- Devices wait for acknowledgment before considering transmission successful
- Used because collision detection is difficult in wireless medium

## 4. Network Layer (IP & Routing)

### What is IP address?
An IP (Internet Protocol) address is a unique logical address assigned to each device on a network. It identifies the device's location on the network and enables routing of data packets across different networks.

### IPv4 vs IPv6
| IPv4 | IPv6 |
|------|------|
| 32-bit address | 128-bit address |
| 4.3 billion addresses | 340 undecillion addresses |
| Dotted decimal notation | Hexadecimal notation |
| Example: 192.168.1.1 | Example: 2001:0db8:85a3::8a2e:0370:7334 |
| Address exhaustion problem | Solves address exhaustion |
| Optional security | Built-in security (IPSec) |
| Manual/DHCP configuration | Auto-configuration support |

### Classes of IPv4 addresses
**Class A**: 1.0.0.0 to 126.255.255.255
- First bit: 0
- Network bits: 8, Host bits: 24
- Used for large networks

**Class B**: 128.0.0.0 to 191.255.255.255
- First two bits: 10
- Network bits: 16, Host bits: 16
- Used for medium networks

**Class C**: 192.0.0.0 to 223.255.255.255
- First three bits: 110
- Network bits: 24, Host bits: 8
- Used for small networks

**Class D**: 224.0.0.0 to 239.255.255.255
- Used for multicast

**Class E**: 240.0.0.0 to 255.255.255.255
- Reserved for experimental use

### Private vs public IP
**Private IP Addresses:**
- Used within private networks
- Not routable on the internet
- Ranges: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16
- Can be reused in different private networks
- Require NAT for internet access

**Public IP Addresses:**
- Globally unique and routable on internet
- Assigned by ISPs and regional registries
- Required for direct internet communication
- Limited in number and expensive

### What is subnetting? (concept only)
Subnetting is the process of dividing a large network into smaller sub-networks (subnets). It helps in:
- Better network organization and management
- Improved security by isolating network segments
- Reduced broadcast traffic
- More efficient use of IP addresses

### What is router?
A router is a Network Layer device that forwards data packets between different networks. It uses routing tables to determine the best path for packet delivery and connects networks with different addressing schemes.

### Router vs switch
| Router | Switch |
|--------|--------|
| Network Layer (Layer 3) | Data Link Layer (Layer 2) |
| Routes between different networks | Connects devices in same network |
| Uses IP addresses | Uses MAC addresses |
| Creates separate broadcast domains | Single broadcast domain |
| More intelligent | Less intelligent |
| Higher latency | Lower latency |
| More expensive | Less expensive |

### What is routing?
Routing is the process of selecting the best path for data packets to travel from source to destination across multiple networks. Routers use routing algorithms and maintain routing tables to make forwarding decisions.

### Static vs dynamic routing
**Static Routing:**
- Routes manually configured by administrator
- Routes don't change automatically
- Suitable for small, stable networks
- Lower overhead, more secure
- No automatic adaptation to network changes

**Dynamic Routing:**
- Routes automatically discovered and updated
- Uses routing protocols (RIP, OSPF, BGP)
- Suitable for large, complex networks
- Higher overhead, automatic adaptation
- Better fault tolerance and load balancing

### Distance vector vs link state routing
**Distance Vector:**
- Shares routing table with neighbors
- Uses hop count as metric
- Slower convergence
- Examples: RIP, EIGRP
- Prone to routing loops

**Link State:**
- Shares link state information with all routers
- Builds complete network topology
- Faster convergence
- Examples: OSPF, IS-IS
- Better loop prevention

### What is NAT?
NAT (Network Address Translation) is a technique that allows multiple devices with private IP addresses to share a single public IP address for internet access. It translates private IPs to public IPs and vice versa.

### What is ICMP?
ICMP (Internet Control Message Protocol) is used for error reporting and diagnostic functions in IP networks. It's used by tools like ping and traceroute to test network connectivity and troubleshoot network issues.

### What is TTL?
TTL (Time To Live) is a field in IP packet headers that specifies the maximum number of hops (routers) a packet can pass through before being discarded. It prevents packets from circulating indefinitely in case of routing loops.

## 5. Transport Layer (Most Asked)

### What is TCP?
TCP (Transmission Control Protocol) is a connection-oriented, reliable transport protocol that provides:
- Guaranteed delivery of data
- Error detection and correction
- Flow control and congestion control
- Ordered delivery of packets
- Full-duplex communication

### What is UDP?
UDP (User Datagram Protocol) is a connectionless, unreliable transport protocol that provides:
- Fast data transmission
- No guarantee of delivery
- No error correction
- No flow control
- Minimal overhead

### TCP vs UDP
| TCP | UDP |
|-----|-----|
| Connection-oriented | Connectionless |
| Reliable | Unreliable |
| Ordered delivery | No ordering guarantee |
| Error detection and correction | Basic error detection only |
| Flow control | No flow control |
| Congestion control | No congestion control |
| Higher overhead | Lower overhead |
| Slower | Faster |
| Examples: HTTP, FTP, SMTP | Examples: DNS, DHCP, streaming |

### What is port number?
A port number is a 16-bit number (0-65535) that identifies specific processes or services running on a device. It allows multiple applications to use network services simultaneously on the same device.

### Well-known ports (HTTP, HTTPS, FTP, SMTP)
- **HTTP**: Port 80
- **HTTPS**: Port 443
- **FTP**: Port 21 (control), Port 20 (data)
- **SMTP**: Port 25
- **POP3**: Port 110
- **IMAP**: Port 143
- **DNS**: Port 53
- **DHCP**: Port 67 (server), Port 68 (client)
- **SSH**: Port 22
- **Telnet**: Port 23

### TCP 3-way handshake
The TCP 3-way handshake establishes a connection between client and server:

1. **SYN**: Client sends SYN packet with initial sequence number
2. **SYN-ACK**: Server responds with SYN-ACK packet
3. **ACK**: Client sends ACK packet to confirm connection

After this handshake, both sides can start sending data.

### Flow control in TCP
Flow control prevents the sender from overwhelming the receiver with data. TCP uses a sliding window mechanism where:
- Receiver advertises its available buffer space (window size)
- Sender limits transmission based on receiver's window
- Window size dynamically adjusts based on receiver's capacity

### Congestion control in TCP
Congestion control prevents network congestion by controlling the sender's transmission rate. TCP uses algorithms like:
- **Slow Start**: Gradually increase transmission rate
- **Congestion Avoidance**: Linear increase after threshold
- **Fast Retransmit**: Quickly retransmit lost packets
- **Fast Recovery**: Avoid slow start after fast retransmit

### Sliding window protocol
Sliding window protocol allows multiple packets to be in transit simultaneously, improving efficiency:
- Sender can transmit multiple packets before receiving acknowledgments
- Window size determines how many unacknowledged packets are allowed
- Window "slides" forward as acknowledgments are received
- Provides both flow control and error control

### What is checksum?
Checksum is an error detection mechanism that calculates a mathematical value based on data content. The receiver recalculates the checksum and compares it with the received checksum to detect transmission errors.

### What happens if TCP packet is lost?
When a TCP packet is lost:
1. **Timeout**: Sender doesn't receive ACK within timeout period
2. **Retransmission**: Sender retransmits the lost packet
3. **Duplicate ACKs**: Receiver sends duplicate ACKs for out-of-order packets
4. **Fast Retransmit**: Sender retransmits after receiving 3 duplicate ACKs
5. **Congestion Control**: Sender reduces transmission rate assuming congestion

## 6. Application Layer (Very Common)

### What is HTTP?
HTTP (HyperText Transfer Protocol) is an application layer protocol used for transferring web pages and other resources over the internet. It's a stateless, request-response protocol that operates over TCP.

### HTTP vs HTTPS
| HTTP | HTTPS |
|------|-------|
| Not encrypted | Encrypted with SSL/TLS |
| Port 80 | Port 443 |
| Faster | Slightly slower due to encryption |
| Less secure | More secure |
| No authentication | Server authentication |
| Data visible to attackers | Data protected from eavesdropping |

### What is SSL/TLS?
SSL/TLS (Secure Sockets Layer/Transport Layer Security) is a cryptographic protocol that provides secure communication over networks. It provides:
- **Encryption**: Protects data from eavesdropping
- **Authentication**: Verifies server identity
- **Integrity**: Ensures data hasn't been tampered with

### What is DNS?
DNS (Domain Name System) is a hierarchical system that translates human-readable domain names (like google.com) into IP addresses that computers use to identify each other on the network.

### How DNS resolution works?
1. **User types URL** in browser
2. **Browser checks cache** for IP address
3. **Query to local DNS resolver** (ISP's DNS server)
4. **Recursive query process**:
   - Root DNS servers
   - Top-level domain (TLD) servers
   - Authoritative DNS servers
5. **IP address returned** to browser
6. **Browser connects** to web server using IP address

### What happens when you type a URL in browser?
1. **DNS Resolution**: Convert domain name to IP address
2. **TCP Connection**: Establish connection with web server
3. **HTTP Request**: Send GET request for the webpage
4. **Server Processing**: Web server processes the request
5. **HTTP Response**: Server sends back HTML, CSS, JavaScript
6. **Rendering**: Browser renders the webpage
7. **Additional Requests**: Load images, stylesheets, scripts

### What is FTP?
FTP (File Transfer Protocol) is an application layer protocol used for transferring files between computers over a network. It uses two connections:
- **Control Connection**: Port 21 for commands
- **Data Connection**: Port 20 for actual file transfer

### What is SMTP?
SMTP (Simple Mail Transfer Protocol) is used for sending emails from email clients to email servers and between email servers. It operates on port 25 and handles the delivery of outgoing emails.

### POP3 vs IMAP
| POP3 | IMAP |
|------|------|
| Downloads emails to local device | Keeps emails on server |
| Emails deleted from server | Emails remain on server |
| Single device access | Multiple device access |
| Offline access after download | Requires internet for access |
| Less server storage needed | More server storage needed |
| Port 110 | Port 143 |
| Simpler protocol | More complex protocol |

### What is REST?
REST (Representational State Transfer) is an architectural style for designing web services. It uses standard HTTP methods and is stateless, making it simple and scalable for web APIs.

### GET vs POST
| GET | POST |
|-----|------|
| Retrieves data from server | Sends data to server |
| Data in URL parameters | Data in request body |
| Limited data size | Large data size supported |
| Cacheable | Not cacheable |
| Idempotent | Not idempotent |
| Less secure | More secure |
| Bookmarkable | Not bookmarkable |

### PUT vs PATCH
| PUT | PATCH |
|-----|-------|
| Replaces entire resource | Updates part of resource |
| Idempotent | May or may not be idempotent |
| Requires complete resource data | Requires only changed fields |
| Creates resource if doesn't exist | Usually doesn't create new resource |

### What is stateless protocol?
A stateless protocol doesn't maintain any information about previous requests. Each request is independent and contains all necessary information. HTTP is stateless - the server doesn't remember previous requests from the same client.

### Cookies vs sessions
**Cookies:**
- Stored on client side (browser)
- Limited size (4KB typically)
- Can have expiration date
- Sent with every request to domain
- Less secure (visible to user)

**Sessions:**
- Stored on server side
- No size limitation
- Expires when browser closes or timeout
- Only session ID sent to client
- More secure (data on server)

## 7. Network Security (Lightweight but Important)

### What is firewall?
A firewall is a network security device that monitors and controls incoming and outgoing network traffic based on predetermined security rules. It acts as a barrier between trusted internal networks and untrusted external networks.

### Types of firewall
- **Packet Filtering Firewall**: Examines packet headers
- **Stateful Firewall**: Tracks connection state
- **Application Layer Firewall**: Examines application data
- **Next-Generation Firewall**: Combines multiple technologies
- **Hardware Firewall**: Dedicated physical device
- **Software Firewall**: Installed on individual computers

### What is proxy server?
A proxy server acts as an intermediary between clients and servers. It receives requests from clients, forwards them to servers, and returns responses back to clients. It provides:
- **Anonymity**: Hides client IP address
- **Caching**: Stores frequently requested content
- **Content Filtering**: Blocks access to certain websites
- **Security**: Additional layer of protection

### What is VPN?
VPN (Virtual Private Network) creates a secure, encrypted connection over a public network (like the internet). It allows users to access private networks remotely as if they were directly connected to the private network.

### What is encryption?
Encryption is the process of converting readable data (plaintext) into unreadable format (ciphertext) using mathematical algorithms and keys. Only authorized parties with the correct key can decrypt and read the data.

### Symmetric vs asymmetric encryption
**Symmetric Encryption:**
- Same key for encryption and decryption
- Faster processing
- Key distribution problem
- Examples: AES, DES
- Used for bulk data encryption

**Asymmetric Encryption:**
- Different keys for encryption and decryption (public/private key pair)
- Slower processing
- Solves key distribution problem
- Examples: RSA, ECC
- Used for key exchange and digital signatures

### What is hashing?
Hashing is a one-way mathematical function that converts input data of any size into a fixed-size string (hash value). It's used for:
- **Data Integrity**: Verify data hasn't been modified
- **Password Storage**: Store password hashes instead of actual passwords
- **Digital Signatures**: Create unique fingerprints for data

### What is digital signature?
A digital signature is a cryptographic mechanism that provides:
- **Authentication**: Verifies sender's identity
- **Non-repudiation**: Sender cannot deny sending the message
- **Integrity**: Ensures message hasn't been tampered with

It uses asymmetric encryption where sender signs with private key and receiver verifies with public key.

### What is authentication?
Authentication is the process of verifying the identity of a user, device, or system. Common methods include:
- **Something you know**: Password, PIN
- **Something you have**: Smart card, token
- **Something you are**: Biometrics (fingerprint, face)
- **Multi-factor Authentication**: Combination of above methods

### What is authorization?
Authorization is the process of determining what actions an authenticated user is allowed to perform. It comes after authentication and defines user permissions and access levels to resources.

### What is DoS vs DDoS attack?
**DoS (Denial of Service):**
- Attack from single source
- Overwhelms target with traffic
- Easier to defend against
- Limited attack capacity

**DDoS (Distributed Denial of Service):**
- Attack from multiple sources (botnet)
- Much larger attack volume
- Harder to defend against
- Can take down large websites and services

## 8. Wireless & Modern Networking

### What is Wi-Fi?
Wi-Fi is a wireless networking technology that allows devices to connect to the internet and communicate with each other using radio waves. It's based on IEEE 802.11 standards and operates in 2.4 GHz and 5 GHz frequency bands.

### Wi-Fi standards (802.11)
- **802.11a**: 54 Mbps, 5 GHz
- **802.11b**: 11 Mbps, 2.4 GHz
- **802.11g**: 54 Mbps, 2.4 GHz
- **802.11n**: 600 Mbps, 2.4/5 GHz, MIMO
- **802.11ac**: 6.93 Gbps, 5 GHz, MU-MIMO
- **802.11ax (Wi-Fi 6)**: 9.6 Gbps, 2.4/5 GHz, improved efficiency

### What is Bluetooth?
Bluetooth is a short-range wireless communication technology that connects devices within a personal area network (PAN). It operates in 2.4 GHz ISM band and is designed for low power consumption.

### Bluetooth vs Wi-Fi
| Bluetooth | Wi-Fi |
|-----------|-------|
| Short range (10 meters) | Longer range (100+ meters) |
| Low power consumption | Higher power consumption |
| Lower data rates | Higher data rates |
| Point-to-point connection | Multiple device connection |
| Personal Area Network | Local Area Network |
| Device pairing required | Network authentication |

### What is mobile hotspot?
A mobile hotspot is a feature that allows a smartphone or dedicated device to share its cellular internet connection with other devices via Wi-Fi. It creates a local Wi-Fi network that other devices can join to access the internet.

### What is packet loss?
Packet loss occurs when data packets traveling across a network fail to reach their destination. Causes include:
- **Network Congestion**: Too much traffic
- **Hardware Issues**: Faulty equipment
- **Software Bugs**: Protocol implementation issues
- **Interference**: In wireless networks

### What is jitter?
Jitter is the variation in packet delay over a network connection. It's the difference in time between when packets should arrive and when they actually arrive. High jitter affects real-time applications like VoIP and video streaming.

### What is CDN?
CDN (Content Delivery Network) is a distributed network of servers that deliver web content to users based on their geographic location. Benefits include:
- **Faster Loading**: Content served from nearby servers
- **Reduced Latency**: Shorter distance to travel
- **Load Distribution**: Reduces load on origin server
- **Better Availability**: Redundancy across multiple servers

### What is load balancing?
Load balancing is the process of distributing network traffic across multiple servers to ensure no single server becomes overwhelmed. It improves:
- **Performance**: Better response times
- **Availability**: Fault tolerance
- **Scalability**: Handle more users
- **Resource Utilization**: Efficient use of servers

## 9. Common Interview Traps / Rapid-Fire

### Why UDP is faster than TCP?
UDP is faster than TCP because:
- **No Connection Setup**: No handshake required
- **No Acknowledgments**: No waiting for ACKs
- **No Flow Control**: No window management
- **No Error Recovery**: No retransmissions
- **Smaller Header**: Less overhead (8 bytes vs 20 bytes)
- **No Ordering**: No packet reordering

### Can TCP work without IP?
No, TCP cannot work without IP because:
- TCP is a transport layer protocol that relies on IP for addressing and routing
- TCP segments are encapsulated in IP packets
- IP provides the logical addressing needed for end-to-end communication
- TCP/IP is designed as an integrated protocol suite

### Why HTTPS is secure?
HTTPS is secure because:
- **Encryption**: Data encrypted using SSL/TLS
- **Authentication**: Server identity verified with certificates
- **Integrity**: Data cannot be modified without detection
- **Protection from Eavesdropping**: Encrypted data unreadable to attackers
- **Protection from Man-in-the-Middle**: Certificate validation prevents impersonation

### Can two devices have same IP?
**In different networks**: Yes, private IP addresses can be reused
**In same network**: No, it causes IP address conflicts and communication issues
**Public IPs**: No, must be globally unique

### Can two devices have same MAC?
**Theoretically**: No, MAC addresses should be globally unique
**In practice**: Possible due to:
- Manufacturing errors
- Virtual machines with cloned MAC addresses
- Manual MAC address changes
- This causes communication issues in the same network segment

### What is localhost?
Localhost refers to the local computer/device itself. It's used to access services running on the same machine:
- **IP Address**: 127.0.0.1 (IPv4) or ::1 (IPv6)
- **Purpose**: Testing and development
- **Loopback**: Traffic doesn't leave the device

### What is loopback address?
The loopback address (127.0.0.1 for IPv4, ::1 for IPv6) is a special IP address that refers to the local machine itself. Traffic sent to loopback address is routed internally without going through network interfaces.

### What is default gateway?
Default gateway is the router that connects a local network to other networks (typically the internet). When a device needs to communicate with a device outside its local network, it sends the packet to the default gateway.

### What is DHCP?
DHCP (Dynamic Host Configuration Protocol) automatically assigns IP addresses and network configuration to devices on a network. It provides:
- **IP Address**: Unique address for each device
- **Subnet Mask**: Network boundary information
- **Default Gateway**: Router address
- **DNS Servers**: Name resolution servers

### Why port numbers are needed?
Port numbers are needed because:
- **Multiple Services**: One device can run multiple network services
- **Process Identification**: Identify which application should receive data
- **Multiplexing**: Allow multiple connections simultaneously
- **Service Standardization**: Well-known ports for common services

### Difference between switch and router?
**Switch:**
- Layer 2 device (Data Link Layer)
- Connects devices in same network
- Uses MAC addresses
- Creates collision domains
- Faster forwarding

**Router:**
- Layer 3 device (Network Layer)
- Connects different networks
- Uses IP addresses
- Creates broadcast domains
- Intelligent path selection

### Can HTTP be used without TCP?
**Standard HTTP**: No, HTTP relies on TCP for reliable delivery
**HTTP/3**: Yes, uses QUIC protocol over UDP
**Custom Implementation**: Theoretically possible but would lose reliability features

---

## Key Interview Tips

### For TCS Prime Success:
1. **Focus on Concepts**: Understand the "why" behind each technology
2. **Real-world Examples**: Relate concepts to everyday internet usage
3. **Layer Understanding**: Know which layer each protocol operates at
4. **Comparison Questions**: Be ready for "A vs B" questions
5. **Practical Scenarios**: Explain what happens when you browse a website

### Must-Know Flow:
**URL to Webpage**: DNS → TCP Connection → HTTP Request → Server Response → Rendering

### Common Mistakes to Avoid:
- Confusing layers in OSI model
- Mixing up TCP and UDP characteristics
- Not understanding the difference between MAC and IP addresses
- Forgetting that HTTP is stateless
- Confusing authentication with authorization

Remember: If you can explain the journey of a packet from your browser to a web server and back, you're well-prepared for most networking questions!