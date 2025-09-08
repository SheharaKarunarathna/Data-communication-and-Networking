1. PAN (Personal Area Network)

Range: A few meters (usually within a room).
Purpose: Connects devices around a single person.

Examples:

    Bluetooth between phone and earbuds.
    USB connection between laptop and mouse.
    Wi-Fi hotspot from your phone.

2. LAN (Local Area Network)

Range: Within a building (up to a few kilometers).
Purpose: Connects computers and devices in a limited area like a home, school, or office.

Examples:
    
    Wi-Fi in your home.
    Ethernet in an office.

3. MAN (Metropolitan Area Network)

Range: A city or large campus (tens of kilometers).
Purpose: Connects multiple LANs across a city.

Examples:
    
    City-wide Wi-Fi.
    Cable TV networks.
    University campus networks.

4. WAN (Wide Area Network)

Range: Country or even worldwide.
Purpose: Connects multiple LANs and MANs over long distances.

Examples:
    
    The Internet is the largest WAN.
    Bank networks connecting branches across countries.

5. Interplanetary Networks (IPN)

Range: Across planets (space communication).
Purpose: Provide communication between Earth, satellites, space stations, and planetary missions.

Challenges:

    Huge latency (minutes to hours).
    Need for Delay-Tolerant Networking (DTN).

Examples:

    NASA’s Interplanetary Internet project.
    Communication between Mars rovers and Earth.

# Bus and Tree topology

  ## Bus 
  
  - A single communication line
  - Stations are attached through hardware interface called Tap.
  - Terminator absorbs signal to remove it from the bus.
  - Full duplex (All stations can recieve signals from all stations)

  ## Tree  
  - More buses are connected to one Headend

    <img width="345" height="150" alt="image" src="https://github.com/user-attachments/assets/3d7b43d5-abda-498b-88d1-78ab1d259eab" />
    <img width="350" height="265" alt="image" src="https://github.com/user-attachments/assets/3ff6ce22-dded-4d98-b54c-0fe1f69fb8b7" />


## The Two Problems in Shared Topologies (like Bus/Tree)

1. Indicating whom the communication is intended to

      * In a shared medium (like a bus cable), when one device sends data, all devices receive it.
      * Problem: How do we make sure only the intended receiver processes it, while others ignore it?

2. When to access the shared medium
      
      * If multiple devices send data at the same time, signals collide → causing errors.
      * Problem: We need a way to decide who can send and when.

## Solutions

1. Data sent as frames with control information in the header
    * Data isn’t sent raw → it’s packed into frames.
    * Each frame has a header that includes:

      - Source address → who sent the data.
      - Destination address → who should receive the data.
      - This ensures that only the intended recipient processes the data.

2. Media Access Control (MAC) protocols

    * Define rules for sharing the medium.
    * Decide when each device can transmit to avoid collisions.

Examples:
    ```
    CSMA/CD (Ethernet) → Devices sense the medium before sending; if collision occurs, they wait and retry.
    Token Passing (Token Ring, Token Bus) → Only the device with the “token” can send.
    ```

# Ring Topology

  - A set of repeaters joined with point-to-point links in a closed loop.
  - In a ring topology, the repeater’s role is very important 👇
      * In a ring, each device is connected to exactly two neighbors, forming a closed loop.
      * Data travels in one direction (or sometimes both, in dual-ring).      
      * As data passes through each device, it can get weaker or distorted due to distance and noise.


Repeater function in ring topology
      
      - Regenerates the signal → Cleans and boosts the signal so it doesn’t weaken as it travels around the ring.
      - Forwards the data → Each node (or repeater) receives the signal, checks if it is addressed to it, and if not, passes it to the next node.
      - Maintains continuous flow → Ensures that data can make a full circle around the ring without degradation.
      - If same data goes through a full circle sender gets the data since it is a waste to send around without a reciever.  

