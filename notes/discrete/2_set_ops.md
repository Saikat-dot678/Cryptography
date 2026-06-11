Excellent. We now begin **Chapter 2 — Basic Structures: Sets, Functions, Sequences, Sums, and Matrices** from Rosen. 

For cryptography, Chapter 2 is extremely important because:
* **Sets** $\rightarrow$ define key spaces, message spaces, ciphertext spaces.
* **Functions** $\rightarrow$ encryption and decryption algorithms.
* **One-to-one functions** $\rightarrow$ permutations and block ciphers.
* **Inverse functions** $\rightarrow$ decryption.
* **Sequences and sums** $\rightarrow$ probability, complexity analysis, cryptographic proofs.
* **Matrices** $\rightarrow$ coding theory, lattices, cryptanalysis.

---

# 📦 Chapter 2.1 — Sets

## 🤔 Why Sets?
Modern mathematics is written in the language of sets.
Consider RSA:
* **Message space:** $\{0, 1, 2, \dots, n-1\}$
* **Key space:** $\{\text{all valid keys}\}$
* **Ciphertext space:** $\{0, 1, 2, \dots, n-1\}$

These are all sets.

---

## 🧩 What is a Set?
A set is:
> **An unordered collection of distinct objects.**

The objects are called *elements* or *members*.

### 📝 Examples
* Set of vowels: $A = \{a, e, i, o, u\}$
* Set of prime numbers less than 10: $P = \{2, 3, 5, 7\}$
* Set of even numbers: $E = \{2, 4, 6, 8, \dots\}$

---

## 🔑 Membership
To indicate membership we use: 
$\in$ (Read: *belongs to* or *is an element of*)

* **Example:** $3 \in \{1, 2, 3, 4\}$ (True) ✅
* **Example:** $5 \in \{1, 2, 3, 4\}$ (False) ❌

To indicate non-membership we use:
$\notin$ 
* **Example:** $5 \notin \{1, 2, 3, 4\}$

---

## ⚖️ Important Properties

### Order Doesn't Matter
Consider: $\{1, 2, 3\}$ and $\{3, 2, 1\}$
These are **exactly the same set**.
Unlike lists, sets are unordered. 🔄

### Duplicates Don't Matter
$\{1, 2, 2, 2, 3\}$ is identical to $\{1, 2, 3\}$
Each element appears at most once. 🚫👯‍♂️

---

## 🏷️ Describing Sets
There are two common methods.

### Method 1: Roster Form
List all elements.
* **Example:** $A = \{1, 2, 3, 4\}$
* **Example:** $V = \{a, e, i, o, u\}$

### Method 2: Set Builder Notation
Describe a property.
* **Example (Even positive integers):** $$E = \{x \mid x \text{ is a positive even integer}\}$$
  *Read: The set of all $x$ such that $x$ is a positive even integer.*
* **Example (Multiples of 3):** $$A = \{x \in \mathbb{Z} \mid 3 \mid x\}$$

---

## 🔢 Common Number Sets
*These must be memorized.* 🧠

* **Natural Numbers:** $\mathbb{N}$
  Usually $\{0, 1, 2, 3, \dots\}$ *(Note: Some books start with 1.)*
* **Integers:** $\mathbb{Z}$
  $\{\dots, -2, -1, 0, 1, 2, \dots\}$
* **Rational Numbers:** $\mathbb{Q}$
  Numbers of the form $\frac{a}{b}$ where $a, b \in \mathbb{Z}, b \neq 0$
* **Real Numbers:** $\mathbb{R}$
  All numbers on the number line.
* **Irrational Numbers:** Examples: $\sqrt{2}, \pi, e$ (Not expressible as fractions).

---

## 🕳️ Empty Set
Sometimes a set has no elements. Called the empty set.
**Notation:** $\emptyset$ or $\{\}$

* **Example:** Positive integers less than 0 = $\{\}$ (No such integers exist).

---

## 🟰 Equality of Sets
Two sets are equal **iff** (if and only if) they contain exactly the same elements.
* **Example:** $A = \{1, 2, 3\}$, $B = \{3, 2, 1\}$. Then $A = B$. ✅
* **Example:** $A = \{1, 2, 3\}$, $B = \{1, 2, 4\}$. Not equal. ❌

---

## 🗂️ Subsets
One of the most important concepts.

**Definition:** $A$ is a subset of $B$ if *every* element of $A$ belongs to $B$.
**Notation:** $A \subseteq B$

* **Example:** $A = \{1, 2\}$, $B = \{1, 2, 3, 4\}$. Then $A \subseteq B$ because every element of $A$ is inside $B$.

### Proper Subset
**Notation:** $A \subset B$
Means: $(A \subseteq B)$ and $(A \neq B)$
* **Example:** $\{1, 2\}$ is a proper subset of $\{1, 2, 3\}$.

### Important Theorem 📜
To prove $A \subseteq B$, show:
> *If $x$ belongs to $A$, then $x$ belongs to $B$.*
*(This proof technique appears constantly).*

**Example Proof:**
Show: $\text{Even Integers} \subseteq \mathbb{Z}$
Let $x$ be an even integer.
Then $x = 2k$ for some integer $k$.
Hence $x$ is an integer.
Therefore: $\text{Even Integers} \subseteq \mathbb{Z}$ ∎

### Empty Set is a Subset of Every Set
Important fact: $\emptyset \subseteq A$ for every set $A$.
*Why?* There is no element in the empty set that can violate the subset condition. This is an example of *vacuous truth*. 👻

---

## 🌌 Power Set
One of the most important constructions.
The power set of $A$ is: **The set of all subsets of $A$.**
**Notation:** $\mathcal{P}(A)$

**Example:** Let $A = \{1, 2\}$
* Subsets: $\{\}$, $\{1\}$, $\{2\}$, $\{1, 2\}$
* Thus: $\mathcal{P}(A) = \{\emptyset, \{1\}, \{2\}, \{1, 2\}\}$

### Counting Subsets 🧮
If a set contains $n$ elements ($|A| = n$), then:
$$|\mathcal{P}(A)| = 2^n$$
*This theorem is enormously important in computer science and cryptography.*

**Example:**
$A = \{1, 2, 3\}$ contains 3 elements.
Therefore: $|\mathcal{P}(A)| = 2^3 = 8$ subsets.

---

## 📏 Cardinality
Cardinality means: **Number of elements.**
**Notation:** $|A|$

* **Example:** $A = \{1, 2, 3, 4\}$. Then $|A| = 4$.
* **Example:** $A = \{\}$. Then $|A| = 0$.

### 🕵️‍♂️ Why Cryptographers Care
Suppose a cryptographic key is 128 bits.
Each bit is $0$ or $1$.
Therefore, key space: $\{0, 1\}^{128}$
Number of keys: $2^{128}$

This is exactly a cardinality problem! Understanding set size is fundamental to security analysis. 🔐

---

## 🏁 Summary
You should now know:
* [x] **Set Notation:** $\in, \notin$
* [x] **Common Sets:** $\mathbb{N}, \mathbb{Z}, \mathbb{Q}, \mathbb{R}$
* [x] **Empty Set:** $\emptyset$
* [x] **Subsets:** $\subseteq, \subset$
* [x] **Power Sets:** $\mathcal{P}(A)$
* [x] **Cardinality:** $|A|$

**Key Fact:** If $|A| = n$, then $|\mathcal{P}(A)| = 2^n$

---

## ✍️ Exercises
1. List all subsets of: $\{a, b, c\}$
2. Determine whether: $\{1, 2\} \subseteq \{1, 2, 3\}$
3. Determine whether: $\{1, 4\} \subseteq \{1, 2, 3\}$
4. Compute: $\mathcal{P}(\{1, 2\})$
5. If $|A| = 5$, compute: $|\mathcal{P}(A)|$
6. Prove: $\emptyset \subseteq A$ for every set $A$.

*Next we'll cover **Section 2.2 — Set Operations**, where we learn unions, intersections, differences, complements, Cartesian products, and the algebra of sets. This is one of the most important sections in discrete mathematics and directly connects to probability, cryptography, and computer science.* 🚀



# 🧮 Chapter 2.2 — Set Operations

In Section 2.1, we learned:
* What sets are
* Membership
* Subsets
* Power sets
* Cardinality

Now we'll learn how to combine and manipulate sets.
This section is the set-theoretic equivalent of arithmetic. 🧮

Just as numbers have: `+`, `−`, `×`, `÷`
Sets have: $\cup$, $\cap$, $-$, $\overline{A}$, $\times$

These operations appear everywhere in:
* Probability 🎲
* Databases 🗄️
* Computer Science 💻
* Cryptography 🔐
* Machine Learning 🤖

---

## 1. Union ➕

The union of two sets contains all elements that belong to either set.
**Notation:** $A \cup B$ (Read: *A union B*)



[Image of Venn diagram showing A union B]


**Definition:**
$$A \cup B = \{x \mid x \in A \text{ or } x \in B\}$$

**Example:**
Let $A = \{1, 2, 3\}$ and $B = \{3, 4, 5\}$
Then:
$$A \cup B = \{1, 2, 3, 4, 5\}$$

*Notice:* **3** appears only once. Sets never duplicate elements. 🚫👯‍♂️

**Venn Diagram Interpretation:**
Imagine two overlapping circles. Union means: *everything inside either circle.*

---

## 2. Intersection ❌

The intersection contains elements common to both sets.
**Notation:** $A \cap B$ (Read: *A intersection B*)



[Image of Venn diagram showing A intersection B]


**Definition:**
$$A \cap B = \{x \mid x \in A \text{ and } x \in B\}$$

**Example:**
$A = \{1, 2, 3\}$ and $B = \{3, 4, 5\}$
Then:
$$A \cap B = \{3\}$$
Because **3** is the only element in both sets.

### 🚫 Disjoint Sets
Two sets are disjoint if they share no elements:
$$A \cap B = \emptyset$$

**Example:**
$A = \{1, 2\}$ and $B = \{4, 5\}$
Then $A \cap B = \emptyset$.

**Example from Cryptography:**
Suppose $A =$ valid AES keys and $B =$ valid RSA keys.
Then $A \cap B$ might be empty because the formats differ completely. 🗝️

---

## 3. Difference ➖

Difference means: *Elements in A but not in B.*
**Notation:** $A - B$



**Definition:**
$$A - B = \{x \mid x \in A \text{ and } x \notin B\}$$

**Example:**
$A = \{1, 2, 3, 4\}$ and $B = \{3, 4, 5\}$
Then:
$$A - B = \{1, 2\}$$

*Notice:* $A - B \neq B - A$ in general.
**Example:**
$$B - A = \{5\}$$
Different result! ⚠️

---

## 4. Complement 🌗

Suppose we have a universal set $U$ containing all objects under discussion.
The complement of A consists of everything in $U$ that is *not* in A.
**Notation:** $\overline{A}$ or $A^c$



[Image of Venn diagram showing the complement of set A]


**Definition:**
$$A^c = U - A$$

**Example:**
Universal set: $U = \{1, 2, 3, 4, 5, 6\}$
Set: $A = \{1, 2, 3\}$
Then:
$$A^c = \{4, 5, 6\}$$

---

## 5. Symmetric Difference 💠

Contains elements in *exactly one* of the sets.
**Notation:** $A \oplus B$



**Definition:**
$$A \oplus B = (A - B) \cup (B - A)$$

**Example:**
$A = \{1, 2, 3\}$ and $B = \{3, 4, 5\}$
Then:
$$A \oplus B = \{1, 2, 4, 5\}$$
*Notice:* **3** is removed because it belongs to both.

---

## ⚖️ Set Identities

Just as algebra has identities (like $x + 0 = x$), set theory has identities too.

### Identity Laws
$$A \cup \emptyset = A$$
$$A \cap U = A$$
*Example:* $\{1, 2\} \cup \{\} = \{1, 2\}$

### Domination Laws
$$A \cup U = U$$
$$A \cap \emptyset = \emptyset$$
*Example:* Anything unioned with the universal set becomes the universal set.

### Idempotent Laws
$$A \cup A = A$$
$$A \cap A = A$$
*Repeating a set changes nothing.*

### Commutative Laws
Order doesn't matter.
$$A \cup B = B \cup A$$
$$A \cap B = B \cap A$$

### Associative Laws
Grouping doesn't matter.
$$(A \cup B) \cup C = A \cup (B \cup C)$$
$$(A \cap B) \cap C = A \cap (B \cap C)$$

### Distributive Laws
Very important. These mirror ordinary algebra.
$$A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$$
$$A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$$

---

## 📜 De Morgan's Laws for Sets

These are among the most important identities in all mathematics. 🌟

**First Law:**
$$(A \cup B)^c = A^c \cap B^c$$
*Meaning:* Everything outside the union equals: Outside A AND outside B.

**Second Law:**
$$(A \cap B)^c = A^c \cup B^c$$
*Meaning:* Not in both means: Not in A OR not in B.

### 📝 Example
Universal set: $U = \{1, 2, 3, 4, 5, 6\}$
$A = \{1, 2, 3\}$
$B = \{3, 4\}$

Compute: $(A \cup B)^c$
First: $A \cup B = \{1, 2, 3, 4\}$
Thus: $(A \cup B)^c = \{5, 6\}$

Now check De Morgan:
$A^c = \{4, 5, 6\}$
$B^c = \{1, 2, 5, 6\}$
Intersection: $\{5, 6\}$
Same answer! ✅

---

## ✖️ Cartesian Product

One of the most important concepts.
**Definition:**
$$A \times B = \{(a, b) \mid a \in A, b \in B\}$$
*Notice:* Order matters.

**Example:**
$A = \{1, 2\}$ and $B = \{x, y\}$
Then:
$$A \times B = \{(1, x), (1, y), (2, x), (2, y)\}$$

### 📏 Cardinality of Cartesian Products
If $|A| = m$ and $|B| = n$, then:
$$|A \times B| = mn$$

**Example:**
$|A| = 3$ and $|B| = 4$
Then: $|A \times B| = 12$

### 🔐 Why Cryptographers Care
Suppose:
* Message set: $M = \{0, 1\}^{128}$
* Key set: $K = \{0, 1\}^{256}$

Then $M \times K$ represents all possible $(\text{message}, \text{key})$ pairs. This idea appears constantly in security definitions.

---

## ✅ Summary

You should now know:
* **Union:** $A \cup B$
* **Intersection:** $A \cap B$
* **Difference:** $A - B$
* **Complement:** $A^c$
* **Symmetric Difference:** $A \oplus B$
* **Cartesian Product:** $A \times B$
* **De Morgan's Laws:** * $(A \cup B)^c = A^c \cap B^c$
  * $(A \cap B)^c = A^c \cup B^c$
* **Product Cardinality:** $|A \times B| = |A||B|$

---

## ✍️ Exercises

Let $A = \{1, 2, 3\}$ and $B = \{2, 3, 4\}$. Compute:
1.  $A \cup B$
2.  $A \cap B$
3.  $A - B$
4.  $B - A$

5.  If $U = \{1, 2, 3, 4, 5\}$ and $A = \{1, 3, 5\}$, find $A^c$.
6.  Verify De Morgan's Law for: $A = \{1, 2\}$ and $B = \{2, 3\}$
7.  Compute: $\{a, b\} \times \{1, 2, 3\}$
8.  If $|A| = 7$ and $|B| = 9$, find $|A \times B|$.

*Next we'll study **Section 2.3 — Functions**, one of the most important sections in the entire book. Encryption, decryption, hash functions, PRFs, block ciphers, and public-key algorithms are all special kinds of mathematical functions.* 🚀


# 🧮 Chapter 2.3 — Functions

This is one of the most important sections in all of discrete mathematics.
For cryptography, functions are everywhere:
* **RSA encryption** = function
* **RSA decryption** = inverse function
* **AES** = function
* **Hash functions** = functions
* **Pseudorandom functions** = functions
* **Digital signatures** = functions

If you deeply understand this chapter, later cryptography—and the rigorous proofs expected in advanced research environments like the ISI R.C. Bose Centre or ETH Zurich—becomes much easier. 🚀

---

## ⚙️ 1. What is a Function?

**Intuitively:** A function is a rule that assigns *exactly one* output to each input.

**Notation:** $$f:A\rightarrow B$$
Read: *f is a function from A to B.*
* $A$ = domain
* $B$ = codomain

**Example:**
$$f(x) = x^2$$
* Domain: $\mathbb{R}$
* Codomain: $\mathbb{R}$
* Input: 2 $\rightarrow$ Output: 4
* Input: 5 $\rightarrow$ Output: 25

### 🏭 Function Machine View
Think of a machine:
```text
   Input x
      ↓
 [Function f]
      ↓
 Output f(x)

```

**Example:** $f(x) = 2x + 1$

* Input: 3 $\rightarrow$ Output: 7, because $f(3) = 2(3) + 1 = 7$.

---

## 🌍 Domain, Codomain, and Range

### Domain

The set of all possible inputs.

* **Example:** $f(x) = \frac{1}{x}$
* Domain is **NOT** all real numbers. Why? $x = 0$ causes division by zero.
* Therefore: Domain is $\mathbb{R} \setminus \{0\}$.

### Codomain

The set where outputs are *allowed* to live.

* **Example:** $f:\mathbb{R}\rightarrow\mathbb{R}$ where $f(x) = x^2$
* Codomain: $\mathbb{R}$

### Range

The *actual* outputs produced.

* For $f(x) = x^2$, outputs are 0, 1, 4, 9, ... and all nonnegative reals.
* Thus: $\text{Range}(f) = \{y \in \mathbb{R} \mid y \ge 0\}$

**Notice:** Range $\neq$ Codomain in general.

* Codomain: $\mathbb{R}$
* Range: $[0, \infty)$
* They are different! ⚠️

---

## 🧮 Evaluating Functions

Given: $f(x) = x^2 + 3x + 1$
**Find $f(2)$:**


$$2^2 + 3(2) + 1 = 4 + 6 + 1 = 11$$

**Find $f(-1)$:**


$$(-1)^2 + 3(-1) + 1 = 1 - 3 + 1 = -1$$

---

## 🚫 When Is Something NOT a Function?

A function must satisfy two rules:

1. **Rule 1:** Every input must have an output.
2. **Rule 2:** Every input must have *exactly one* output.

**Not a Function Example 1:**

* 1 $\rightarrow$ a
* 1 $\rightarrow$ b
*(Input 1 has two outputs. Not a function.)* ❌

**Not a Function Example 2:** Let Domain = $\{1, 2, 3\}$

* 1 $\rightarrow$ a
* 2 $\rightarrow$ b
*(Input 3 has no output. Not a function.)* ❌

---

## 📏 Floor and Ceiling Functions

One of Rosen's favorite examples.

### Floor Function

**Notation:** $\lfloor x \rfloor$
**Meaning:** Largest integer less than or equal to $x$.

* $\lfloor 3.7 \rfloor = 3$
* $\lfloor 5 \rfloor = 5$
* $\lfloor -2.3 \rfloor = -3$ *(Notice: Not -2. Must be less than or equal!)*

### Ceiling Function

**Notation:** $\lceil x \rceil$
**Meaning:** Smallest integer greater than or equal to $x$.

* $\lceil 3.2 \rceil = 4$
* $\lceil 5 \rceil = 5$
* $\lceil -2.3 \rceil = -2$

---

## 🎯 Function Properties

### 1. One-to-One Functions (Injective)

Very important.
**Definition:** A function is one-to-one if different inputs produce different outputs.
**Formally:** $f(a) = f(b)$ implies $a = b$.

* **Injective Example:** $f(x) = 2x + 1$
Suppose $f(a) = f(b)$. Then $2a + 1 = 2b + 1 \Rightarrow 2a = 2b \Rightarrow a = b$. Thus injective. ✅
* **Non-Injective Example:** $f(x) = x^2$ over real numbers.
Because $f(2) = 4$ and $f(-2) = 4$. Different inputs, same output. Not injective. ❌

**Why Injective Matters in Cryptography:**
Suppose: Message A $\rightarrow$ Ciphertext X, and Message B $\rightarrow$ Ciphertext X.
The receiver cannot know which message was sent! Many cryptographic constructions require injectivity. 🔐

### 2. Onto Functions (Surjective)

**Definition:** Every element of the codomain is hit by some input.
**Formally:** For every $y \in B$, there exists $x \in A$ such that $f(x) = y$.

* **Surjective Example:** $f(x) = x^3$ over $\mathbb{R}$. Every real number has a cube root. ✅
* **Non-Surjective Example:** $f(x) = x^2$ over $\mathbb{R}$. Negative values never appear. ❌

### 3. Bijective Functions

A function that is **both injective and surjective** is called bijective.

* **Example:** $f(x) = x + 1$ over real numbers.
* **Why Bijections Matter:** A bijection creates a perfect pairing. Every input $\leftrightarrow$ exactly one output. This is *exactly* what encryption/decryption needs. 🤝

---

*To truly grasp injectivity and surjectivity, interact with the graphs below. Try to find horizontal lines that hit the curve more than once (failing injectivity) or gaps in the y-axis (failing surjectivity).*

---

## 🔄 Inverse Functions

Suppose $f:A\rightarrow B$ is bijective. Then an inverse exists.
**Notation:** $f^{-1}$
**Definition:** 

$$f^{-1}(f(x)) = x$$

**Example:** $f(x) = x + 5$

* To reverse: $y = x + 5 \Rightarrow x = y - 5$
* Therefore: $f^{-1}(x) = x - 5$
* Check: $f^{-1}(f(10)) = f^{-1}(15) = 10$. Correct! ✅

**Example from Cryptography:**

* Encryption: $E_k(m)$
* Decryption: $D_k(c)$
* Requirement: $D_k(E_k(m)) = m$
* This means: $D_k = E_k^{-1}$. Decryption is the inverse function! 🔓

---

## 🔗 Function Composition

Apply one function after another.
**Notation:** 

$$(f \circ g)(x) = f(g(x))$$

**Example:** $f(x) = x + 1$ and $g(x) = 2x$
Find $(f \circ g)(x)$:

1. First: $g(x) = 2x$
2. Then: $f(g(x)) = f(2x) = 2x + 1$
3. Thus: $(f \circ g)(x) = 2x + 1$

**Composition Is NOT Commutative:**
Generally, $f \circ g \neq g \circ f$.

* Using the example above: $g(f(x)) = 2(x + 1) = 2x + 2$. Different! ⚠️

**Why Cryptographers Care:**
Modern encryption often looks like:


$$f_n \circ f_{n-1} \circ \cdots \circ f_1$$


AES is essentially multiple rounds of composed functions. 🛡️

---

## ✅ Summary

You should know:

* **Function:** $f:A\rightarrow B$
* **Domain:** Possible inputs.
* **Codomain:** Allowed outputs.
* **Range:** Actual outputs.
* **Injective:** Different inputs $\rightarrow$ different outputs.
* **Surjective:** Every output reached.
* **Bijective:** Injective + Surjective.
* **Inverse:** $f^{-1}$ reverses $f$.
* **Composition:** $f \circ g$ (Apply $g$ first, then $f$).

---

## ✍️ Exercises

### Easy

1. Let $f(x) = 3x + 2$. Find $f(5)$.
2. Compute $\lfloor 4.7 \rfloor$.
3. Compute $\lceil -3.4 \rceil$.

### Medium

4. Determine whether $f(x) = 2x + 1$ is injective.
5. Determine whether $f(x) = x^2$ over real numbers is injective.
6. Determine whether $f(x) = x^3$ is surjective over real numbers.

### Hard

7. Find the inverse of $f(x) = 5x - 7$.
8. Compute $(f \circ g)(x)$ if $f(x) = x^2$ and $g(x) = x + 1$.
9. Show that if $f$ and $g$ are bijections, then $f \circ g$ is a bijection.
10. Explain why decryption must be the inverse of encryption in a symmetric cipher.

*Next we'll study **Section 2.4 — Sequences and Summations**, which introduces mathematical notation heavily used in algorithm analysis, probability theory, and cryptographic security proofs.* 🚀



# 📖 Chapter 2.4 — Sequences and Summations

This section is extremely important because it forms the mathematical foundation for:
* Algorithm Analysis ⏱️
* Probability Theory 🎲
* Information Theory 📡
* Complexity Theory 🧩
* Cryptography 🔐

When you later read cryptography papers, you'll constantly see expressions like:
$$\sum_{i=1}^{n} a_i$$
and sequences such as:
$2^n, \quad n^2, \quad \log n$

This chapter teaches that language. 🗣️

---

## 🔢 1. What is a Sequence?

A sequence is an **ordered list** of elements.
Unlike sets (e.g., $\{1, 2, 3\}$ where order doesn't matter), for sequences, $1, 2, 3$ is different from $3, 2, 1$.

### 📝 Examples
* Sequence of positive integers: $1, 2, 3, 4, 5, \dots$
* Sequence of odd numbers: $1, 3, 5, 7, 9, \dots$
* Sequence of powers of two: $1, 2, 4, 8, 16, 32, \dots$ *(This one appears everywhere in cryptography!)*

---

## 🏷️ Sequence Notation

A sequence is often written:
$$a_1, a_2, a_3, \dots, a_n$$
where $a_i$ is called the $i$-th term.

**Example:**
$2, 4, 6, 8, 10, \dots$ can be written as:
$$a_n = 2n$$
*Check:*
* $a_1 = 2(1) = 2$
* $a_2 = 2(2) = 4$
* $a_3 = 2(3) = 6$
Correct! ✅

### Explicit Formula
An explicit formula gives the $n$-th term directly.
**Example:** $$a_n = 3n + 1$$
* $a_1 = 4$
* $a_2 = 7$
* $a_3 = 10$

---

## 📈 Types of Sequences

### 1. Geometric Sequences
A geometric sequence multiplies by the same ratio each step.
**Example:** $1, 2, 4, 8, 16, \dots$
* Ratio: $r = 2$

**General formula:**
$$a_n = a_1 r^{n-1}$$

**Example:**
$a_1 = 3, \quad r = 2$
Then:
$$a_n = 3 \cdot 2^{n-1}$$
*Check:* $a_4 = 3 \cdot 2^3 = 24$. Correct! ✅

### 2. Arithmetic Sequences
Each term differs by a constant amount.
**Example:** $3, 7, 11, 15, 19, \dots$
* Difference: $d = 4$

**Formula:**
$$a_n = a_1 + (n-1)d$$

**Example:**
$a_1 = 3, \quad d = 4$
Then:
$$a_n = 3 + 4(n-1)$$

---

## 🔄 Recursive Definitions

Sometimes we define a sequence using previous terms.
**Example:**
* $a_1 = 1$
* $a_n = a_{n-1} + 2$

Compute:
* $a_2 = 1 + 2 = 3$
* $a_3 = 3 + 2 = 5$
* $a_4 = 5 + 2 = 7$
Thus: $1, 3, 5, 7, \dots$

### 🌀 Fibonacci Sequence
One of the most famous recursive sequences.
**Definition:**
* $F_0 = 0$
* $F_1 = 1$
* $F_n = F_{n-1} + F_{n-2}$ for $n \ge 2$

First terms: $0, 1, 1, 2, 3, 5, 8, 13, 21, \dots$
This sequence appears in Mathematics, Algorithms, Number Theory, and Cryptography. 🌿

---

## ➕ Summation Notation

Instead of writing $1 + 2 + 3 + 4 + 5$, we use:
$$\sum_{i=1}^{5} i$$
Read: *Sum $i$ from 1 to 5.*
Meaning: $1 + 2 + 3 + 4 + 5 = 15$

### 🧩 Components of Sigma Notation
$$\sum_{i=1}^{5} i$$
* $i$ = index
* $1$ = starting value
* $5$ = ending value
* $i$ = expression being summed

**Example 1:** Compute $\sum_{i=1}^{4} i$
Expand: $1 + 2 + 3 + 4 = 10$

**Example 2:** Compute $\sum_{i=1}^{4} i^2$
Expand: $1^2 + 2^2 + 3^2 + 4^2 = 1 + 4 + 9 + 16 = 30$

---

## 📜 Important Summation Formulas
*You must memorize these.* 🧠

### Formula 1: First $n$ integers
$$\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$
**Example:** $1 + 2 + \dots + 100$
$$= \frac{100(101)}{2} = 5050$$

### Formula 2: Squares
$$\sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6}$$
**Example:** For $n = 3$
$1 + 4 + 9 = 14$
Formula gives: $\frac{3 \cdot 4 \cdot 7}{6} = \frac{84}{6} = 14$. Correct! ✅

### Formula 3: Cubes
$$\sum_{i=1}^{n} i^3 = \left(\frac{n(n+1)}{2}\right)^2$$
**Example:** For $n = 3$
$1 + 8 + 27 = 36$
Formula: $\left(\frac{3 \cdot 4}{2}\right)^2 = 6^2 = 36$. Correct! ✅

---

## 📏 Linearity of Summation
Very important.

**Rule 1:**
$$\sum (a_i + b_i) = \sum a_i + \sum b_i$$

**Rule 2:**
$$\sum c \cdot a_i = c \sum a_i$$
(where $c$ is a constant).

**Example:**
Compute: $\sum_{i=1}^{4}(2i + 1)$
Expand manually: $3 + 5 + 7 + 9 = 24$
Using linearity:
$$2 \sum_{i=1}^{4} i + \sum_{i=1}^{4} 1$$
$$= 2(10) + 4 = 24$$

---

## 🔣 Double Summations
**Example:**
$$\sum_{i=1}^{2}\sum_{j=1}^{3} 1$$
* Inner sum: $1 + 1 + 1 = 3$
* Outer sum: $3 + 3 = 6$
Answer: $6$

---

## 🕵️‍♂️ Why Cryptographers Care

Suppose an attacker succeeds with probability $\frac{1}{2^n}$ over all keys.
Total probability calculations often involve $\sum$ expressions. Security proofs are full of summations.

**Example from Complexity Theory:**
Suppose an algorithm performs $1 + 2 + 3 + \dots + n$ operations.
Using the formula $\frac{n(n+1)}{2}$, this is approximately $\frac{1}{2}n^2$, which leads to **$O(n^2)$** running time. ⏱️

---

To help visualize how different sequences and their partial sums grow, explore this interactive tool:



---

## ✅ Summary

You should know:

* **Arithmetic Sequence:** $a_n = a_1 + (n-1)d$
* **Geometric Sequence:** $a_n = a_1 r^{n-1}$
* **Recursive Sequence:** Defined using previous terms.
* **Fibonacci Sequence:** $F_n = F_{n-1} + F_{n-2}$
* **Summation Notation:** $\sum$

**Essential Formulas:**

* $\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$
* $\sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6}$
* $\sum_{i=1}^{n} i^3 = \left(\frac{n(n+1)}{2}\right)^2$

---

## ✍️ Exercises

### Basic

1. Find the 10th term of: $3, 7, 11, 15, \dots$
2. Find the 8th term of: $2, 6, 18, 54, \dots$
3. Compute: $\sum_{i=1}^{5} i$

### Medium

4. Compute: $\sum_{i=1}^{10} i$
5. Compute: $\sum_{i=1}^{5} i^2$
6. Compute: $\sum_{i=1}^{4}(3i + 2)$

### Hard

7. Prove: $1 + 3 + 5 + \dots + (2n - 1) = n^2$
8. Find a closed form for: $5 + 10 + 15 + \dots + 5n$
9. Compute: $\sum_{i=1}^{100}(2i - 1)$
10. Explain why $\sum_{i=1}^{n} i$ grows on the order of $O(n^2)$.

*Next comes **Section 2.5 — Cardinality of Sets**, where Rosen develops finite and infinite sets, countable vs uncountable infinity, and Cantor's theorem. This is one of the deepest and most beautiful chapters in discrete mathematics and has surprising connections to cryptography and theoretical computer science.* 🚀



# ♾️ Chapter 2.5 — Cardinality of Sets

This is one of the most profound sections in discrete mathematics.
Until now, cardinality simply meant:
> *The number of elements in a set.*

For example:
$A = \{1, 2, 3, 4\}$
has cardinality
$|A| = 4$
Easy. 

But what about:
$\mathbb{N} = \{0, 1, 2, 3, \dots\}$
How many elements does it have? **Infinite.**

Can different infinite sets have different sizes?
Surprisingly: **Yes.** 🤯
This discovery by Georg Cantor completely changed mathematics.

---

## 📏 1. Cardinality Revisited

For finite sets:
$|A|$ means the number of elements.
*Example:*
$A = \{a, b, c, d\}$
Then:
$|A| = 4$

For infinite sets we need a more sophisticated definition.

### ⚖️ Comparing Sizes of Sets
Suppose:
$A = \{1, 2, 3\}$
$B = \{a, b, c\}$

How do we know they have the same size?
Match elements:
* 1 ↔ a
* 2 ↔ b
* 3 ↔ c

Every element gets exactly one partner. No leftovers.
This idea is called a **bijection**. 🤝

### 📖 Definition
Sets $A$ and $B$ have the same cardinality if there exists a bijection:
$$f: A \to B$$
between them.

**Notation:**
$|A| = |B|$

### 📝 Example
$A = \{1, 2, 3\}$
$B = \{x, y, z\}$

Define:
* 1 → x
* 2 → y
* 3 → z

Bijection exists.
Therefore:
$|A| = |B|$

---

## 🌌 Infinite Sets

Now consider:
$\mathbb{N} = \{0, 1, 2, 3, \dots\}$
This set is infinite. Can a proper subset have the same size?

* For finite sets: Subset → smaller (always).
* For infinite sets: Subset → maybe same size. (Surprisingly!)

### 📝 Example
Consider even numbers:
$E = \{0, 2, 4, 6, 8, \dots\}$
Clearly:
$E \subset \mathbb{N}$
Looks smaller. But define:
$$f(n) = 2n$$

Then:
* 0 ↔ 0
* 1 ↔ 2
* 2 ↔ 4
* 3 ↔ 6

Every natural number matches exactly one even number. Bijection exists.
Therefore:
$$|E| = |\mathbb{N}|$$
Amazing. A proper subset has the same size. ✨

---

## 🔢 Countably Infinite Sets

A set is countably infinite if it has the same cardinality as $\mathbb{N}$.

**Definition:**
A set $A$ is countable if:
$|A| = |\mathbb{N}|$

### 📝 Examples:
* **Natural Numbers** ($\mathbb{N}$): Countable.
* **Even Numbers** ($\{0, 2, 4, 6, \dots\}$): Countable.
* **Odd Numbers** ($\{1, 3, 5, 7, \dots\}$): Countable.
* **Multiples of 100** ($\{100, 200, 300, \dots\}$): Countable.

### 🧮 Integers Are Countable
At first glance:
$\mathbb{Z} = \{\dots, -2, -1, 0, 1, 2, \dots\}$
seems larger than $\mathbb{N}$.

But we can list integers:
* 0
* 1
* -1
* 2
* -2
* 3
* -3
* ...

This creates a bijection.
Therefore:
$|\mathbb{Z}| = |\mathbb{N}|$
Integers are countable. ✅

### 🍕 Rational Numbers Are Countable
This is one of Cantor's most surprising discoveries.
Rationals:
$$\mathbb{Q} = \left\{\frac{a}{b} \mid a, b \in \mathbb{Z}, b \neq 0\right\}$$
There seem to be vastly more rationals.
Yet Cantor proved:
$|\mathbb{Q}| = |\mathbb{N}|$
Countable. The proof uses a clever diagonal traversal of fractions arranged in a grid.

---

## 🚫 Uncountable Sets

Not every infinite set is countable. Some infinities are larger.

### 📉 Real Numbers
Consider: $\mathbb{R}$
Can we list all real numbers?
Cantor proved: **No.**
No matter how you try to list them, some real number will always be missing.
Therefore:
$|\mathbb{R}| > |\mathbb{N}|$
Real numbers are uncountable.

### 📐 Cantor's Diagonal Argument
One of the greatest proofs in mathematics.
Suppose all real numbers in $(0, 1)$ could be listed:
* $0.12345\dots$
* $0.87654\dots$
* $0.11111\dots$
* ...

Construct a new number. Change:
* first digit of first number
* second digit of second number
* third digit of third number
* and so on.

The new number differs from every listed number.
Therefore it is not in the list. Contradiction.
Hence: $(0, 1)$ cannot be countable. 💥

### 💡 Important Consequence
$|\mathbb{R}| > |\mathbb{N}|$
There are strictly more real numbers than natural numbers.

---

## 📦 Power Sets

Recall:
$\mathcal{P}(A)$ means: All subsets of $A$.

### 🎲 Finite Example
If $|A| = 3$, then:
$|\mathcal{P}(A)| = 2^3 = 8$

Example: $A = \{1, 2, 3\}$
Power set contains 8 subsets.

### 🏆 Cantor's Theorem
One of the deepest theorems in mathematics.
For every set $A$:
$$|\mathcal{P}(A)| > |A|$$
Always.

For finite sets: $2^n > n$, which is obvious.
The amazing part: **It remains true even for infinite sets.**

**Example:**
$|\mathcal{P}(\mathbb{N})| > |\mathbb{N}|$
Thus: $\mathcal{P}(\mathbb{N})$ is uncountable.

---

## 🔐 Why Cryptographers Care

Suppose:
* Key length: $n$
* Possible keys: $\{0, 1\}^n$
* Number of keys: $2^n$

This is cardinality.

**Example: AES-128**
Key space: $2^{128}$ possible keys.

Security often depends on the attacker searching through a huge set.
Understanding cardinality tells us: How many possibilities exist? 🕵️‍♂️

---

## 📊 Finite vs Infinite

| Set | Cardinality |
| :--- | :--- |
| $\{1, 2, 3\}$ | $3$ |
| $\mathbb{N}$ | Countably infinite |
| $\mathbb{Z}$ | Countably infinite |
| $\mathbb{Q}$ | Countably infinite |
| $\mathbb{R}$ | Uncountable |
| $\mathcal{P}(\mathbb{N})$ | Uncountable |

---

## 🧠 Important Facts to Memorize

**Countable:**
* $\mathbb{N}$
* $\mathbb{Z}$
* $\mathbb{Q}$

**Uncountable:**
* $\mathbb{R}$
* $(0, 1)$
* $\mathcal{P}(\mathbb{N})$

**Cantor's Theorem:**
$|\mathcal{P}(A)| > |A|$

**Power Set Formula:**
For finite sets:
$|\mathcal{P}(A)| = 2^{|A|}$

---

## ✍️ Exercises

### Medium
1. Show that: $|\{2, 4, 6, 8, \dots\}| = |\mathbb{N}|$
2. Explain why $\mathbb{Z}$ is countable.
3. Find: $|\mathcal{P}(\{a, b, c, d\})|$

### Hard
4. Explain why $\mathbb{Q}$ is countable even though it seems larger than $\mathbb{N}$.
5. State Cantor's theorem.
6. Explain the basic idea behind Cantor's diagonal argument.
7. Why does $|\mathcal{P}(\mathbb{N})| > |\mathbb{N}|$ imply multiple sizes of infinity exist?

*Next we'll study **Section 2.6 — Matrices**, where Rosen introduces matrix operations, Boolean matrices, and applications to graphs and relations. These ideas later connect to coding theory, cryptanalysis, and advanced discrete structures.* 🚀



# 🧮 Chapter 2.6 — Matrices

This is the last major section of Chapter 2.
At first, matrices may seem unrelated to cryptography, but they appear in:
* Error-Correcting Codes 🛡️
* Coding Theory 💻
* Lattice-Based Cryptography 🕸️
* Graph Algorithms 🛤️
* Network Analysis 🌐
* Hill Cipher (classical cryptography) 🔐
* Boolean Relations 🔗

Rosen focuses on matrices as discrete structures rather than advanced linear algebra.

---

## 🧱 1. What is a Matrix?

A matrix is a rectangular arrangement of numbers.

**Example:**
$$A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$$

* **Rows:** `1 2` and `3 4`
* **Columns:** `1 3` and `2 4`

### 📏 Matrix Dimensions
If a matrix has $m$ rows and $n$ columns, it is called an $m \times n$ matrix.

**Example:**
$$\begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}$$
has 2 rows and 3 columns.
Therefore, it is a $2 \times 3$ matrix.

### 📍 Matrix Entries
The entry in row $i$ and column $j$ is denoted as $a_{ij}$.

**Example:**
$$A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$$
Then:
* $a_{11} = 1$
* $a_{12} = 2$
* $a_{21} = 3$
* $a_{22} = 4$

---

## ⚖️ Equality of Matrices

Two matrices are equal **iff** (if and only if):
1. They have the same dimensions.
2. Corresponding entries are equal.

**Example (Equal):**
$$\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$$

**Example (Not Equal):**
$$\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} \neq \begin{bmatrix} 1 & 2 \\ 4 & 3 \end{bmatrix}$$

---

## ➕ Matrix Addition

Matrices must have the **same size**. Add corresponding entries.

**Example:**
$$A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}, \quad B = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}$$
Then:
$$A + B = \begin{bmatrix} 6 & 8 \\ 10 & 12 \end{bmatrix}$$

---

## ✖️ Scalar Multiplication

Multiply every entry by the scalar.

**Example:**
$$2 \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} = \begin{bmatrix} 2 & 4 \\ 6 & 8 \end{bmatrix}$$

---

## 💥 Matrix Multiplication

This is the most important operation.

### 🚦 Condition
If $A$ is $m \times n$ and $B$ is $n \times p$, then $AB$ exists and is an $m \times p$ matrix.

**Example:**
$$A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}, \quad B = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}$$

Compute $AB$:
* First entry (Row 1 $\times$ Col 1): $1\cdot5 + 2\cdot7 = 19$
* Second entry (Row 1 $\times$ Col 2): $1\cdot6 + 2\cdot8 = 22$
* Third entry (Row 2 $\times$ Col 1): $3\cdot5 + 4\cdot7 = 43$
* Fourth entry (Row 2 $\times$ Col 2): $3\cdot6 + 4\cdot8 = 50$

Result:
$$AB = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}$$

### ⚠️ Important Fact
Matrix multiplication is **NOT** commutative.
Generally:
$$AB \neq BA$$

**Example:** Using the same matrices:
$$AB = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}$$
while
$$BA = \begin{bmatrix} 23 & 34 \\ 31 & 46 \end{bmatrix}$$
Different!
*Memorize:* $AB \neq BA$ in general. 🧠

---

## 🪞 Identity Matrix

Analogous to the number 1.
**Notation:** $I_n$

**Example:**
$$I_2 = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$$

**Property:** $AI = A$ and $IA = A$

**Example:**
$$\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} I_2 = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$$

---

## 🔄 Transpose

Transpose swaps rows and columns.
**Notation:** $A^T$

**Example:**
$$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}$$
Then:
$$A^T = \begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}$$

---

## 🤖 Boolean Matrices

Very important in discrete mathematics. Entries are only **0** and **1**.

**Example:**
$$\begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 0 \end{bmatrix}$$

Boolean matrices represent:
* Graphs 📈
* Relations 🔗
* Networks 🌐

### 🔣 Boolean Operations
Replace ordinary arithmetic by logic.
* Addition becomes: $1 + 1 = 1$ (**OR** $\vee$)
* Multiplication becomes: $1 \cdot 1 = 1$ (**AND** $\wedge$)

**Truth table (OR):**
| $x$ | $y$ | $x \vee y$ |
| :---: | :---: | :---: |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

### ✖️ Boolean Matrix Product
Suppose:
$$A = \begin{bmatrix} 1 & 0 \\ 1 & 1 \end{bmatrix}, \quad B = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$$

* Entry (1,1): $(1 \wedge 1) \vee (0 \wedge 0) = 1$
* Entry (1,2): $(1 \wedge 1) \vee (0 \wedge 1) = 1$
* Entry (2,1): $(1 \wedge 1) \vee (1 \wedge 0) = 1$
* Entry (2,2): $(1 \wedge 1) \vee (1 \wedge 1) = 1$

Result:
$$AB = \begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix}$$

---

## 🕸️ Applications to Graphs

Suppose we have the following paths:
* A → B
* A → C
* B → C

**Adjacency matrix:**
$$M = \begin{bmatrix} 0 & 1 & 1 \\ 0 & 0 & 1 \\ 0 & 0 & 0 \end{bmatrix}$$
* **Rows:** Source node.
* **Columns:** Destination node.

Boolean matrix powers help count paths. This becomes important in graph theory. 🛤️

---

## 🔐 Why Cryptographers Care

**Hill Cipher:**
Classical encryption: $C = KM$
where $K$ = key matrix, $M$ = message vector.

**Coding Theory:**
Parity-check matrices, Generator matrices, Error correction. 🛡️

**Lattice Cryptography:**
Modern post-quantum cryptography uses huge matrices. Schemes like *Learning With Errors (LWE)* and *Ring-LWE* are fundamentally matrix-based. ⚛️

---

## 📌 Important Properties

* **Associative:** $(AB)C = A(BC)$
* **Distributive:** $A(B+C) = AB+AC$ and $(A+B)C = AC+BC$
* **Not Commutative:** $AB \neq BA$ ⚠️

---

## ✅ Summary

You should know:
* **Matrix:** $m \times n$ rectangular array.
* **Matrix Addition:** Add corresponding entries.
* **Scalar Multiplication:** Multiply every entry.
* **Matrix Multiplication:** Row $\times$ Column rule.
* **Identity Matrix:** $I_n$ acts like 1.
* **Transpose:** $A^T$ swap rows and columns.
* **Boolean Matrix:** Uses **OR** and **AND** instead of $+$ and $\times$.
* **Key Fact:** $AB \neq BA$ generally.

---

## ✍️ Exercises

### Medium
1. Add:
   $$\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} + \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}$$
2. Compute:
   $$3 \begin{bmatrix} 2 & 1 \\ 4 & 5 \end{bmatrix}$$
3. Find $A^T$ for:
   $$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}$$

### Hard
4. Multiply:
   $$\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} \begin{bmatrix} 2 & 0 \\ 1 & 5 \end{bmatrix}$$
5. Verify $AI = A$ for:
   $$A = \begin{bmatrix} 2 & 3 \\ 4 & 5 \end{bmatrix}$$
6. Explain why matrix multiplication is not commutative.

*At this point you've completed the core of Chapter 2. The next major chapter in Rosen is typically **Algorithms and the Growth of Functions**, which becomes essential for complexity theory, cryptography, and understanding why algorithms like RSA key generation are efficient while brute-force attacks are infeasible.* 🚀