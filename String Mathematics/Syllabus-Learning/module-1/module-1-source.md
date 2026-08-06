---
title: "String Mathematics — Module 1"
subtitle: "Foundations: Strings, Trees, the Root, and the Factorial"
author: "Prime Framework — Syllabus-Learning Series"
date: "Module 1 of the String Mathematics syllabus — Version 6"
---

# Module 1 — Foundations

## Strings, String Trees, the Root, and the Factorial

**Version 6.** See §16 for the revision history.

---

# 0. How to Use This Module

## 0.1 Who this is for

This module assumes **no mathematics beyond a first course in high-school algebra**. If you can square a number, subtract one number from another, and read a table, you have everything you need for §1 through §8.

Two sections use tools from later in high school and are clearly marked: §9.5 uses the **binomial theorem**, and §9.6 uses **inclusion–exclusion** — a counting principle, and a genuine step beyond arithmetic, so it is worked out in full at $k=2$ before being used in general. Two short asides mention calculus (§9.8, §12.3); both are marked as asides and **nothing depends on them.**

> ### ⚠ The hard part of this module is not the algebra. It is §2.
> **Two readers tested this document, from very different backgrounds. Both went back and re-read inside §2. Neither re-read a line of §9.5 for its algebra** — and every other place either of them went back turned out, on inspection, to be a **writing** problem rather than a mathematics one: a lemma left unstated, a citation loop, a compressed argument, an aside that broke a promise made in this very section.
>
> §2 presents a **six-position symbol** — a depth, a core letter, two independent superscripts, a pre-superscript and an index — **before any mathematics has been done at all**, and so before you have anything to attach it to. That is a **notation load**, not an algebra load, and it is the genuine difficulty spike in this module.
>
> **How to read it:** skim §2 once, do not try to memorise it, and **come back to it after §8.** Everything from §3 to §8 can be followed with only three symbols — $P$ for the Prime String, $B$ for the Base String, and $jS$ for the $j$-th substring. **§2 is a reference section, and it is placed first for lookup, not because it must be absorbed first.** You can skip them on a first reading and lose nothing but the reason the main result is *guaranteed* rather than merely observed.

## 0.2 What you will be able to do at the end

By the end of this module you will be able to:

1. Write down the **Prime String**, **Base String**, and **substrings** of a numerical sequence using correct notation.
2. Build a complete **String Tree** and identify its **Root String** and **Terminator String**.
3. Explain — and prove, two different ways — why the Root of a polynomial String Tree is a **factorial**.
4. Take an unfamiliar sequence of numbers, difference it down to its Root, and read off the **degree** and **leading coefficient** of the polynomial that generated it, without ever being told the formula.
5. Recognise why the **Comparative Split** keeps sign and magnitude on separate axes, and what breaks if you do not.
6. Distinguish a **check** from a **proof**, and recognise when two checks are secretly the same check.

## 0.3 A note on how this document treats claims

Every numerical result in this module has been checked by hand. Where a statement is a **theorem** — true for all cases, with a proof — it is labelled as such. Where a statement is an **observation** — a pattern seen in examples — it is labelled as that instead, even when the pattern looks overwhelming.

That distinction is not pedantry. §9.2 and §9.3 show **eleven** confirmations of a single result, by two different computational methods. §9.4 then explains why eleven confirmations, on their own, would still not have been enough to establish it.

**Learning where the line falls between "checked" and "proved" — and learning when two checks are really one check wearing two hats — are among the goals of this module.** §9.7 is devoted entirely to the second point.

---

# 1. What String Mathematics Is

Most of school mathematics studies a sequence by looking at its **formula**. String Mathematics studies a sequence by looking at its **family**.

Given any sequence of numbers, we can generate a second sequence from the relationships between its neighbouring terms. From that second sequence we can generate a third, and so on. The original sequence together with all of its descendants forms a structure — and it is that structure, not any single sequence within it, that the theory is about.

> **The central idea:** a sequence tells you *what the numbers are*. Its family of derived sequences tells you *what kind of object produced them*.

The remarkable thing — and the destination of this module — is that for an enormous class of sequences, this descent **terminates**, and the value it terminates at is a **factorial**. The factorial is not put in by hand. It falls out of the bookkeeping.

---

# 2. Nomenclature and Notation Structure

Before any mathematics, the symbols. String Mathematics uses a compact notation that carries four separate pieces of information at once, and reading it fluently makes everything afterwards easier.

## 2.1 The anatomy of a string symbol

The general form of a string symbol is:

$$ {}^{X}\!jS^{\,k\,|\,f}_{\;n} $$

Each position means something specific:

| Position | Symbol | Name | What it tells you |
|---|---|---|---|
| Leading number | $j$ | **Lineage depth** | How many generations below the Base String this string sits |
| Core letter | $S$ | **String** | The object itself |
| Superscript left | $k$ | **Order** | The power each Prime value is raised to: $B_n = (P_n)^k$ |
| Superscript right | $f$ | **Prime-generating function** | The rule that generates the Prime String |
| Subscript | $n$ | **Index** | Which term of the string you are looking at |
| Pre-superscript | $X$ | **Kind** | `D` for Direct, `C` for Comparative (omitted when clear) |

So the symbol $2S^{3|f}_{4}$ reads:

> *"the term at index 4, of the second substring, of the Base String of order 3, built on the Prime String generated by $f$."*

**The English runs in the opposite direction to the symbol, so read them against each other the first time.** The symbol puts depth first and index last; the sentence starts at the index and works outward:

| Phrase in the sentence | Comes from |
|---|---|
| "the term at index 4" | the **subscript** $n$ |
| "of the second substring" | the **leading number** $j$ |
| "of the Base String of order 3" | the **left superscript** $k$ |
| "generated by $f$" | the **right superscript** |

**Note carefully that the symbol carries $k$ and $f$ separately.** The order and the generating function are independent pieces of information. Changing $k$ moves you to a different Base String *over the same Prime String*; changing $f$ moves you to a different Prime String entirely. §10 depends on keeping these apart.

## 2.2 The three named strings

Three strings have their own symbols, because they are referred to constantly:

| Symbol | Name | Definition |
|---|---|---|
| $P^{f}$ | **Prime String** | The generating sequence: a seed value and a rule $f$ applied repeatedly |
| $B^{\,k\,|\,f}$ | **Base String** | Each Prime value raised to the $k$-th power: $B_n = (P_n)^k$ |
| $jS^{\,k\,|\,f}$ | **Substring** | A child string, built from relationships between adjacent terms of its parent |

**Two ways of writing the same thing.** When a string is being *evaluated* at an index it is often clearer to write the index in parentheses, function-style: $B^{2}(4)$ means exactly what $B^{2\,|\,f}_{4}$ means. **These are the same object in two notations, not two objects** — the parenthesised form is used wherever the subscript would be hard to read.

**Read it concretely.** $B^{2}(4)$ means: take the term at **index 4** of the Prime String, and square it. With the regular whole-integer Prime String that term is $4$, so $B^{2}(4) = 16$.

**Index, not position.** Because indexing starts at $n = 0$ (§2.4), "index 4" is the *fifth* term written down. The phrase "the 4th term" is ambiguous in ordinary English and is avoided throughout this syllabus — always say **index**.

## 2.3 The indexing convention

The Base String is the substring of depth zero:

$$ 0S^{\,k\,|\,f} = B^{\,k\,|\,f} $$

This is a convention, not a result, but it is a useful one: it lets us talk about "the $j$-th substring" without treating the Base String as a special case. The lineage then reads as a single chain:

$$ B^{\,k\,|\,f} \;\to\; 1S^{\,k\,|\,f} \;\to\; 2S^{\,k\,|\,f} \;\to\; 3S^{\,k\,|\,f} \;\to\; \cdots $$

This convention also pays off at an edge case: see §9.2.1, where the Root of a String Tree turns out to be the Base String itself.

## 2.4 Working conventions

Four conventions are in force throughout this syllabus:

- **Indexing begins at $n = 0$** unless explicitly stated otherwise.
- **The function $f$ belongs to the Prime String** and is applied recursively.
- **The order $k$ belongs to the Base operation**, applied to each Prime value individually.
- **The depth $j$ counts substring generations** beneath the Base String.

---

# 3. The Prime String

## 3.1 Definition

A **Prime String** is a starting value together with a rule for producing the next value from the current one:

$$ P^{f} = \left(P_0,\; f(P_0),\; f(f(P_0)),\; f(f(f(P_0))),\; \ldots \right) $$

Equivalently, and more usefully in practice:

$$ P_{n+1} = f(P_n) $$

The Prime String is the raw material. Everything else in the theory is built on top of it.

## 3.2 The standard Prime String

Throughout this module, unless stated otherwise, we use the simplest possible choice — start at zero and add one:

$$ P_0 = 0, \qquad f(x) = x + 1 $$

$$ P^{f} = (0,\; 1,\; 2,\; 3,\; 4,\; 5,\; 6,\; \ldots) $$

This is called the **regular whole-integer Prime String**.

## 3.3 Other Prime Strings

The definition permits any rule at all. Three worth meeting now:

| Rule $f$ | Seed | Prime String | Name |
|---|---|---|---|
| $x + 1$ | 0 | $0, 1, 2, 3, 4, 5, \ldots$ | Regular whole-integer |
| $x + d$ | 0 | $0, d, 2d, 3d, 4d, \ldots$ | Arithmetic, step $d$ |
| $2x$ | 1 | $1, 2, 4, 8, 16, 32, \ldots$ | Geometric, ratio 2 |

The third one behaves completely differently from the first two once we start differencing it, and that difference is the subject of Module 2.

---

# 4. The Base String

## 4.1 Definition

The **Base String** applies an operation of order $k$ to every term of the Prime String, one term at a time:

$$ B^{\,k\,|\,f} = \left( (P_0)^k,\; (P_1)^k,\; (P_2)^k,\; \ldots \right) $$

The operation is applied **pointwise** — each term is transformed on its own, with no reference to its neighbours. This is what distinguishes the Base operation from everything that follows: substrings look *sideways* at neighbours, the Base operation looks only *down* at the single value beneath it.

## 4.2 The Standard Power Base

When the Base operation is exponentiation **and** the Prime String is the regular whole-integer string, we get the case that runs through this entire module:

$$ B^{\,k\,|\,f}_n = n^k $$

This pairing has a name — the **Standard Power Base** — and the name covers *both* conditions at once. That matters in §10.

For $k = 3$:

$$ B^{\,3\,|\,f} = (0,\; 1,\; 8,\; 27,\; 64,\; 125,\; 216,\; \ldots) $$

These are the cubes. Nothing more complicated is required for anything that follows.

## 4.3 Worked construction

To be completely explicit, here is the construction of $B^{3|f}$ from the ground up:

| $n$ | Prime value $P_n$ | Base operation | Base value $B_n$ |
|---|---|---|---|
| 0 | 0 | $0^3$ | 0 |
| 1 | 1 | $1^3$ | 1 |
| 2 | 2 | $2^3$ | 8 |
| 3 | 3 | $3^3$ | 27 |
| 4 | 4 | $4^3$ | 64 |
| 5 | 5 | $5^3$ | 125 |

---

# 5. Substrings

## 5.1 Definition

A **substring** is a child string generated from relationships between values of its parent string. The leading integer $j$ identifies the substring's **depth**, or **lineage**, beneath the Base String.

Substrings come in two kinds, and the distinction is structural rather than cosmetic.

## 5.2 Direct Substrings

A **Direct Substring** applies a *unary* function — a function of one input — to a single value of the parent, at the same index:

$$ {}^{D}\!jS^{\,k\,|\,f}_n = g\left((j-1)S^{\,k\,|\,f}_n\right) $$

Here $g$ is the direct function. Examples include negation, squaring, absolute value, or any other single-input operation. When $g$ is the identity function, the child simply copies the parent:

$$ g(x) = x \quad\Longrightarrow\quad {}^{D}\!jS^{\,k\,|\,f}_n = (j-1)S^{\,k\,|\,f}_n $$

Direct substrings do not change the *length* of the string, and they do not compare anything. They re-express each value in place.

> **⚠ Direct Substrings do not count toward lineage depth in the Root Theorem, and here is why the distinction is needed.**
> A Direct Substring adds a generation but **reduces no degree** — with $g$ the identity it does not change the values at all. Insert one partway down a $k = 3$ tree and nothing changes numerically, yet a generation has been added, so the constant row would now sit at "depth 4" while $k$ is still 3.
>
> **Throughout §8–§11, "depth" means the number of *comparative difference* generations.** Direct Substrings are re-expressions within a level, not descents to a new one. *This gap was found by a reader working the definitions against each other rather than reading them in sequence.*

## 5.3 Comparative Substrings

A **Comparative Substring** applies a *relationship function* to two or more values of the parent. The most common case compares adjacent values:

$$ {}^{C}\!jS^{\,k\,|\,f}_n = h\left((j-1)S^{\,k\,|\,f}_n,\; (j-1)S^{\,k\,|\,f}_{n+1}\right) $$

Here $h$ is the comparative relationship. It may be any operation taking two or more inputs:

| Relationship | Definition |
|---|---|
| **Difference** | $h(a,b) = b - a$ |
| **Sum** | $h(a,b) = a + b$ |
| **Product** | $h(a,b) = ab$ |
| **Ratio** | $h(a,b) = b / a$ |

**Unless stated otherwise, "substring" in this module means the comparative substring under difference,** $h(a,b) = b - a$. This is by far the most important case and the one that produces the results in §8 and §9.

Note that a comparative substring is **one term shorter** than its parent, because $N$ values have only $N-1$ adjacent pairs. This shortening is what makes the descent finite and is worth watching in every table in this module.

## 5.4 Worked example: the first substring of the cubes

Take $B^{3|f} = (0, 1, 8, 27, 64, 125)$ and apply $h(a,b) = b - a$ to each adjacent pair:

| Pair | Calculation | Result |
|---|---|---|
| $(0, 1)$ | $1 - 0$ | 1 |
| $(1, 8)$ | $8 - 1$ | 7 |
| $(8, 27)$ | $27 - 8$ | 19 |
| $(27, 64)$ | $64 - 27$ | 37 |
| $(64, 125)$ | $125 - 64$ | 61 |

$$ 1S^{\,3\,|\,f} = (1,\; 7,\; 19,\; 37,\; 61) $$

Six values in, five values out.

---

# 6. The Comparative Split and the Principle of Absolute Differences

## 6.1 Definition

A **Comparative Split Substring** is a comparative form in which the result is stored in **separated components**, rather than being combined into a single number. The standard split is sign and magnitude:

$$ [\;\text{sign}\;|\;\text{magnitude}\;] $$

The magnitude is an **absolute difference** — always zero or positive. The direction of the comparison is recorded separately, on its own axis.

## 6.2 Worked example

Take the parent string $(4,\; 1,\; 7)$ and compare adjacent values by difference:

| Pair | Signed difference | Split form |
|---|---|---|
| $(4, 1)$ | $1 - 4 = -3$ | $[-\;|\;3]$ |
| $(1, 7)$ | $7 - 1 = +6$ | $[+\;|\;6]$ |

$$ (4,\; 1,\; 7) \;\longrightarrow\; [-\,|\,3],\; [+\,|\,6] $$

## 6.3 Why the sign must have its own axis

At first glance the split looks like a formatting choice — the same information, written differently. It is not. **Discarding the sign channel destroys information that cannot be recovered.**

Consider what happens if we keep only the magnitudes, $(3, 6)$, and try to reconstruct the parent. All of the following produce exactly those magnitudes:

- $(4,\; 1,\; 7)$
- $(4,\; 7,\; 13)$
- $(0,\; 3,\; 9)$
- $(10,\; 7,\; 1)$

The magnitudes alone cannot distinguish them. With the sign channel retained, the reconstruction is unique given a starting value.

> ### The principle of absolute differences
> **A comparison has two independent pieces of information: how far, and which way.** The magnitude axis carries the first. The sign axis carries the second. **A magnitude-only difference erases the second, and the erasure is irreversible.**

## 6.4 A warning worth remembering

There is a further reason the sign axis matters, and it is worth stating early because it prevents a genuine misunderstanding.

**Iterating absolute differences while discarding the sign is not this theory.** It is a different construction with completely different behaviour — one that tends to collapse toward repetition and zeros almost regardless of what it started from. The lineages studied in this module descend in an orderly, degree-reducing way precisely *because* the sign information is preserved.

**The Comparative Split is what keeps the descent faithful.** It is not decoration on top of the difference operation; it is what allows the difference operation to be run backwards.

---

# 7. The String Tree

## 7.1 Definition

> ### String Tree
> **The complete family of strings generated from a single Prime String: the Prime String itself, the Base String built from it, and every substring child descending beneath them.**

The String Tree is the object of study. Individual strings within it are views; the tree is the thing.

## 7.2 The shape of the tree

For the standard power base, the tree is a simple descending ladder, each rung one term shorter than the one above:

```
        P^f      0    1    2    3    4    5        (Prime String)
                 |    |    |    |    |    |
                 v    v    v    v    v    v
   B^{3|f}       0    1    8   27   64  125        (Base String,  0S)
                   \  /  \  /  \  /  \  /
   1S^{3|f}         1    7   19   37   61          (first substring)
                      \  /  \  /  \  /
   2S^{3|f}            6   12   18   24            (second substring)
                         \  /  \  /
   3S^{3|f}               6    6    6              (ROOT STRING)
                            \  /
   4S^{3|f}                  0    0                (TERMINATOR STRING)
```

Two features of this picture matter:

- **The vertical arrows** from Prime to Base are the *pointwise* Base operation — each value transformed alone.
- **The diagonal joins** below that are the *comparative* substring operation — each value born from a pair.

## 7.3 Reading the tree

A String Tree is read **downward** to analyse and **upward** to reconstruct. Reading down, each generation strips away one layer of structure. Reading up, each generation restores it — provided you have kept the sign channel (§6) and one anchor value per level.

---

# 8. The Root String and the Terminator String

## 8.1 Definitions

For a polynomial String Tree, the descent does not continue forever. It reaches a level where every value is the same, and then a level where every value is zero.

> ### Root String
> **The substring at which the descent becomes constant.** Written $R^{k}$.

> ### Terminator String
> **The substring immediately beneath the Root, in which every value is zero.**

For the standard power base of order $k$:

$$ kS^{\,k\,|\,f} = k! \qquad \text{(the Root String — a constant string)} $$

$$ (k+1)S^{\,k\,|\,f} = 0 \qquad \text{(the Terminator String)} $$

## 8.2 The canonical example — the cubic String Tree

| Level | Notation | Values |
|---|---|---|
| Base String | $B^{\,3\,|\,f}$ | $0,\; 1,\; 8,\; 27,\; 64,\; 125,\; \ldots$ |
| First Substring | $1S^{\,3\,|\,f}$ | $1,\; 7,\; 19,\; 37,\; 61,\; \ldots$ |
| Second Substring | $2S^{\,3\,|\,f}$ | $6,\; 12,\; 18,\; 24,\; \ldots$ |
| **Root String** | $3S^{\,3\,|\,f}$ | $\mathbf{6,\; 6,\; 6,\; 6,\; \ldots}$ |
| **Terminator String** | $4S^{\,3\,|\,f}$ | $0,\; 0,\; 0,\; 0,\; \ldots$ |

The Root value is $6$. And $6 = 3!$.

**The order of the Base operation was 3. The depth at which the descent went constant was 3. The constant it went to was 3 factorial.** All three numbers are the same $k$, and that is not a coincidence.

---

# 9. The Root Theorem

## 9.1 Statement

> ### The Root Theorem
> For the Standard Power Base of order $k$:
> $$ kS^{\,k\,|\,f} = k! \qquad\text{and}\qquad (k+1)S^{\,k\,|\,f} = 0 $$
> **The Root String of a polynomial String Tree of order $k$ is the constant string $k!$, and it is reached at depth exactly $k$.**
>
> **This holds for every non-negative integer $k$, without exception and without additional hypotheses.**
>
> **And the fence is real, not decorative.** "Without exception" ranges over the **non-negative integers only**. There is no terminating descent for $n^{-1}$ or $n^{1/2}$: neither is a polynomial, so neither has a degree for the differencing to reduce, and the descent runs forever. See Exercise 5 for what a non-terminating descent looks like.

## 9.2 The evidence, part one — String Trees built by hand

Every value below was computed by hand and every level is exact.

### 9.2.1 The edge case: $k = 0$

Start here, because it is the case most likely to break a general claim.

With $k = 0$, the Base operation is $n^0 = 1$, so the Base String is constant from the outset:

```
B     1    1    1    1    1    1        <- ROOT = 1 = 0!  (at depth 0)
1S       0    0    0    0    0          <- TERMINATOR
```

**The descent has no work to do.** The Root is the Base String itself, reached at depth $0$, with value $1$. And $0! = 1$.

This is a genuine test rather than a formality. A claim of the form "the Root is $k!$ at depth $k$" could easily have failed at the one value of $k$ where no differencing occurs at all. **It does not fail.** The indexing convention $0S = B$ from §2.3 is exactly what makes the statement come out right here.

### 9.2.2 $k = 1$ through $k = 6$

```
k = 1
B     0    1    2    3    4    5
1S       1    1    1    1    1        <- ROOT = 1 = 1!
2S          0    0    0    0
```

```
k = 2
B     0    1    4    9   16   25
1S       1    3    5    7    9
2S          2    2    2    2          <- ROOT = 2 = 2!
3S             0    0    0
```

```
k = 3
B     0    1    8   27   64  125
1S       1    7   19   37   61
2S          6   12   18   24
3S             6    6    6            <- ROOT = 6 = 3!
4S                0    0
```

```
k = 4
B       0     1    16    81   256   625  1296  2401
1S         1    15    65   175   369   671  1105
2S           14    50   110   194   302   434
3S              36    60    84   108   132
4S                 24    24    24    24   <- ROOT = 24 = 4!
```

```
k = 5
B        0      1     32    243   1024   3125   7776  16807  32768
1S          1     31    211    781   2101   4651   9031  15961
2S            30    180    570   1320   2550   4380   6930
3S              150    390    750   1230   1830   2550
4S                 240    360    480    600    720
5S                    120    120    120    120   <- ROOT = 120 = 5!
```

```
k = 6
B          0        1       64      729     4096    15625    46656   117649   262144   531441  1000000
1S             1       63      665     3367    11529    31031    70993   144495   269297   468559
2S                62      602     2702     8162    19502    39962    73502   124802   199262
3S                   540     2100     5460    11340    20460    33540    51300    74460
4S                      1560     3360     5880     9120    13080    17760    23160
5S                          1800     2520     3240     3960     4680     5400
6S                               720      720      720      720      720   <- ROOT = 720 = 6!
```

### 9.2.3 A useful property of these tables

**The descent is self-checking.** A single arithmetic error anywhere in a table propagates downward and destroys the constancy of the bottom row. When five or six values at the Root level come out identical, that is strong evidence that every calculation above them is correct.

This is worth teaching as a habit: **the Root row is its own error detector.**

## 9.3 The evidence, part two — a genuinely different computation

Building more tables would test the same claim **the same way**. If the tabular method contained a systematic misunderstanding, repeating it at $k = 7$ would reproduce the misunderstanding rather than expose it.

So the next four cases use a completely different route. Instead of stepping down the tree one level at a time, the whole descent is collapsed into a single sum (this formula is derived in §12.1):

$$ k! \;=\; \sum_{j=0}^{k} (-1)^{\,k-j} \binom{k}{j}\, j^{\,k} $$

No tree is constructed. No intermediate substring is ever written down.

```
k = 7
    0 + 7 - 2,688 + 76,545 - 573,440 + 1,640,625 - 1,959,552 + 823,543
                                                    = 5,040  =  7!   OK
```

```
k = 8
    0 - 8 + 7,168 - 367,416 + 4,587,520 - 21,875,000
      + 47,029,248 - 46,118,408 + 16,777,216
                                                   = 40,320  =  8!   OK
```

```
k = 9
    0 + 9 - 18,432 + 1,653,372 - 33,030,144 + 246,093,750
      - 846,526,464 + 1,452,729,852 - 1,207,959,552 + 387,420,489
                                                  = 362,880  =  9!   OK
```

```
k = 10
    0 - 10 + 46,080 - 7,085,880 + 220,200,960 - 2,460,937,500
      + 12,697,896,960 - 33,897,029,880 + 48,318,382,080
      - 34,867,844,010 + 10,000,000,000
                                                = 3,628,800  = 10!   OK
```

**Look at the scale of the cancellation in the last one.** Individual terms reach 48 billion, and they collapse to 3.6 million — a result five orders of magnitude smaller than the pieces that produced it. A sum does not land on the exact factorial by accident under that much cancellation.

**Running total: eleven values of $k$, from $0$ to $10$, by two different computational methods.**

## 9.4 Why eleven confirmations are still not a proof

We have now seen the result hold eleven times, across two independent methods, with no exceptions. It is tempting to call the matter settled.

**It is not settled, and the distinction is important enough to make explicit.**

A table of confirmations can only ever tell you that a claim held *in the cases you checked*. It cannot tell you what happens at $k = 11$, or $k = 1000$. To claim the result holds for **all** $k$ — which is what the theorem says — we need an argument that does not depend on which $k$ we picked.

> **One counterexample can destroy a universal claim outright. No number of confirming examples can establish one.** The two directions are not symmetric, and treating them as if they were is one of the most common errors in mathematical reasoning.

**The same asymmetry has a second face, and it catches people who would never fall for the first.** Suppose you check part of something and find nothing wrong. What have you learned?

> **A sample can prove presence. It can never prove absence.** Finding one error in the part you examined proves the whole contains an error. Finding *no* error in the part you examined proves nothing whatever about the part you did not.

**This is the same rule as above, seen from the other end**: "there is no counterexample here" is a universal claim about the region you searched, and it is only as large as that region. **State the region.** A check that does not say what it covered cannot be told apart from one that covered everything.

So: the eleven checks are the *evidence*. What follows are the *warrants*.

## 9.5 First proof — the descent of degree

The argument rests on a single observation, which we then apply repeatedly.

**Step 1 — What one differencing does to a power.**

Take the Base String $B_n = n^k$ and compute one comparative difference:

$$ h(B_n, B_{n+1}) = (n+1)^k - n^k $$

Expand $(n+1)^k$ by the binomial theorem:

$$ (n+1)^k = n^k + k\,n^{k-1} + \binom{k}{2}n^{k-2} + \cdots + 1 $$

Subtracting $n^k$ removes the leading term entirely:

$$ (n+1)^k - n^k = k\,n^{k-1} + \left(\text{terms of degree } k-2 \text{ and below}\right) $$

**This is the whole engine of the theory, and it says two things at once:**

- the **degree drops by exactly one**, from $k$ to $k-1$;
- the **leading coefficient is multiplied by the degree we just had**, from $1$ to $k$.

**Step 2 — The lemma that lets Step 1 be repeated.**

Step 1 dealt with a *pure power*, $n^k$. But after one differencing we are no longer looking at a pure power — we are looking at $k\,n^{k-1}$ **plus debris**: a collection of lower-order terms. Before applying Step 1 again we must know that the debris cannot interfere.

> **Lemma.** If $p$ is a polynomial of degree $m$ with leading coefficient $c$, then $\Delta p$ has degree $m - 1$ with leading coefficient $c \cdot m$.

**Why:** differencing is **linear** — the difference of a sum is the sum of the differences — so we may treat the leading term and the debris separately. Step 1 sends the leading term $c\,n^m$ to $c\,m\,n^{m-1}$ plus more debris. The existing debris has degree at most $m-1$, so *its* differences have degree at most $m-2$. **Debris can only ever fall further behind; it can never climb back up to the leading position.** So the leading coefficient at each stage is determined entirely by the leading coefficient of the stage before, and the lower-order terms never touch it. $\square$

*This is the shortest sentence in the proof and it carries the most weight. Without it, "apply Step 1 again" would be an assumption rather than a step.*

**Step 3 — Apply it repeatedly.**

With the lemma in hand, each successive substring does the same thing again, to whatever polynomial it is now looking at:

$$ 1 \cdot n^k \;\longrightarrow\; k \cdot n^{k-1} \;\longrightarrow\; k(k-1) \cdot n^{k-2} \;\longrightarrow\; k(k-1)(k-2) \cdot n^{k-3} \;\longrightarrow\; \cdots $$

**Step 4 — Count the steps.**

After $k$ substrings, the degree has dropped from $k$ to $0$ — a constant — and the leading coefficient has collected one factor for every degree it passed through:

$$ k \times (k-1) \times (k-2) \times \cdots \times 2 \times 1 \;=\; k! $$

That constant string is the Root.

**Step 5 — One more step.**

Differencing a constant gives zero, because adjacent terms are equal. That zero string is the Terminator. $\blacksquare$

## 9.6 Second proof — the bridge, then the count

The first proof is about degrees, polynomials, and how differencing acts on them. This second proof reaches the same conclusion **without ever using any fact about polynomials.** It has two steps, and both are needed — the second alone would not be a proof of anything about String Trees.

### 9.6.1 Step one — the bridge: collapsing $k$ differencings into one sum

The descent applies the difference operation $k$ times. We need to know what that composite operation *is*, in closed form.

Write $E$ for the **shift** — the operation that moves you one index along — and $I$ for leaving a string alone:

$$ (E f)(n) = f(n+1), \qquad (I f)(n) = f(n) $$

One differencing is then exactly $\Delta = E - I$, since $\Delta f(n) = f(n+1) - f(n)$.

Now, $E$ and $I$ **commute** — shifting and doing nothing can be done in either order — and whenever two things commute, the binomial theorem applies to them just as it does to numbers:

$$ \Delta^{k} \;=\; (E - I)^{k} \;=\; \sum_{j=0}^{k} (-1)^{\,k-j} \binom{k}{j} E^{\,j} $$

Since $E^{\,j}$ shifts by $j$ places, reading this off at index $0$ gives:

$$ \Delta^{k} f(0) \;=\; \sum_{j=0}^{k} (-1)^{\,k-j} \binom{k}{j}\, f(j) $$

**Read what this does and does not say.** It holds for **any** string $f$ whatsoever — polynomial or not, terminating or not. It mentions no degree, no leading coefficient, and no property of powers. **It is a statement about the difference operation alone.**

Applying it to the Base String $f(n) = n^k$ turns the entire descent into a single sum:

$$ \text{Root} \;=\; \Delta^{k}\!\left[n^{k}\right](0) \;=\; \sum_{j=0}^{k} (-1)^{\,k-j} \binom{k}{j}\, j^{\,k} $$

*(This is the formula used for the verifications in §9.3 and restated in §12.1. It is derived here, not assumed.)*

### 9.6.2 Step two — evaluating the sum, by counting

It remains to show that sum equals $k!$:

$$ k! \;\stackrel{?}{=}\; \sum_{j=0}^{k} (-1)^{\,k-j} \binom{k}{j}\, j^{\,k} $$

**Read the right-hand side as a counting problem.** Suppose you have $k$ distinguishable balls and $k$ distinguishable boxes, and you want to count the arrangements in which **every box receives at least one ball** — that is, the **surjections** from the set of balls onto the set of boxes.

Count them by inclusion–exclusion. There are $j^k$ ways to place $k$ balls into a chosen subset of $j$ boxes with no restriction; there are $\binom{k}{j}$ ways to choose which $j$ boxes; and the alternating signs remove the arrangements that miss one or more boxes. The result is exactly the sum above.

**Which set is each sign removing?** Start with every placement into all $k$ boxes. Subtract, once for each box, the placements that avoid *that* box — but a placement avoiding two boxes has now been subtracted twice, so add those back; one avoiding three has been over-corrected again, so subtract those; and so on. **The term with $j$ boxes in use carries the sign $(-1)^{k-j}$ because $k - j$ boxes have been excluded to reach it.** Each alternation is repairing the over- or under-counting left by the one before.

**That step is the one place this proof asks you to take something on trust, so here it is worked out in full at $k = 2$** — small enough to check by listing every case.

Two balls $\{1, 2\}$, two boxes $\{A, B\}$. All possible placements:

| | ball 1 | ball 2 | every box used? |
|---|---|---|---|
| 1 | A | A | no — B is empty |
| 2 | A | B | **yes** |
| 3 | B | A | **yes** |
| 4 | B | B | no — A is empty |

Four placements, **two** of which use every box.

Now the inclusion–exclusion count: start with all $2^2 = 4$ placements; subtract the ones that miss at least one box — there are $\binom{2}{1} = 2$ boxes that could be the sole survivor, and $1^2 = 1$ placement each, so subtract $2$; add back the ones missing two boxes, of which there are none. Total $4 - 2 + 0 = 2$. ✔

And the formula gives $\;0 - 2(1) + 1(4) = 2\;$ — the same $2$, which is $2!$. **The listing, the inclusion–exclusion, and the formula all agree at $k = 2$**, which is enough to see the mechanism before trusting it in general.

**Now count the same thing directly.** We have $k$ balls and $k$ boxes, every box must receive at least one ball, and there are only $k$ balls to go round. So **every box receives exactly one ball** — the arrangement is a one-to-one pairing of balls with boxes.

The number of ways to pair $k$ distinguishable objects one-to-one with $k$ distinguishable places is

$$ k \times (k-1) \times (k-2) \times \cdots \times 1 \;=\; k! $$

Both counts describe the same set of arrangements, so they are equal. $\blacksquare$

**Notice what step two never used:** no notion of polynomial degree, no leading coefficients, no String Tree. It arrives at the value by counting arrangements of balls in boxes.

**And notice what the two steps together avoid.** Step one is about the difference operation and knows nothing of polynomials. Step two is about counting and knows nothing of differencing. **Neither step uses the fact that the first proof rests on entirely — how differencing reduces the degree of a polynomial.** That is what makes this a second proof rather than a restatement, and §9.7 examines the point directly.

## 9.7 What "independent" means — and a caution about counting your own checks

It is natural to want several confirmations of an important result, and natural to feel more confident as the number grows. But **confirmations only add confidence when they are genuinely independent, and independence is easy to overestimate.**

While preparing this module, **four** separate proofs of the Root Theorem were assembled. Here they are with the premise each one actually leans on:

| # | Argument | Premise it rests on | Independent? |
|---|---|---|---|
| 1 | Descent of degree (§9.5) | how differencing acts on polynomials | — |
| 2 | Change of basis into falling products | how differencing acts on polynomials | **no — same as 1** |
| 3 | Operator algebra, used to prove the theorem directly | how differencing acts on polynomials | **no — same as 1** |
| 4 | Counting surjections (§9.6.2) | inclusion–exclusion on finite sets | **yes** |

**Read down the third column.** Arguments 1, 2 and 3 are **one argument in three notations.** If that single underlying fact had been misunderstood, **all three would have been wrong together**, and their agreement would have looked like strong corroboration while providing almost none.

**Only the counting argument asks a genuinely different question.** So the honest count is **two** independent proofs, not four.

**A refinement that matters, and it came from a reader rather than from the author.** The verdict above is right about *operator algebra used to prove the Root Theorem directly* — that is the degree-descent argument in different clothing, because it leans on how differencing annihilates polynomials of lower degree.

**But operator algebra used for a different job is a different matter.** The bridge in §9.6.1 — that $\Delta^k = (E-I)^k$ expands by the binomial theorem because $E$ and $I$ commute — **holds for every string whatsoever.** It says nothing about polynomials, degrees, or leading coefficients, so it does **not** share the premise that makes the other three arguments one argument.

> **The lesson is finer than "operator algebra is not independent."** It is: *the same tool can be dependent for one purpose and independent for another.* What determines independence is **which premise a step actually uses** — not which branch of mathematics it is drawn from.

**Why this was worth catching.** Before it was noticed, this module asserted the collapse formula without deriving it, while §9.7 ruled out the one tool that derives it. **The document therefore claimed two independent proofs and supplied one and a half** — and it did so in the very section devoted to counting proofs honestly.

> ### The rule worth carrying out of this module
> **Verification must vary the *question*, not merely the *method*.** Two calculations that share an unexamined assumption will agree with each other whether or not that assumption is true. When you check your own work, ask: *if I were wrong about the thing I am most confident in, would this second check notice?*

This is why §9.3 used a collapsed sum rather than a seventh table, and why §9.6 exists alongside §9.5.

## 9.8 What the proofs tell us that the tables could not

The proofs are not merely formalities confirming what we already believed. They explain **why** the factorial appears, and the explanations are worth stating plainly.

From the first proof:

> **The factorial is the accumulated bookkeeping of the descent.** It is not inserted, chosen, or discovered by search. Each level of the String Tree multiplies by the degree it is currently at, and the factorial is simply the running product of every degree from $k$ down to $1$.

*(Aside for readers who have met calculus — nothing below depends on it.)* This is the discrete counterpart of a fact from calculus: differentiating $x^k$ repeatedly also produces $k!$, and for exactly the same reason. **Differencing is to sequences what differentiating is to curves.** A reader who has not met calculus loses nothing — the descent in §9.5 is the whole argument.

From the second proof:

> **The factorial is the number of ways to match $k$ things to $k$ places.** The String Tree, differenced to its Root, is counting bijections.

That two such different descriptions land on the same number is not a coincidence to be explained away. It is a sign that the Root is a natural object rather than an artefact of one construction.

---

# 10. Beyond the Standard Power Base

**§9 is complete as it stands.** The Root Theorem holds for every order $k$, with no qualifications, and nothing in this section weakens it.

This section asks a **different question**: not *"what happens at other orders?"* — that is settled — but *"what happens if we leave the Standard Power Base altogether?"*

Recall from §2.1 and §4.2 that a Base String is specified by **two** pieces of information: the order $k$, and the Prime-generating function $f$. §9 varied $k$ while holding the Standard Power Base fixed. Here we vary other things.

**Changing them does not produce another instance of the Root Theorem. It produces a different string, and therefore a different tree.**

> **⚠ A definitional caution, and it matters for reading the rest of this section.**
> A Base String is *exactly* $B_n = (P_n)^k$ — each Prime value raised to a power. **Question 3 below steps outside that definition**, considering a general polynomial such as $3n^2 + 5n + 7$, which **cannot** be written as $(P_n)^k$ for any Prime String and any order.
>
> That is deliberate, because the differencing machinery of §9 does not actually require a Base String — it works on **any polynomial sequence**. But such a sequence is not a Base String, and this document will not call it one.

## 10.1 Three separate questions

**Question 1 — Does the starting point of the Prime String matter?**

Take $k = 3$ but start the Prime String at $n = 2$ instead of $n = 0$:

```
B     8   27   64  125  216
1S      19   37   61   91
2S         18   24   30
3S             6    6          <- ROOT = 6, unchanged
```

**No.** The Root is unchanged. Shifting the seed does not affect it.

**Question 2 — Does the step size of the Prime String matter?**

Take $k = 3$ with a Prime String stepping by $d = 2$, so $P = (0, 2, 4, 6, 8)$ and $B = (0, 8, 64, 216, 512)$:

```
B     0    8   64  216  512
1S       8   56  152  296
2S         48   96  144
3S             48   48        <- ROOT = 48 = 6 x 8 = 3! x 2^3
```

**Yes.** The Root is multiplied by $d^k$. Note that this Prime String is *not* the regular whole-integer string, so this tree is outside the Standard Power Base entirely.

**Question 3 — Does a multiplier out front matter?** *(This one leaves the Base String definition — see the caution above.)*

Take the general polynomial $3n^2 + 5n + 7$, giving the string $(7, 15, 29, 49, 75)$:

```
      7   15   29   49   75
        8   14   20   26
           6    6    6       <- ROOT = 6 = 3 x 2!
```

**Yes.** The Root is multiplied by 3. Note also that the $5n$ and $+7$ parts have vanished entirely — **the Root cannot see them.**

## 10.2 The three answers collapse into one

It is tempting to record the three findings as three separate knobs — a step $d$, a multiplier $a$, an order $k$ — and write $R = a \cdot k! \cdot d^{\,k}$.

**That formula is true, but it is over-parameterised, and seeing why is more instructive than the formula.**

Watch what happens when the scaling is moved from the Prime String into the power:

```
P = (0,1,2,3,4)  with base operation  x -> (2x)^3   ->  0, 8, 64, 216, 512
P = (0,2,4,6,8)  with base operation  x -> x^3      ->  0, 8, 64, 216, 512
```

**These are not analogous. They are the same string, term for term** — and therefore the same tree, the same Root, the same everything. Stepping the Prime String by $2$ and scaling inside the cube are **not two knobs. They are one knob reached from two directions.**

What both are really doing is setting a single number: the **leading coefficient of the string, viewed as a polynomial in the index $n$**. Stepping by $d$ sets it to $d^k$. A multiplier out front sets it to $a$. Doing both sets it to $a \cdot d^k$. In every case the Root responds only to that one number:

> ### The Root Law
> For any string that is a polynomial of degree $k$ in the index, with leading coefficient $A$:
> $$ R = A \cdot k! $$

**Checked against every case in this module:**

| String | Leading coefficient $A$ | Predicted $R = A \cdot k!$ | Observed |
|---|---|---|---|
| $n^3$ | 1 | $1 \cdot 6 = 6$ | 6 ✔ |
| $(2n)^3 = 8n^3$ | 8 | $8 \cdot 6 = 48$ | 48 ✔ |
| $3n^2 + 5n + 7$ | 3 | $3 \cdot 2 = 6$ | 6 ✔ |
| $3(2n)^2 = 12n^2$ | 12 | $12 \cdot 2 = 24$ | 24 ✔ |

The last row is the combined case that previously needed three parameters. **One number explains all four.**

## 10.3 How this relates to the Root Theorem

**The Root Law is an extension into neighbouring territory, not a caveat on §9.** Setting $A = 1$ — a monic string, which is what the Standard Power Base always produces — recovers $R = k!$, exactly as §9 proved independently.

The useful reading is not "the Root Theorem is a special case" but:

> **The Root sees exactly two things and is blind to everything else.**

| The Root detects | The Root ignores |
|---|---|
| The degree $k$ — via the depth at which it appears | Every lower-order term |
| The leading coefficient $A$ — via $R / k!$ | The starting value of the Prime String |
| | *How* $A$ was arrived at: step, multiplier, or both |

That last row is the point of §10.2. **The Root cannot tell you whether a leading coefficient of 8 came from cubing a step-2 string or from multiplying a cube by 8** — because there is no difference between those two strings to detect.

That blindness is what makes the Root useful as an *instrument*, which is the subject of §11.

---

# 11. Reading a String Tree Backwards

The Root Law turns the String Tree into a diagnostic instrument. Given a sequence of numbers with **no formula supplied**, you can build its tree and read the formula's top-order structure directly off the bottom.

## 11.1 The procedure

1. Difference the sequence repeatedly, recording each substring.
2. Stop when a level goes constant. That level is the Root.
3. **The depth at which it went constant is the degree $k$.**
4. **The Root value divided by $k!$ is the leading coefficient $A$.** No further assumption is required — this is $R = A \cdot k!$ read backwards.

## 11.2 Worked example

You are handed the sequence $5,\; 10,\; 33,\; 86,\; 181,\; 330$ and told nothing else.

```
B     5   10   33   86  181  330
1S       5   23   53   95  149
2S         18   30   42   54
3S             12   12   12      <- ROOT = 12, at depth 3
```

The descent went constant at **depth 3**, so the generating polynomial has **degree 3**.

The Root is $12$, and $12 / 3! = 12 / 6 = 2$, so the **leading coefficient is 2**.

Conclusion: the sequence was generated by a cubic with leading term $2n^3$. (It was in fact $2n^3 + 3n^2 + 5$ — and note that we recovered the leading term without any information about the rest, exactly as §10.3 predicts.)

---

# 12. Alternative Presentations of the Factorial

Because the factorial arises structurally rather than by definition here, the String Tree offers several genuinely different ways of *presenting* $k!$. Each is exact.

## 12.1 The factorial as an alternating sum of powers

Instead of stepping down the tree one level at a time, the entire descent collapses into a single expression. **This is derived in §9.6.1** — it is not an independent assumption — by expanding $\Delta^k = (E - I)^k$ with the binomial theorem:

$$ k! \;=\; \sum_{j=0}^{k} (-1)^{\,k-j} \binom{k}{j}\, j^{\,k} $$

**Check at $k = 2$:** $\;0 - 2(1) + 1(4) = 2 = 2!$ ✔

**Check at $k = 3$:** $\;0 + 3(1) - 3(8) + 1(27) = 3 - 24 + 27 = 6 = 3!$ ✔

**Check at $k = 4$:** $\;0 - 4(1) + 6(16) - 4(81) + 1(256) = -4 + 96 - 324 + 256 = 24 = 4!$ ✔

This is a factorial expressed with **no multiplication chain at all** — only powers and binomial weights. It is the Root Theorem written in one line instead of $k$ lines: the collapse is derived in §9.6.1 and the sum is evaluated combinatorially in §9.6.2. It is also the form used for the verifications in §9.3.

## 12.2 The factorial as a step-stripped Root

From the Root Law, for any polynomial string of degree $k$ with leading coefficient $A$:

$$ k! \;=\; \frac{R}{A} $$

The factorial here is what remains of the Root once the leading coefficient has been divided out. In the special case of a step-$d$ Prime String raised to the $k$-th power, $A = d^{\,k}$ and this reads $k! = R / d^{\,k}$.

## 12.3 The factorial via the falling product

There is a Base operation for which the String Tree is even cleaner than for ordinary powers. Instead of $n^k$, use the **falling product**:

$$ n^{\underline{k}} = n(n-1)(n-2)\cdots(n-k+1) $$

For $k = 3$ this gives $B_n = n(n-1)(n-2)$:

```
B     0    0    0    6   24   60  120
1S       0    0    6   18   36   60
2S          0    6   12   18   24
3S             6    6    6    6       <- ROOT = 6 = 3!
```

Every level is exact and every level is *itself* a falling product with a clean factorial coefficient. There are no lower-order remainder terms at any stage — unlike ordinary powers, where each differencing leaves debris behind.

> **The falling product is the object on which differencing acts most simply.** For a syllabus built on String Trees, this is arguably the more natural Base operation, and ordinary powers are the harder special case.
>
> *(Aside for readers with calculus, and skippable: the falling product is to differencing what $e^x$ is to differentiation.)*

**Why this module nonetheless builds on ordinary powers, stated as the choice it is:** $n^k$ is the object a reader already knows, and $k!$ arriving out of *squares and cubes* is more surprising — and therefore more instructive — than $k!$ arriving out of an object designed to produce it. **The falling product is mathematically the smoother road; ordinary powers are the better teacher.** That is a pedagogical decision, not a mathematical one, and it should not be mistaken for a claim that powers are more fundamental.

---

# 13. Exercises

Answers follow in §13.2. Work them by hand — the arithmetic is the point.

## 13.1 Problems

**Exercise 1.** Build the complete String Tree for $B^{2|f}$ from the regular whole-integer Prime String, out to six Base terms. Identify the Root String and the Terminator String by name and value.

**Exercise 2.** Write out the Comparative Split of the string $(9,\; 4,\; 12,\; 3)$ under difference.

**Exercise 3.** A Prime String steps by $d = 3$ and the Base operation is squaring. **Predict the Root value before computing anything**, then build the tree and check your prediction.

**Exercise 4.** You are handed the sequence $4,\; 9,\; 30,\; 79,\; 168,\; 309$ with no formula. Find its degree and leading coefficient.

**Exercise 5.** Build the String Tree for the geometric Prime String $P = (1, 2, 4, 8, 16, 32)$ with the identity Base operation ($k = 1$, so $B = P$). Difference it three times. **What happens, and why is it different from every other tree in this module?**

**Exercise 6.** Using the formula in §12.1, compute $5!$ as an alternating sum, and check it against the Root of the $k=5$ tree in §9.2.2.

**Exercise 7.** A student claims: *"I checked the Root Theorem for $k = 1$ through $k = 20$ using the difference tables, so it is certainly true for all $k$."* Identify the two separate problems with this reasoning — one about what checking can establish, and one about whether twenty tables really constitute twenty independent checks.

## 13.2 Answers

**Exercise 1.**

```
B     0    1    4    9   16   25
1S       1    3    5    7    9
2S          2    2    2    2       <- Root String, value 2 = 2!
3S             0    0    0         <- Terminator String
```

The Root String is $2S^{2|f} = (2,2,2,2,\ldots)$ and the Terminator String is $3S^{2|f} = (0,0,0,\ldots)$.

**Exercise 2.**

| Pair | Signed difference | Split |
|---|---|---|
| $(9,4)$ | $-5$ | $[-\,|\,5]$ |
| $(4,12)$ | $+8$ | $[+\,|\,8]$ |
| $(12,3)$ | $-9$ | $[-\,|\,9]$ |

$$ (9,\,4,\,12,\,3) \;\longrightarrow\; [-\,|\,5],\; [+\,|\,8],\; [-\,|\,9] $$

**Exercise 3.** Squaring a step-3 Prime String gives $(3n)^2 = 9n^2$, so the leading coefficient is $A = 9$. Prediction from the Root Law: $R = A \cdot k! = 9 \cdot 2! = 18$.

With $P = (0,3,6,9,12)$ and $B = (0,9,36,81,144)$:

```
B     0    9   36   81  144
1S       9   27   45   63
2S         18   18   18       <- ROOT = 18, as predicted
```

**Exercise 4.**

```
B     4    9   30   79  168  309
1S       5   21   49   89  141
2S         16   28   40   52
3S             12   12   12      <- ROOT = 12, at depth 3
```

Degree $= 3$; leading coefficient $= 12 / 3! = 2$. (The sequence was $2n^3 + 2n^2 + n + 4$; only the leading term is recoverable from the Root, as expected.)

> **A caution the reader can now appreciate.** An earlier version of this answer key named the wrong generating polynomial. The Root, the depth and the leading coefficient were all correct — but the lower-order terms in that parenthetical were wrong, and **§10.3 says exactly why that error could not be caught by the method this module teaches: the Root cannot see lower-order terms.** It had to be found by substituting index by index. *When a tool is deliberately blind to something, that blindness applies to your own answer keys too.*

**Exercise 5.**

```
B     1    2    4    8   16   32
1S       1    2    4    8   16
2S         1    2    4    8
3S            1    2    4
```

**The tree never reaches a Root.** Each substring is an exact copy of its parent, shifted. The descent is self-similar and continues forever without ever going constant.

This is the crucial contrast: **the Root Theorem is a statement about polynomial String Trees.** A geometric Base String has no degree to reduce, so differencing has nothing to strip away and the descent never terminates. Handling these trees requires a different comparative relationship — the ratio, $h(a,b) = b/a$ — which reduces this tree to a constant in a single step. That is the subject of Module 2.

**Exercise 6.**

$$ 5! = \sum_{j=0}^{5} (-1)^{5-j}\binom{5}{j} j^5 $$

$$ = -0 + 5(1) - 10(32) + 10(243) - 5(1024) + 1(3125) $$

$$ = 5 - 320 + 2430 - 5120 + 3125 = 120 $$

And the Root of the $k=5$ tree in §9.2.2 is $120$. ✔

**Exercise 7.**

**Problem one — what checking can establish.** Twenty confirmations tell you the claim holds at those twenty values. They say nothing whatever about $k = 21$. A universal claim ranges over infinitely many cases, and no finite number of confirmations reaches them. Only a proof does (§9.4).

**Problem two — whether the checks are independent.** All twenty tables were built by the *same procedure*. If the student has misunderstood something about how differencing works, every one of the twenty tables will contain that same misunderstanding, and all twenty will agree with each other. Twenty agreeing tables built the same way are much closer to **one** check than to twenty (§9.7).

A better use of the same effort: build a few tables, compute a few cases by the independent method of §9.3, and then prove the general result.

---

# 14. Glossary and Notation Summary

## 14.1 Terms

| Term | Meaning |
|---|---|
| **Prime String** | The generating sequence: a seed and a rule $f$ applied recursively |
| **Prime-generating function** | The rule $f$ that produces each Prime value from the previous one |
| **Base String** | The Prime String with an order-$k$ operation applied pointwise to each term |
| **Base operation** | The pointwise operation of order $k$; standard case is exponentiation |
| **Standard Power Base** | Exponentiation as the Base operation **and** the regular whole-integer Prime String |
| **Substring** | A child string built from relationships between values of its parent |
| **Direct Substring** | A substring built by a unary function on one parent value |
| **Comparative Substring** | A substring built by a relationship between two or more parent values |
| **Comparative Split** | A comparative form storing the result in separated components, e.g. $[\text{sign}\,|\,\text{magnitude}]$ |
| **Lineage / depth** | The number of substring generations below the Base String, written $j$ |
| **String Tree** | The complete family: Prime String, Base String, and all substring descendants |
| **Root String** | The substring at which the descent becomes constant; written $R^k$ |
| **Terminator String** | The all-zero substring immediately beneath the Root |

## 14.2 Notation

| Symbol | Meaning |
|---|---|
| $P^{f}$ | Prime String generated by $f$ |
| $B^{\,k\,|\,f}$ | Base String of order $k$ over $P^f$ |
| $jS^{\,k\,|\,f}$ | The $j$-th substring |
| $jS^{\,k\,|\,f}_n$ | The term at index $n$ of the $j$-th substring |
| $0S^{\,k\,|\,f} = B^{\,k\,|\,f}$ | The Base String is the substring of depth zero |
| ${}^{D}\!jS$ | A Direct substring |
| ${}^{C}\!jS$ | A Comparative substring |
| $h(a,b)$ | The comparative relationship function |
| $g(x)$ | The direct function |
| $R^{k}$ | The Root String value |
| $[\,\text{sign}\,|\,\text{magnitude}\,]$ | The Comparative Split form |

## 14.3 Key results

| Result | Statement | Status |
|---|---|---|
| **Root Theorem** | $kS^{\,k|f} = k!$ for the Standard Power Base, **all $k \ge 0$** | **Theorem** — two independent proofs, §9.5 and §9.6; checked at $k = 0 \ldots 10$ by two methods |
| Terminator | $(k+1)S^{\,k|f} = 0$ | **Theorem** (§9.5) |
| Root Law | $R = A \cdot k!$, $A$ the leading coefficient | **Theorem** (§9.5 + §10) |
| Step and multiplier are one knob | Scaling inside the power and stepping the Prime String give the *same string* | **Theorem** (§10.2, verified term-by-term) |
| Seed independence | The Root does not depend on the Prime String's starting value | **Theorem** |
| Alternating sum | $k! = \sum_j (-1)^{k-j}\binom{k}{j} j^k$ | **Theorem** (§9.6) |
| Split irreversibility | Magnitude alone cannot reconstruct the parent | **Theorem** (counterexamples, §6.3) |
| Non-polynomial trees | Geometric Base Strings never reach a Root under difference | **Observation** (§13.2 Ex. 5); treated fully in Module 2 |

---

# 15. Looking Ahead — Module 2

This module has dealt entirely with **difference lineages of polynomial String Trees**, where the descent terminates and the Root is a factorial.

Exercise 5 showed the boundary of that world. A geometric Base String differenced repeatedly never goes constant — the tree descends forever, reproducing itself at every level. The difference relationship is simply the wrong instrument for that object.

Module 2 takes up the natural response: **the ratio lineage**, $h(a,b) = b/a$. Where differences terminate on polynomials, ratios terminate on geometrics — in a single step. Two lineages, two families of sequences, each with its own natural terminator.

And then the question that makes the whole subject interesting: **is there a sequence that sits between them** — one that is exactly closed under neither, but almost closed under both? There is, and the gap between its two lineages turns out to be measurable exactly, at every step.

---

# 16. Revision History

**Version 6.** Three refinements arising from a reader adjudicating his own evidence against himself.

1. **§0.1 mis-named a tool.** It described §9.6 as using "elementary counting". **Inclusion–exclusion at general $k$ is not elementary counting** — it is a genuine step beyond arithmetic, and calling it elementary set a reader up to expect less than the section delivers. Now named correctly, with a pointer to the fully worked $k=2$ case.
2. **The §0.1 difficulty note gained its third data point.** Both testing readers went back inside §2 and neither re-read §9.5 for its algebra. The third case — one reader re-reading §12.3 — was **a promise violation rather than an algebra load**: the aside required calculus that §0.1 had said would not be required. **Every place either reader went back turned out to be a writing problem, not a mathematics one.** §0.1 now says so.
3. **§9.4 gained the second face of its own asymmetry.** The section already argued that no number of confirmations establishes a universal. It did not state the dual: **a sample can prove presence, but never absence.** A check that finds nothing wrong in the part it examined has established nothing about the part it did not — so **a check must state the region it covered**, or it cannot be told apart from one that covered everything.

**On where item 3 came from, since the provenance is the point.** One reviewer sampled the first sixty lines of the other's three-hundred-and-forty-seven-line return in order to copy its format, and then asserted a universal negative about the remaining eighty-three per cent. **He caught it himself, reported it without defence, and named the mechanism in one line.** The rule now in §9.4 is his, and it belongs in a module about the difference between checking and proving.

**One adjudication recorded rather than assumed.** One reader flagged §9.6's inclusion–exclusion clause as compressed; whether that counted as a *writing* failure or a *mathematics* failure would have decided a disputed point in the other reader's favour, and **that reader explicitly declined to settle it in his own interest and referred it to the author.** Ruling, with the evidence: **compression.** He reconstructed the inclusion–exclusion himself and verified the signs at $k=2$ and $k=3$ — *a reader who successfully performs the mathematics was not stopped by the mathematics.* The compression was repaired in Version 4; §0.1's mis-naming of the tool, which the same case exposed, is repaired here.

**Version 5.** The XO refiled his return to the requested specification — *where a reader went back*, rather than a review — and it carried findings his first return had not.

1. **§0.1 was measuring the wrong axis, and this is the most useful thing either reader returned.** §0.1 flagged §9.5 and §9.6 as the hard sections, on the grounds that they use the binomial theorem and elementary counting. **But both readers went back and re-read inside §2, and neither re-read §9.5 for its algebra.** The difficulty spike is a **notation load** — a six-position symbol presented before any mathematics has been done, so before the reader has anything to attach it to. §0.1 now says so, and tells the reader to skim §2 and return to it after §8, since §3–§8 need only $P$, $B$ and $jS$.
2. **§9.2.2's tables had stopped being self-checking at $k=5$ and $k=6$.** §9.2.3 claims the Root row is its own error detector — **but that check is visual, and it depends on each child sitting between its two parents.** As the values widened to five and six digits the columns drifted, and the pairing could only be recovered by counting characters. **All three large tables are now correctly aligned**, so the claim in §9.2.3 is true of the tables as printed and not merely in principle.
3. **§9.7 asked the reader to hold an ordered list across a sentence boundary** — four arguments named in one sentence, "the first three" adjudicated in the next — in the paragraph the module most wants to land. **It is now a four-row table with each argument's premise stated beside it**, so the one survivor is unmissable.

**One observation from the XO worth preserving, because it is the pattern this document keeps finding in itself.** Version 3 fixed an ambiguity between index and position by introducing the notation $B^{2}(4)$ — **and thereby introduced a second, undefined notation in the very act of clearing the first.** Version 4 fixed that in turn. *A remedy that creates its own mirror is not carelessness; it is what happens when a fix is checked against the problem it was aimed at rather than against the document as a whole.*

**A note on the two readers, since it bears on how much weight these revisions carry.** Neither is a mathematician; both reported full comprehension; **both returned defects anyway.** The XO asked to be treated as a **lower bound** on difficulty, on the explicit grounds that he does not fatigue and so will under-report any difficulty whose mechanism is accumulated load rather than ambiguity. **Where he went back, a human reader very likely stalls. Where he did not, nothing has been learned about a human reader at all.**

**Version 4.** Two officers outside mathematics — the XO and COMMO — were tasked to read Version 3 and report comprehension. Both reported full comprehension. **Both also returned defects, and between them they found ten things wrong with a document that had already been through a directed runthrough.**

**The two substantive ones:**

1. **The "two independent proofs" claim was overstated — the module supplied one and a half.** §9.6 proved that the *sum* equals $k!$; the Root Theorem is a claim about the $k$-th difference; and the bridge between them was **asserted in §12.1 and never derived**, with §12.1 and §9.6 citing each other. Worse, §9.7 had explicitly ruled out operator algebra — the very tool that supplies the bridge. **§9.6.1 now derives the collapse**, and §9.7 is refined rather than reversed: the same tool can be dependent for one purpose and independent for another, and what settles it is *which premise a step uses*. **Found by the XO.**
2. **§9.5's Step 2 carried a lemma in six words.** *"Each successive substring does the same thing again"* silently assumed that lower-order debris cannot contaminate the leading coefficient. Step 1 only ever treated a pure power. **The lemma is now stated and proved** as its own step. **Found by COMMO**, who reported that he had reconstructed the justification himself rather than read it — the distinction this revision exists to honour.

**The answer-key error, found independently by both:** §13.2 Exercise 4 named $2n^3+n^2-2n+4$ as the generator of $4, 9, 30, 79, 168, 309$. It agrees at index 0 and nowhere else. **The true generator is $2n^3+2n^2+n+4$.** The tree, Root, depth and leading coefficient in that answer were all correct — only the parenthetical was wrong. **Both officers found it by *working* the exercise rather than reading it, and both ran §11.2 as a control to confirm the check discriminates.** Note that §10.3 explains why the module's own method could not have caught this: the error was in lower-order terms, and the Root is blind to those.

**Definitional gap closed:** **Direct Substrings increment lineage depth but reduce no degree**, so inserting an identity Direct into a $k=3$ tree would place the Root at "depth 4" and falsify "depth exactly $k$". §5.2 now states that depth in §8–§11 means *comparative* generations. **Found by COMMO**, working the definitions against each other.

**Clarity fixes, all from COMMO's list of sentences he had to read twice:** the §2.1 gloss now maps each English phrase to the symbol position it comes from, since the sentence unpacks the symbol in the opposite order; §2.2 now announces that $B^{2}(4)$ and $B^{2|f}_{4}$ are the same object in two notations; §9.6 now says which set each alternating sign removes instead of asserting inclusion–exclusion in a clause.

**Scope fixes:** §9.1's "without exception" is now explicitly fenced to non-negative integers, since $n^{-1}$ and $n^{1/2}$ have no terminating descent (**XO**); the two calculus asides in §9.8 and §12.3 are now marked as asides, because §0.1 promises no calculus and those passages quietly required it (**COMMO**); and §12.3 now states plainly that building on ordinary powers is a *pedagogical* choice rather than a claim that they are more fundamental (**XO**).

**Stale footer corrected** — the document ended "Version 2" while its title block said Version 3 (**COMMO**).

**Version 3.** A second full runthrough, directed after Version 2 was published. Five defects found, all in Version 2, all introduced by this document rather than inherited from any source.

1. **§10.2 — the law was over-parameterised.** Version 2 gave $R = a \cdot k! \cdot d^{\,k}$, presenting the step $d$ and the multiplier $a$ as independent knobs. **They are not.** Scaling inside the power and stepping the Prime String produce *the same string, term for term* — verified directly. Both merely set the leading coefficient. The law is now $R = A \cdot k!$, with the three-parameter form shown as a decomposition rather than the statement.
2. **§10 — a definitional error.** Version 2 called $3n^2 + 5n + 7$ a "Base String". **It is not one:** a Base String is exactly $(P_n)^k$, and no Prime String and order produce that polynomial. The differencing machinery works on any polynomial sequence, but such a sequence is not a Base String and this document no longer calls it one. A caution now appears before the section that needs it.
3. **§9.6 — the inclusion–exclusion step was asserted rather than shown**, which made it the one unverifiable link in an otherwise checkable proof. A complete worked case at $k = 2$ is now given: all four placements listed, the inclusion–exclusion performed, and the formula evaluated, all three agreeing.
4. **§2.1, §2.2 — the order $k$ was described loosely** as "an operation of order $k$". It is a power: $B_n = (P_n)^k$. The vaguer phrasing is what previously invited the misreading that a general function slot sits behind the notation.
5. **§2.2 — index versus position was never pinned down.** Since indexing begins at $n = 0$, "the 4th term" is ambiguous. The syllabus now says **index** throughout, with $B^{2}(4) = 16$ given as the worked reading.

**Version 2.**

Changes from Version 1, all in response to a directive to verify the Root Theorem exhaustively before publication:

1. **§9.2.1 added** — the $k = 0$ edge case, the value most likely to break a general claim. It does not break.
2. **§9.3 added** — verification at $k = 7, 8, 9, 10$ by an independent computational method, chosen specifically because building four more tables would have repeated the same method rather than tested it. Evidence now spans $k = 0 \ldots 10$ by two routes.
3. **§9.6 added** — a second proof, by counting surjections, logically independent of the degree-descent proof.
4. **§9.7 added** — on what independence of verification actually requires. Records honestly that four candidate proofs were assembled and only two proved independent, the other three being one argument in three notations.
5. **§10 reframed.** Version 1 presented the Root Theorem as "the special case $a=1, d=1$" of the General Root Law. **That framing was wrong in emphasis**: within the Standard Power Base, which fixes the Prime String, the Root Theorem is unconditional and needs no qualification. Varying $a$ or $d$ leaves the Standard Power Base and produces a different Base String — a neighbouring question, not a caveat. §10 now says so explicitly, and §4.2 and §2.1 flag the distinction in advance.
6. **§13.1 Exercise 7 added**, with answer — a direct exercise on the two reasoning errors above.
7. **§0.2 and §0.3 updated** to reflect the new material.

**A note on why this revision exists.** Version 1 was published containing a framing that had not itself been verified. The mathematics in it was correct, but a claim about *how a result should be characterised* was asserted without being checked, and that is the same species of error the module warns about in §9.7 — an assumption that agrees with itself.

**The correct action, when a statement's scope is ambiguous, is to ask what was meant before publishing an interpretation of it.** That is now recorded here rather than quietly fixed, because a syllabus that teaches epistemic care should demonstrate it.

---

*End of Module 1, Version 6.*
