# How Internet Works

Shout out to [Crash Course](https://www.youtube.com/watch?v=3QhU9jd03a0&list=LLeVAzL66F8UlP34kGyAhg2w&index=5&t=0s) for this amazing play-list on how computer networks work.

The first computer network appear in 1950's to facilitate the flow of information of people and hardware. They were used in companies and research facilities, and also allowed to starting sharing resources, like printers and storage drives. These first networks were called [**Local Area Network (LAN)**](https://en.wikipedia.org/wiki/Local_area_network).

LANs can be as small as two machines in the same room, or as large as an University Campus with thousands of computers connected together. LANs are often the first connection from one's computer to the Internet, normally through a [**router**](https://en.wikipedia.org/wiki/Router_(computing)) that forwards data between computer networks.

LANs are normally connected to a bigger network called [**Wide Area Network (WAN)**](https://en.wikipedia.org/wiki/Wide_area_network), which is likely to be also connected to another router, run by the Internet Service provider. That WAN itself can be connected to even bigger WANs.

To request a particular file from let's say Youtube, data has to work its way up to the **backbone**, travel along that for a bit, and then work its way back down to a Youtube server that had the file.

## Ethernet

The most famous LAN technology is [**Ethernet**](https://en.wikipedia.org/wiki/Ethernet), and was developed by Xerox in 1973 and first standardized into IEEE 802.3 ten years later, in 1983.

Ethernet defines the two first layers of the [**Open Systems Interconnection model (OSI)**](https://en.wikipedia.org/wiki/OSI_model), which is a model that partitions the communication system into abstraction layers, being the physical layer (data between a device and a physical transmission medium) and data link layer (node-to-node data transfer) covered by Ethernet.

Layer architecture of the OSI model:

1. [Physical Layer](#physical)
2. [Data Link Layer](#data)
3. [Network Layer](#network)
4. [Transport Layer](#transport)
5. [Session Layer](#session)
6. [Presentation Layer](#presentation)
7. [Application Layer](#application)

One of the most critical problems of the networks is the possibility of having **data collision**. As network traffic increases, it's more likely that two computers transmit data at the same time. This can cause data to be lost in the middle of the transmission.

Fortunately, this can be solved adding different special devices to control the data flowing in the network, and using dedicated algorithms to free the network when needed.

Sometimes data is too big to be transmitted at once using one route, so in order to not clog the network, data is chopped in many small pieces called [**packets**](https://en.wikipedia.org/wiki/Network_packet). Each packet contains a destination address on the network, so routers know where to forward them.

### 1. Physical Layer <a name="physical"></a>

The first layer of the OSI consists of **cabling** and **devices**.

Over the course of its history, Ethernet data transfer rates have been increased from the original 2.94 MB/s to the latest 400 Gb/s. In its beginnings it used coaxial cable, but nowadays twisted pair cable and fiber optic cable is used for the communication.

![Twisted pair cables](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/Twisted%20pair%20cables.png)

In order to reduce the probability of collisions, **network switches** are used. They split the network in several collision domains, so that information is transmitted in the fastest way possible.

![Switches](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/Switches.png)

On the other hand, **routers** are in charge of finding the path to connect the data from one point to the final destination. Routers perform the traffic directing functions on the network.

Switches and routers act as the directors of the network and enable communications between all the different devices.

### 2. Data Link Layer <a name="data"></a>

The data link layer is the protocol layer in a program that handles the moving of data into and out of a physical link in a network. It is divided into two sub-layers:

**Media Access Control (MAC)** is an hardware related ID assigned to the network interface cards (NIC) to identify specific devices, and show the source and destination of data transmission. Computers connected to the Ethernet cable only listen to the data transmitted if the see their MAC address in the header of the data. **MAC Address** is used to ensure the physical address of computer. It uniquely identifies the devices on a network.

![MAC Address](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/MAC%20Address.png)

**Logical Link Control (LLC)** establishes paths for data on the Ethernet to transmit between devices. It's also responsible of multiplexing protocols transmitted over the MAC layer (when transmitting) and demultiplexing them (when receiving), and also provides node-to-node flow control and error management.

### 3. Network Layer <a name="network"></a>

This is the most important layer of the OSI model, which performs real time processing and transfer data from nodes to nodes. Internet Protocol stands on this layer.

**Internet Protocol (IP)**: IP is in charge of delivering packets from the source to the destination solely based on the IP addresses in the packet headers. This protocol transmit datagrams which have two components: a header (includes IP addresses from source and destination, and other meta-data) and a payload (data transported).

However, IP is a low level protocol: IP addresses help to get the data to the computer, but there is no information on which program shall use that data. Because of that, more advanced protocols have been developed to sit on top of the IP.

![IP](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/IP.png)

It's not rocket science to realize one needs an **IP address** to be able to surf on the Internet. An IP address is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol. It is used to uniquely identifies the connection of network with that device take part in a network.

Both MAC Address and IP Address are used to uniquely defines a device on the Internet. NIC Card’s Manufacturer provides the MAC Address, on the other hand Internet Service Provider provides IP Address.

### 4. Transport Layer <a name="transport"></a>

This layer is responsible for point-to-point data transfer, and error detection and recovery when it's is possible.

**User Datagram Protocol (UDP)**: Designed in 1980, this low-latency protocol uses a simple connectionless communication with a minimum mechanism. It provides checksums for data integrity checking, and port numbers for addressing different functions at the source and destination of the datagram.

On the other hand, there is no guarantee of delivery, ordering or duplicate protection. UDP is suitable for purposes where error checking and correction are not mandatory, such as time-sensitive applications (gaming, voice & video communication, etc.).

![UDP Protocol](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/UDP%20Protocol.png)

**Transmission Control Protocol (TCP)**: It's the most widely used protocol on the Internet. TCP is a reliable stream delivery service which guarantees that all bytes received will be identical and in the same order as those sent. Like the UDP, TCP has to check the port and the checksum of the data, but also contains other features more focused on **reliability of delivery**.

TCP is able to order different packets in the final destination, even if they have been delivered at different times. It has a mechanism to acknowledge the packets received, sending back an ack message to the sender once it gets to the receiver (this doubles the messages sent by the system). If a packet is missing and no message is sent, the packet is sent again to ensure the transmission. It also is able to send many packets at the same time, and has a congestion-control mechanism to not overload the network according to available bandwidth.

![TCP/IP Protocol](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/TCP%20Protocol.png)

### 5. Session Layer <a name="session"></a>

This layer creates a session between the source and the destination nodes and terminates sessions on completion of the communication process. UPD and TCP protocols opens a connection or **session** using the once the information is received by the DNS.

**Domain Name Service (DNS)**: It's like the phone-book of the Internet. It contains both the name and the IP address of all the existing domains.

![DNS](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/DNS.png)

### 6. Presentation Layer <a name="presentation"></a>

It converts data formats into a format readable by the application layer. The presentation layer is responsible for the formatting and delivery of information to the application layer for further processing or display.

Encryption is typically done at this level too, although it can be done on the application, session, transport, or network layers, each having its own advantages and disadvantages. Decryption is also handled at the presentation layer. For example, when logging on to bank account sites, the presentation layer will decrypt the data as it is received. Another example is representing structure, which is normally standardized at this level, often by using XML.

In many widely used applications and protocols, no distinction is made between the presentation and application layers.

### 7. Application Layer <a name="application"></a>

This layer works at the user end to interact with user applications. File transfer and email are the major popular services of this layer. It uses several protocols, like HTTP, SMTP, FTA and SMPP.

**Hypertext Transfer Protocol (HTTP)**: It's an application protocol, foundation of the data communication for the [**Word Wide Web**](https://en.wikipedia.org/wiki/World_Wide_Web). 

When you request a site, the first thing the computer does is a DNS look-up. It takes the domain name as input, and replies back with the matching IP address. Then, once the web-page IP address is known, the computer opens a TCP connection for the web server and ask for the hypertext web-page. Web server retrieves the web-page and send it back. Web-page is interpreted by the computer web-browser and is rendered on the screen. In latest version, HTTP has added some response codes, like 404 - page not found code.

![HTTP](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/HTTP.png)