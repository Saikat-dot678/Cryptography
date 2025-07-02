

---

### **What is a Cipher?**

- **Fundamental Definition:**  
  - A cipher is a pair of algorithms:  
    - **E** (encryption) and **D** (decryption).
  - Operates over 3 sets:
    - **Key space** (\(\mathcal{K}\)): all possible keys.
    - **Message space** (\(\mathcal{M}\)): all possible plaintexts.
    - **Ciphertext space** (\(\mathcal{C}\)): all possible ciphertexts.

- **Correctness Property:**  
  - For any key \( K \in \mathcal{K} \) and any message \( M \in \mathcal{M} \):  
    \[
    D_K(E_K(M)) = M
    \]
  - Decrypting an encryption (with the same key) always recovers the original message.
  - **Efficient** means “runs in reasonable time” — either polynomial time (theory) or “fast enough in practice”.

- **Encryption Randomness:**  
  - Many encryption algorithms use randomness (e.g., to select an IV or nonce), so encrypting the same message twice can yield different ciphertexts.
  - Decryption must always be deterministic: given key and ciphertext, the plaintext is uniquely determined.

---

### **One-Time Pad (Vernam Cipher):**

- **Spaces:**
  - Messages: All binary strings of some given length.
  - Ciphertexts: Same as message space.
  - Keys: Also all binary strings of that same length.

- **Encryption:**
  - \( C = M \oplus K \) (bitwise XOR).

- **Decryption:**
  - \( D_K(C) = C \oplus K = (M \oplus K) \oplus K = M \) (using associativity and that \( K \oplus K = 0 \)).

- **Key Recovery:**
  - Given \( M \) and \( C \), the key \( K = M \oplus C \).
  - Shows that if someone knows the plaintext and ciphertext, they instantly know the key used.

- **Practical Drawback:**  
  - **Key must be as long as the message** and truly random.
  - Secure, but the key distribution problem makes it impractical at scale.

---

### **Security: Perfect Secrecy (Shannon’s Definition)**

- **Intuitive Notion:**  
  - Ciphertext should reveal *no information* about the plaintext.
  - Even an all-powerful adversary with unlimited computation gains nothing about the message just from the ciphertext.

- **Formal Definition:**  
  - For any two messages \( m_0, m_1 \) of equal length, and any ciphertext \( c \):
    \[
    \Pr[E_K(m_0) = c] = \Pr[E_K(m_1) = c]
    \]
    where the probability is over the random (uniform) choice of key \( K \).
  - In other words, for every ciphertext, it's equally likely to correspond to *any* possible plaintext.

- **Implication:**  
  - Given any ciphertext \( c \), all \( m \) of matching length are equally likely to be the original message.
  - Ciphertext-only attacks are **impossible**: you literally learn nothing.

---

### **Proof that One-Time Pad Achieves Perfect Secrecy**

- For any given \( m \) and \( c \),  
  there is **one unique key** \( K = m \oplus c \) that produces \( c \) from \( m \).
- Number of possible keys mapping \( m \) to \( c \) = 1 (constant for all \( m, c \)).
- The probability, therefore, is \( \frac{1}{|\mathcal{K}|} \) for any message/ciphertext pair, and the distribution is uniform.
- Hence, one-time pad achieves perfect secrecy.

---

### **Shannon’s Impossibility Theorem**

- **Can we get perfect secrecy with shorter keys?**
  - **NO:** If a cipher has perfect secrecy, the number of possible keys must be at least the number of possible messages.
  - For an n-bit message, you need an n-bit key (or more).

- **Why is this important?**
  - Explains why the one-time pad, though perfectly secret, is impractical: the “key distribution problem” is inherent.

---

### **Key Takeaways**

- Ciphers are precisely defined with key/message/ciphertext spaces and efficient E/D algorithms. Correctness and (ideally) security are required.
- One-time pad is a theoretical ideal: provides perfect secrecy but cannot be used for general-purpose communication (due to key size and management).
- Perfect secrecy means the ciphertext leaks no information whatsoever. Only the one-time pad (with a perfectly random, unique, same-length key) achieves this.
- If you want perfect secrecy, you must pay the price: your key must be at least as big as your message.

---

Let me know if you’d like examples, diagrams, or to go deeper on practical replacements for the one-time pad (like stream ciphers or block ciphers)!
