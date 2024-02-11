# This file represents what I learnt

## What is Hashing?

-   Hashing is the process of scrambling a piece of information or data beyond recognition. We use hash functions to convert input into hash Digest. These functions are irreversible by design.
-   NOTE: key difference between this and encryption is that hashing is irreversible and has no reversing key
-   Use cases are integrity checks, storing key data like passwords in cache

## What is SHA?

-   SHA or Secure Hash Algorithm is a cryptographic hash function developed by the NSA & NIST joint development
-   Has multiple families such as SHA-0, SHA-1, SHA-2 & SHA-3
-   SHA-1 160 bit
-   SHA-2 256 and 512 bit
-   SHA-3 256 and 512 bit + different internal structure

## Characteristics of SHA?

-   Length of original message should be less than 2^64 bits
-   Length of digest is always 160 bits in length
-   Digest should not be able to produce the original message ( to prevent brute force attacks )

## Procedure of SHA

-   Step 1 Padding bits:

    -   Bits are padded with 1 and rest 0s
    -   Do this until 64 bits short of a multiple of 512

-   Step 2 Padding length:

    -   Length of the original message is padded to the result from step 1 (in the form of 64 bits)
    -   Resultant will be a multiple of 512, and this increases complexity

-   Step 3 Initialize Chaining Variables:

    -   The entire message is broken down into blocks of 512 bits each
    -   5 buffers are used of 32 bits each
        They are 5 words named A, B, C, D, and E.
    -   The first iteration has fixed hexadecimal values.

-   Step 4 Process each block
    -   each 512 bit block is broken down into 16 sub blocks of 32 bit each
    -   There are 4 rounds of operations, each of them utilizing the abcde register, the 512 bit block and a constant K[t].
    -   Each round has 20 iterations, so total iterations = 4x20 = 80 rounds.
    -   The constant value is an array of 80 elements, with 16 elements being used every round.
    -   Formula: ABCDE = E + Proces P + (S^5)(A) + W(t) + K(t)
        -   **ABCDE** = Register value of the chaining variables
        -   **P** = Logical Process that changes each round
        -   **S^5** = Circular shift by 5 bits
        -   **W(t)** = A 32 bit string derived from existing sub block
        -   **K(t)** = One of the constants which changes each round
        -   For the words from 0-16 (W(0-15)),, the **sub block M(t)** is the same as **W(t)**.
        -   The remaining 64 values are calculated as: **W[t]** = S(W(t-16) XOR W(t-14) XOR W(t-8) XOR W(t-3))

#### Thanks for reading

#### Happy Coding!
