✅ Part 1: Exhaustive Search Attack on DES
🎯 Goal:

Given known plaintext-ciphertext pairs (mi,ci)(mi​,ci​), find the key kk such that:
DESk(mi)=ci
DESk​(mi​)=ci​
📘 Lemma: One Pair is Enough to Uniquely Identify the Key (w.h.p.)
Assumption: DES behaves like an ideal cipher

(meaning for each key kk, DESkDESk​ is a random permutation over {0,1}64{0,1}64).
🎲 Uniqueness Proof (Sketch):

    Suppose there exists some other key k′≠kk′=k such that:
    DESk′(m)=DESk(m)=c
    DESk′​(m)=DESk​(m)=c

    Probability for one such k′k′ to satisfy this is:
    Pr⁡[DESk′(m)=c]=1264
    Pr[DESk′​(m)=c]=2641​

    Total number of other keys: 256−1256−1

    Total collision probability (via union bound):
    (256−1)⋅1264≈128=1256
    (256−1)⋅2641​≈281​=2561​

✅ Conclusion:

    With 99.5% probability, only one key maps mm to cc

    With two pairs, this probability is virtually 1

🧪 Part 2: The DES Challenge

    Issued by RSA to demonstrate DES’s weakness

    Provided: 3 plaintext-ciphertext pairs

    Task: Recover the key by brute-force

    Subsequent ciphertexts: decrypt using recovered key

⏱️ Timeline:
Year	Method	Time
1997	Internet search (distributed.net)	3 months
1998	EFF Deep Crack ($250k)	3 days
1999	Deep Crack + Internet Search	22 hours
Later	COPACABANA (120 FPGAs, $10k)	7 days
🔐 Part 3: Strengthening DES
🚫 Why Not Just Use Double DES?
❌ Double DES:
c=Ek2(Ek1(m))
c=Ek2​(Ek1​(m))

You’d think:

    2 keys → 21122112 keyspace

    Should be secure

💥 But it’s not! Meet-in-the-Middle Attack:
🧠 Meet-in-the-Middle Attack (Diagram)

Goal: Find k1,k2k1​,k2​ such that:
Ek2(Ek1(m))=c
Ek2​(Ek1​(m))=c

We rewrite as:
Ek1(m)=Dk2(c)
Ek1​(m)=Dk2​(c)
🔧 Steps:

    Build Table of Ek(m)Ek​(m) for all k1∈{0,1}56k1​∈{0,1}56

    For each k2k2​, compute Dk2(c)Dk2​​(c) and search in table

    When values match → found candidate pair (k1,k2)(k1​,k2​)

⏱️ Time & Space Complexity:

    Time: 256256 encryptions + 256256 decryptions + lookups → total ≈ 257−263257−263

    Space: Table of 256256 entries

🔑 Conclusion: Only twice as slow as single DES, but still breakable in 263263 time
🔁 Part 4: Triple DES (3DES)
🛠️ Construction:
Ek1(Dk2(Ek3(m)))
Ek1​(Dk2​(Ek3​(m)))

    EDE mode chosen so that if k1=k2=k3k1​=k2​=k3​, it reduces to single DES

    Used to allow backward compatibility

📏 Key Size: 168 bits (3 × 56)
🧠 Effective Security: ≈ 2¹¹², due to meet-in-the-middle attack
🧩 Part 5: DESX – Efficient Strengthening
🛠️ Construction:
DESXk1,k2,k3(m)=k1⊕DESk2(m⊕k3)
DESXk1​,k2​,k3​​(m)=k1​⊕DESk2​​(m⊕k3​)

    XOR before and after DES

    Very fast, adds only two XORs

    Key length: 184 bits (64 + 56 + 64)

🔐 Security: No known attack faster than 21202120
🧨 Important Warning:

Just doing one XOR (only before or only after DES) is insecure — it doesn't improve resistance to exhaustive search.
📌 Summary Table
Cipher	Keys Used	Security Level	Time to Break (est.)	Status
DES	56 bits	2⁵⁶	22 hours (old HW)	🔴 Broken
Double DES	112 bits	2⁶³ (attack)	Practical	🔴 Broken
Triple DES	168 bits	2¹¹²	Safe (slow)	🟡 Legacy Use
DESX	184 bits (w/ XORs)	2¹²⁰	Very Strong	🟢 OK (limited)












🎯 Goal:

Given:

    A known plaintext m

    A known ciphertext c
    Find the two DES keys (k1, k2) such that:

c = DES_k2(DES_k1(m))

🔐 Double DES Encryption

  m 
   |
   |  Encrypt with k1
   v
+-------------+
|   DES(k1)   |
+-------------+
   |
   |  Intermediate value (let's call it X)
   v
+-------------+
|   DES(k2)   |
+-------------+
   |
   v
   c

💥 Meet-in-the-Middle Attack Structure

We want to find a collision at the intermediate point X by computing it from both directions:
Step 1: Encrypt from Plaintext Side (All Possible k1)

For all 2^56 possible k1:
    X = DES_k1(m)
    Store (X, k1) in a table

            m
             |
        +-----------+   Try all k1
        | DES(k1_i) |----------------------+
        +-----------+                      |
             |                             |
             v                             |
        Intermediate X_i                  Store in table:
                                          (X_i, k1_i)

Step 2: Decrypt from Ciphertext Side (All Possible k2)

For all 2^56 possible k2:
    X' = DES_k2⁻¹(c)
    Check: Is X' in the table?
          If yes → Match found → Retrieve k1, k2

            c
             |
        +--------------+   Try all k2
        | DES⁻¹(k2_j)  |----------------------+
        +--------------+                      |
             |                                |
             v                                |
        Intermediate X'_j               Check if X'_j in table:
                                        If match: (X'_j == X_i)
                                        → Keys found: (k1_i, k2_j)

⏱️ Time & Space Complexity
Metric	Value
Time	~2^57 (2×2^56)
Space	~2^56 entries
This is much faster than exhaustive search over 2^112 key combinations.
