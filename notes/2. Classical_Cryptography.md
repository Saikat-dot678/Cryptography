# 🔐 Classical Cryptography

> A deep dive into the origins of cryptography, the evolution of ciphers, and the lessons that shaped modern cryptographic systems.

---

## 📚 Topics Covered

- Caesar Cipher
- Monoalphabetic Substitution Cipher
- Frequency Analysis
- Vigenère Cipher
- Kasiski Examination
- Transposition Ciphers
- Hill Cipher
- Enigma Machine
- Classical Cryptanalysis
- Key Lessons for Modern Cryptography

---

Excellent. If your goal is to eventually understand RSA, ECC, AES, post-quantum cryptography, cryptanalysis, and even do research in cryptography, then **Classical Cryptography is not just history**. It teaches the exact problems that modern cryptography was designed to solve.

Think of classical cryptography as learning mechanics before studying quantum physics.


---


# Classical Cryptography

Before computers existed, encryption had to be done:

* by hand
* with paper
* mechanical devices

Because computation was limited, ciphers were relatively simple.

Yet almost every modern cryptographic idea originates here:

* substitution
* permutation
* confusion
* diffusion
* key spaces
* brute force attacks
* statistical attacks
* cryptanalysis


---


# The Fundamental Problem

Suppose Alice wants to send:

```text
ATTACKATDAWN
```

to Bob.

An attacker (Eve) can read every message sent.

How can Alice transform the message so Eve cannot understand it?

This question gave birth to cryptography.


---


# The Earliest Idea: Substitution

The simplest idea is:

> Replace one symbol with another.

Instead of sending:

```text
HELLO
```

send:

```text
KHOOR
```

Only Bob knows how the replacement works.

This leads us to the first famous cipher.


---


# Caesar Cipher

Named after:

Julius Caesar

who reportedly used it for military communication.


---


## Core Idea

Shift every letter by a fixed amount.

Suppose:

```text
Shift = 3
```

Alphabet:

```text
ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

After shifting:

```text
DEFGHIJKLMNOPQRSTUVWXYZABC
```

So:

```text
A → D
B → E
C → F
```


---


# Example Encryption

Plaintext:

```text
HELLO
```

Shift each letter by 3:

```text
H → K
E → H
L → O
L → O
O → R
```

Ciphertext:

```text
KHOOR
```


---


# Mathematical Representation

Assign numbers:

```text
A=0
B=1
...
Z=25
```

Encryption:


$$
E(x)=(x+k)\bmod 26
$$

where:

* x = plaintext letter
* k = secret shift


---


Example:


$$
H=7
$$

Shift = 3


$$
(7+3)\mod 26=10
$$

10 corresponds to K.


---


# Why Modulo?

Suppose:

```text
Z = 25
```

Shift by 3:


$$
25+3=28
$$

But alphabet only has 26 letters.

So:


$$
28 \mod 26=2
$$

Which corresponds to:

```text
C
```

Thus:

```text
Z → C
```

This is actually your first encounter with modular arithmetic, one of the most important concepts in all cryptography.


---


# Key Space

How many possible keys exist?

Possible shifts:

```text
1 to 25
```

Only:


$$
25
$$

keys.

That is tiny.


---


# Brute Force Attack

An attacker simply tries:

```text
Shift 1
Shift 2
Shift 3
...
Shift 25
```

One result immediately becomes readable English.

Thus Caesar cipher is insecure.


---


# Important Lesson #1

Security must not depend on a small key space.

Modern cryptography uses key spaces like:

AES-128:


$$
2^{128}
$$

possible keys.

That's approximately:


$$
340,282,366,920,938,463,463,374,607,431,768,211,456
$$

keys.

Brute force becomes impossible.


---


# Monoalphabetic Substitution Cipher

People quickly realized Caesar cipher was weak.

So they expanded the idea.

Instead of shifting:

Create a completely random alphabet mapping.

Example:

```text
A → Q
B → W
C → E
D → R
...
```


---


# Example

Normal alphabet:

```text
ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

Secret alphabet:

```text
QWERTYUIOPASDFGHJKLZXCVBNM
```

Message:

```text
HELLO
```

might become:

```text
ITSSG
```


---


# Key Space Explosion

Now the key is an entire alphabet arrangement.

Number of possibilities:


$$
26!
$$

which equals:


$$
403291461126605635584000000
$$

This is enormously larger than Caesar's 25 keys.


---


# At First Glance It Looks Secure

Even trying all keys is impossible.

Yet it is still breakable.

Why?

Because language has patterns.

This leads to one of the most important concepts in cryptanalysis.


---


# Frequency Analysis

Every language has statistical structure.

In English:

Most common letters:

```text
E
T
A
O
I
N
```

Rare letters:

```text
Q
X
Z
J
```


---


# Example

Suppose attacker intercepts:

```text
XKQMXTXMXQX
```

and notices:

```text
X appears most frequently
```

Likely:

```text
X = E
```

because E is most common English letter.


---


# Why This Works

Human language is NOT random.

Consider English:

```text
THE
AND
THAT
ING
TION
```

appear repeatedly.

Patterns leak information.


---


# Big Lesson #2

Even if brute force is impossible,

statistical properties can break encryption.

Modern ciphers are designed to destroy these patterns.

This idea eventually became:

> Confusion and Diffusion

which you'll see later in DES and AES.


---


# Digraph Frequencies

Attackers don't stop with single letters.

They examine pairs:

```text
TH
HE
IN
ER
AN
RE
```


---


# Trigraph Frequencies

Three-letter patterns:

```text
THE
ING
AND
ION
```


---


# Cryptanalysis Begins

This was the birth of scientific code breaking.

Instead of:

```text
Try every key
```

people started using:

* statistics
* mathematics
* probability

This eventually evolved into modern cryptanalysis.


---


# Vigenère Cipher

For centuries people thought:

"Frequency analysis breaks substitution because every E always becomes the same symbol."

Solution:

Change the substitution continuously.


---


## Core Idea

Use a keyword.

Suppose keyword:

```text
KEY
```

Message:

```text
HELLOWORLD
```

Repeat key:

```text
KEYKEYKEYK
```

Now each position uses a different shift.


---


# Encryption

```text
H + K
E + E
L + Y
L + K
...
```

Each letter is shifted differently.


---


# Why This Was Revolutionary

In Caesar cipher:

```text
E always becomes H
```

In Vigenère:

```text
E might become H
E might become X
E might become P
```

depending on position.

Frequency analysis becomes much harder.


---


# Polyalphabetic Encryption

This is called:

> Polyalphabetic Substitution

Multiple alphabets instead of one.

A major milestone in cryptography.


---


# Why It Was Called "Le Chiffre Indéchiffrable"

French cryptographers called it:

> The Indecipherable Cipher

because it resisted known attacks for centuries.


---


# How It Was Broken

Eventually cryptanalysts discovered:

the keyword repeats.

Repeated keys create repeated statistical patterns.


---


# Kasiski Examination

Named after:

Friedrich Kasiski

Idea:

Repeated plaintext segments create repeated ciphertext segments.

From spacing between repetitions, attacker can estimate:

* keyword length

Once keyword length is known:

Cipher breaks into several Caesar ciphers.

Then frequency analysis works again.


---


# Big Lesson #3

Patterns are the enemy.

Every successful attack so far exploits patterns.

Modern ciphers aim to eliminate all detectable structure.


---


# Transposition Ciphers

Until now:

Letters changed.

Now consider:

Letters stay the same,
positions change.

Example:

```text
HELLOWORLD
```

Arrange in rows:

```text
H E L L O
W O R L D
```

Read columns:

```text
HWEOOLRLLD
```


---


# Important Observation

Frequency analysis fails.

Why?

Because letters themselves did not change.

Counts remain identical.


---


# Yet It Is Still Weak

Because:

language structure survives.

Words and patterns partially remain.


---


# Huge Lesson #4

Substitution changes symbols.

Transposition changes positions.

Modern ciphers use BOTH.

AES and DES heavily combine:

* substitution
* permutation

This idea started here.


---


# Hill Cipher

This is where cryptography first becomes mathematical.

Developed by:

Lester S. Hill


---


Instead of shifting letters:

Represent letters as vectors.

Example:

```text
A=0
B=1
...
Z=25
```

Message:

```text
HI
```

becomes:


$$
\begin{bmatrix}
7\
8
\end{bmatrix}
$$

---


Now multiply by a matrix:


$$
K=
\begin{bmatrix}
3&3\
2&5
\end{bmatrix}
$$

Then:


$$
C=K \cdot P \mod 26
$$

This produces ciphertext.


---


# Why Hill Cipher Matters

For the first time:

Cryptography uses:

* vectors
* matrices
* linear algebra

These ideas appear again in:

* AES
* coding theory
* post-quantum cryptography


---


# Weakness

Linear systems have structure.

Enough plaintext/ciphertext pairs allow solving the equations.


---


# Big Lesson #5

Linearity often creates vulnerabilities.

Modern ciphers intentionally introduce nonlinearity.


---


# The Enigma Machine

This was the most famous classical cipher system.

Used by:

Nazi Germany

during WWII.


---


Enigma combined:

* substitution
* rotation
* changing alphabets
* mechanical state

Every keypress changed future encryption.

This was a massive leap beyond simple ciphers.


---


# Why Enigma Was Powerful

The encryption changed continuously.

Even:

```text
AAAAA
```

might encrypt as:

```text
QWERTY
```

all different letters.

This defeated traditional frequency analysis.


---


# The Weaknesses

Not mathematics.

Implementation and design flaws.

Examples:

A letter could never encrypt to itself.

So:

```text
A ≠ A
B ≠ B
...
```

This leaked information.


---


# The Birth of Modern Cryptanalysis

At places like:

Bletchley Park

cryptanalysts built machines to attack Enigma.

Key figures included:

Alan Turing

and many others.


---


# Why Classical Cryptography Matters Today

Every modern cipher still fights the same enemies:

1. Brute force
2. Statistical attacks
3. Pattern leakage
4. Structural weaknesses
5. Key recovery attacks

The solutions evolved, but the problems remain identical.


---


# The Five Biggest Lessons From Classical Cryptography

### Lesson 1

Large key spaces are necessary.

(Caesar failed.)


---


### Lesson 2

Language statistics leak information.

(Monoalphabetic substitution failed.)


---


### Lesson 3

Repeated patterns leak information.

(Vigenère failed.)


---


### Lesson 4

Substitution alone is insufficient.

(Need permutations too.)


---


### Lesson 5

Linearity is dangerous.

(Hill cipher weaknesses.)


---


These five lessons directly lead to the design philosophy behind DES, AES, stream ciphers, RSA padding schemes, and modern cryptography.

The next topic should be **Modular Arithmetic**, where we start the mathematical foundation. This is the point where cryptography changes from historical ciphers to the mathematics behind RSA, Diffie-Hellman, ECC, and post-quantum systems. We can go as deep as a university number theory course if that's your goal.
