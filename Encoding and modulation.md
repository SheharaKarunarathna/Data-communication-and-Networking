# Encoding techniques

1. Digital data, Digital signal

Terms
```
1. Unipolar signaling

 Uses only one polarity (e.g., 0 V and +V).
 Simple, but inefficient (no negative voltages used).
 Example: Unipolar NRZ (Non-Return-to-Zero).

2. Polar signaling

 Uses two polarities (e.g., -V and +V).
 More efficient, average voltage closer to 0.
 Example: Polar NRZ or Manchester coding.

3. Data rate

 Number of bits transmitted per second (bps).
 
 Formula:
 𝑅𝑏 = 1/𝑇𝑏


4. Duration (or length) of a bit

 The time to send 1 bit.
 
 Formula:
 𝑇𝑏 = 1/𝑅𝑏

5. Encoding
 Encoding takes a digital or an analog signal and
 converts it to a form suitable for sending on a wire or
 a fibre

6. Modulation
 Modulation takes a digital or an analog signal and
 modifies a carrier signal with it

7. Modulation rate
  Modulation rate = Baud rate

8. Mark and Space
  Binary 1 and 0 respectively  
```

```
✅ In short:
Unipolar → only positive voltages.
Polar → both positive & negative voltages.
Data rate = bits per second.
Bit duration = inverse of data rate.
```

## Baseband VS Broadband
```
1. Baseband

Uses the entire channel bandwidth to send a single signal.
Signal type: Digital (square wave, pulses).
Transmission: One signal at a time.
Range: Short-distance (LAN, Ethernet).
Example: Ethernet (IEEE 802.3), USB.

2. Broadband

Divides the available bandwidth into multiple channels using modulation.
Signal type: Analog (modulated carriers).
Transmission: Multiple signals simultaneously.
Range: Long-distance (WAN, cable TV, Internet).
Example: Cable TV, DSL, 4G/5G.
```

## Interpreting Signals
```
Need to know - 
1. Timing of bits - when they start and end
2. Signal levels

Factors affecting successful interpreting of signals
* Signal to noise ratio
* Data rate
* Bandwidth
```
## NRZ

1. Nonreturn to Zero-level (NRZ-L)

```
* Two different voltages for 0 and 1
* Never stay in zero so we get plus and minus values to map 1 and 0. (ex : +5V for 1 and -5V for 0)
* Stay at the level between the bit interval
```  
3.  Nonreturn to Zero Inverted (NRZ-I) - (Differential encoding)

   * Transition (0to1 or 1to0) denotes a binary 1 .
   * When no change of the signal it means it is binary 0 .
   adv = More reliable detection of transition rather than level
   disadv = In complex transmission layouts it is easy to lose sense of polarity

NRZ pros and cons
Pros-
* Easy to engineer
* Make good use of bandwidth
Cons -
* DC component (sync loss on long 0s, DC component, and error propagation)
* Lack of synchronization capability

## Alternative mark inversion
     
1. Bipolar-AMI (Alternative Mark Inversion)

   * Alternating the polarity of the signal for each binary 1, While binary 0 is represented by a zero voltage.  
   ``` 0 1 1 0 1 0 1 0 1 1 - 0 +5 -5 0 +5 0 -5 0 +5 -5 ```
   * Easy error detection
   * No net DC component
   * Lower bandwidth
   * No loss of sync for long string of 1s but zeros have the problem
    
2.  Psuedoternary

    * Binary 0s are represented by alternative positive and negative voltages. While binary 1 comes the level is zero


Trade off for Multilevel Binary
   * Not as efficient as NRZ
        - Each signal element only represents one bit
        - Two levels are used to represent 1
        - Requires approx 3dB more signal power for same probability of bit error.

## Biphase

 1. Manchester  

   * Mid of the interval always has a transition  
             - High to Low if data bit is 0  
             - Low to high if data bit is 1
   (Self Synchronizing - The mid of the interval always has a transition so the synchronization never missed)

<img width="687" height="219" alt="image" src="https://github.com/user-attachments/assets/9e737dde-1201-4f41-bbd3-14d69e9e6aac" />
 
 2. Differential Manchester

   * Presence or absence of a transition at the start of the bit period determines the bit value.  If there is a transition in the start of the bit interval the bit is 0.
   * Mid of the interval always have a transition it is for clocking only.
   * No transition at the start of a bit period represents one.
<img width="615" height="200" alt="image" src="https://github.com/user-attachments/assets/ee474640-45f2-422d-b1ee-d97b3b948f16" />

Trade off of Bipase
     Con:
          * Requires more bandwidth (Number of Signal changes is high)
          * At least one transition per bit time and possibly two
          * Maximum modulation rate is twice NRZ
     Pros:
          * Synchronization on mid bit transition (self clocking)
          * No DC component
          * Error detection  


## Scrambling  
``` 
     Scrambling is a technique that replaces long sequences of 0s with predefined patterns to maintain synchronization and eliminate DC components, without adding extra bits.
* Filling sequence
— Must produce enough transitions to sync
— Must be recognized by receiver and replace with original
— Same length as original
• No dc component
• No long sequences of zero level line signal
• No reduction in data rate
• Error detection capability
     NRZ (L or I) → Needs scrambling (or some other technique) because long runs of 0s (or no transitions) cause synchronization loss and a strong DC component.
     
     Manchester (and Differential Manchester) → Does not need scrambling, since every bit has a transition in the middle, which guarantees synchronization and avoids DC bias.
```
## AMI-based scrambling methods to handle long zeros.

### B8ZS → 8 zeros, HDB3 → 4 zeros.

1. B8ZS (Bipolar with 8-Zero Substitution)
     ```
     Used mainly in North America (T1 lines).
     Problem it solves: AMI cannot handle 8 consecutive 0s → causes loss of synchronization.
     Solution: Replace 8 consecutive zeros with a special pattern containing two bipolar violations.
     Example substitution: 00000000 → 000VB0VB
     V = violation (same polarity as previously met 1)
     B = normal bipolar pulse (Opposite polarity as previously met 1)
     ```
2. HDB3 (High-Density Bipolar 3-Zero)
     ```
     Used mainly in Europe (E1 lines).
     Problem it solves: AMI cannot handle 4 consecutive zeros.
     Solution: Replace 4 consecutive zeros with a pattern 000V or B00V depending on number of previous ones to maintain bipolar rules.
     Ensures sufficient transitions for clock recovery.
     
     ```
```
Ex :
   B8ZS : 1 0 0 0 0 0 0 0 0 1 = + 0 0 0 + − 0 − + 1
   HDB3 : 1 0 0 0 0 1 0 0 0 0 1 = + 0 0 0 − + 0 0 0 + −
```
<img width="967" height="684" alt="image" src="https://github.com/user-attachments/assets/75031269-98a7-40d8-9e1a-4b5d681b9a48" />



2. Digital data to Analog signal
   * Amplitude shift keying (ASK)
   * Frequency shift keying (FSK)
   * Phase shift keying (PK)


1. Amplitude shift keying
   <img width="550" height="249" alt="image" src="https://github.com/user-attachments/assets/42cb4009-8e1e-4da5-9ad7-7d3bc98a05a0" />
   * Less used
   * If a gain happen malware created

2. Binary frequency shift keying
   * Most common form
   * Two binary values represented from two freaquencies
   * Less susceptible to error than ASK
   * High frequency radio
   <img width="330" height="145" alt="image" src="https://github.com/user-attachments/assets/f15b94b4-5a52-4f20-a36c-b6362e40696e" />
    ### Multiple FSK:
   * More than two frequencies used
   * More bandwidth efficient
   * Each signalling element represents more than one bit
   * Used for duplex voice calls, 4 frequencies for 4 data lines is needed
 3.  Binary phase shift keying

   * Phase of carrier signal is shifted to represent data
   * Binary PSK - Two phases represents two binary digits
   <img width="286" height="113" alt="image" src="https://github.com/user-attachments/assets/bd1ded72-a641-43f1-aae7-92a780eb29d9" /> <br>
   * Different PSK -  Phase shifted relative to previous transmission rather
than some reference signal  
       ```
       A ‘1’ is represented by a phase change (e.g., 180°).  
       A ‘0’ is represented by no phase change.
       ```
   <br>  
   <img width="309" height="139" alt="image" src="https://github.com/user-attachments/assets/666c0707-1340-412c-91ff-5c19309219e4" />
   
  4. Quadrature PSK
More efficient use by each signal element representing more than one bit
— e.g. shifts of  /2 (90 o
— Each element represents two bits


3. Analog Data to Digital Signal


   * PCM - Pulse Code Modulation
     ```
     Pulse amplitude modulation (Reading the amplitude) -> Quantization (Rounding off) -> Pulse code modulation (Converting to the bits)
     ```
     <img width="930" height="675" alt="image" src="https://github.com/user-attachments/assets/99992a73-ae11-4d45-b9e4-6f8af016c9af" />

Nonlinear Encoding
    <img width="625" height="342" alt="image" src="https://github.com/user-attachments/assets/b50da618-f952-48de-85f7-a9fa07a04f5a" />
    * Delta Modulation
    Analog input is approximated by a staircase
function.  
    Move up or down one level () at each sample interval.  
    <img width="732" height="592" alt="image" src="https://github.com/user-attachments/assets/da4c5351-4ead-486c-9b38-1bcc679733d6" />

     ```
     If the analog signal is higher than the staircase function, the function moves up by delta. This upward movement is represented by a binary 1.
     If the analog signal is lower than the staircase function, the function moves down by delta. This downward movement is represented by a binary 0.
     ```
   Performance:
        Good voice reproduction
        The performance achieved by PCM using 7bits is comparable to delta modulation which use only 1bit. So the bitrate is much lower. Because for every sample, PCM generates 7bit versus delta modulation produces only 1bit.


 4. Analog Data to Analog Signals
       * Higher frequency can give more efficient transmission
       * Permits frequency division multiplexing
 ### Types of Modulation
 - Amplitude
 - Frequency
 - Phase

   *Amplitude Modulation*
   -  Amplitude of a carrier signal is altered according to information in a message signal
   -  Frequency of the carrier signal is usually much greater than the highest frequency of the input signal
    <img width="729" height="560" alt="image" src="https://github.com/user-attachments/assets/2b711851-b0c4-4244-ac65-fc43c646d05e" />

   
