
---

### 🔐 **The Problem: What Does It Mean for a Stream Cipher to Be Secure?**

When defining the security of encryption, we need to answer:

* What can the **attacker** do?
* What is the **attacker** trying to learn?

For stream ciphers (used with one-time keys), the attacker is assumed to **only see one ciphertext**. We want to define security in this limited context.

---

## 🚫 Flawed Security Definitions

### 1. **“The attacker shouldn’t recover the key”**

Bad definition: An insecure cipher like `C = M` (plaintext equals ciphertext) wouldn’t leak the key — but it still leaks **everything** else. So clearly, that’s not secure.

### 2. **“The attacker shouldn’t recover the full plaintext”**

Still bad: Imagine a cipher that reveals half the plaintext (e.g., M₀‖OTP(M₁)). Even though it encrypts M₁ securely, revealing M₀ openly violates confidentiality.

---

## ✅ What We *Really* Want: **No Information Leakage**

Shannon’s **Perfect Secrecy** said:

> For any two messages `M₀` and `M₁` of the same length, the ciphertext distributions of `Enc(M₀)` and `Enc(M₁)` should be **identical**.

But perfect secrecy requires:

* Keys as long as the message (impractical).
* Key reuse is forbidden.

So we move to a more practical notion: **Semantic Security**.

---

## 🔍 **Semantic Security Definition (One-Time Key)**

We define **semantic security** via an experiment with a **challenger** and an **adversary A**:

### 🔁 **Experiment B (where B ∈ {0, 1})**

1. Challenger generates a random key.
2. Adversary A submits two equal-length messages: `M₀`, `M₁`.
3. Challenger encrypts `M_B` (either `M₀` or `M₁`) and gives ciphertext `C` to A.
4. A outputs a guess `B′` trying to determine which message was encrypted.

---

## 📈 Semantic Security Advantage

Let:

* `W₀ = Pr[B′ = 1 | ciphertext of M₀]`
* `W₁ = Pr[B′ = 1 | ciphertext of M₁]`

Then:

```
Advantage(A) = |W₀ - W₁|
```

**Interpretation**:

* If `Adv ≈ 0`: A can’t tell which message was encrypted ⇒ Secure
* If `Adv ≈ 1`: A can reliably distinguish ⇒ Insecure

A scheme is **semantically secure** if **all efficient adversaries** have **negligible advantage**.

---

## 🧠 Implication: Leaking *Any Bit* Breaks Semantic Security

Suppose there's an adversary A that can always guess **one bit** of plaintext from ciphertext (say, the least significant bit). Then we can construct B to:

1. Choose `M₀` ending in `0`, and `M₁` ending in `1`.
2. Use A to extract the LSB of ciphertext → that directly reveals B.

So advantage = 1 → system is broken.

Hence, **revealing any bit (MSB, parity, XOR of bits)** breaks semantic security.

---

## 🔒 One-Time Pad is Semantically Secure (and More)

The OTP satisfies **perfect secrecy**, which is stronger than semantic security.

In OTP:

```
C = K ⊕ M
```

Since K is random and used once, the ciphertext distribution is uniform and independent of M.

Therefore, for any M₀ and M₁:

```
Dist(C|M₀) == Dist(C|M₁)
```

No adversary (efficient or not) can distinguish — so **semantic security is trivially satisfied**.

---

## 💡 Summary

| Concept                 | Description                                                                           |
| ----------------------- | ------------------------------------------------------------------------------------- |
| **Semantic Security**   | An attacker cannot distinguish encryptions of two chosen plaintexts.                  |
| **Definition**          | Based on indistinguishability between experiments with encryptions of `M₀` and `M₁`.  |
| **Advantage**           | The attacker’s probability of correctly guessing which message was encrypted.         |
| **Leakage of Any Bit**  | Violates semantic security.                                                           |
| **OTP**                 | Perfectly and semantically secure.                                                    |
| **PRG + Stream Cipher** | The goal is to show that using a secure PRG implies semantic security (next segment). |

---

