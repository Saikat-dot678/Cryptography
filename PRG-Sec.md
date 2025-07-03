
---

## 🔐 1. What is a Pseudorandom Generator (PRG)?

### ➤ Formal Definition:

A **Pseudorandom Generator** is a deterministic function:

$$
G : \mathcal{K} \rightarrow \{0, 1\}^n
$$

* It takes a short, uniformly random **seed** `k ∈ K` and outputs a longer, `n`-bit string.
* The output of `G` is **not truly random** but should appear **indistinguishable from random** to any efficient observer.

### ➤ Goal of a PRG:

To ensure that:

$$
\text{Distribution of } G(k) \text{ (for random } k) \approx \text{Uniform distribution over } \{0,1\}^n
$$

---

## 🎯 2. What Does "Indistinguishable from Random" Mean?

We compare two distributions:

1. **PRG Output Distribution**: $G(k)$ where $k \leftarrow \mathcal{K}$
2. **Truly Uniform Distribution**: $r \leftarrow \{0,1\}^n$

We want **no efficient algorithm** to tell the difference between these two.

---

## 🧪 3. Statistical Tests (Distinguishers)

### ➤ What is a Statistical Test?

A **statistical test** is an algorithm:

$$
A : \{0,1\}^n \rightarrow \{0,1\}
$$

* `A(x) = 1`: Thinks `x` is **random**
* `A(x) = 0`: Thinks `x` is **not random**

### ➤ Examples:

1. **Balance Test**:

   * Accepts if the number of 0’s and 1’s in `x` differ by at most $10\sqrt{n}$.
   * For random strings, this condition is usually satisfied.

2. **Double Zero Pattern Test**:

   * Accepts if the number of occurrences of `00` ≈ $n/4$.
   * Rejects strings like all 0s or all 1s.

3. **Maximum Run Test**:

   * Accepts if the longest run of 0s ≤ $10 \cdot \log n$.
   * Fails on long uniform patterns.

> Statistical tests don’t have to be perfect—they can be fooled. Many such tests exist (e.g., NIST randomness tests).

---

## ⚖️ 4. Advantage of a Statistical Test

### ➤ Definition:

The **advantage** of a statistical test `A` against a PRG `G` is:

$$
\text{Adv}_{\text{PRG}}^A = \left| \Pr_{k \leftarrow \mathcal{K}}[A(G(k)) = 1] - \Pr_{r \leftarrow \{0,1\}^n}[A(r) = 1] \right|
$$

* Measures how **differently** A behaves on PRG output vs truly random.
* If:

  * **Adv ≈ 0** → `A` can’t distinguish PRG output from random.
  * **Adv ≈ 1** → `A` can easily distinguish PRG output (PRG is insecure).

### ➤ Example:

If the first bit of G(k) is 1 with 2/3 probability:

* A test that outputs 1 iff first bit is 1 has:

  $$
  \Pr[A(G(k)) = 1] = \frac{2}{3}, \quad \Pr[A(r) = 1] = \frac{1}{2}
  $$

  So,

  $$
  \text{Adv} = \left| \frac{2}{3} - \frac{1}{2} \right| = \frac{1}{6}
  $$
* 1/6 is non-negligible ⇒ **PRG is broken**.

---

## ✅ 5. Definition of a Secure PRG

A PRG `G` is **secure** if:

$$
\forall \text{ efficient statistical tests } A, \quad \text{Adv}_{\text{PRG}}^A \text{ is negligible}
$$

* That is, no polynomial-time algorithm `A` can distinguish `G(k)` from random with significant advantage.
* Must restrict to **efficient** `A`, otherwise brute-force attacks would always work.

---

## 🔁 6. Link to Unpredictability

### ➤ Definition of Unpredictability:

A PRG is **unpredictable** if:

$$
\forall i < n, \quad \text{given } G(k)_1, G(k)_2, ..., G(k)_i, \text{ it’s hard to predict } G(k)_{i+1}
$$

* Predicting correctly with probability $\frac{1}{2} + \epsilon$ for **non-negligible ε** breaks unpredictability.

### ➤ Why Security Implies Unpredictability:

* If a predictor `A` exists that predicts `G(k)_{i+1}` given the first `i` bits with advantage ε:

  * Then we can create a statistical test `B`:

    * Input: full `n`-bit string `x`
    * Run `A` on first `i` bits
    * Check if prediction matches `x_{i+1}`
  * This `B` distinguishes PRG output from random ⇒ PRG is **not secure**.

Hence,

> **Secure PRG ⇒ Unpredictable**

---

## 📜 7. Yao’s Theorem (1982)

> 🔁 **Yao's Theorem**: If a PRG is unpredictable at **every bit position**, then it is secure.

Formally:

* If for **every i**, no efficient algorithm can predict $G(k)_{i+1}$ from $G(k)_1, ..., G(k)_i$,
* Then no efficient statistical test can distinguish $G(k)$ from a uniform string.

### ➤ Implication:

* Next-bit unpredictability is **equivalent** to indistinguishability from random.
* So we don’t need to test all distinguishers—just next-bit predictors.

---

## 🔄 8. Application of Yao's Theorem

Suppose:

* It's easy to compute the **first bit** of `G(k)` from the **last n-1 bits**.

Then:

* This doesn’t fit "next-bit" prediction, but still implies **G is not secure**.
* By Yao’s theorem, any insecure PRG is also **predictable at some position** (even if not the first or last).
* So this reverse predictability still implies insecurity.

---

## 🔧 9. Computational Indistinguishability (Generalized)

### ➤ Notation:

$$
P_1 \approx_c P_2
$$

Means:

* Distributions $P_1$ and $P_2$ are **computationally indistinguishable**.
* No **polynomial-time algorithm** can distinguish them with non-negligible advantage.

### ➤ Applied to PRGs:

$$
\{ G(k) \mid k \leftarrow \mathcal{K} \} \approx_c \mathcal{U}_n
$$

→ Output of `G` is indistinguishable from uniform distribution.

---

## 🧠 10. Summary Table

| Concept                       | Summary                                                             |
| ----------------------------- | ------------------------------------------------------------------- |
| PRG                           | Expands short random seed to longer pseudorandom output             |
| Statistical Test              | Efficient algorithm trying to decide if input is random             |
| Advantage                     | Difference in behavior on PRG vs uniform input                      |
| Secure PRG                    | All statistical tests have negligible advantage                     |
| Unpredictability              | Can't predict next bit from previous                                |
| Yao’s Theorem                 | Unpredictability ⇔ Indistinguishability                             |
| Indistinguishability Notation | $P_1 \approx_c P_2$ means indistinguishable by efficient algorithms |

---


