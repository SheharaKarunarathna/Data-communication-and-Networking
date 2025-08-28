# Intro
## Layered architecture  

The benefit of having a layered architecture in networking (like the OSI or TCP/IP model) is that it simplifies the design, implementation, and management of complex network systems. Key advantages:  

1. Modularity – Each layer has a specific function (e.g., routing, addressing, error handling), making it easier to design and understand.
2. Abstraction – Higher layers don’t need to know the details of lower layers (e.g., an application doesn’t care how bits are transmitted).
3. Interoperability – Standardized layers allow devices and software from different vendors to work together.
4. Simplified Troubleshooting – Problems can be isolated to a specific layer.
5. Flexibility – Layers can be updated or replaced independently without affecting the whole system.
6. Reusability – Common services (e.g., error detection, flow control) can be implemented once and reused across application
   
## Baud rate
Baud rate = Number of signal changes per second through a channel of communication.  
Measured in baud . Each signal change represented from 1 or more bits depending on the modulation  
* Think of a signal change as a car passing a checkpoint. The number of cars per second is the baud rate, but each car could carry multiple packages (bits).  
![Alt text](Images/pasted image.png)
