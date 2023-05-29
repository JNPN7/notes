
- TCP/IP: Transmission Control Protocol/Internet Protocol

![](/assets/networking/osi-tcp.png)
Left Side: OSI
Right Side: TCP/IP

![](/assets/networking/osi-tcp-protocol.png)

## OSI model
![](/assets/networking/osi-model.png)

**1. Application Layer**
The layer that directly interacts with data from the user. Software application like web browsers and email clients rely on the application layer to initiate communications. But it should be clear that client software appllication is not application layer. Application layer is responsible for **protocols and data manipulation**. Application layer provides protocols that allow software to send and receive information and present meaningful data to users. Application layer protocols includes HTTP, FTP, SMTP, DNS, POP(Post Office Protocol).
![](/assets/networking/osi-layer-application.png)

**2. Presentation Layer**
The presentation layer prepares data for the application layer. The presentation layer is responsible for **translation, encryption and compression of data** so it is received correctly on the other end. The presentation layer takes any data transmitted by the application layer and prepares it for transmission over the session layer.

Two communicating devices may be using different encoding methods, so layer 6 is responsible for translating incoming data into a syntax that the application layer of the receiving device can understand.

Also, presentation layer is responsible for **compressing data** it receives from the application layer before delivering it to layer 5. This helps to **improve the speed** and efficiency of communication by minimizing amount of data that will be transferred.
![](/assets/networking/osi-layer-presentation.png)

**3. Session Layer**
The session layer **creates communication channels, called sessions**, between devices. This layer is responsible for opening and closing communication between the two devices. The time between when the communication is opened and closed is known as session. The session layer ensures that the session stays open long enough to transfer all the data being exchanged, and then promptly closes the session in order to avoid wasting resources.

The session layer can also **set checkpoints** during a data transfer. If the session is interrupted, devices can resume data transfer from the last checkpoint.

For example, if a 200 MB data is to be transferred, and session layer sets a checkpoint every 5 MB. Then, if interruption occurred in 78 MB data transfer then the session can be resumed form the last checkpoint which will be from 75 MB.
![](/assets/networking/osi-layer-session.png)

**4. Transport Layer**
This layer is responsible for **end-to-end communication** between the two devices. This includes taking data from the session layer and **breaking it up into chunks called segments** before sending it to layer 3 (network layer). It is responsible for reassembling the segments on the receiving end, turning back into data that can be used by the session layer.

The transport layer is also responsible for the **flow control and error control**. Flow control determines an optimal speed of transmission to ensure that a sender with a fast connection doesn't overwhelms a receiver with a slow connection. The transport layer performs error control on the receiving end by ensuring that the data received is complete, and requesting a re-transmission if it isn't.

Reliable (TCP) → Transmission Control Protocol
Unreliable (UDP) → User Datagram Protocol
Port number
![](/assets/networking/osi-layer-transport.png)

**5. Network Layer**
This layer is responsible for facilitating data transfer betweed two different networks. The network layer has two main functions. One is breaking up segments into **network packets**, and reassembling the packets on the receiving end. The other is **routing packets by discovering the best path across a physical network.** The network layer uses network addresses (typically IP address) to route packets to a destination node.
![](/assets/networking/osi-layer-network.png)

**6. Data Link Layer**
The data link layer is similar to the network layer, except the data link layer facilitates data transfer between two devices on the SAME NETWORK. The data link takes packets from layer and breaks them into smaller pieces called **frames**. Like network layer, data link layer is responsinble for flow control and error control in **intra-network communication**.

This layer composed of two parts **Logical Link Control (LLC)**, which identifies network protocols, performs error checking and synchronizes frames, and **Media Access Control (MAC)** → Burned-In address which uses MAC addresses to connect devices and define permissions to transmit and receive data.
![](/assets/networking/osi-layer-datalink.png)

**7. Physical Layer**
This layer includes the physical equipment involved in the data transfer, such as the cables and switches. This is also the layer where the data gets converted into a bit stream, which is string of 1s and 0s. The physical layer of both devices must also agree on a signal convention so that 1s can be distinguished from the 0s on the both devices.
![](/assets/networking/osi-layer-physical.png)



## TCP/IP model
![](/assets/networking/tcp-ip-model.png)
