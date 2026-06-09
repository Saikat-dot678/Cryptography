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
