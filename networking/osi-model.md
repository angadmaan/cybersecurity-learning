# OSI Model

The OSI model has 7 layers.

- 7 (Application)  
- 6 (Presentation)  
- 5 (Session)  
- 4 (Transport)  
- 3 (Network)  
- 2 (Data Link)  
- 1 (Physical)  

## Purpose
The OSI model helps understand how data travels across a network.

## OSI: A Layered Network Model

- The process of breaking up the functions or tasks of networking into layers reduces complexity.
- Each layer provides a service to the layer above it in the protocol specification.
- Each layer communicates with the same layer’s software or hardware on other computers. 
- The lower 4 layers (transport, network, data link and physical —Layers 4, 3, 2, and 1) are concerned with the flow of data from end to end through the network. 
- The upper four layers of the OSI model (application, presentation and session—Layers 7, 6 and 5) are orientated more toward services to the applications. 
- Data is Encapsulated with the necessary protocol information as it moves down the layers before network transit.

### Physical Layer 
- Provides physical interface for transmission of information.
- Defines rules by which bits are passed from one system to another on a physical communication medium.
- Covers all - mechanical, electrical, functional and procedural - aspects for physical communication.
- Such characteristics as voltage levels, timing of voltage changes, physical data rates, maximum transmission distances, physical connectors, and other similar attributes are defined by physical layer specifications. 

### Data Link Layer
- Data link layer attempts to provide reliable communication over the physical layer interface. 
- Breaks the outgoing data into frames and reassemble the received frames.
- Create and detect frame boundaries.
- Handle errors by implementing an acknowledgement and retransmission scheme.
- Implement flow control.
- Supports points-to-point as well as broadcast communication.
- Supports simplex, half-duplex or full-duplex communication.

### Network Layer
- Implements routing of frames (packets) through the network.
- Defines the most optimum path the packet should take from the source to the destination
- Defines logical addressing so that any endpoint can be identified. 
- Handles congestion in the network.
- Facilitates interconnection between heterogeneous networks (Internetworking).
- The network layer also defines how to fragment a packet into smaller packets to accommodate different media.



