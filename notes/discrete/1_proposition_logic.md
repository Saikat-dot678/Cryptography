Perfect. If we're studying Rosen's Discrete Mathematics and Its Applications properly, then we should start from Chapter 1, not jump directly to cryptography.

For someone aiming at cryptography research, I recommend mastering Chapters 1–5 extremely well because they build the mathematical maturity needed for modern cryptography.

According to Rosen, Chapter 1 is about The Foundations: Logic and Proofs. Everything afterward depends on it. A cryptographer spends more time proving than encrypting.

---

## Chapter 1: The Foundations – Logic and Proofs

### Why Logic?
Suppose someone claims:

> "This cryptographic protocol is secure."

How do we know? In mathematics, we don't accept statements because:
* someone famous said them,
* they seem true,
* a computer tested many examples.

We need a **proof**. Logic is the language used to build proofs.

---

## Section 1.1 — Propositional Logic

### What is a Proposition?
A proposition is a declarative sentence that is either true or false, but not both.

**Examples:**
* $2 + 3 = 5$ (True)
* 10 is a prime number (False)

Both are propositions.

### Not Propositions
* **Questions:** What time is it? *(Not a proposition)*
* **Commands:** Close the door. *(Not a proposition)*
* **Variables:** $x + 2 = 5$ *(Not a proposition because truth depends on $x$)*

### Propositional Variables
We use letters like $p, q, r, s$ to represent propositions.

**Example:**
* $p$: "It is raining."
* $q$: "The ground is wet."

### Truth Values
Every proposition has exactly one truth value.
* **T** = True
* **F** = False

**Example:** $p = \text{T}, q = \text{F}$

---

## Logical Operators

### Negation (NOT)
If $p$ is a proposition, then $\neg p$ means "not $p$".

**Example:** * $p$: It is raining.
* $\neg p$: It is not raining.

**Truth Table:**

| $p$ | $\neg p$ |
| :---: | :---: |
| T | F |
| F | T |

*Negation flips truth values.*

### Conjunction (AND)
**Symbol:** $p \land q$ (Read: $p$ AND $q$)

**Example:** * $p$: I study cryptography.
* $q$: I study number theory.
* $p \land q$: I study cryptography AND number theory.

**Truth Table:**

| $p$ | $q$ | $p \land q$ |
| :---: | :---: | :---: |
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

*AND is only true when both are true.*

### Disjunction (OR)
**Symbol:** $p \lor q$ (Read: $p$ OR $q$)

In mathematics, OR is inclusive.

**Example:** "I will eat pizza OR pasta."
Mathematical interpretation:
* pizza only ✓
* pasta only ✓
* both ✓

**Truth Table:**

| $p$ | $q$ | $p \lor q$ |
| :---: | :---: | :---: |
| T | T | T |
| T | F | T |
| F | T | T |
| F | F | F |

### Exclusive OR (XOR)
Sometimes we want either $p$ or $q$, but **not both**.
**Symbol:** $p \oplus q$

**Truth Table:**

| $p$ | $q$ | $p \oplus q$ |
| :---: | :---: | :---: |
| T | T | F |
| T | F | T |
| F | T | T |
| F | F | F |

---

## Implications and Conditionals

### Conditional Statement
One of the most important ideas in mathematics.
**Symbol:** $p \rightarrow q$ (Read: "If $p$, then $q$.")

**Example:** * $p$: It rains.
* $q$: Ground becomes wet.
* **Statement:** If it rains, then the ground becomes wet.

**Truth Table:**

| $p$ | $q$ | $p \rightarrow q$ |
| :---: | :---: | :---: |
| T | T | T |
| T | F | F |
| F | T | T |
| F | F | T |

**Why is False $\rightarrow$ True equal to True?**
This confuses everyone initially.
*Example:* "If $2 = 5$, then I am the King of India."
Since the premise is already false, the implication is considered true in logic. This is called **vacuous truth**. It feels strange, but it makes mathematics consistent.

---

### Converse, Inverse, and Contrapositive
Given the original conditional statement: $p \rightarrow q$

#### Converse: $q \rightarrow p$
* **Original:** If a number is divisible by 4, then it is even. (True)
* **Converse:** If a number is even, then it is divisible by 4. (False)
  * *Counterexample:* 6 is even and not divisible by 4.

#### Inverse: $\neg p \rightarrow \neg q$
* **Original:** If divisible by 4, then even.
* **Inverse:** If not divisible by 4, then not even. (False)
  * *Counterexample:* 6 is not divisible by 4, but still even.

#### Contrapositive: $\neg q \rightarrow \neg p$
* **Original:** If divisible by 4, then even.
* **Contrapositive:** If not even, then not divisible by 4. (True)

> **Extremely Important Theorem**
> A statement and its contrapositive always have the same truth value. 
> $p \rightarrow q$ is logically equivalent to $\neg q \rightarrow \neg p$.
> *Cryptography papers use contrapositives constantly.*

---

### Biconditional
**Symbol:** $p \leftrightarrow q$ (Read: "$p$ if and only if $q$" or "$p$ iff $q$")

**Meaning:** $(p \rightarrow q) \land (q \rightarrow p)$. Both directions must hold.

**Example:** "An integer is even iff it is divisible by 2." (Both statements are true.)

**Truth Table:**

| $p$ | $q$ | $p \leftrightarrow q$ |
| :---: | :---: | :---: |
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | T |

---

## Why Cryptographers Need Logic
When reading a security proof, you'll constantly see arguments like:

* "If an adversary breaks the scheme, then we can solve factoring." *(This is an implication.)*
* "If factoring is hard, then the scheme is secure." *(Another implication.)*

Understanding **implication**, **contrapositive**, **equivalence**, and **logical reasoning** is essential before moving into proofs, number theory, and cryptography.

---

## Exercises
Determine whether each statement is True or False.

1. If 5 is even, then $2 + 2 = 4$.
2. If 8 is divisible by 4, then 8 is even.
3. What is the converse of "If a number is divisible by 6, then it is divisible by 3"?
4. What is the contrapositive of "If $n$ is prime and $n > 2$, then $n$ is odd"?
5. Why are a statement and its contrapositive always equivalent?

## Chapter 1.1 (Continued) — Truth Tables, Logical Equivalence, and Logical Laws

In the previous lesson we learned:
* Propositions
* Negation
* AND, OR
* Implication
* Converse, Inverse, Contrapositive
* Biconditional

Now we learn how mathematicians manipulate logical statements the same way algebra manipulates equations. This is the foundation of mathematical proofs.

---

### Truth Tables
A truth table lists every possible combination of truth values. 

Suppose we have two propositions, $p$ and $q$. Each can be True (T) or False (F). Therefore, there are $2 \times 2 = 4$ possibilities:

| $p$ | $q$ |
| :---: | :---: |
| T | T |
| T | F |
| F | T |
| F | F |

* For three propositions ($p, q, r$), there are $2^3 = 8$ possibilities.
* For $n$ propositions, there are **$2^n$ possibilities**.

> This exponential growth appears constantly in cryptography and complexity theory.

### Example: Build a Truth Table
Construct the truth table for: $(p \land q) \rightarrow p$

| $p$ | $q$ | $p \land q$ | $(p \land q) \rightarrow p$ |
| :---: | :---: | :---: | :---: |
| T | T | T | **T** |
| T | F | F | **T** |
| F | T | F | **T** |
| F | F | F | **T** |

**Notice:** The final column is always True. This means the statement is special.

---

### Tautology, Contradiction, and Contingency

#### Tautology
A proposition that is always true is called a **tautology**.
* **Example:** $(p \land q) \rightarrow p$ is a tautology.
* **Law of Excluded Middle:** $p \lor \neg p$

| $p$ | $\neg p$ | $p \lor \neg p$ |
| :---: | :---: | :---: |
| T | F | **T** |
| F | T | **T** |

#### Contradiction
A proposition that is always false is called a **contradiction**.
* **Example:** $p \land \neg p$

| $p$ | $\neg p$ | $p \land \neg p$ |
| :---: | :---: | :---: |
| T | F | **F** |
| F | T | **F** |

#### Contingency
Some statements are sometimes true and sometimes false (e.g., $p \land q$). These are called **contingencies**.

---

### Logical Equivalence
Suppose two statements always have the same truth values. Then they are **logically equivalent**.
* **Notation:** $p \equiv q$ (or $p \leftrightarrow q$ when discussing equivalence).

#### Example: Double Negation Law
Show $\neg(\neg p)$ is equivalent to $p$.

| $p$ | $\neg p$ | $\neg(\neg p)$ |
| :---: | :---: | :---: |
| **T** | F | **T** |
| **F** | T | **F** |

The last column equals the first column. Therefore: $\neg(\neg p) \equiv p$.

---

### Logical Laws (The Algebra of Reasoning)

#### De Morgan's Laws
Among the most important laws in mathematics and computer science. They appear everywhere: Boolean algebra, digital circuits, cryptography, complexity theory, and security proofs. **Memorize them.**

1. **First Law:** $\neg(p \land q) \equiv \neg p \lor \neg q$
   * *Meaning:* NOT ($p$ and $q$) equals (not $p$) OR (not $q$).
   * *Example:* "I am not both rich and famous" $\equiv$ "I am not rich OR I am not famous."
2. **Second Law:** $\neg(p \lor q) \equiv \neg p \land \neg q$
   * *Meaning:* NOT ($p$ or $q$) equals (not $p$) AND (not $q$).

#### Commutative Laws (Order doesn't matter)
* $p \land q \equiv q \land p$
* $p \lor q \equiv q \lor p$

#### Associative Laws (Grouping doesn't matter)
* $(p \land q) \land r \equiv p \land (q \land r)$
* $(p \lor q) \lor r \equiv p \lor (q \lor r)$

#### Distributive Laws (Very important)
* $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$
* $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$

#### Identity Laws
* $p \land \text{T} \equiv p$ (Compare to $x \times 1 = x$)
* $p \lor \text{F} \equiv p$ (Compare to $x + 0 = x$)

#### Domination Laws
* $p \lor \text{T} \equiv \text{T}$ (Always true)
* $p \land \text{F} \equiv \text{F}$ (Always false)

#### Idempotent Laws
Repeating a statement changes nothing.
* $p \lor p \equiv p$
* $p \land p \equiv p$

#### Absorption Laws
Very useful in simplifying expressions. The second part adds no new information.
* $p \lor (p \land q) \equiv p$
* $p \land (p \lor q) \equiv p$
* *Example:* "I passed OR (I passed AND I studied)" is equivalent to just "I passed."

#### Implication as OR
One of the most useful identities. It appears constantly in proofs.

**Identity:** $p \rightarrow q \equiv \neg p \lor q$

**Verification:**

| $p$ | $q$ | $p \rightarrow q$ | $\neg p \lor q$ |
| :---: | :---: | :---: | :---: |
| T | T | **T** | **T** |
| T | F | **F** | **F** |
| F | T | **T** | **T** |
| F | F | **T** | **T** |

Same truth values. Therefore: $p \rightarrow q \equiv \neg p \lor q$.

---

### Why Cryptographers Care
Modern cryptographic proofs often look like:
> "If the adversary succeeds ($A$), then factoring succeeds ($F$)."

Symbolically: $A \rightarrow F$

We often rewrite it:
* Using Implication as OR: $\neg A \lor F$
* Using the Contrapositive: $\neg F \rightarrow \neg A$

Without logical equivalence, reading research papers becomes impossible.

---

### Key Laws to Memorize Summary
* **Double Negation:** $\neg(\neg p) \equiv p$
* **De Morgan:** * $\neg(p \land q) \equiv \neg p \lor \neg q$
  * $\neg(p \lor q) \equiv \neg p \land \neg q$
* **Implication:** $p \rightarrow q \equiv \neg p \lor q$
* **Contrapositive:** $p \rightarrow q \equiv \neg q \rightarrow \neg p$
* **Excluded Middle:** $p \lor \neg p$
* **Contradiction:** $p \land \neg p$

---

### Exercises
1. Construct the truth table for: $(p \lor q) \rightarrow q$
2. Show that $\neg(p \lor q)$ and $\neg p \land \neg q$ are logically equivalent.
3. Rewrite $p \rightarrow q$ using only NOT and OR.
4. Is $(p \land q) \rightarrow p$ a tautology, contradiction, or contingency?
5. Prove using a truth table: $p \rightarrow q \equiv \neg q \rightarrow \neg p$

*Next, we'll study Section 1.2 — Applications of Propositional Logic, where Rosen begins using logic to model real-world reasoning, puzzles, digital circuits, and computer systems. This is where logic starts becoming useful rather than just symbolic.*

## Chapter 1.2 — Applications of Propositional Logic

In Section 1.1, we learned the syntax of logic: propositions, truth values, logical operators, and truth tables. Now, Rosen begins showing how logic is actually used to model reasoning and solve problems. 

This section is extremely important because cryptography, algorithms, AI, formal verification, and computer security all start by converting real-world statements into logical formulas.

---

### Translating English into Logic
The first skill is converting natural language into symbolic language. 

Suppose:
* $p$: It is raining.
* $q$: I carry an umbrella.

**Example 1**
* **Statement:** It is raining and I carry an umbrella.
* **Translation:** $p \land q$

**Example 2**
* **Statement:** It is raining or I carry an umbrella.
* **Translation:** $p \lor q$

**Example 3**
* **Statement:** If it is raining, then I carry an umbrella.
* **Translation:** $p \rightarrow q$

**Example 4**
* **Statement:** It is not raining.
* **Translation:** $\neg p$

---

### Necessary and Sufficient Conditions
Students often confuse these. Cryptography papers use these terms constantly.

#### Sufficient Condition
Consider the implication: $p \rightarrow q$
We say **$p$ is sufficient for $q$** because whenever $p$ occurs, $q$ follows.
* *Example:* $n \text{ divisible by } 4 \rightarrow n \text{ even}$
* Being divisible by 4 is *sufficient* for being even.

#### Necessary Condition
For the same implication: $p \rightarrow q$
We also say **$q$ is necessary for $p$** because $p$ cannot occur unless $q$ occurs.
* *Example:* $\text{divisible by } 4 \rightarrow \text{even}$
* Being even is *necessary* for divisibility by 4.

> **Easy Memory Trick**
> For $p \rightarrow q$, think: "$p$ gives $q$". 
> Then: $p$ is **sufficient**, $q$ is **necessary**.

---

### Translating Complex Statements

**Example:** "You can access the server only if you are authenticated."
* Let $p = \text{access server}$
* Let $q = \text{authenticated}$

"Only if" means: $p \rightarrow q$ 
(Not $q \rightarrow p$. This mistake appears frequently in exams!)

#### Important Language Patterns
Memorize these translations:

| English | Logic |
| :--- | :--- |
| $p$ if $q$ | $q \rightarrow p$ |
| $p$ only if $q$ | $p \rightarrow q$ |
| $p$ iff $q$ | $p \leftrightarrow q$ |
| $p$ unless $q$ | $\neg q \rightarrow p$ |
| either $p$ or $q$ | $p \lor q$ |

---

### System Specifications
Logic is heavily used to describe computer systems.

**Example 1: A server rule**
* **Rule:** If the user is authenticated and has permission, then access is granted.
* **Let:** $a = \text{authenticated}$, $p = \text{permission}$, $g = \text{granted}$
* **Specification:** $(a \land p) \rightarrow g$

**Example 2: Another rule**
* **Rule:** If access is granted, then the user is logged.
* **Let:** $l = \text{logged in}$
* **Specification:** $g \rightarrow l$

These logical specifications precisely describe how systems should behave.

---

### Consistency
A collection of statements is **consistent** if they can all be true simultaneously.

* **Consistent Example:** $p$ and $q$. (Both can be true).
* **Inconsistent Example:** $p$ and $\neg p$. (Impossible. One says true, one says false).

**Example of a Consistency Check:**
Suppose a security policy states:
1. User is authenticated ($p$).
2. User is not authenticated ($\neg p$).

Symbolically: $p \land \neg p$. This is a contradiction, meaning the policy is **inconsistent**.

---

### Rules of Inference
A rule of inference is a valid reasoning pattern. These are fundamental for formal proofs.

#### Rule 1: Modus Ponens
* **Given:** $p \rightarrow q$ AND $p$
* **Conclude:** $q$

> **Example:**
> If RSA is broken, then factoring is easy. ($p \rightarrow q$)
> RSA is broken. ($p$)
> **Therefore:** Factoring is easy. ($q$)

#### Rule 2: Modus Tollens (Contrapositive Reasoning)
* **Given:** $p \rightarrow q$ AND $\neg q$
* **Conclude:** $\neg p$

> **Example:**
> If divisible by 4, then even. ($p \rightarrow q$)
> Not even. ($\neg q$)
> **Therefore:** Not divisible by 4. ($\neg p$)
> *(Cryptographic security reductions use this constantly.)*

#### Rule 3: Hypothetical Syllogism
* **Given:** $p \rightarrow q$ AND $q \rightarrow r$
* **Conclude:** $p \rightarrow r$

> **Example:**
> Study $\rightarrow$ Pass
> Pass $\rightarrow$ Graduate
> **Therefore:** Study $\rightarrow$ Graduate

#### Rule 4: Disjunctive Syllogism
* **Given:** $p \lor q$ AND $\neg p$
* **Conclude:** $q$

> **Example:**
> Either Alice or Bob knows the key. ($p \lor q$)
> Alice does not know the key. ($\neg p$)
> **Therefore:** Bob knows the key. ($q$)

---

### Fallacies
Not all reasoning is valid. Rosen emphasizes these common mistakes.

#### Fallacy 1: Affirming the Consequent (**INVALID**)
* **Given:** $p \rightarrow q$ AND $q$
* **Conclude:** $p$ 

> **Example:**
> If divisible by 4, then even. ($p \rightarrow q$)
> 8 is even. ($q$)
> *Can we conclude 8 is divisible by 4?* Here, yes. But logic asks whether it **always** works.
> *Counterexample:* 6 is even, yet 6 is not divisible by 4. Therefore, invalid.

#### Fallacy 2: Denying the Antecedent (**INVALID**)
* **Given:** $p \rightarrow q$ AND $\neg p$
* **Conclude:** $\neg q$

> **Example:**
> If divisible by 4, then even. ($p \rightarrow q$)
> Not divisible by 4. ($\neg p$)
> *Can we conclude not even?* No. 6 is a counterexample.

---

### Why This Matters for Cryptography
A typical security proof looks like this:
* "If attacker A exists, then factoring algorithm F exists."
* **Symbolically:** $A \rightarrow F$

We usually know:
* Factoring is hard (meaning no factoring algorithm exists: $\neg F$)

Using **Modus Tollens**:
* $A \rightarrow F$
* $\neg F$
* **Therefore:** $\neg A$ (No attacker exists).

*This exact pattern appears throughout modern cryptography.*

---

### What You Should Know Before Moving On
* **Translation:** English $\leftrightarrow$ Logic
* **Conditions:** Necessary vs. Sufficient
* **Inference Rules:** Modus Ponens, Modus Tollens, Hypothetical Syllogism, Disjunctive Syllogism
* **Common Fallacies:** Affirming the Consequent, Denying the Antecedent

---

### Exercises

**Translate into logic:**
1. If the server is online, users can log in.
2. Users can log in only if they are authenticated.
3. Either Alice or Bob generated the key.
4. Alice generated the key iff Bob did not generate the key.

**Determine whether each argument is valid:**

1. 
$p \rightarrow q$, 
$p$
$\therefore q$

2. 
$p \rightarrow q$, 
$q$
$\therefore p$

3. 
$p \rightarrow q$, 
$\neg q$
$\therefore \neg p$

4. 
$p \lor q$, 
$\neg p$
$\therefore q$

*Next, we'll cover Section 1.3 — Propositional Equivalences, where Rosen teaches formal algebraic manipulation of logical statements without building huge truth tables every time. This is the beginning of proof techniques.*


## Chapter 1.3 — Propositional Equivalences

In Section 1.1, we used truth tables to determine whether two logical statements were equivalent. That works well for small expressions. But consider:

$$((p \lor q) \land (\neg r \lor s)) \rightarrow ((p \land s) \lor (q \land \neg r))$$

A truth table would require:
* 4 variables: $2^4 = 16$ rows.
* 10 variables: $2^{10} = 1024$ rows.
* 20 variables: $2^{20} \approx 1,000,000$ rows.

Clearly, we need a better method. Just as algebra manipulates equations, logic has its own algebra.

---

### What is a Propositional Equivalence?
Two propositions are equivalent if they always have the same truth value.

**Example:**
$\neg(\neg p)$ and $p$ always match.
Therefore: $\neg(\neg p) \equiv p$

### Why Equivalences Matter
Suppose a security policy says: *"If not authenticated, deny access."* 
We may need to rewrite it into a different but equivalent form for implementation. Security proofs constantly transform statements into equivalent forms.

---

### Basic Logical Laws
These laws are the "algebra rules" of logic. **Memorize them.**

**1. Identity Laws**
Just as $x + 0 = x$ and $x \times 1 = x$, we have:
* $p \lor \text{F} \equiv p$
* $p \land \text{T} \equiv p$
> *Example:* (Alice knows key) $\land$ True $\equiv$ Alice knows key

**2. Domination Laws**
* $p \lor \text{T} \equiv \text{T}$ (Always true)
* $p \land \text{F} \equiv \text{F}$ (Always false)
> *Example:* Server authenticated $\lor$ True $\equiv$ Always true. (No need to check authentication).

**3. Idempotent Laws**
Repeating a statement changes nothing.
* $p \lor p \equiv p$
* $p \land p \equiv p$

**4. Double Negation**
One of the most important laws.
* $\neg(\neg p) \equiv p$
> *Example:* "It is not true that it is not raining" means "It is raining."

**5. Commutative Laws**
Order does not matter.
* $p \lor q \equiv q \lor p$
* $p \land q \equiv q \land p$

**6. Associative Laws**
Grouping does not matter.
* $(p \lor q) \lor r \equiv p \lor (q \lor r)$
* $(p \land q) \land r \equiv p \land (q \land r)$

**7. Distributive Laws**
Just like algebra ($a(b+c) = ab + ac$):
* $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$
* $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$

**8. De Morgan's Laws**
These are absolutely essential.
* **First Law:** $\neg(p \land q) \equiv \neg p \lor \neg q$
* **Second Law:** $\neg(p \lor q) \equiv \neg p \land \neg q$
> *Example:* "It is NOT true that Alice and Bob both know the key" $\rightarrow \neg(A \land B)$. 
> Using De Morgan: $\neg A \lor \neg B$ ("Alice doesn't know the key OR Bob doesn't know the key.")

**9. Absorption Laws**
Very useful simplifications.
* $p \lor (p \land q) \equiv p$
* $p \land (p \lor q) \equiv p$
> *Example:* Authenticated $\lor$ (Authenticated $\land$ Admin) $\equiv$ Authenticated. (The second part adds nothing).

**10. Negation Laws**
* $p \lor \neg p \equiv \text{T}$ (Law of Excluded Middle — Always true)
* $p \land \neg p \equiv \text{F}$ (Law of Contradiction — Always false)

---

### Rewriting Implications
This is one of the most useful transformations. 

Recall: $p \rightarrow q$ is equivalent to $\neg p \lor q$.

**Example:**
* **Statement:** If authenticated, then access granted.
* **Let:** $a = \text{authenticated}$, $g = \text{access granted}$
* **Translation:** $a \rightarrow g$
* **Rewritten:** $\neg a \lor g$

This conversion appears constantly in theorem proving, SAT solvers, cryptographic proofs, and formal verification.

### Rewriting Biconditionals
Recall: $p \leftrightarrow q$ means $(p \rightarrow q) \land (q \rightarrow p)$.
Using the implication law, this is equivalent to: 
$$(\neg p \lor q) \land (\neg q \lor p)$$

---

### Example Simplifications

**Example 1: Simplify $\neg(p \lor \neg q)$**
1. Using De Morgan's Law: $\neg p \land \neg(\neg q)$
2. Apply Double Negation: $\neg p \land q$
* **Final answer:** $\neg p \land q$

**Example 2: Simplify $(p \land \text{T}) \lor \text{F}$**
1. Identity law ($p \land \text{T} \equiv p$): $p \lor \text{F}$
2. Identity law again: $p$
* **Final answer:** $p$

---

### Why Cryptographers Care
Modern cryptography uses proofs like: *"If an attacker exists, then a factoring algorithm exists."*

We often rewrite $A \rightarrow F$ as:
* $\neg A \lor F$
* Or use the contrapositive: $\neg F \rightarrow \neg A$

Without propositional equivalences, reading security reductions becomes extremely difficult.

---

### Strategy for Simplifying Logical Expressions
When given a complex expression, follow these steps:

1. **Remove implications:** Change $p \rightarrow q$ to $\neg p \lor q$.
2. **Remove biconditionals:** Change $p \leftrightarrow q$ to $(p \rightarrow q) \land (q \rightarrow p)$.
3. **Push negations inward:** Use De Morgan's Laws to move $\neg$ directly next to variables.
4. **Apply basic laws:** Use Identity, Domination, Absorption, and Double Negation until the expression is fully simplified.

---

### Exercises
Simplify the following completely:

1. $\neg(p \land \neg q)$
2. $(p \lor \text{F}) \land \text{T}$
3. $p \lor (p \land q)$
4. $\neg(p \rightarrow q)$
5. Rewrite $p \leftrightarrow q$ using only $\neg$, $\land$, and $\lor$.

---

### What Comes Next?
**Section 1.4 Predicates and Quantifiers.** 
This is where mathematics becomes much more powerful. Instead of talking about individual propositions, we start talking about:
* *"For every integer $n$..."*
* *"There exists a prime $p$..."*

Almost every theorem in number theory, cryptography, algebra, and computer science is written using quantifiers. This section is one of the most important in the entire book, so we'll cover it very carefully next.


## Chapter 1.4 — Predicates and Quantifiers

This is one of the most important sections in all of discrete mathematics. Up until now, we have worked with propositions like:
* $p$: "2 is even"
* $q$: "7 is prime"

These statements are already either true or false. However, mathematics rarely deals with isolated statements. Most mathematical statements look like:
> "Every prime greater than 2 is odd."
> "There exists a prime larger than 100."
> "For every integer $n$, $n^2 \ge 0$."

These are not simple propositions anymore. To express them, we need **predicates** and **quantifiers**.

---

### 1. Predicates
Consider the statement: $x > 3$
Is it true? We cannot answer. Why? Because we do not know $x$.
* If $x = 5$, it is true.
* If $x = 1$, it is false.

Such a statement is called a **predicate**.

#### Definition
A predicate is a statement involving variables that becomes a proposition when specific values are assigned.

**Example:** $P(x): x > 3$
Let's test values:
* $x = 5 \rightarrow P(5): 5 > 3$ (True)
* $x = 2 \rightarrow P(2): 2 > 3$ (False)
* $x = 100 \rightarrow P(100): 100 > 3$ (True)

So, $P(x)$ is not a proposition, but $P(5)$ is a proposition.

#### Examples of Predicates
* **Example 1:** $P(x): x \text{ is prime}$
* **Example 2:** $Q(n): n \text{ is even}$
* **Example 3:** $R(a,b): a + b = 10$ (Two-variable predicate)
  * $R(4,6)$ is True.
  * $R(2,5)$ is False.

---

### Domains (Universes of Discourse)
Predicates require a domain.

**Example:** $P(x): x^2 = 1$
* If domain is **Real Numbers**, solutions: $1, -1$
* If domain is **Positive Integers**, solution: $1$ only.

Therefore, the domain matters.

---

### Quantifiers
Quantifiers allow us to make statements about many elements at once. There are two major quantifiers.

#### Universal Quantifier ($\forall$)
* **Symbol:** $\forall$
* **Read:** "for all" or "for every"

Suppose $P(x): x^2 \ge 0$ for real numbers. Then "For every $x$, $x^2 \ge 0$" becomes:
$$\forall x (x^2 \ge 0)$$
**Meaning:** Every value in the domain satisfies the predicate.

**Example:**
* **Statement:** Every integer is less than 100.
* **Symbolically:** $\forall x (x < 100)$
* **False.** (Counterexample: 1000)

*A universal statement is false if even one counterexample exists.*

#### Counterexamples
This idea is extremely important. Suppose someone claims: "Every prime number is odd."
To disprove it, we only need one counterexample.
* **Example:** 2 is prime, but not odd.
* Therefore, the statement is false.

*One counterexample destroys a universal statement.*

#### Existential Quantifier ($\exists$)
* **Symbol:** $\exists$
* **Read:** "there exists"

**Example:** "There exists an integer whose square equals 25."
* **Symbolically:** $\exists x (x^2 = 25)$
* **True.** Because $x = 5$ or $x = -5$ works.

**Example:** "There exists an integer greater than 1000."
* **True.** (Example: 1001)

*Existential statements need only one example.*

---

### Universal vs Existential
* **Universal:** $\forall x P(x)$ means **everyone works**.
* **Existential:** $\exists x P(x)$ means **at least one works**.

#### Example Comparison
Consider $P(x): x \text{ is even}$. Domain: Integers.
* **Statement 1:** $\forall x P(x)$
  * *Meaning:* Every integer is even. (False)
* **Statement 2:** $\exists x P(x)$
  * *Meaning:* There exists an even integer. (True)

---

### Nested Quantifiers
Things become more interesting.

**Example:** "For every integer $x$, there exists an integer $y$ such that $y > x$."
* **Symbolically:** $\forall x \exists y (y > x)$
* **True.** (Choose $y = x + 1$)

#### Order Matters!
Consider:
1. $\forall x \exists y (y > x)$
2. $\exists y \forall x (y > x)$

These are completely different.
* **First statement:** For each $x$ we can choose a larger $y$. (True)
* **Second statement:** There exists one $y$ bigger than every integer. (False. No largest integer exists.)

This distinction becomes crucial later in Number Theory, Cryptography, Complexity Theory, and Security Definitions.

---

### Negating Quantifiers
One of the most important topics.

#### Negation of Universal
**Rule:** $\neg(\forall x P(x)) \equiv \exists x \neg P(x)$
* **Read:** "Not everyone satisfies P" means "Someone does not satisfy P"
* **Example:** "Not all students passed" is equivalent to "Some student did not pass."

#### Negation of Existential
**Rule:** $\neg(\exists x P(x)) \equiv \forall x \neg P(x)$
* **Read:** "There does not exist an $x$ with P" means "Every $x$ fails P"
* **Example:** "No student passed" is equivalent to "Every student failed."

---

### Why Cryptographers Care
Security definitions are almost entirely written with quantifiers.

**Example (A simplified security statement):**
> "For every efficient attacker $A$, there exists only negligible probability that $A$ breaks the scheme."

This kind of statement contains predicates, universals, existentials, and implications. Without understanding quantifiers, modern cryptography becomes unreadable.

---

### Common Mistakes

#### Mistake 1
Confusing $\forall x \exists y$ with $\exists y \forall x$. These are usually very different!

#### Mistake 2
Negating incorrectly. Many students write:
* $\neg \forall x P(x) \equiv \forall x \neg P(x)$ *(Wrong!)*
* **Correct:** $\neg \forall x P(x) \equiv \exists x \neg P(x)$

---

### Exercises
Let $P(x): x \text{ is prime}$. Domain = positive integers.

1. **Express:** Every positive integer is prime.
2. **Express:** There exists a prime greater than 100.
3. **Negate:** $\forall x P(x)$
4. **Negate:** $\exists x P(x)$
5. **Determine whether:** $\forall x \exists y (y > x)$ is true over the integers.
6. **Determine whether:** $\exists y \forall x (y > x)$ is true over the integers.

*Next comes Section 1.5 — Nested Quantifiers, where Rosen goes much deeper into translating complex mathematical statements and proving them true or false. This section is critical because most theorems in number theory and cryptography use multiple layers of quantifiers.*

## Chapter 1.5 — Nested Quantifiers

This section is one of the most important in the entire book. By now you know:
* Predicates
* Universal quantifier ($\forall$)
* Existential quantifier ($\exists$)

Now we learn how to combine them. Most mathematical theorems look like:
> "For every $x$, there exists a $y$ such that..." 
> *or* > "There exists an $x$ such that for every $y$..."

**The order matters enormously.**

---

### Why Nested Quantifiers Matter
Consider the statement: *"Every person has a mother."*

This actually means: "For every person $x$, there exists a person $y$ such that $y$ is the mother of $x$."
* **Symbolically:** $\forall x \exists y M(x,y)$ 
  *(where $M(x,y)$ means $y$ is the mother of $x$)*

**Notice:** We choose $x$ first. Then $y$ may depend on $x$. Different people have different mothers.

---

### First Important Example
Consider the following statement over the domain of **Integers**:
$$\forall x \exists y (y > x)$$

**Read:** For every integer $x$, there exists an integer $y$ greater than $x$.
* **Is this true?**
  * Take $x = 5 \rightarrow$ Choose $y = 6$ (Works)
  * Take $x = 1000 \rightarrow$ Choose $y = 1001$ (Works)
* In general, $y = x + 1$ always works. 
* **Therefore: TRUE**

---

### Second Important Example
Now, let's reverse the order:
$$\exists y \forall x (y > x)$$

**Read:** There exists an integer $y$ that is greater than every integer $x$.
* **Is this true?**
  * Suppose $y = 100 \rightarrow$ Then $x = 101$ breaks it.
  * Suppose $y = 1,000,000 \rightarrow$ Then $x = 1,000,001$ breaks it.
* No integer is larger than all integers.
* **Therefore: FALSE**

> **Key Lesson**
> These two statements are NOT equivalent. 
> $\forall x \exists y$ is very different from $\exists y \forall x$.
> **The order of quantifiers changes the meaning.**

---

### Example from Number Theory
Consider: *"Every positive integer has a larger prime."*
* **Symbolically:** $\forall n \exists p$ such that $p$ is prime and $p > n$.
* **True.** (It is essentially a consequence of the fact that there are infinitely many primes.)

Now consider: *"There exists a prime larger than every integer."*
* **Symbolically:** $\exists p \forall n$ with $p > n$.
* **False.** (No largest prime exists.)

---

### Understanding Dependencies
A useful way to think about nested quantifiers:

#### Universal First: $\forall x \exists y$
* **Meaning:** $y$ may depend on $x$.
* *Example:* $y = x + 1$. Different $x$ values give different $y$ values.

#### Existential First: $\exists y \forall x$
* **Meaning:** One fixed $y$ must work for every $x$. (Much harder!)

#### Example with Real Numbers
**Statement 1:** $\forall x \in \mathbb{R} \exists y \in \mathbb{R} (x + y = 0)$
* **Read:** Every real number has an additive inverse.
* **Proof:** Choose $y = -x$. Then $x + y = x - x = 0$. 
* **Therefore: TRUE**

**Statement 2:** $\exists y \in \mathbb{R} \forall x \in \mathbb{R} (x + y = 0)$
* **Read:** There exists *one* real number $y$ that makes $x + y = 0$ for *every* real number $x$.
* **Impossible.** If $x = 1$, we need $y = -1$. If $x = 2$, we need $y = -2$. One value cannot satisfy both. 
* **Therefore: FALSE**

---

### Translating English Statements
Let $P(x,y)$ mean: "student $x$ passed exam $y$".

**Example 1:**
* **Statement:** Every student passed some exam.
* **Translation:** $\forall x \exists y P(x,y)$
  *(Each student may pass a different exam).*

**Example 2:**
* **Statement:** There is an exam that every student passed.
* **Translation:** $\exists y \forall x P(x,y)$
  *(One particular exam must be passed by everyone).*

---

### Negating Nested Quantifiers
This is extremely important for proofs. Apply the negation rules one at a time.

* **Rule 1:** $\neg \forall x P(x) \equiv \exists x \neg P(x)$
* **Rule 2:** $\neg \exists x P(x) \equiv \forall x \neg P(x)$

#### Example
Negate: $\forall x \exists y (y > x)$

1. **Step 1 (Negate outer universal):** $\exists x \neg \exists y (y > x)$
2. **Step 2 (Negate existential):** $\exists x \forall y \neg(y > x)$

**Equivalent English:** *"There exists an integer $x$ such that no integer is greater than $x$."*
This says there is a largest integer, which is false. Hence, the original statement is true.

---

### Mathematical Proofs Often Start Here
These four patterns form the backbone of mathematical proofs:

| Goal | Technique |
| :--- | :--- |
| **Prove $\forall x P(x)$** | Pick an arbitrary $x$ and show $P(x)$ holds. |
| **Prove $\exists x P(x)$** | Exhibit a specific, concrete example where $P(x)$ is true. |
| **Disprove $\forall x P(x)$** | Find a counterexample. |
| **Disprove $\exists x P(x)$** | Show that every possible $x$ fails. |

---

### Why Cryptographers Care
Security definitions are packed with nested quantifiers. A simplified statement might look like:
> *"For every efficient attacker $A$, there exists a negligible function $\epsilon$ such that the attack succeeds with probability at most $\epsilon$."*

* **Structure:** $\forall \text{ attacker } \exists \text{ negligible function } \dots$

Modern cryptography is essentially quantifier-heavy mathematics. Many students understand RSA computations but struggle with security proofs because they don't understand nested quantifiers.

---

### Summary
You should now understand:
* **Universal ($\forall x$):** For every $x$.
* **Existential ($\exists x$):** There exists an $x$.
* **Important Difference:** $\forall x \exists y \neq \exists y \forall x$
* **Negation Rules:** $\neg\forall \equiv \exists\neg$ and $\neg\exists \equiv \forall\neg$

---

### Exercises
1. **Translate:** Every integer has a larger integer.
2. **Translate:** There exists an integer larger than every integer.
3. **Negate:** $\forall x \exists y (x + y = 0)$
4. **Determine whether:** $\forall x \exists y (xy = 1)$ is true over the real numbers.
5. **Determine whether:** $\exists y \forall x (xy = 1)$ is true over the real numbers.

*Next is Section 1.6 — Rules of Inference, where Rosen formally develops the machinery of mathematical proofs. This section is arguably the most important proof-oriented part of Chapter 1 and is essential before we study induction, number theory, and cryptography.*


## Chapter 1.6 — Rules of Inference

This section is where logic becomes proofs. Up to now we've learned:
* Propositions
* Logical equivalences
* Predicates
* Quantifiers
* Nested quantifiers

Now we answer the question: **How do mathematicians move from known facts to new facts?** The answer is **Rules of Inference**. A proof is essentially a sequence of applications of valid rules of inference.

---

### What is an Argument?
An argument consists of:
* **Premises:** Statements assumed to be true.
* **Conclusion:** Statement derived from the premises.

**Example:**
* *Premise 1:* If it rains, the ground is wet. ($p \rightarrow q$)
* *Premise 2:* It is raining. ($p$)
* *Conclusion:* Therefore, the ground is wet. ($q$)

This is a valid argument.

#### Valid Arguments
An argument is valid if: **Whenever all premises are true, the conclusion must also be true.** > **Notice:** A valid argument can have false premises.
> * If $2=3$, then elephants can fly. ($p \rightarrow q$)
> * $2=3$. ($p$)
> * Therefore, elephants can fly. ($q$)
> 
> *Still valid.* Validity concerns the **logical structure**, not the truth of the premises.

---

### Propositional Rules of Inference

#### Rule 1: Modus Ponens
The most important inference rule.
* **Structure:**
  $p \rightarrow q$
  $p$
  $\therefore q$
* **Read:** If $p$ implies $q$, and $p$ is true, then $q$ is true.
* **Example:** If a number is divisible by 4, then it is even. 12 is divisible by 4. Therefore, 12 is even.

> **Why It Matters for Cryptography**
> Many cryptographic proofs have this form:
> * If an attacker exists, then a factoring algorithm exists.
> * An attacker exists.
> * **Therefore:** A factoring algorithm exists.

#### Rule 2: Modus Tollens
* **Structure:**
  $p \rightarrow q$
  $\neg q$
  $\therefore \neg p$
* **Read:** If $p$ implies $q$, and $q$ is false, then $p$ is false.
* **Example:** If divisible by 4, then even. 15 is not even. Therefore, 15 is not divisible by 4.
* *Note:* Modus Tollens is really just applying the contrapositive ($\neg q \rightarrow \neg p$).

#### Rule 3: Hypothetical Syllogism
* **Structure:**
  $p \rightarrow q$
  $q \rightarrow r$
  $\therefore p \rightarrow r$
* **Example:** If I study, I pass. If I pass, I graduate. Therefore, if I study, I graduate.

#### Rule 4: Disjunctive Syllogism
* **Structure:**
  $p \lor q$
  $\neg p$
  $\therefore q$
* **Example:** Either Alice knows the key or Bob knows the key. Alice does not know the key. Therefore, Bob knows the key.

#### Rule 5: Addition
* **Structure:**
  $p$
  $\therefore p \lor q$
* **Example:** Today is Monday. Therefore, today is Monday OR RSA is broken. *(Strange, but logically correct because OR requires only one side to be true).*

#### Rule 6: Simplification
* **Structure:**
  $p \land q$
  $\therefore p$ 
  *(or $\therefore q$)*
* **Example:** Alice knows the key AND Bob knows the key. Therefore, Alice knows the key.

#### Rule 7: Conjunction
* **Structure:**
  $p$
  $q$
  $\therefore p \land q$
* **Example:** Alice authenticated. Bob authenticated. Therefore, Alice authenticated AND Bob authenticated.

#### Rule 8: Resolution
One of the most important rules in computer science. It powers SAT solvers, automated theorem provers, and formal verification systems.
* **Structure:**
  $p \lor q$
  $\neg p \lor r$
  $\therefore q \lor r$
* **Example:** Alice knows the key OR Bob knows the key. Alice does not know the key OR Charlie knows the key. Therefore, Bob knows the key OR Charlie knows the key.

---

### Using Several Rules Together
**Goal:** Prove $r$

**Premises:**
1. $p \rightarrow q$
2. $q \rightarrow r$
3. $p$

**Step 1:** Use Modus Ponens on (1) and (3) to obtain $q$.
**Step 2:** Use Modus Ponens on (2) and $q$ to obtain $r$. *(Proof complete).*

---

### Rules of Inference with Quantifiers
Now we extend inference rules to predicates. These are extremely important.

#### 1. Universal Instantiation (UI)
* **Rule:** From $\forall x P(x)$, we may conclude $P(a)$ for any specific $a$.
* **Example:** Every integer is less than its successor ($\forall n (n < n+1)$). Choose $n=100$. Then $100 < 101$.

#### 2. Universal Generalization (UG)
* **Rule:** If we prove $P(x)$ for an arbitrary $x$, we may conclude $\forall x P(x)$.
* **Example:** Suppose we show $x+0=x$ for an arbitrary real number $x$. Then $\forall x (x+0=x)$.

#### 3. Existential Instantiation (EI)
* **Rule:** Given $\exists x P(x)$, we may introduce a temporary object $c$ such that $P(c)$.
* **Example:** Given "There exists a prime greater than 100," we may write "Let $p$ be such a prime" without knowing its exact value.

#### 4. Existential Generalization (EG)
* **Rule:** If $P(a)$ is true, then $\exists x P(x)$ is true.
* **Example:** Because 101 is prime, we conclude "There exists a prime greater than 100."

---

### Common Logical Fallacies
These look valid but are **wrong**.

#### Fallacy 1: Affirming the Consequent (INVALID)
* **Structure:**
  $p \rightarrow q$
  $q$
  $\therefore p$
* **Example:** If divisible by 4, then even. 6 is even. Can we conclude 6 is divisible by 4? No.

#### Fallacy 2: Denying the Antecedent (INVALID)
* **Structure:**
  $p \rightarrow q$
  $\neg p$
  $\therefore \neg q$
* **Example:** If divisible by 4, then even. 6 is not divisible by 4. Can we conclude 6 is not even? No.

---

### Why Cryptographers Care
Modern cryptography is built almost entirely on inference chains. A typical security reduction says:

> *"If attacker A exists, then algorithm B solves factoring."* ($A \rightarrow B$)
> 
> We know: Factoring cannot be solved efficiently. ($\neg B$)
> 
> Using **Modus Tollens**:
> $A \rightarrow B$
> $\neg B$
> $\therefore \neg A$
> 
> **Therefore:** An efficient attacker does not exist. 

This exact reasoning appears throughout Katz-Lindell, Goldreich, and advanced cryptographic research papers.

---

### Summary Checklist
You should now know:
* **Propositional Rules:** Modus Ponens, Modus Tollens, Hypothetical Syllogism, Disjunctive Syllogism, Addition, Simplification, Conjunction, Resolution.
* **Quantifier Rules:** Universal Instantiation, Universal Generalization, Existential Instantiation, Existential Generalization.
* **Fallacies:** Affirming the Consequent, Denying the Antecedent.

---

### Exercises
Determine which rule is being used:

1. 
$p \rightarrow q$
$p$
$\therefore q$

2. 
$p \rightarrow q$
$\neg q$
$\therefore \neg p$

3. 
$p \lor q$
$\neg p$
$\therefore q$

4. 
$\forall x P(x)$
$\therefore P(7)$

5. 
$P(101)$
$\therefore \exists x P(x)$

*Next, we move to Section 1.7 — Introduction to Proofs, where Rosen teaches how to actually write mathematical proofs: direct proofs, proof by contraposition, proof by contradiction, existence proofs, and uniqueness proofs. This is the section where you start thinking like a mathematician rather than just manipulating logic.*


## Chapter 1.7 — Introduction to Proofs

This is arguably the most important section in the entire first chapter. 
* Logic tells us what statements mean.
* Rules of inference tell us how to reason.
* Proofs are where we combine these ideas to establish mathematical truth.

For cryptography, proofs are everything. Modern cryptography is essentially a collection of security proofs.

---

### What Is a Proof?
A proof is a valid argument that establishes the truth of a mathematical statement. A proof must:
1. Start with known facts.
2. Use valid reasoning.
3. End with the desired conclusion.

**Example**
* **Claim:** If $n$ is an even integer, then $n^2$ is even.
* **We know:** $n$ is even means $n = 2k$ for some integer $k$.
* **Then:** $$n^2 = (2k)^2 = 4k^2 = 2(2k^2)$$
* **Since:** $(2k^2)$ is an integer, $n^2$ is divisible by 2.
* **Therefore:** $n^2$ is even. (Proof complete. $\square$)

---

### The Structure of Mathematical Proofs
Every proof has:
* **Hypothesis:** What is assumed.
* **Conclusion:** What must be shown.

*Example:* "If $n$ is even, then $n^2$ is even."
* **Hypothesis:** $n$ is even.
* **Conclusion:** $n^2$ is even.

---

### Direct Proof
The most common proof technique.
* **Strategy:** Assume hypothesis. Use definitions and known facts. Derive conclusion.

**Example 1: Prove the sum of two even integers is even.**
* **Step 1 (Assume):** Let $a = 2m$ and $b = 2n$, where $m$ and $n$ are integers.
* **Step 2 (Add):** $a+b = 2m + 2n = 2(m+n)$
* **Step 3 (Conclude):** Since $m+n$ is an integer, $a+b$ is divisible by 2. Therefore, $a+b$ is even. $\square$

---

### Proof by Contraposition
Sometimes proving directly is difficult. Instead, prove the contrapositive.
* **Remember:** $p \to q \equiv \neg q \to \neg p$

**Example:** Prove: *If $n^2$ is odd, then $n$ is odd.*
Direct proof is possible but awkward. Instead use the contrapositive:
* *If $n$ is even, then $n^2$ is even.*

We already proved this. Therefore the original statement is true. $\square$

> **Why Contraposition Matters**
> Cryptographic security proofs often use: *"If attack succeeds, then hard problem is solved."*
> Then prove: *"Hard problem cannot be solved."*
> Thus: *"Attack cannot succeed."* > This is contrapositive reasoning.

---

### Proof by Contradiction
One of the most powerful techniques.
* **Strategy:** Assume the statement is false. Derive a contradiction. Therefore the assumption must be wrong.

**Basic Example:** Prove there is no largest integer.
* **Assume:** $N$ is the largest integer.
* **Then:** $N+1$ is also an integer.
* **And:** $N+1 > N$. 
* **Contradiction.** Therefore, no largest integer exists. $\square$

**Famous Example: $\sqrt{2}$ is Irrational**
This is one of the most famous contradiction proofs.
* **Claim:** $\sqrt{2}$ is irrational.
* **Assume the opposite:** Suppose $\sqrt{2} = \frac{a}{b}$ where $a, b$ are integers and the fraction is in lowest terms.
* **Square both sides:** $2b^2 = a^2$.
* **Then:** $a^2$ is even, therefore $a$ is even. Let $a = 2k$.
* **Substitute:** $2b^2 = (2k)^2 \implies 2b^2 = 4k^2 \implies b^2 = 2k^2$.
* **So:** $b^2$ is even, which means $b$ is even.
* **Now:** Both $a$ and $b$ are even. But then the fraction was not in lowest terms.
* **Contradiction.** Hence, $\sqrt{2}$ is irrational. $\square$

---

### Existence Proofs
Sometimes we want to prove something exists.

**Example:** Prove there exists an even prime.
* **Give an example:** 2 is prime and even.
* **Therefore:** An even prime exists. $\square$
*(This is called a **constructive** existence proof.)*

**Nonconstructive Existence Proof:**
Sometimes we prove something exists without finding it. These appear often in advanced mathematics. Rosen introduces the idea, but later courses use it heavily.

---

### Uniqueness Proofs
Sometimes we must show:
1. Something exists.
2. It is the only one.

**Example:** Prove 0 is the unique additive identity of the integers.
* **Existence:** $a + 0 = a$ for every integer $a$. So, the additive identity exists.
* **Uniqueness:** Suppose $e$ is another additive identity. 
  * Then $e + 0 = e$ (because 0 is an identity). 
  * Also $e + 0 = 0$ (because $e$ is an identity). 
  * Hence, $e = 0$.
* **Therefore:** 0 is unique. $\square$

---

### Common Mistakes in Proofs

**Mistake 1: Checking examples only.**
* Example: $2^2 = 4$, $4^2 = 16$, $6^2 = 36$ does NOT prove "Every even number squared is even." Examples suggest truth; they do not prove it.

**Mistake 2: Assuming what you're trying to prove.**
* This is called **circular reasoning**.
* *Bad proof:* Assume $n^2$ is even because $n$ is even. (You are using the conclusion before proving it).

**Mistake 3: Using undefined statements.**
* Always use precise definitions. 
* *Example:* "Even" means $n = 2k$ for some integer $k$. Start there.

---

### Strategy for Reading Proofs
Whenever you see a theorem:
1. **Identify:** Hypothesis and Conclusion.
2. **Ask:** Which proof method is best? (Direct? Contrapositive? Contradiction? Existence? Uniqueness?)
3. **Write:** Write out every logical step. Never skip reasoning.

---

### Why Cryptographers Need Proofs
Modern cryptography is proof-based. A typical theorem looks like: 
> *"If factoring is hard, then RSA is secure."*

This is a mathematical statement requiring proof. Security is not established by testing, intuition, or examples. It is established through rigorous proofs. The proof techniques in this section appear constantly in Number Theory, Abstract Algebra, Complexity Theory, and Modern Cryptography.

---

### Summary
You should now know:
* **Direct Proof:** Assume hypothesis $\to$ derive conclusion.
* **Contrapositive Proof:** Prove $\neg q \to \neg p$ instead of $p \to q$.
* **Contradiction Proof:** Assume opposite $\to$ derive contradiction.
* **Existence Proof:** Show something exists.
* **Uniqueness Proof:** Show it exists and is the only one.

---

### Exercises
1. Prove that the sum of two odd integers is even.
2. Prove by contraposition: If $n^2$ is divisible by 3, then $n$ is divisible by 3.
3. Prove by contradiction: There is no smallest positive rational number.
4. Give a constructive proof that an odd prime exists.
5. Prove that the multiplicative identity of the real numbers is unique.

*Next is Section 1.8 — Proof Methods and Strategy, where Rosen brings together everything from Chapter 1 and teaches how mathematicians decide which proof technique to use for different kinds of statements. This section is extremely valuable because it develops mathematical problem-solving rather than just mechanics.*



## Chapter 1.8 — Proof Methods and Strategy

By now you've learned:
* Logic
* Quantifiers
* Rules of inference
* Direct proofs
* Contraposition
* Contradiction
* Existence proofs
* Uniqueness proofs

A natural question arises: **When I see a theorem, how do I know which proof method to use?** Section 1.8 answers exactly that. This section is less about new mathematics and more about mathematical thinking.

---

### The Art of Proof
Beginning students often think:
> Theorem $\rightarrow$ Apply formula $\rightarrow$ Done

Mathematics rarely works this way. Instead, the process is:
> Theorem $\rightarrow$ **Analyze structure** $\rightarrow$ **Choose proof method** $\rightarrow$ Execute proof

The hardest step is often choosing the method.

---

### Recognizing the Form of a Statement
The structure of a statement usually suggests the proof technique.

#### Type 1: Implication
Statements of the form: "If $p$, then $q$" (Symbolically: $p \rightarrow q$)
* *Examples:* * If $n$ is even, then $n^2$ is even.
  * If a number is divisible by 6, then it is divisible by 3.
* *Possible methods:* Direct proof, Contrapositive, Contradiction.

---

### When to Use Direct Proof
**Use direct proof when:** The hypothesis naturally leads to the conclusion.

**Example:** Prove: *If $n$ is even, then $n^2$ is even.*
* Start with definition: $n = 2k$
* Immediately obtain: $n^2 = 4k^2$
* Conclusion follows naturally. Direct proof is ideal.

### When to Use Contraposition
**Use contraposition when:** The conclusion is easier to negate, OR the hypothesis is difficult to use directly.

**Example:** Prove: *If $n^2$ is odd, then $n$ is odd.*
* Direct proof is awkward. 
* Instead prove the contrapositive: *If $n$ is even, then $n^2$ is even.*
* Much easier. Thus, contrapositive is preferred.

### When to Use Contradiction
**Use contradiction when:** * Negation creates a useful assumption.
* Existence or uniqueness statements appear.
* The statement says something is impossible.

**Example:** Prove: *There is no largest integer.*
* Assume $N$ is largest. Then $N+1$ exists. Contradiction.

---

### Proof Strategy Example
Consider: *If $3n+2$ is odd, then $n$ is odd.*

* **Direct Approach:** Assume $3n+2$ is odd. Need to show $n$ is odd. *(Possible but messy).*
* **Contrapositive Approach:** Prove: *If $n$ is even, then $3n+2$ is even.*
  * Let $n = 2k$.
  * Then $3n+2 = 6k+2 = 2(3k+1)$.
  * Since this is a multiple of 2, it is even. *(Much easier).*

---

### Working Backwards
A powerful technique. Suppose the goal is to show $A=B$. Ask: *"What would imply $A=B$?"* Work backward, then prove those intermediate steps.

**Example:** Prove: *$n^2-1$ is even whenever $n$ is odd.*
* **Work backwards:** $n^2-1 = (n-1)(n+1)$
* If $n$ is odd, both $n-1$ and $n+1$ are even. 
* The product of two even numbers is even. Done.

---

### Looking for Definitions
Many proofs become easy once the correct definition is used. Many beginners get stuck because they forget to start from definitions.

**Example:** Prove: *Sum of two odd integers is even.*
* **Use definition:** odd $= 2k+1$
* **Immediately:** $(2m+1) + (2n+1) = 2(m+n+1)$. 
* This is a multiple of 2, so it is even.

#### Common Proof Templates
* **Even Number:** Start with $n=2k$
* **Odd Number:** Start with $n=2k+1$
* **Divisibility:** Start with $a \mid b$, meaning $b=ak$ for some integer $k$.
* **Rational Number:** Start with $a/b$ where $a, b$ are integers and $b \neq 0$.
* **Prime Number:** Start with definition: positive divisors are only 1 and $p$.

---

### Existence Proof Strategy
Suppose a statement says: $\exists x P(x)$. There are two possibilities:
1. **Constructive:** Find $x$. 
   * *Example:* There exists an even prime. (Choose 2. Done.)
2. **Nonconstructive:** Show some $x$ must exist without explicitly finding it.

### Uniqueness Strategy
When proving uniqueness, **always do two steps:**
1. **Step 1:** Show existence.
2. **Step 2:** Assume two objects satisfy the property. Show they are equal.

*Example:* Show the additive identity is unique.
* Assume $e$ and $f$ are both identities.
* Then $e = e+f = f$.
* Hence $e=f$. Unique.

---

### Cases
Sometimes you must divide a problem into cases.

**Example:** Prove $n(n+1)$ is even.
* **Case 1 ($n$ is even):** The product of an even and anything is even.
* **Case 2 ($n$ is odd):** Then $n+1$ is even. The product is even.
* All cases covered. Therefore, the statement is true.

---

### Counterexamples
To disprove $\forall x P(x)$, you need only **one** counterexample.

**Example:** Claim: *Every prime is odd.*
* Counterexample: 2. (Done. No proof needed. One counterexample destroys a universal statement.)

#### Finding Counterexamples
When a statement seems suspicious, test small numbers and boundary values: $0, 1, -1, 2$. These often reveal flaws.

**Example:** Claim: *If $n^2$ is prime, then $n$ is prime.*
* Test $n=2$, which gives $n^2 = 4$ (not prime). The hypothesis fails.
* *Logical Subtlety:* You will eventually discover $n^2$ cannot be prime for *any* integer greater than 1. The statement is actually *vacuously true*.

---

### Forward–Backward Strategy
Expert mathematicians often use both:
* **Forward:** Start from hypothesis.
* **Backward:** Start from conclusion.
* *Meet in the middle.* This technique appears constantly in research mathematics.

---

### Why This Matters for Cryptography
Cryptographic proofs are rarely straightforward. A security theorem may require contradiction, contraposition, case analysis, quantifier manipulation, and existence arguments. 

The ability to choose the correct proof strategy is what separates someone who *knows* mathematics from someone who *can do* mathematics.

---

## End of Chapter 1 Summary

You now know:
* **Logic:** Propositions, Truth tables, Equivalences.
* **Quantifiers:** Universal, Existential, Nested quantifiers.
* **Inference:** Modus Ponens, Modus Tollens, Resolution.
* **Proofs:** Direct, Contrapositive, Contradiction, Existence, Uniqueness, Cases.
* **Strategy:** How to choose proof methods, find counterexamples, and structure arguments.

### Before Moving to Chapter 2
For cryptography, Chapter 1 is absolutely fundamental. If you are comfortable proving statements about even/odd numbers, negating quantified statements, and understanding contrapositives and contradictions, then you're ready.

Chapter 2 covers **Sets, Functions, Sequences, and Sums.** For a future cryptographer, Chapter 2 is extremely important because:
* **Functions** become cryptographic algorithms.
* **Inverses** become decryption functions.
* **One-to-one functions** become permutations.
* **Sequences** lead to probability and complexity theory.



Excellent idea. Before moving to Chapter 2, you should test whether you've actually internalized Chapter 1. For cryptography, Chapter 1 is not about memorization—it's about being able to reason formally.

Here are the 35 medium-to-hard problems covering the entire chapter, along with full solutions so you can self-check.

---

## Part A: Logic and Truth Tables

### Question 1
Construct a truth table for:
$$(p \rightarrow q) \leftrightarrow (\neg q \rightarrow \neg p)$$
Show it is a tautology.

**Solution:**

| $p$ | $q$ | $p \rightarrow q$ | $\neg q$ | $\neg p$ | $\neg q \rightarrow \neg p$ | $\leftrightarrow$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| T | T | T | F | F | T | **T** |
| T | F | F | T | F | F | **T** |
| F | T | T | F | T | T | **T** |
| F | F | T | T | T | T | **T** |

Always true. Therefore, it is a tautology.

### Question 2
Determine whether the following is a tautology:
$$(p \land q) \rightarrow p$$

**Solution:**
Whenever $(p \land q)$ is true, $p$ must be true. Hence, the implication is always true. 
**Tautology.**

### Question 3
Show that $p \oplus q$ is equivalent to:
$$(p \lor q) \land \neg(p \land q)$$

**Solution:**
XOR ($p \oplus q$) means exactly one is true. 
The second expression says:
* At least one true: $(p \lor q)$
* AND not both true: $\neg(p \land q)$

Same meaning. **Equivalent.**

### Question 4
Determine whether the following is a tautology:
$$(p \rightarrow q) \rightarrow p$$

**Solution:**
Take: $p = \text{F}, \quad q = \text{F}$
Then:
$$p \rightarrow q = \text{T}$$
and
$$\text{T} \rightarrow \text{F} = \text{F}$$
**Not a tautology.**

### Question 5
Show $p \rightarrow q$ is equivalent to $\neg p \lor q$.

**Solution:**
A truth table comparison gives identical final columns for both expressions.

---

## Part B: Logical Equivalences

### Question 6
Simplify:
$$\neg(p \lor \neg q)$$

**Solution:**
De Morgan's Law:
$$\neg p \land \neg(\neg q)$$
Double negation:
$$\boxed{\neg p \land q}$$

### Question 7
Simplify:
$$(p \land \text{T}) \lor \text{F}$$

**Solution:**
Identity laws:
$$p \land \text{T} = p$$
$$p \lor \text{F} = p$$
Answer:
$$\boxed{p}$$

### Question 8
Simplify:
$$p \lor (p \land q)$$

**Solution:**
Absorption law:
$$\boxed{p}$$

### Question 9
Show $\neg(p \land q)$ and $\neg p \lor \neg q$ are equivalent.

**Solution:**
This is exactly De Morgan's Law.

### Question 10
Convert $p \leftrightarrow q$ using only AND, OR, NOT.

**Solution:**
$$(p \rightarrow q) \land (q \rightarrow p)$$
Applying the implication law:
$$(\neg p \lor q) \land (\neg q \lor p)$$

---

## Part C: Quantifiers

### Question 11
**Translate:** Every positive integer has a larger positive integer.

**Solution:**
$$\forall n \in \mathbb{Z}^+, \exists m \in \mathbb{Z}^+ (m > n)$$

### Question 12
**Translate:** There exists a prime larger than 1000.

**Solution:**
$$\exists p (p > 1000 \land p \text{ is prime})$$

### Question 13
**Negate:** $\forall x P(x)$

**Solution:**
$$\boxed{\exists x \neg P(x)}$$

### Question 14
**Negate:** $\exists x P(x)$

**Solution:**
$$\boxed{\forall x \neg P(x)}$$

### Question 15
**Negate:** $\forall x \exists y (y > x)$

**Solution:**
$$\boxed{\exists x \forall y (y \le x)}$$

### Question 16
**Determine truth value:** $$\forall x \in \mathbb{R}, \exists y \in \mathbb{R} (x + y = 0)$$

**Solution:**
Choose $y = -x$.
**True.**

### Question 17
**Determine truth value:** $$\exists y \in \mathbb{R}, \forall x \in \mathbb{R} (x + y = 0)$$

**Solution:**
One fixed $y$ cannot work for every $x$.
**False.**

---

## Part D: Rules of Inference

### Question 18
**Identify the rule:**
* $p \rightarrow q$
* $p$
* Therefore: $q$

**Solution:**
Modus Ponens.

### Question 19
**Identify the rule:**
* $p \rightarrow q$
* $\neg q$
* Therefore: $\neg p$

**Solution:**
Modus Tollens.

### Question 20
**Identify the rule:**
* $p \lor q$
* $\neg p$
* Therefore: $q$

**Solution:**
Disjunctive Syllogism.

### Question 21
**Show argument validity:**
* $p \rightarrow q$
* $q \rightarrow r$
* $p$
* Therefore: $r$

**Solution:**
Modus Ponens on the first and third premises gives $q$. Modus Ponens again on the second premise and $q$ gives $r$. 
**Valid.**

### Question 22
**Show why this argument is invalid:**
* $p \rightarrow q$
* $q$
* Therefore: $p$

**Solution:**
Counterexample: $p = \text{F}, \quad q = \text{T}$
Premises are true, but the conclusion is false. This is the Fallacy of Affirming the Consequent.
**Invalid.**

---

## Part E: Proofs

### Question 23
**Prove:** Sum of two odd integers is even.

**Solution:**
Let $a = 2m + 1$ and $b = 2n + 1$.
Then:
$$a + b = (2m + 1) + (2n + 1) = 2m + 2n + 2 = 2(m + n + 1)$$
This is a multiple of 2, hence **even**. $\square$

### Question 24
**Prove:** Product of two odd integers is odd.

**Solution:**
$$(2m + 1)(2n + 1) = 4mn + 2m + 2n + 1 = 2(2mn + m + n) + 1$$
This is of the form $2k + 1$, hence **odd**. $\square$

### Question 25
**Prove:** Square of an even integer is even.

**Solution:**
Let $n = 2k$.
$$n^2 = (2k)^2 = 4k^2 = 2(2k^2)$$
This is a multiple of 2, hence **even**. $\square$

### Question 26
**Prove by contraposition:** If $n^2$ is odd, then $n$ is odd.

**Solution:**
**Contrapositive:** If $n$ is even, then $n^2$ is even.
We already proved this in Question 25. $\square$

### Question 27
**Prove:** If $a \mid b$ and $a \mid c$, then $a \mid (b + c)$.

**Solution:**
By definition, $b = am$ and $c = an$ for some integers $m, n$.
Then:
$$b + c = am + an = a(m + n)$$
Therefore, $a \mid (b + c)$. $\square$

### Question 28
**Prove:** Sum of an even and odd integer is odd.

**Solution:**
Let the even integer be $2m$ and the odd integer be $2n + 1$.
$$2m + (2n + 1) = 2(m + n) + 1$$
This is of the form $2k + 1$, hence **odd**. $\square$

---

## Part F: Contradiction Proofs

### Question 29
**Prove:** No largest integer exists.

**Solution:**
Assume $N$ is the largest integer.
Then $N + 1$ is an integer, and $N + 1 > N$.
**Contradiction.** $\square$

### Question 30
**Prove:** $\sqrt{2}$ is irrational.

**Solution:**
Use the standard contradiction proof.
Assume $\sqrt{2} = \frac{a}{b}$ as a rational fraction in lowest terms.
Squaring gives $2b^2 = a^2$, meaning $a^2$ is even, so $a$ is even ($a = 2k$).
Substitute to get $2b^2 = 4k^2 \implies b^2 = 2k^2$, meaning $b$ is even.
If both $a$ and $b$ are even, the fraction was not in lowest terms.
**Contradiction.** $\square$

### Question 31
**Prove:** There is no smallest positive rational number.

**Solution:**
Assume there is a smallest positive rational number $r$.
Then $\frac{r}{2}$ is also a positive rational number, and $\frac{r}{2} < r$.
**Contradiction.** $\square$

---

## Part G: Harder Mixed Problems

### Question 32
**Prove:** $n(n + 1)$ is always even.

**Solution:**
* **Case 1:** $n$ is even. An even number multiplied by anything is even.
* **Case 2:** $n$ is odd. Then $n + 1$ is even. An odd number multiplied by an even number is even.
Both cases result in an even product. $\square$

### Question 33
**Negate correctly:**
$$\forall x \exists y (x + y = 0)$$

**Solution:**
$$\boxed{\exists x \forall y (x + y \neq 0)}$$

### Question 34
**Determine whether the following is even:**
$$\forall n \in \mathbb{Z} (n^2 + n)$$

**Solution:**
Notice that $n^2 + n = n(n + 1)$.
These are consecutive integers. One of them must be even. Therefore, their product is even.
**True.** $\square$

### Question 35 (Challenge)
**Prove:** If $a + b$ is odd, then one of $a, b$ is even and the other is odd.

**Solution:**
Let's look at the possible parity combinations:

| $a$ | $b$ | $a + b$ |
| :---: | :---: | :---: |
| Even | Even | Even |
| Odd | Odd | Even |
| **Even** | **Odd** | **Odd** |
| **Odd** | **Even** | **Odd** |

For the sum to be odd, only the last two rows work. Hence, exactly one is even and one is odd. $\square$

---

## Cryptography Readiness Check
If you can solve Questions **15, 17, 22, 26, 30, 33, and 35** without looking at the solutions, then your Chapter 1 foundation is strong enough to move into Chapter 2, later tackle Rosen Chapter 4 (Number Theory & Cryptography), and eventually Katz & Lindell security proofs. These questions test the exact logical skills used repeatedly in modern cryptography.