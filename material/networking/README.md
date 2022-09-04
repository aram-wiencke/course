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


![OSIvsTCP/IP](https://www.imperva.com/learn/wp-content/uploads/sites/13/2020/02/OSI-vs.-TCPIP-models.jpg)

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
Hypertext Transfer Protocol is the application layer protocol we going first to have a look at. HTTP is the foundation of data communication for the World Wide Web. 
As you might know we use it daily when browsing on the Web. Our device is the client which is requesting a website from a server. 
Or in short: HTTP is a request-response protocol that uses a client-server model. Unlike FTP HTTP is a stateless protocol i.e. the server does not need to retain information for each user over multiple requests.
A HTTP request or response is consist out of three sections the start line, the Header and the Body. Let's first have a look how a http request is structured and then we'll have a look whats different at the HTTP response.

#### HTTP request
HTTP requests are message sent by the client to initiate an action on the server. Their start-line contain three elements:
- HTTP method like GET, which describes the action to be performed
- the request target, usually an URL
- and the HTTP version, which defines the structure of the remaining message and acting as an indicator of the expected version to use for the response.
The HTTP Headers follow after the start line. They are case-insensitive string that is followed by a colon (':') and a value for that header. One header is one line in the HTTP message.
The final part of the request is the body. Not all request have one. For example a request with the method GET is used for fetching data. The body can contain different kind of data with the header "Content-Type" and "Content-Length" the receiver can understand what type of data it gets and what size the data have in order to make sure when it is finished.

```
POST /examples HTTP/1.1
Host: localhost:8080
Connection: keep-alive
Context-Type: text/html
Content-Length: 123

Body line 1
Body line 2
...

```

##### Methods


#### HTTP Response
The HTTP response also consists out of the start line, the header and the body. It divers from the request only at the start line. The start line does not contain a method since the server is responding with an result and is not demanding an action from the client. Instead of the method the start line contains the status code which indicate the success or the failure of that demanded action.

```
HTTP/1.1 200 OK
Connection: keep-alive
Context-Type: text/html
Content-Length: 123

Body line 1
Body line 2
...

```

##### Status codes

### Websocket
### MQTT
### TLS
#### Encryption & Certificates
## Coding 
We are going to use https://github.com/vladimirvivien/go-networking as reference for programming



## What component handles which layer?
The device (e.g. our computer) is running on covers the physical layer and tha data link layer. The hardware and firmware translates between physical signals and bits. They also group them to frames. The device's driver controls the according functions. The network layer and the transport layer are covered by the OS, although privileged user space processes may get access to the data.

>A modern computer operating system usually segregates virtual memory into user space and kernel space. Primarily, this separation serves to provide memory protection and hardware protection from malicious or errant software behaviour.

Kernel space is strictly reserved for running a privileged operating system kernel, kernel extensions, and most device drivers. In contrast, user space is the memory area where application software and some drivers execute.

The frame header data tells what to do with the frame. If the kernel (more precisely: the network driver) knows the type of the payload (e.g. IPv4 or IPv6) then the packet (after stripping off data link layer headers and trailers) is passed up to the according network layer driver.

It will handle all peculiarities of the network layer protocol, such as fragmentation and reassembly, checksum calculation and verification, etc. plus all network layer specific tasks such as routing and packet filtering. Depending on the payload (TCP, UDP, etc.) the packet is passed further up to the according transport layer driver. It will handle all the transport layer specific stuff. For connection oriented protocols like TCP it means for instance keeping track of the connection state, maintaining the queues and doing the bookkeeping; another thing is congestion control.

Once a packet has passed that layer it is passed further up (again after stripping the transport layer header), but this time to the user space process. The user space process sees virtually nothing of the lower level processing.

