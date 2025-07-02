Here are well-structured, in-depth notes based on your transcript, broken into clear sections for easier revision and understanding:

---

# 📘 **Stream Cipher & Pseudorandom Generators (PRGs) – Detailed Notes**

---

## 🔐 **Recap: What is a Cipher?**

A **cipher** is defined over:

* **Key space (𝒦)**
* **Message space (𝑀)**
* **Ciphertext space (𝒞)**

It consists of:

* **Encryption (E)** and **Decryption (D)** algorithms
* **Correctness property**:

  > D(k, E(k, m)) = m for all keys *k* and messages *m*

---

## 🧠 **One-Time Pad (OTP)**

* **Key = message = ciphertext = n-bit strings**
* **Encryption**: `C = M ⊕ K`
* **Decryption**: `M = C ⊕ K`
* ⛑️ **Perfect secrecy**: ciphertext reveals no info about plaintext
* ❗ **Limitation (Shannon’s Bad News Lemma)**: Key must be as long as the message ⇒ impractical

---

## 🚀 **Stream Cipher: Making OTP Practical**

### 🎯 **Goal**

* Reduce key length by generating long pseudorandom sequences from short keys

---

## 🔁 **Pseudorandom Generator (PRG)**

### 🧩 Definition

A PRG is a deterministic function:
**G: {0,1}ˢ → {0,1}ⁿ**, where **n ≫ s**

### ✅ Required Properties

1. **Efficient** to compute (deterministic)
2. Input seed (s-bit) is random
3. Output must **“look” random** (defined formally)

---

## 🔐 **Stream Cipher Construction using PRG**

### 📦 Key Idea

* Use short random seed `k ∈ {0,1}^s` as key
* Generate long pad: `G(k) ∈ {0,1}^n`
* Encrypt: `C = M ⊕ G(k)`
* Decrypt: `M = C ⊕ G(k)`

> ⚠️ **No perfect secrecy**, because key is shorter than the message.

---

## ❓ **Why Is Stream Cipher Secure Then?**

It’s secure **only if** the PRG output is **unpredictable**.

---

## ❌ Insecurity from Predictable PRG

### 🔍 Predictable PRG ⇒ Insecure Cipher

* If attacker knows partial plaintext (e.g., standard prefix like "From: "), they can recover part of the pad using `C ⊕ prefix`
* If PRG is predictable, they can compute rest of `G(k)` ⇒ decrypt full message

---

## ⚠️ **Definition: Predictable PRG**

A PRG **G** is **predictable** if:

> ∃ efficient algorithm A, position i ∈ \[1, n-1], and ε non-negligible
> such that:
> `Pr[A(G(k)₁…i) = G(k)_{i+1}] ≥ ½ + ε`

→ i.e., given prefix, can guess next bit with noticeable advantage

---

## ✅ **Definition: Unpredictable PRG**

G is **unpredictable** if:

> ∀ efficient algorithms A and all positions i:
> `Pr[A(G(k)₁…i) = G(k)_{i+1}] ≈ ½ (≤ ½ + negligible)`

---

## 🚫 **Bad PRG Examples**

### ❌ 1. XOR checksum generator

If all bits XOR to 1, the last bit is predictable given the rest

### ❌ 2. Linear Congruential Generator (LCG)

* Formula: `rₙ = (a·rₙ₋₁ + b) mod p`
* Has good statistical properties
* But **predictable**, so **never use in crypto**

### ❌ 3. glibc `random()` (used in early Linux & Kerberos v4)

* Built on LCG
* **Predictable**, should **never be used for crypto**

---

## 📉 **Negligible vs Non-Negligible (Theory)**

### 🔹 Practical View:

* **Non-negligible**: > 1 / 2³⁰ (e.g., 1 in a billion ⇒ possible!)
* **Negligible**: < 1 / 2⁸⁰ (too rare to worry about)

### 🔹 Theoretical Definition:

Let ε(λ) be a function of security parameter λ:

* **Negligible**: ∀ polynomials p(λ), ∃ λ₀ s.t. ∀ λ > λ₀:

  > ε(λ) < 1 / p(λ)

* **Non-negligible**: ∃ polynomial p(λ), ε(λ) > 1 / p(λ) infinitely often

---

## 💡 Examples of Negligibility

| Function                        | Negligible? | Why?                       |
| ------------------------------- | ----------- | -------------------------- |
| `1/2^λ`                         | ✅ Yes       | Exponentially small        |
| `1/λ^1000`                      | ❌ No        | Still > 1/poly(λ)          |
| `1/2^λ` (odd λ), `1/λ` (even λ) | ❌ No        | Happens polynomially often |

---

## 📌 **Key Takeaways**

1. One-time pad is perfectly secure but impractical.
2. Stream ciphers use PRGs to generate long pads from short keys.
3. Security depends on the **unpredictability** of the PRG.
4. Avoid weak PRGs like LCGs or `random()` from glibc.
5. Understand negligible vs non-negligible to reason about security.

---

Let me know if you want these notes as a **Markdown file**, **PDF**, or **flashcards**!
