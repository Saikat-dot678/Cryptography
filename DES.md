🔹 1. Introduction to Block Ciphers
✅ What Is a Block Cipher?

    A block cipher is a deterministic algorithm that maps fixed-length blocks of plaintext (N bits) to ciphertext (N bits) using a secret key.

    Examples: DES, Triple DES (3DES), AES.

🔹 2. DES Overview
📜 Historical Context

    1970s: IBM developed a cipher named Lucifer, led by Horst Feistel.

    1973: U.S. National Bureau of Standards (NBS) issued a request for a standard encryption algorithm.

    1976: A modified Lucifer variant was adopted as the Data Encryption Standard (DES).

    1997: DES was practically broken via exhaustive key search (brute-force).

    2000: NIST (formerly NBS) standardized AES (Rijndael) as DES’s successor.

🔹 3. DES Parameters
Parameter	Value
Key Size	56 bits (effective key length)
Block Size	64 bits
Rounds	16 Feistel rounds
Round Keys	16 keys of 48 bits each
Structure	Feistel Network
S-Boxes	8 S-boxes (each maps 6 bits → 4 bits)
🔹 4. Feistel Network: The Core of DES
🔁 Structure of a Feistel Round

Given an input of 2n2n bits:

    Split into two halves: Left (L) and Right (R)

Round Transformation (i-th round):
Li=Ri−1
Li​=Ri−1​
Ri=Li−1⊕Fi(Ri−1)
Ri​=Li−1​⊕Fi​(Ri−1​)
🔁 Inversion of a Feistel Round

Given output Li,RiLi​,Ri​, we can recover the input:
Ri−1=Li
Ri−1​=Li​
Li−1=Ri⊕Fi(Ri−1)
Li−1​=Ri​⊕Fi​(Ri−1​)

Observation: Feistel rounds are easily invertible, even if FiFi​ is not invertible.
🔹 5. Luby-Rackoff Theorem (1985)

    Three rounds of a Feistel network using a secure PRF results in a secure pseudorandom permutation (PRP).

    If each round uses a distinct key for a secure PRF:

        The result is indistinguishable from a truly random permutation.

    Ensures block cipher security from PRF assumptions.

🔹 6. High-Level DES Structure

[ Input Block (64 bits) ]
        ↓
[ Initial Permutation (IP) ]
        ↓
[ 16-Round Feistel Network ]
        ↓
[ Final Permutation (IP⁻¹) ]
        ↓
[ Output Ciphertext (64 bits) ]

    Initial/Final Permutations: Bitwise rearrangements, not essential for security.

    Main security lies in the Feistel network and function F.

🔹 7. DES Round Function: F Function
📥 Inputs:

    32-bit half-block R

    48-bit round key KiKi​

⚙️ Steps:

    Expansion (E-box): Expand 32 bits → 48 bits (by bit replication and permutation).

    Key Mixing: XOR expanded output with 48-bit round key.

    Substitution (S-boxes):

        Break 48 bits into 8 groups of 6 bits.

        Each group → passed through an S-box.

        Each S-box maps 6 bits → 4 bits (non-linear).

        Output: 8 × 4 = 32 bits

    Permutation (P-box): Rearrange the 32 bits using a fixed permutation.

🔹 8. S-Boxes in DES
✅ Key Properties

    8 S-boxes, labeled S1 to S8.

    Each is a lookup table: 64 entries, each with 4-bit output.

    The S-boxes are non-linear to avoid algebraic attacks.

    Carefully designed to resist linear and differential cryptanalysis.

⚠️ Why Non-Linearity Matters

    If S-boxes were linear:

        Entire DES could be written as a matrix-vector product.

        Would result in a linear function → trivially broken.

    Linearity implies structural weaknesses (e.g., XOR of outputs = XOR of inputs).

    Non-linear S-boxes introduce confusion (Shannon's principle).

🔹 9. Security Failures & Key Search
🔓 DES Broken by Brute-Force

    Key length: 56 bits → 256256 possible keys.

    1997: DES cracked via exhaustive key search.

    Cost-effective hardware can search all keys within hours now.

🔹 10. DES Summary
Component	Purpose
Initial/Final Permutation	Bit rearrangement (not security-critical)
Feistel Network	Provides invertibility with arbitrary round functions
Function F	Main source of confusion; applies expansion, XOR, S-boxes, permutation
S-boxes	Introduce non-linearity, resist algebraic attacks
Round Keys	Derived from the 56-bit key; each round uses a different 48-bit subkey
🔹 11. Key Insights

    DES is an iterated cipher based on Feistel networks.

    Feistel structure enables easy inversion, making encryption/decryption symmetric.

    Security critically depends on:

        Non-linearity of S-boxes

        Proper key schedule

        Number of rounds

    DES has historical significance but is no longer considered secure.

🔹 12. Looking Ahead
➤ Next Topics:

    Triple DES (3DES): Extension to increase security by using DES three times.

    AES (Advanced Encryption Standard): Replacement for DES, based on substitution-permutation networks, not Feistel.

📝 Exercises (Optional)

    Feistel Inversion Practice:
    Given a Feistel round output, compute the original input.

    DES Linearity Exploration:
    Why does linearity in S-boxes allow for trivial recovery of keys?

    S-box Implementation:
    Write a function that simulates an S-box from a lookup table.


📌 1. Feistel Network Structure

           Feistel Round (i-th round)
          -----------------------------
          |                           |
Input:   Lᵢ₋₁         Rᵢ₋₁            ← 2n bits
          |            |              
          |            |            
          |     +------+-----+       
          |     |   Round     |      
          |     | Function Fᵢ|<------- Key Kᵢ
          |     +------+-----+
          |            |
          |         Fᵢ(Rᵢ₋₁)
          |            |
          |            |        
          |         XOR ◄──────────── Lᵢ₋₁
          |            |
          |            v
Output:  Lᵢ = Rᵢ₋₁     Rᵢ = Lᵢ₋₁ ⊕ Fᵢ(Rᵢ₋₁)

📌 2. DES Full Structure Overview

        +---------------------------+
        |   64-bit Plaintext Block  |
        +---------------------------+
                    |
                    v
       +-----------------------------+
       | Initial Permutation (IP)    |
       +-----------------------------+
                    |
              +-----+-----+
              |           |
           Left₀       Right₀       (32 bits each)
              |           |
         [16 Feistel Rounds]
              |           |
           Left₁       Right₁
              |           |
               ...
              |           |
          Left₁₆      Right₁₆
              |           |
        +-----+-----+
              |
       +-----------------------------+
       | Final Permutation (IP⁻¹)    |
       +-----------------------------+
                    |
                    v
       +---------------------------+
       |   64-bit Ciphertext Block |
       +---------------------------+

📌 3. DES Round Function F (inside one Feistel round)

             32-bit input (Rᵢ₋₁)
                    |
            +------------------+
            | Expansion (E-box)| → 48 bits
            +------------------+
                    |
                    v
              +-----------+
              |  XOR with |
              | 48-bit Kᵢ |
              +-----------+
                    |
                    v
      +-----+-----+-----+-----+-----+-----+-----+-----+
      | S1  | S2  | S3  | S4  | S5  | S6  | S7  | S8  | ← Each S-box gets 6 bits
      +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
         |    |    |    |    |    |    |    |
         v    v    v    v    v    v    v    v
        4b   4b   4b   4b   4b   4b   4b   4b → 32 bits
                    |
                    v
        +------------------------+
        | Permutation (P-box)    |
        +------------------------+
                    |
               Final 32-bit Output

📌 4. Inside One S-Box

         6-bit input: b1 b2 b3 b4 b5 b6
                      ↑     ↑     ↑
         Row index: b1b6    → determines row (2 bits)
         Col index: b2b3b4b5 → determines column (4 bits)

        S-Box: 4x16 Table = 64 values (each 4 bits)

        Example:
        Input: 011011 (binary)
          Row: 01 (1)
          Col: 1101 (13)
          Output = S[row=1][col=13] = 4-bit output

📌 5. DES Encryption & Decryption (Symmetry)

    Decryption is just the same process as encryption, but round keys are used in reverse order.

Encryption:
  K1 → Round 1
  K2 → Round 2
   ...
  K16 → Round 16

Decryption:
  K16 → Round 1
  K15 → Round 2
   ...
  K1 → Round 16

    Because Feistel networks are symmetric, the same circuit can be reused for encryption and decryption.

📌 Summary Diagram

    [Plaintext] → [Initial Permutation]
                    ↓
        +--------------------------+
        | 16-Round Feistel Network |
        |  Each round uses F + Kᵢ  |
        +--------------------------+
                    ↓
          [Final Permutation]
                    ↓
              [Ciphertext]

