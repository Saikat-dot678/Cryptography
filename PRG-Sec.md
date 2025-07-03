
---

## 🔐 Pseudorandom Generator (PRG) – Formal Definition & Security

### 🌱 What is a PRG?

* A **PRG** is a deterministic algorithm `G` that takes a **short random seed** from a keyspace `K` and outputs a **longer string** of `n` bits:

  $$
  G: K \rightarrow \{0,1\}^n
  $$
* **Goal**: The output should be *computationally indistinguishable* from a **uniform random string** in $\{0,1\}^n$.

---

## 🎯 Indistinguishability from Random

### 🤖 What does it mean to look "random"?

* Let:

  * `G(k)` be the PRG output for uniformly random seed `k`.
  * `U_n` be the uniform distribution over all `n`-bit strings.
* A PRG is secure if **no efficient algorithm** (statistical test) can distinguish between `G(k)` and a truly random `n`-bit string.

---

## 🧪 Statistical Tests

### ✅ What is a Statistical Test?

* A statistical test `A` is any **efficient algorithm**:

  $$
  A: \{0,1\}^n \rightarrow \{0,1\}
  $$

  * `A(x) = 1`: "x looks random"
  * `A(x) = 0`: "x does not look random"

### 🧠 Example Tests:

1. **Balance Test**: Number of 0s ≈ number of 1s (difference < $10\sqrt{n}$)
2. **Double Zero Pattern**: Count of `00` blocks ≈ $n/4$
3. **Max Run Length**: Longest sequence of 0s ≈ $\log n$

> 🔎 Note: Statistical tests can behave wrongly (e.g., consider the all-1s string passing the max run test).

---

## ⚖️ Advantage of a Statistical Test

### 📐 Formal Definition

$$
\text{Adv}_{\text{PRG}}^A = \left| \Pr_{k \leftarrow K}[A(G(k)) = 1] - \Pr_{r \leftarrow \{0,1\}^n}[A(r) = 1] \right|
$$

* **High advantage (\~1)** → `A` can distinguish PRG output from random → PRG is **insecure**
* **Low advantage (\~0)** → `A` cannot distinguish → PRG is **secure against A**

### 🧩 Examples:

* If `A` **always outputs 0**, then `Adv = 0` (useless test).
* If in 2/3 of keys `G(k)` starts with 1, and test checks if first bit is 1:

  $$
  \text{Adv} = \left| \frac{2}{3} - \frac{1}{2} \right| = \frac{1}{6}
  $$

  → Non-negligible ⇒ **PRG is broken**.

---

## ✅ Secure PRG Definition

A PRG `G` is **secure** if for **all efficient statistical tests** `A`,

$$
\text{Adv}_{\text{PRG}}^A \text{ is negligible}
$$

* **Necessity of efficiency**: If you allow *all* tests (even inefficient ones), **no PRG can be secure**, because brute-force tests can distinguish.

---

## 🔁 Link to Unpredictability

### 🎯 Definition of Unpredictability:

* Given the first `i` bits of `G(k)`, it is hard to **predict the (i+1)ᵗʰ bit** with probability better than ½ + ε (for non-negligible ε).

### 🔁 Implication:

> **Secure PRG ⇒ Unpredictable**

**Proof sketch**:

* If an algorithm `A` can predict the next bit with ε advantage,
* Then construct a test `B` that:

  * Uses `A` to predict bit i+1
  * Outputs 1 if prediction is correct
* `B` becomes a distinguisher ⇒ PRG is **not secure**

---

## 🔁 Converse: Yao’s Theorem (1982)

### 📘 Theorem:

> If a PRG is unpredictable at *every* position i, then it is a **secure PRG**.

* **Meaning**: Next-bit predictors are **universal distinguishers**
* So **PRG is secure ⇔ PRG is unpredictable**

---

## 🔁 Backward Predictability & Security

### Question:

> If you can predict **first bit** from the **last bits**, is the PRG predictable?

### Answer: **Yes**, because:

* Then PRG is **not secure**
* ⇒ By **Yao's theorem**, PRG is **predictable** (at some position)

---

## 🧾 Computational Indistinguishability Notation

### Generalized View:

Two distributions $P_1$ and $P_2$ are **computationally indistinguishable** if:

$$
P_1 \approx_c P_2
$$

Means:

* For all **efficient** statistical tests `A`,

$$
\left| \Pr_{x \leftarrow P_1}[A(x) = 1] - \Pr_{x \leftarrow P_2}[A(x) = 1] \right|
$$

is **negligible**

### 📌 PRG Security (Rewritten):

$$
\{G(k) \mid k \leftarrow K\} \approx_c \mathcal{U}_n
$$

---

## 💡 Summary

| Concept                            | Key Idea                                           |
| ---------------------------------- | -------------------------------------------------- |
| PRG                                | Outputs long string from short seed                |
| Secure PRG                         | Output indistinguishable from uniform              |
| Statistical Test                   | Efficient distinguisher algorithm                  |
| Advantage                          | Test’s ability to distinguish PRG from random      |
| Secure PRG ⇒ Unpredictable         | Next bit cannot be guessed from previous bits      |
| Yao’s Theorem                      | Unpredictability ⇔ Security                        |
| Computational Indistinguishability | Core idea behind defining security in cryptography |

---

Let me know if you'd like this turned into a **PDF**, **visual mind map**, or **flashcards**!
