# ⚙️ Chapter 3 — Algorithms

This chapter is one of the most important chapters for:
* Cryptography 🔐
* Competitive Programming 💻
* Complexity Theory 🧩
* Software Engineering 🛠️
* Computer Science Research 🔬

Before cryptography asks: *"Is RSA secure?"*
it first asks: *"How efficiently can we compute RSA operations?"*
That is an algorithm question.

---

## 🧭 3.1 What Is an Algorithm?

An algorithm is:
> **A finite sequence of precise instructions that solves a problem.**

An algorithm must possess these properties:
* **Input:** Accept zero or more inputs.
* **Output:** Produce at least one output.
* **Definiteness:** Every step must be unambiguous.
* **Finiteness:** Must terminate after finitely many steps.
* **Effectiveness:** Each step must be executable.

### 📝 Example: Find Maximum
**Input:** `5, 8, 2, 10, 3`

**Algorithm:**
```text
max = first element
for every remaining element:
    if element > max
        max = element
return max

```

**Output:** `10`

### 🔐 Why Cryptographers Care

* RSA encryption ($c = m^e \bmod n$) is an algorithm.
* RSA decryption ($m = c^d \bmod n$) is an algorithm.
* AES rounds are algorithms.
* SHA-256 is an algorithm.

Security proofs often compare algorithms!

---

## 📝 Pseudocode

Instead of programming language syntax, mathematicians use pseudocode.

**Example: Sum(n)**

```pascal
Algorithm Sum(n)
    sum := 0
    for i := 1 to n
        sum := sum + i
    return sum

```

**Example: Linear Search**
Problem: Find `x` in a list `A`.

```pascal
Algorithm LinearSearch(A, x)
    for i := 1 to n
        if A[i] = x
            return i
    return NOT FOUND

```

**Trace:**
Array: `[4, 7, 2, 9, 1]` | Search: `9`
Check: `4` ❌, `7` ❌, `2` ❌, `9` ✅
Found at position: `4`

---

## ✅ Correctness of Algorithms

An algorithm is useful only if it is correct. We must prove:

> *It always produces the correct answer.*

**Example: Maximum Algorithm**

* **Claim:** After processing all elements, `max` contains the largest value.
* **Proof idea:** At every step, `max` stores the largest value seen *so far*. By the end, *all* values have been seen. Therefore, `max` is the largest element overall. ∎

---

## ➗ Integer Division

Very important in cryptography.

Given integers $a$ and $d > 0$, there exist unique integers $q$ (quotient) and $r$ (remainder) such that:


$$a = dq + r$$


with


$$0 \le r < d$$

**Example:** $23 \div 5$
gives $q=4$ and $r=3$, because:


$$23 = 5 \times 4 + 3$$

This is the foundation of modular arithmetic. 🧱

---

## 🏛️ Euclidean Algorithm

One of the most important algorithms in mathematics.
Used in: RSA, Diffie-Hellman, ECC, Modular inverses.

**Problem:** Compute $\gcd(a,b)$

* **Naive approach:** Check all divisors. (Slow 🐢)
* **Euclidean Algorithm:**
If $a > b$, then:

$$\gcd(a,b) = \gcd(b, a \bmod b)$$



Repeat until remainder becomes 0.

### 📝 Example: Find $\gcd(252, 105)$

* **Step 1:** $252 = 105 \times 2 + 42$
* **Step 2:** $105 = 42 \times 2 + 21$
* **Step 3:** $42 = 21 \times 2 + 0$
Stop. Answer: **21**

### 💻 Pseudocode

```pascal
Algorithm Euclid(a, b)
    while b ≠ 0
        r := a mod b
        a := b
        b := r
    return a

```

### 🔐 Why RSA Depends on This

RSA key generation requires $\gcd(e, \phi(n))$ to be $1$. The Euclidean Algorithm checks this efficiently. Without it, RSA becomes impractical.

---

## 🔍 Binary Search

A classic algorithm.
**Requirement:** Array must be sorted.

**Example:** `[1, 3, 5, 7, 9, 11, 13]`, Search: `9`

1. Check middle: `7`. Target is larger. Discard left half.
2. Remaining: `[9, 11, 13]`. Middle: `11`. Target is smaller. Discard right half.
3. Remaining: `[9]`. Found. ✅

### 🚀 Why Binary Search Is Amazing

* **Linear Search:** $1, 2, 3, \dots, n$ (May examine every element).
* **Binary Search:** Cuts problem in half each step. For 1,000,000 elements, only about 20 checks needed!

This idea leads directly to complexity theory.

---

## 🔄 Recursive Algorithms

An algorithm can call itself.

### 📝 Example: Factorial

Definition: $n! = n(n-1)!$

```pascal
Algorithm Factorial(n)
    if n = 0 return 1
    return n * Factorial(n - 1)

```

**Trace:**
`Factorial(4)` becomes:
$4 \times \text{Factorial}(3)$
$4 \times 3 \times \text{Factorial}(2)$
$4 \times 3 \times 2 \times \text{Factorial}(1)$
$4 \times 3 \times 2 \times 1 = \mathbf{24}$

### 🌀 Recursive Fibonacci

Definition: $F_n = F_{n-1} + F_{n-2}$

```pascal
Algorithm Fib(n)
    if n = 0 return 0
    if n = 1 return 1
    return Fib(n-1) + Fib(n-2)

```

Works correctly, but inefficient. This motivates algorithm analysis. 📈

---

## ⏱️ Algorithm Efficiency

Two algorithms may solve the same problem. One may take 1 second; another, 100 years. We need a way to compare them.
This leads to:

* **Time Complexity:** How many operations?
* **Space Complexity:** How much memory?

### 📈 Growth Rate Intuition

Suppose:

* Algorithm A: $n$ operations
* Algorithm B: $n^2$ operations

For $n=10$: A takes 10, B takes 100.
For $n=1,000,000$: A takes 1,000,000, B takes 1,000,000,000,000. Huge difference. 🤯

### 🔐 Why Cryptographers Care

Cryptography is fundamentally about:

* **Efficient algorithms for legitimate users** (e.g., fast decryption, encryption).
* **Infeasible algorithms for attackers** (e.g., slow brute force, factoring).

Security often boils down to:
*Good guys have a fast algorithm. Bad guys only have a slow algorithm.*

---

## ✅ Summary

You should understand:

* **Algorithm:** Finite sequence of instructions.
* **Pseudocode:** Language-independent description.
* **Correctness:** Algorithm must always produce right answer.
* **Euclidean Algorithm:** Efficient gcd computation.
* **Binary Search:** Divide-and-conquer searching.
* **Recursion:** Algorithm calling itself.
* **Efficiency:** Measure resource usage.

---

## ✍️ Exercises

### Medium

1. Use Euclidean Algorithm to compute $\gcd(84, 30)$.
2. Use Euclidean Algorithm to compute $\gcd(119, 34)$.
3. Write pseudocode for finding the minimum element in a list.
4. Perform Binary Search for `15` in: `[3, 5, 7, 9, 11, 13, 15, 17]`.

### Hard

5. Prove: $\gcd(a, b) = \gcd(b, a \bmod b)$.
6. Trace the recursive calls for: `Factorial(5)`.
7. Explain why Binary Search requires a sorted list.
8. Explain why Euclid's Algorithm is dramatically faster than checking every divisor.

*Next comes **Chapter 3.2 — The Growth of Functions**, where Rosen introduces Big-O, Big-$\Omega$, and Big-$\Theta$ notation. This chapter is absolutely essential for cryptography because security is based on computational complexity. Understanding why $2^{128}$ is secure and why $n^3$ is practical starts there.* 🚀




# 📈 Chapter 3.2 — The Growth of Functions

This is one of the most important chapters for:
* Cryptography 🔐
* Algorithms ⚙️
* Competitive Programming 💻
* Complexity Theory 🧩
* Machine Learning 🤖

Modern cryptography is built on one idea:
> **Legitimate users should run fast algorithms.**
> **Attackers should face astronomically slow algorithms.**

To understand that, we need to study how functions grow.

---

## 🤔 Why Growth Matters

Suppose two algorithms solve the same problem.
* Algorithm A: $$T(n)=n$$
* Algorithm B: $$T(n)=n^2$$

For $n=10$:
* A: 10 operations.
* B: 100 operations.
*(Not terrible.)*

For $n=1,000,000$:
* A: 1,000,000 operations.
* B: 1,000,000,000,000 operations.
*(Huge difference! 🤯)*

**Therefore:** The growth rate matters more than the exact running time.

---

## ✂️ Ignoring Constants

Suppose $T_1(n)=100n$ and $T_2(n)=n$.
Both grow linearly. The constant 100 matters little for very large $n$. We care about the *shape*.

Example: $100n$ and $n$ belong to the same growth class.

---

## ⭕ Big-O Notation

Most important notation in algorithm analysis.

### 📖 Definition
We say $f(n)=O(g(n))$ if there exist constants $C>0$ and $k$ such that:
$$|f(n)| \le C|g(n)|$$
for all $n>k$.

**Intuition:** Big-O gives an **upper bound**.
Meaning: $f(n)$ grows no faster than $g(n)$ up to constant factors. 🛑

### 📝 Example 1
$3n+5$
Claim: $3n+5=O(n)$
For $n\ge5$:
$$3n+5 \le 4n$$
Choose $C=4$.
Therefore: $3n+5=O(n)$ ✅

### 📝 Example 2
$7n^2+10n+100$
Claim: $O(n^2)$
For large $n$: $10n<n^2$ and $100<n^2$.
Thus:
$$7n^2+10n+100 < 9n^2$$
for sufficiently large $n$.
Hence: $O(n^2)$ ✅

---

## 📏 Rule of Thumb

For polynomials: **Keep only the highest-degree term.**
* **Example:** $5n^3+100n^2+7n+1 \rightarrow O(n^3)$
* **Example:** $n^5+n^2+100 \rightarrow O(n^5)$

---

## 📊 Common Growth Rates

From fastest to slowest growth:
1. $1$ (Constant)
2. $\log n$ (Logarithmic)
3. $n$ (Linear)
4. $n\log n$ (Log-linear)
5. $n^2$ (Quadratic)
6. $n^3$ (Cubic)
7. $2^n$ (Exponential)
8. $3^n$ (Exponential)
9. $n!$ (Factorial)

*Memorize this order. It appears constantly.* 🧠

### ⏱️ Constant Time: $O(1)$
Running time independent of input size.
*Example:* `return first element`. Always one operation.

### 📉 Logarithmic Time: $O(\log n)$
*Example:* Binary Search. Every step halves the problem.
*Example:* Search among 1,000,000 items. Binary search needs roughly $\log_2(1,000,000) \approx 20$ steps. Amazing. ✨

### 📏 Linear Time: $O(n)$
*Example:* Linear Search. May inspect every element.
*Example:* Array of 1,000,000 elements. Worst case: 1,000,000 checks.

### 🔲 Quadratic Time: $O(n^2)$
*Example:* Nested loops.
```pascal
for i=1 to n
    for j=1 to n

```

Operations: $n^2$. For 1000 elements: 1,000,000 operations.

### 🧊 Cubic Time: $O(n^3)$

*Example:* Three nested loops. Operations: $n^3$. Often too slow for very large inputs. 🐢

### 🚀 Exponential Time: $O(2^n)$

Dangerous. ⚠️

* For $n=10$: $2^{10} = 1024$
* For $n=100$: $2^{100} \approx 1.27 \times 10^{30}$. Impossible.

### 💥 Factorial Time: $O(n!)$

Even worse.

* $10! = 3,628,800$
* $20! \approx 2.4 \times 10^{18}$. Enormous.

---

## 🎯 Big-O Examples

* **Example 1:** $n^2+100n+7 \rightarrow O(n^2)$
* **Example 2:** $50n\log n+1000 \rightarrow O(n\log n)$
* **Example 3:** $2^n+n^5 \rightarrow O(2^n)$ *(Exponential dominates polynomial)*

---

## 📉 Big-$\Omega$ Notation

Omega gives a **lower bound**.
**Definition:** $f(n)=\Omega(g(n))$ if $f(n)$ grows *at least as fast* as $g(n)$.
*Example:* $3n+5$ is $\Omega(n)$.

---

## 🎯 Big-$\Theta$ Notation

Theta means: **Upper and lower bounds match.**
**Definition:** $f(n)=\Theta(g(n))$ if $f(n)=O(g(n))$ AND $f(n)=\Omega(g(n))$.
*Example:* $3n+5$ is $\Theta(n)$.
*Example:* $7n^2+10n+1$ is $\Theta(n^2)$.

---

## ⚖️ Comparing Growth Rates

Suppose $n=10^6$:

* **Linear:** $10^6$
* **Quadratic:** $10^{12}$
* **Cubic:** $10^{18}$
* **Exponential:** $2^{1000000}$ (Unimaginably huge)

This is why exponential algorithms are usually impossible.

*To truly grasp the massive chasm between polynomial time and exponential time, use the interactive widget below. Adjust the value of $n$ to see how quickly $2^n$ dwarfs algorithms like $n^2$ and $n^3$.*

---

## 🔐 Why Cryptographers Care

Cryptography depends on a gap.

* **Legitimate user:** RSA decryption is approximately polynomial time. Example: $O(n^3)$ or better.
* **Attacker:** Brute-force search is $O(2^n)$.

For a 128-bit key, the attacker faces $2^{128}$ possibilities. This is roughly $3.4 \times 10^{38}$ keys. **Impossible.** 🛡️
Security comes from exponential growth.

---

## ⚔️ Polynomial vs Exponential

This distinction is fundamental.

* **Polynomial:** $n$, $n^2$, $n^3$, $n^{100}$
* **Exponential:** $2^n$, $3^n$, $10^n$

**For large n: Any exponential eventually beats every polynomial.**
Example: $n^{100}$ looks huge. But $2^n$ eventually becomes much larger.

---

## 📌 Important Limits

Memorize:


$$\log n < n < n\log n < n^2 < n^3 < 2^n < n!$$


This ordering appears throughout computer science. 🎓

---

## ✅ Summary

You should know:

* **Big-O:** Upper bound. $f(n)=O(g(n))$
* **Big-$\Omega$:** Lower bound. $f(n)=\Omega(g(n))$
* **Big-$\Theta$:** Exact asymptotic growth. $f(n)=\Theta(g(n))$

**Important Classes:**
$O(1)$, $O(\log n)$, $O(n)$, $O(n\log n)$, $O(n^2)$, $O(n^3)$, $O(2^n)$, $O(n!)$

**Cryptography Insight:**
Security relies on the difference between **Polynomial-time algorithms** and **Exponential-time attacks**. 🛡️

---

## ✍️ Exercises

### Medium

1. Find Big-O of: $5n^2+7n+1$
2. Find Big-O of: $100n+200$
3. Find Big-O of: $n^4+n^3+n$
4. Is $n^2$ also $O(n^3)$? Explain.

### Hard

5. Show: $3n+7=\Theta(n)$
6. Compare $n^5$ and $2^n$ for large $n$.
7. Explain why Binary Search is $O(\log n)$.
8. Explain why brute-force search of a 256-bit key requires $O(2^{256})$ operations.

*Next we'll study **Chapter 3.3 — Complexity of Algorithms**, where Rosen formally analyzes running times of loops, recursive algorithms, and common algorithmic patterns. This is the chapter that directly prepares you for computational complexity theory and cryptographic hardness assumptions.* 🚀




# ⚙️ Chapter 3.3 — Complexity of Algorithms

This section teaches you how to analyze the running time of algorithms.
This is one of the most important topics for:
* Cryptography 🔐
* Algorithms ⏱️
* Competitive Programming 💻
* Complexity Theory 🧩
* Research 🔬

When cryptographers say: *"Factoring appears hard,"* they mean: *"No known efficient algorithm exists."*
Efficiency is measured using complexity.

---

## 🤔 Why Analyze Complexity?

Consider two algorithms.
* **Algorithm A:** 1 second for input size 100.
* **Algorithm B:** 2 seconds for input size 100.

You might think A is better. But what if:
* A $\rightarrow O(n^2)$
* B $\rightarrow O(n \log n)$

For huge inputs, **B becomes much faster.**
Therefore: We care about *growth*, not current speed. 📈

---

## 🧮 Counting Operations

The basic idea: Count how many primitive operations an algorithm performs.
Examples: `+`, `-`, `*`, `/`, `=`, `comparison`.

### Example 1: Constant Time
```pascal
x := a + b
return x

```

* Operations: 1 addition, 1 assignment, 1 return.
* Total: **$O(1)$** (Constant).

### Example 2: Single Loop

```pascal
sum := 0
for i := 1 to n
    sum := sum + i

```

* Loop runs $n$ times. Each iteration is $O(1)$.
* Total: **$O(n)$**

### Example 3: Two Consecutive Loops

```pascal
for i := 1 to n
    ...
for j := 1 to n
    ...

```

* First loop: $n$ operations. Second loop: $n$ operations.
* Total: $2n$. Therefore: **$O(n)$** (Constants are ignored).

### Example 4: Nested Loops

```pascal
for i := 1 to n
    for j := 1 to n
        ...

```

* Outer loop: $n$ times. Inner loop: $n$ times for each outer iteration.
* Total: $n \times n = n^2$.
* Complexity: **$O(n^2)$**

### Example 5: Triple Nested Loop

```pascal
for i := 1 to n
    for j := 1 to n
        for k := 1 to n
            ...

```

* Operations: $n^3$. Complexity: **$O(n^3)$**

**General Rule:** $k$ nested loops ($n \times n \times \dots \times n$): Complexity is **$O(n^k)$**.

### Example 6: Unequal Bounds

```pascal
for i := 1 to n
    for j := 1 to m
        ...

```

* Operations: $n \times m$. Complexity: **$O(nm)$**

### Example 7: Halving Loop

```pascal
i := n
while i > 1
    i := i / 2

```

* Values: $n, n/2, n/4, n/8, \dots, 1$
* Number of iterations: $\log_2 n$.
* Complexity: **$O(\log n)$**

### 🔍 Binary Search Analysis

Recall Binary Search. Each step removes half the data.
Size progression: $n, n/2, n/4, \dots, 1$
After $k$ steps: $\frac{n}{2^k} = 1 \Rightarrow 2^k = n \Rightarrow k = \log_2 n$.
Therefore: **$O(\log n)$**

### Example 8: Doubling Loop

```pascal
i := 1
while i < n
    i := 2 * i

```

* Values: $1, 2, 4, 8, 16, \dots$
* Again: **$O(\log n)$**

### Example 9: Triangular Loop

```pascal
for i := 1 to n
    for j := 1 to i
        ...

```

* Iterations: $1 + 2 + 3 + \dots + n$
* Using sum formula: $\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$
* Complexity: **$O(n^2)$**

### Example 10: Geometric Work

```pascal
for i := 1 to n
    do 2^i operations

```

* Total: $2 + 4 + 8 + \dots + 2^n$
* Geometric sum: $2^{n+1} - 2$.
* Complexity: **$O(2^n)$** (Exponential ⚠️)

---

## 📊 Types of Complexity

### Worst-Case Complexity

Usually we analyze the maximum possible running time.
*Example:* Linear Search. Searching first element = 1 comparison. Searching last element = $n$ comparisons. Worst case: **$O(n)$**.

### Average-Case Complexity

Expected running time over all inputs. Often harder to analyze. Rosen mainly focuses on worst case.

### Best-Case Complexity

Minimum running time.
*Example:* Linear Search targeting first element is $O(1)$. But best-case is often less useful.

---

## 🔄 Recursive Algorithms

Now complexity becomes more interesting.

### Example: Factorial

```pascal
Factorial(n)
    if n = 0 return 1
    return n * Factorial(n-1)

```

* Calls: $n, n-1, n-2, \dots, 1$
* Total: $n$. Complexity: **$O(n)$**

### Example: Recursive Fibonacci

```pascal
Fib(n)
    return Fib(n-1) + Fib(n-2)

```

Produces a recursion tree.
`Fib(5)` creates: `Fib(4)` and `Fib(3)`. `Fib(4)` creates `Fib(3)` and `Fib(2)`...
Many repeated calculations.
Complexity approximately: **$O(2^n)$**. Very inefficient. 🐢

**Why Fibonacci Matters:** A simple recursive algorithm can become exponential. This teaches: **Correct $\neq$ Efficient**. Both matter.

---

## ⚖️ Comparing Common Algorithms

| Algorithm | Complexity |
| --- | --- |
| Array access | $O(1)$ |
| Binary Search | $O(\log n)$ |
| Linear Search | $O(n)$ |
| Merge Sort | $O(n \log n)$ |
| Bubble Sort | $O(n^2)$ |
| Matrix Multiplication (basic) | $O(n^3)$ |
| Recursive Fibonacci | $O(2^n)$ |

*Memorize the first three.* 🧠

---

## 🔐 Complexity and Cryptography

Modern cryptography relies on asymmetry.

* **Good guy (Encryption):** Polynomial time.
* **Attacker (Brute force):** Exponential time.

**Example: AES-128.**
Attacker tries keys. Number of possibilities: $2^{128}$. Complexity: $O(2^{128})$.
This is why AES remains secure. 🛡️

### 🚀 Polynomial-Time Algorithms

Algorithms with complexity $O(n)$, $O(n^2)$, $O(n^3)$, $O(n^{100})$ are polynomial-time. Computer scientists consider these "Efficient" (at least theoretically).

### 🛑 Exponential-Time Algorithms

Examples: $O(2^n)$, $O(3^n)$, $O(n!)$. These become infeasible rapidly.
This distinction leads directly to **P versus NP**, which you will study later.

---

## 📏 Important Analysis Rules

1. **Sequential blocks:** Add complexities. $O(n) + O(n^2) = O(n^2)$. *Keep largest term.*
2. **Nested loops:** Multiply complexities. $O(n) \times O(n) = O(n^2)$.
3. **Ignore constants:** $1000n$ becomes $O(n)$.
4. **Keep dominant term:** $n^3 + n^2 + n$ becomes $O(n^3)$.

---

## ✅ Summary

You should now understand:

* **Loop Analysis:** Single loop ($O(n)$), Nested loops ($O(n^2)$, $O(n^3)$).
* **Halving/Doubling Processes:** $O(\log n)$.
* **Recursive Factorial:** $O(n)$.
* **Recursive Fibonacci:** $O(2^n)$.
* **Worst Case:** Most commonly used complexity measure.
* **Key Cryptography Idea:** Security depends on the difference between polynomial-time legitimate algorithms and exponential-time attacks. 🛡️

---

## ✍️ Exercises

### Medium

1. Determine the complexity:

```pascal
for i = 1 to n
    print(i)

```

2. Determine the complexity:

```pascal
for i = 1 to n
    for j = 1 to n

```

3. Determine the complexity:

```pascal
i = n
while i > 1
    i = i/2

```

4. Analyze the complexity:

```pascal
for i=1 to n
    for j=1 to i

```

### Hard

5. Show why Binary Search is $O(\log n)$.
6. Explain why recursive Fibonacci is exponential.
7. Compare $n \log n$ and $n^2$ for large $n$.
8. Explain why brute forcing AES-256 requires approximately $O(2^{256})$ work.

*Next we'll move to **Chapter 4 — Number Theory and Cryptography**, which is where Rosen begins modular arithmetic, divisibility, primes, congruences, the Euclidean algorithm in depth, and the mathematical foundations of RSA, Diffie–Hellman, and modern cryptography. This is likely the chapter most directly aligned with your cryptography goals.* 🚀

