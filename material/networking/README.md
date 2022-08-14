# Networking
The topic of networks is a large broad field from hardware to software solutions. 
Most common Software Systems use TCP over IP. Therefore this will be our focus for this chapter.
We want to gain an understanding how common high level protocols like HTTP work upon this stack.
But to provide an general overview this chapter starts with the OSI model showing the layers for communication for computing systems in an abstract form. Later on it will continue describing examples of layers' implementations like IP, TCP, HTTP, etc. 
## OSI model
The Open Systems Interconnection model is a conceptual model that splits the functions of communication in abstract layers. It does not describe the possible internal implementation, it rather 
 Each intermediate layer serves a class of functionality to the layer above it and is served by the layer below it.

The functions  describe the basic applications for communication of all communication protocols.
 The OSI model consists out of the following layers Physical, Data link, Network, Transport, Session, Presentation and Application.

 |              | Layer |              | Protocol data unit (PDU) |                                                                     Function                                                                     |
|:------------:|:-----:|:------------:|:------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------:|
|  Host layers | 7     | Application  | Data                     | High-level protocols such as for resource sharing or remote file access, e.g. HTTP.                                                              |
|              | 6     | Presentation |                          | Translation of data between a networking service and an application; including character encoding, data compression and encryption/decryption    |
|              | 5     | Session      |                          | Managing communication sessions, i.e., continuous exchange of information in the form of multiple back-and-forth transmissions between two nodes |
|              | 4     | Transport    | Segment, Datagram        | Reliable transmission of data segments between points on a network, including segmentation, acknowledgement and multiplexing                     |
| Media layers | 3     | Network      | Packet                   | Structuring and managing a multi-node network, including addressing, routing and traffic control                                                 |
|              | 2     | Data link    | Frame                    | Transmission of data frames between two nodes connected by a physical layer                                                                      |
|              | 1     | Physical     | Bit, Symbol              | Transmission and reception of raw bit streams over a physical medium                                                                             |
## Network layer
 The network layer is responsible for packet forwarding including routing through intermediate routers. Examples of protocols operating at the network layer are DDP, IGMP, IP (IPv4/IPv6).
 Let's have a look at IP.
### IP
Internet Protocol provides the ability of computers to communicate with other computers on the same network. This connection-less protocol specifies concepts such as Addressing and Routing to enable it to send data packets (datagrams) from one host to another host connected on the same network or across network boundaries.
The basic unit for IP is called packet:

![IP packet](https://www.w3.org/People/Frystyk/thesis/IPFrame.gif) 
## Transport layer
### Ports
In computer networking, a port is a number assigned to uniquely identify a connection endpoint and to direct data to a specific service. At the software level, within an operating system, a port is a logical construct that identifies a specific process or a type of network service. A port is identified for each transport protocol and address combination by a 16-bit unsigned number, known as the port number.
### UDP
UDP - The User Datagram Protocol (UDP) is a very thin protocol build on top of the IP. It is, what is known as, a connectionless transmission protocol designed to reduce latency of delivery. To do this, UDP sends data packets (or datagrams) to hosts, on an IP network, with minimum reliability and delivery guarantee.
The basic unit of data is the User datagram:

![User datagram](https://www.w3.org/People/Frystyk/thesis/UDPFrame.gif) 
### TCP
TCP - When the transmission of data, between hosts on a network, requires a more robust guarantees of delivery than, say UDP, the Transmission Control Protocol (or TCP) is used over an IP network. The protocol uses a session between communicating parties which starts with a handshake to establish a durable connection between hosts that can handle transmission error, out-of-order packets, and delivery guarantee.
The basic data unit is called segment in TCP:

![User datagram](https://www.w3.org/People/Frystyk/thesis/TCPSegment.gif) 

## Application Layer
Now that we understand the TCP/IP we stack them to understand how they are used to implement for the application layer. As our first example we use HTTP.

![User datagram](https://www.oreilly.com/library/view/http-the-definitive/1565925092/httpatomoreillycomsourceoreillyimages96904.png) 

### HTTP

### Websocket
### MQTT
### TLS
#### Encryption & Certificates
## Coding 
We are going to use https://github.com/vladimirvivien/go-networking as reference for programming
