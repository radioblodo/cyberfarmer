---
title: The OSI Model
date: '2025-06-13'
---

The OSI (Open Systems Interconnection) model is a reference model developed by the International Organization for Standardization (ISO) that provides a common basis for the coordination of standards development for the purpose of systems interconnection. The OSI model is a conceptual reference model rather than a protocol on its own.

**The OSI Model** 
| Layer| Name         | Function                       | Example Protocols |
|------|--------------|--------------------------------|-------------------|
| 7    | Application  | User-facing services           | HTTP, FTP, SMTP   |
| 6    | Presentation | Data formatting, encryption    | SSL/TLS, JPEG     |
| 5    | Session      | Connection management          | NetBIOS, RPC      |
| 4    | Transport    | End-to-end delivery            | TCP, UDP          |
| 3    | Network      | Routing and addressing         | IP, ICMP          |
| 2    | Data Link    | MAC addressing, frame delivery | Ethernet, ARP     |
| 1    | Physical     | Transmission medium            | Cables, hubs, NIC |

**Layer 7: Application** 
The application layer provides the interface between the user applications and the network. It mainly handles user interactions, API access, web browsers, file transfers and emails. Some of the protocols in the application layer would include HTTP, FTP, SMTP and DNS. 

**Layer 6: Presentation** 
The presentation layer translates data between application and network formats. It handles encrytion, compression and character encoding. Some example protocols of this layer would include SSL/TLS, JPEG, MPEG, ASCII and JSON. 

**Layer 5: Session** 
The session layer mainly establishes, maintains and ends communication sessions between applications. For example, it handles login sessions, authentication and reconnections. The more commonly known protocols for this layer are NetBIOS, RPC and PPTP. 

**Layer 4: Transport** 
The transport layer ensures complete data delivery with error checking and flow control. It breaks messages into multiple segments. The tasks of the transport layer would involve ensuring reliable transmission, packet sequencing and retransmission in the event of failure of delivery. The protocols for transport layer would include Transport Communication Protocol (TCP) and User Datagram Protocol (UDP). 

**Layer 3: Network** 
The network layer determines the best path to send data from one network to another and it deals with logical addressing and routing. It handles IP addressing, routing and packet forwarding. The protocols are IP, ICMP and IPsec. 

**Layer 2: Data Link** 
The data link layer transfers data between two directly connected devices and deals with MAC addresses and framing. There is also error detection, although it does not handle the correction process and there is MAC addressing. The protocols for this layer would be Ethernet, ARP and PPP. 

**Layer 1: Physical** 
The physical layer is the foundation of the OSI model. It is responsible for the actual transmission of raw binary data (0s and 1s) over a physical medium. This layer is the layer where communication starts and ends (bits get converted into signals like electric, light or radio) that travel across cables or through the air. 

Some common devices and technologies at the physical layer would include ethernet cables (Cat5e, Cat6, Cat6a, Cat7 and Cat8), fiber-optic cables, coaxical cables, Wi-Fi radio transceivers and Network Interface Cards (NICs). 

