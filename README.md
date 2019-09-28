# How Internet Works

Shout out to [Crash Course](https://www.youtube.com/watch?v=3QhU9jd03a0&list=LLeVAzL66F8UlP34kGyAhg2w&index=5&t=0s) for this amazing playlist on how computer networks work.

The first computer network appear in 1950's to facilitate the flow of information of people and hardware. There were used in companies and research facilities and also allowed to starting sharing resourses, like printers and storage drives. These first networks were called Local Area Network, or LAN.

LANs can be as small as two machines in the same room or as large as an University Campus with thousands of computers connected together.

## Ethernet

The most famous LAN technology is [Ethernet](https://en.wikipedia.org/wiki/Ethernet), and was developed by Xerox in 1973 and first standarized into IEEE 802.3 ten years later, in 1983.

Ehternet defines the two first layers of the [Open Systems Interconnection model (OSI)](https://en.wikipedia.org/wiki/OSI_model), which is a model that partitions the communication system into abstraction layers, being the physical layer (data between a device and a physical transmission medium) and data link layer (node-to-node data transfer) covered by Ethernet.

Layer architecture of the OSI model:

1. Physical Layer
2. Data Link Layer
3. Network Layer
4. Transport Layer
5. Session Layer
6. Presentation Layer
7. Application Layer

One of the most critical problems of the networks is the possibility having **data collision**. As network traffic increases, it's more likely that two computers transmit data at the same time. This can cause data to be lost in the middle of the transmission.

Fortunately, this can be solved adding different special devices to control the data flowing in the network, and using dedicated algorithms to free the network when needed.

Sometimes data is too big to be transmited at once using one route, so in order to not clog the network, data is chopped in many small pieces called **packets**. Each packet contains a destination address on the network, so routers know where to forward them.

### 1. Physical Layer

The first layer of the OSI consists of **cabling** and **devices**.

Over the course of its history, Ethernet data transfer rates have been increased from the original 2.94 MB/s to the latest 400 Gb/s. In its beginings it used coaxial cable, but nowadays twisted pair cable and fiber optic cable is used for the communication.

![Twisted pair cables](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/Twisted%20pair%20cables.png)

In order to reduce the probability of collisions, **network switches** are used. They split the network in several collosion domains, so that information is transmited in the fastest way possible.

![Switches](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/Switches.png)

On the other hand, **routers** are in charge of finding the path to connect the data from one point to the final destination. Routers perform the traffic directing functions on the network.

Switches and routers act as the directors of the network and enable communications between all the different devices.

### 2. Data Link Layer

Data Link Layer is divided into two sublayers:

**Media Access Control (MAC)** is an hardware related ID assigned to the network interface cards (NIC) to identify specific devices, and show the source and destination of data transmission. Computers connected to the Ethernet cable only listen to the data transmited if the see their MAC address in the header of the data.

![MAC Address](https://raw.githubusercontent.com/darroyolpz/How-Internet-Works/master/Images/MAC%20Address.png)

**Logical Link Control (LLC)** establishes paths for data on the Ethernet to transmit between devices. It's also responsible of multiplexing protocols transmitted over the MAC layer (when transmitting) and demultiplexing them (when receiving), and also provides node-to-node flow control and error management.

### 3. Network Layer

This is the most important layer of the OSI model, which performs real time processing and transfer data from nodes to nodes. Internet Protocol stands on this layer.

### 4. Transport Layer

This layer transmit data from source to destination node and uses many protocols like TCP/IP, UDP, SPX, DCCP and SCTP.

### 5. Session Layer

This layer creates a session between the source and the destination nodes and terminates sessions on completion of the communication process.

### 6. Presentation Layer

It converts data formats into a format readable by the application layer.

### 7. Application Layer

This laer works at the user end to interact with user applications. File transfer and email are the major popular services of this layer. It uses several protocols, like HTTP, SMTP, FTA and SMPP.