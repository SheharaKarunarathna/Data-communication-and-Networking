# Information redundancy - Coding

* A data word with d bits is encoded into a codeword with c bits c>d
* c bits must be decoded to get the original data
* If the c bits do not constitute a valid cordword an error is detected.
* For certain encoding schemes some types of errors can also be corrected

## Separability of a code

* A code is separable if it has separate fields for the data and the code bits
* A non separable code has the data and code bits integrated together extracting the data from the encoded word requires some processing.

## Parity code
  * Parity of the code is set so that the total number of '1's in the bit word (Including parity bit is even).
    ```
    If the number of 1s in the original word is odd parity is 1
    If the number of 1s in the original word is even parity is 0
    ```
## Hamming Distance
Hamming Distance is a measure of how different two binary strings are.
Definition
The Hamming distance between two equal-length binary strings is the number of bit positions in which they differ.
```
Example  
String A: 1011101  
String B: 1001001 
```
Differences at positions: 2, 4, 6 → Hamming distance = 3

Hamming code and CRC is in the back of DB book. 
