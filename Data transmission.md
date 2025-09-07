# Transmission modes
1. Parallel
2. Serial


## Parallel Transmission
  - Parallel: group of bits sent simultaneously by using a separate line for each bit
```
Pros  
  - Fast
Cons
  - Over longer distances;
  - costly to use many wires
  - need thicker wires to reduce signal degradation and bundling into a single cable is not practical
  - bits may not be received simultaneously
```
## Serial Transmission
  - Serial: bits sent over a single line one bit after another
```
Pros:
  - Cheap
  - Reliable
Cons:
  - Complexity because, sender and receiver must determine the order of bits
```

1. Asynchronous Transmission
   - Bits are divided into small groups (e.g. byte) and sent independently   
          E.g. keyboard inputs
Properties :
  * receiver does not know when a group of bits will arrive.
  * unpredictable time intervals between transmissions.
  * timing maintained within each group
  * Must signal that sender is going to send a group of bits before sending actual bits (Start Bit - Changes the line from idle stage(1) to 0).
  * Must signal that sender has finished sending a group of bits. (Stop Bits changing line state back to logic 1 (idle))
  * Cons - Too much of overhead bits.
    <img width="521" height="156" alt="image" src="https://github.com/user-attachments/assets/ca6bb2cf-3d24-407a-be1c-51bb04bb2a82" />
2. Synchronous Transmission
   - Larger bit groups sent without start/stop bits for each character.
   - Such groups called a frame
   - Frame structure varies from protocol to protocol
Organization
      <img width="744" height="184" alt="image" src="https://github.com/user-attachments/assets/654e2fa5-8e25-4ecd-8aa2-ee5e99332443" />

3. Isochronous Transmission
   - Combines features of both synchronous and asynchronous.
   - An isochronous data transfer system sends blocks of data asynchronously, in other words the data stream can be transferred at random intervals.
   - To mark the boundaries of each transmission, a start packet (or start-of-frame) indicates when the data begins, and an end packet (or end-of-frame) indicates when the data stops.
   - Isochronous transmission is a method of data transmission where data must be delivered at a consistent, regular time interval. It is often used in real-time applications where timing is critical.
   - Error correction is usually skipped (to avoid delays), but the timing is guaranteed.

## Simplex , half duplex and duplex
* Simplex
   - one direction
     * eg. television
* Half duplex
   - either direction, but only one way at a time
     * eg. police radio
* Full duplex
    - both directions at the same time
      * eg. telephone

## Multiplexing
1. Frequency division Multiplexing
  Several signals share the same communication channel at the same time, but each one is assigned a particular frequency band.  
  Among the many available frequencies in the channel, a specific frequency (band) is selected for each signal.  
  ```
  Example: In radio broadcasting, multiple stations transmit simultaneously, but a listener tunes in to the particular frequency of the station they want.  
  ```

2. Time Division Multiplexing
   Several signals share the same channel, but instead of dividing frequencies, the channel is divided into time slots.  
   Each signal is transmitted in its particular time slot in a repeating cycle.
   ```
   Example: In digital telephony, multiple voice calls are interleaved into time slots over the same line.
   ```
<img width="703" height="505" alt="image" src="https://github.com/user-attachments/assets/30fe4b67-2d9b-4146-a747-e853fb0cbd1f" />


### FDM issues
```
* Crosstalk: It is unwanted coupling between communication channels. Signal from one channel “leaks” into another channel, causing interference.
      Example: Hearing another person’s conversation faintly in your phone line.
* Intermodulation noise: creation of new unwanted frequencies due to signal mixing
      Example: In a radio, if two strong stations mix, you might hear a third “ghost” station that doesn’t really exist.

```
