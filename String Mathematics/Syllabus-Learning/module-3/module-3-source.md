---
title: "String Mathematics — Module 3"
subtitle: "Tuned Comparisons, Locating Damage, and the Minimum a Tree Remembers"
author: "Prime Framework — Syllabus-Learning Series"
date: "Module 3 of the String Mathematics syllabus — Version 2"
---

# Module 3 — Tuning the Comparison

## One Relationship That Contains Both Lineages, and Two Things a String Tree Knows About Itself

**Version 2.** Prerequisite: Modules 1 and 2.

---

# 0. How to Use This Module

## 0.1 What you need

Modules 1 and 2. Specifically: the String Tree and the Root (Module 1), and the ratio lineage, the Bridge, and the fact that difference *scales* geometrics rather than reducing them (Module 2).

## 0.2 What this module does

Modules 1 and 2 gave you two instruments and showed that each is blind to what the other sees. Module 2 then handed you a string that **neither** closes.

**This module builds the instrument that closes it** — and the instrument turns out to contain both of the earlier ones as special cases. There is only ever one idea here, and this is the module where that becomes visible.

Then two questions about what a String Tree knows:

- **Where** an error is, not merely that one exists.
- **How little** of a tree you must keep in order to rebuild all of it.

## 0.3 One new notation, arriving after the idea

As in Module 2: one new symbol, introduced after the thing it names.

---

# 1. The String Neither Instrument Closes

Module 2's Exercise 4 gave a string built from a polynomial **times** a geometric:

$$ B_n = n \cdot 2^{\,n} \qquad\Longrightarrow\qquad 2,\; 8,\; 24,\; 64,\; 160 $$

Difference it:

```
B      2    8   24   64  160
1S        6   16   40   96
2S         10   24   56
3S            14   32
```

No Root. Take ratios instead: $4,\; 3,\; 2.\overline{6},\; 2.5$ — heading toward 2, never constant. No Root either.

**Why neither works, stated exactly:**

- **Differencing** strips one degree of the polynomial per step (Module 1 §9.5) — **but it leaves the geometric factor untouched**, because differencing only *scales* a geometric (Module 2 §7).
- **The ratio** strips the geometric factor in one step — **but it leaves the polynomial behind** as a ratio $p(n{+}1)/p(n)$, which is not constant.

> **Each instrument removes its own half and leaves the other. The string needs a comparison that does both at once.**

---

# 2. The Tuned Difference

## 2.1 Definition

Module 1 §5.3 permits any relationship $h$. Take one with a dial on it:

$$ h_r(a, b) \;=\; b - r\,a $$

We write this lineage $jS_{(r)}$ and call $r$ the **tuning**. **This is the module's one new notation.**

The ordinary difference is what you get with the dial at 1.

## 2.2 What it does to a geometric

$$ h_r\!\left(c\,r^{\,n},\; c\,r^{\,n+1}\right) \;=\; c\,r^{\,n+1} - r \cdot c\,r^{\,n} \;=\; 0 $$

**A geometric string tuned to its own ratio dies in one step.** Not reduced — annihilated.

## 2.3 What it does to a polynomial times a geometric

This is the calculation the module turns on. Let $B_n = p(n)\,r^{\,n}$ with $p$ a polynomial:

$$ h_r(B_n, B_{n+1}) \;=\; p(n{+}1)\,r^{\,n+1} \;-\; r\,p(n)\,r^{\,n} \;=\; r^{\,n+1}\left[\,p(n{+}1) - p(n)\,\right] $$

The bracket is **the ordinary difference of $p$**. So:

$$ \boxed{\;h_r\left[\,p(n)\,r^{\,n}\,\right] \;=\; r \cdot \left[\Delta p(n)\right] \cdot r^{\,n}\;} $$

> ### The tuned difference passes straight through the geometric factor and differences the polynomial underneath it.
> The geometric survives unchanged, the polynomial loses a degree, and **the shape of the string is preserved: it is still (polynomial) × (geometric).**

## 2.4 The termination result

> ### The Tuned Root Theorem
> For $B_n = p(n)\,r^{\,n}$ with $\deg p = k$:
> $$ (k{+}1)S_{(r)} \;=\; 0 $$
> **A polynomial of degree $k$ times a geometric of ratio $r$ is annihilated by the tuned difference at depth $k+1$.**

**Proof.** By §2.3 each application reduces $\deg p$ by exactly one while leaving the factor $r^{\,n}$ in place. After $k+1$ applications the polynomial has been differenced past constancy to zero, and zero times anything is zero. $\blacksquare$

## 2.5 The worked case, by hand

$B_n = n \cdot 2^{\,n}$, so $p(n) = n$, degree 1, and $r = 2$. The theorem predicts termination at depth $2$.

```
B          0    2    8   24   64  160
1S(2)         2    4    8   16   32
2S(2)            0    0    0    0        <- TERMINATOR, at depth 2
```

Each entry, computed:

| | |
|---|---|
| $1S_{(2)}$ | $2-2(0)=2$ · $8-2(2)=4$ · $24-2(8)=8$ · $64-2(24)=16$ · $160-2(64)=32$ |
| $2S_{(2)}$ | $4-2(2)=0$ · $8-2(4)=0$ · $16-2(8)=0$ · $32-2(16)=0$ |

**Exactly as predicted.** And note $1S_{(2)} = 2, 4, 8, 16, 32 = 2^{\,n+1}$, which is $r \cdot (\Delta p) \cdot r^n$ with $\Delta p = 1$ — the formula in §2.3, confirmed term by term.

---

# 3. The Tuned Difference Contains Both Earlier Lineages

**This is the point of the module.** Two special cases of one dial:

## 3.1 Dial at 1 — Module 1

$$ h_1(a,b) = b - 1 \cdot a = b - a $$

**The ordinary difference.** Everything in Module 1 is the tuned difference with $r = 1$, and the polynomials it terminates on are exactly $p(n) \cdot 1^{\,n}$.

## 3.2 Degree zero — Module 2

Take $p$ constant, so $B_n = c\,r^{\,n}$ is purely geometric. Then $h_r$ annihilates it in one step, and

$$ b - r\,a = 0 \qquad\Longleftrightarrow\qquad \frac{b}{a} = r \quad (a \neq 0) $$

**The tuned difference at $r$ is the ratio test written additively.** Module 2's Ratio Root Theorem is the degree-zero case of §2.4.

## 3.3 And it repairs Module 2's partiality

Module 2 §4 recorded an asymmetry that could not be patched away: **difference is total, ratio is partial.** $b/a$ is undefined when $a = 0$, and the module's own standard example began at zero.

**The tuned difference has no such defect.** $b - r\,a$ is defined for every pair, including $a = 0$.

Take the string that broke the ratio lineage — $0, 2, 8, 24, 64, 160$ — where the first comparison $2/0$ was undefined. Tuned: $2 - 2(0) = 2$. **Defined, and it is the first entry of the table in §2.5.**

> **The tuned difference does the ratio's work as a total operation.** Module 2's partiality was real, and it was a property of *that formulation of the comparison*, not of the underlying idea.

## 3.4 The picture

| Tuning | Terminates on | Depth | Known as |
|---|---|---|---|
| $r = 1$ | polynomials of degree $k$ | $k+1$ | the difference lineage (Module 1) |
| any $r$, $p$ constant | geometrics with ratio $r$ | $1$ | the ratio test (Module 2) |
| any $r$, $\deg p = k$ | polynomial × geometric | $k+1$ | **this module** |

---

# 4. More Than Two Inputs — and Why the Right Comparison Is the Family's Own Rule

## 4.1 The permission was always there

Module 1 §5.3 defines a comparative substring using *"two or more values"* of the parent. Nothing so far has used more than two.

## 4.2 Fibonacci, in one step

Module 2 §9 showed the Fibonacci string defeating both lineages: differencing reproduces it shifted, ratios converge without arriving. **Give it a three-input comparison instead:**

$$ h(a,b,c) \;=\; c - b - a $$

```
1, 1, 2, 3, 5, 8, 13

(1,1,2) -> 2-1-1 = 0
(1,2,3) -> 3-2-1 = 0
(2,3,5) -> 5-3-2 = 0
(3,5,8) -> 8-5-3 = 0
(5,8,13) -> 13-8-5 = 0
```

**Depth 1.** The string that neither earlier instrument could close terminates immediately — because that comparison **is the string's own defining rule, rearranged to equal zero.**

## 4.3 The general principle

> ### Choosing $h$ is choosing which family you want to be invisible.
> $b - a$ makes constants invisible. $b - r\,a$ makes geometrics of ratio $r$ invisible. $c - b - a$ makes Fibonacci invisible. **In each case the comparison is the family's own recurrence, written as a test for zero.**

**And "depth" is then a measure of complexity relative to that choice.** Polynomial degree is nothing more exotic than *difference-depth*. Ask a different comparison and you get a different, equally legitimate notion of how complicated a string is.

## 4.4 The two-input and three-input versions are the same thing

**This connects §2 and §4.2, and it is worth the half-page.**

The Fibonacci rule has two characteristic ratios — the numbers $x$ for which $x^2 = x + 1$:

$$ \varphi = \frac{1+\sqrt5}{2}, \qquad \psi = \frac{1-\sqrt5}{2}, \qquad\text{with}\quad \varphi + \psi = 1, \quad \varphi\psi = -1 $$

Apply the tuned difference **twice, once at each ratio.** Writing $h_\psi$ then $h_\varphi$:

$$ h_\varphi\!\left(h_\psi B\right)_n \;=\; \left[B_{n+2} - \psi B_{n+1}\right] - \varphi\left[B_{n+1} - \psi B_n\right] $$
$$ =\; B_{n+2} - (\varphi + \psi)\,B_{n+1} + \varphi\psi\,B_n \;=\; B_{n+2} - B_{n+1} - B_n $$

> ### The composition of two tuned differences, at the two golden ratios, **is exactly the integer three-term rule.**
> The irrational numbers cancel completely. **$\varphi$ and $\psi$ enter the calculation and are gone by the end of it** — which is why Fibonacci is a string of whole numbers despite being governed by two irrationals.

**This is the same φ that Module 2 arrived at as a fixed point.** There it was the value where addition and multiplication give the same instruction; here it is a tuning that annihilates half the string. **Two routes, one number — and neither route began by assuming it mattered.**

---

# 5. ⭐ Reading the Damage: Locating an Error, Not Merely Detecting One

Module 1 §9.2.3 observed that the Root row is its own error detector: corrupt any term and the constancy breaks. **A detector tells you something is wrong. This section asks where.**

## 5.1 The setup

Take a clean tree and change exactly one value. Because differencing is **linear** (Module 1 §9.5's lemma), the damage travels independently of the string it damages: whatever the tree was, the *deviation* from it obeys its own tree.

## 5.2 Worked, by hand

$B_n = n^3$, and index 3 is corrupted from $27$ to $37$ — an error of $\varepsilon = +10$.

```
B'     0    1    8   37   64  125  216
1S'      1    7   29   27   61   91
2S'        6   22   -2   34   30
3S'         16  -24   36   -4
```

Set that beside the clean tree from Module 1 and subtract:

| Level | Clean | Corrupted | **Deviation** |
|---|---|---|---|
| $1S$ | $1, 7, 19, 37, 61, 91$ | $1, 7, 29, 27, 61, 91$ | $0, 0, +10, -10, 0, 0$ |
| $2S$ | $6, 12, 18, 24, 30$ | $6, 22, -2, 34, 30$ | $0, +10, -20, +10, 0$ |
| $3S$ | $6, 6, 6, 6$ | $16, -24, 36, -4$ | $+10, -30, +30, -10$ |

## 5.3 The pattern

Read the deviation rows as multiples of $\varepsilon = 10$:

```
depth 1:    1,  -1
depth 2:    1,  -2,   1
depth 3:    1,  -3,   3,  -1
```

**Those are the binomial coefficients with alternating signs.** The damage does not spread randomly — it spreads as Pascal's triangle, signed.

> ### The Damage Wedge
> A single error $\varepsilon$ at index $m$ appears at depth $j$ as exactly $j+1$ consecutive nonzero entries, with values
> $$ \varepsilon \cdot (-1)^{\,i}\binom{j}{\,j-i\,} $$
> **and the wedge ends at index $m$.**

## 5.4 Reading it backwards — the locator

The wedge gives up three things:

1. **That the error is a single point error** — because the deviations are in binomial ratio. Two separate errors would superpose and generally would not.
2. **Where it is.** The **right-hand edge of the wedge is the corrupted index.** In the table above the depth-3 wedge occupies indices $0,1,2,3$ and ends at $3$ — **and index 3 is exactly the term that was corrupted.**
3. **How large it is.** The outermost entries carry binomial coefficient $\binom{j}{0} = 1$, so **they are $\pm\varepsilon$ directly.** Here the wedge ends at $-10$, giving $\varepsilon = 10$.

> **So a String Tree does not merely report that it has been damaged. It reports where and by how much** — provided the damage is a single term.

## 5.5 What this does not do, stated plainly

**The limits are as important as the result**, and Module 2 §8 is the reason to insist on them:

- **Two or more errors** superpose. Their wedges may overlap and partially cancel, and the binomial signature is then not a reliable indicator of a single fault.
- **An error near either end** of the string produces a **truncated** wedge — you see part of the pattern, and the right edge may lie outside your data. **A truncated wedge is not evidence of a small error; it is evidence you cannot see the whole thing.**
- **The method assumes the underlying string genuinely terminates.** If it does not, there is no clean Root row to measure deviation against.

**State which case you are in.** A locator that cannot tell "one error at index 3" from "two errors whose wedges cancelled" will confidently report the first.

---

# 6. The Minimum a Tree Remembers

Module 1 §7.3 said a String Tree can be read upward to reconstruct, given the sign channel and *"one anchor value per level."* **It did not say whether that was the minimum.** It is, and here is why.

## 6.1 The left edge is enough

Keep only the **first entry of every level** — the left edge of the tree. For $B_n = n^3$ that is

$$ 0S_0 = 0, \qquad 1S_0 = 1, \qquad 2S_0 = 6, \qquad 3S_0 = 6 $$

Four numbers. Every other value in the tree can be rebuilt from them:

$$ B_n \;=\; \sum_{j} \binom{n}{j}\,\bigl(jS_0\bigr) $$

**Checked by hand:**

| $n$ | $0\binom{n}{0} + 1\binom{n}{1} + 6\binom{n}{2} + 6\binom{n}{3}$ | Result | $n^3$ |
|---|---|---|---|
| 3 | $0 + 3 + 6(3) + 6(1)$ | $27$ | 27 ✔ |
| 4 | $0 + 4 + 6(6) + 6(4)$ | $64$ | 64 ✔ |
| 5 | $0 + 5 + 6(10) + 6(10)$ | $125$ | 125 ✔ |

## 6.2 And it is the minimum

A string that terminates at depth $k$ is a polynomial of degree $k$ in the index. **A polynomial of degree $k$ has exactly $k+1$ coefficients** — that many independent numbers and no fewer determine it.

The left edge has exactly $k+1$ entries. So:

> ### The left edge is both sufficient and minimal.
> $k+1$ numbers rebuild the whole tree, and **no set of $k$ numbers can**, because $k$ numbers cannot distinguish between polynomials of degree $k$.

**Answering the question as it was asked:** sign-plus-anchor is sufficient, and the anchors alone — one per level — are already minimal. There is no cheaper set.

## 6.3 The trade this exposes

**A String Tree is enormous and its information content is tiny.** A tree over $N$ terms holds roughly $N^2/2$ numbers, and all of them are determined by $k+1$ of them.

**That redundancy is exactly what §5 exploits.** A tree can locate its own damage *because* it is carrying vastly more numbers than it needs — the surplus is what the error has to disagree with.

> **Detection and correction are not free properties of the notation. They are paid for by redundancy**, and here the price is visible: $N^2/2$ numbers standing in for $k+1$.

---

# 7. Appendix: Making the Independence Test Operational

Module 1 §9.7 argued that verification must vary the *question*, not merely the method, and that independence is easy to overestimate. **It gave no procedure**, which is a fair complaint against it.

Here is one. It is crude and it beats judgement.

1. **Write each argument as a list of the premises it actually uses.** Not the branch of mathematics it comes from — the specific facts it leans on.
2. **Compare the lists.** Two arguments are independent to the extent their lists are disjoint.
3. **For any premise appearing in more than one list, ask: if this were false, how many of my arguments fail?** That count, not the number of arguments, is what your confidence should track.

**Worked on this syllabus's own material** — the four arguments assembled for the Root Theorem:

| Argument | Premise it uses | |
|---|---|---|
| Descent of degree | how differencing acts on polynomials | ← |
| Falling-product basis | how differencing acts on polynomials | ← **same** |
| Operator algebra, used directly | how differencing acts on polynomials | ← **same** |
| Counting surjections | inclusion–exclusion on finite sets | ✔ different |

**Three lists identical, one disjoint. Honest count: two independent arguments, not four.**

## 7.1 The same problem when counting evidence, not proofs

The procedure above compares *arguments*. The identical failure occurs when counting *evidence*, and there it has a one-line test.

Suppose several independent mechanisms all point at one conclusion. **It is tempting to count them as several pieces of evidence. Usually they are one.**

> ### Test before counting
> **Is this a new *look* at the world, or a second *story* about the same look?**
> **Only the first goes in the tally.**

- **Independent observations add weight.** Two people running two different tests on the same object have genuinely looked twice.
- **Independent mechanisms explaining one observation add robustness, not weight.** The conclusion survives if one explanation is wrong — which is worth something — but **you have not seen anything twice.**

**Robustness and weight are different quantities, and a narrative runs them together**: describing one event through two mechanisms makes it feel like two events. The test above is what separates them, and it can be applied in the moment rather than reconstructed afterwards.

*This section exists because the author of this syllabus committed exactly that error while arguing an unrelated point, described a single bad outcome through two different failure mechanisms, and reported the result as if it were two findings.*

## 7.2 A note on the two halves

**The refinement that only appears once you write the lists out:** the *same tool* can be dependent for one purpose and independent for another. Operator algebra used to prove the theorem directly leans on the polynomial premise; operator algebra used only to establish the collapse formula (Module 1 §9.6.1) does not, because that identity holds for every string whatsoever. **The tool is not the unit of analysis. The premise is.**

---

# 8. Exercises

## 8.1 Problems

**Exercise 1.** Apply the tuned difference with $r = 3$ to $5,\; 15,\; 45,\; 135$. What happens, and why in one step?

**Exercise 2.** $B_n = (n+1)\,3^{\,n}$ gives $1,\; 6,\; 27,\; 108,\; 405$. **Predict the termination depth from §2.4 before computing**, then compute $1S_{(3)}$ and $2S_{(3)}$ and check.

**Exercise 3.** Explain, in one sentence each, why $h_1$ recovers Module 1 and why $h_r$ on a constant polynomial recovers Module 2.

**Exercise 4.** A clean cubic tree has Root row $6, 6, 6, 6, 6$. A corrupted copy has Root row $6, 6, -1, 27, -15, 9$. Locate the error and give its size. *(Careful: state anything you cannot determine.)*

**Exercise 5.** A tree terminates at depth 4. How many numbers must you keep to rebuild it, and which ones?

**Exercise 6.** Why does the composition $h_\varphi \circ h_\psi$ produce a rule with no irrational numbers in it, when both tunings are irrational?

## 8.2 Answers

**Exercise 1.** The string is geometric with ratio 3, so tuning to $r = 3$ annihilates it immediately:

```
5, 15, 45, 135    ->   15-3(5)=0 | 45-3(15)=0 | 135-3(45)=0   ->   0, 0, 0
```

Depth 1, per §2.2 — a geometric tuned to its own ratio dies in one step, because $b - r a = 0$ is precisely the statement $b/a = r$.

**Exercise 2.** $p(n) = n+1$ has degree 1, so §2.4 predicts termination at depth $k+1 = 2$.

```
B          1    6   27  108  405
1S(3)         3    9   27   81
2S(3)            0    0    0        <- TERMINATOR at depth 2, as predicted
```

Working: $6-3(1)=3$, $27-3(6)=9$, $108-3(27)=27$, $405-3(108)=81$; then $9-3(3)=0$, $27-3(9)=0$, $81-3(27)=0$.

**Exercise 3.** $h_1(a,b) = b - a$ is the ordinary difference, so Module 1 is the whole theory with the dial at 1. With $p$ constant the string is purely geometric and $b - ra = 0$ says exactly $b/a = r$, so Module 2's ratio test is the degree-zero case.

**Exercise 4.** Deviations from the clean row $6,6,6,6,6$:

```
0, 0, -7, +21, -21, +9
```

Hmm — the clean row has five entries and the corrupted row has six, so **they are not the same tree** and cannot be subtracted term by term. **State that and stop.** With rows of different lengths you do not know whether a term was inserted, whether the strings started at different indices, or whether one was differenced to a different depth.

*This exercise is a trap, and deliberately so.* Module 2 §8.4 requires a Root claim to state the region it covers; the same applies to a comparison. **Two rows of different lengths are not comparable, and the arithmetic will happily proceed anyway if you let it.**

**Exercise 5.** Five numbers — the left edge $0S_0,\, 1S_0,\, 2S_0,\, 3S_0,\, 4S_0$. A tree terminating at depth 4 is a degree-4 polynomial, which has five coefficients, so five is both sufficient (§6.1) and minimal (§6.2).

**Exercise 6.** Because the composition depends on $\varphi$ and $\psi$ only through their **sum** and their **product**, which are $1$ and $-1$ — both integers. The irrationals appear symmetrically and cancel. *This is why a rule with irrational roots can still generate whole numbers forever.*

---

# 9. Glossary, Notation, and Status

| Symbol | Meaning |
|---|---|
| $h_r(a,b) = b - r\,a$ | The **tuned difference**, with tuning $r$ |
| $jS_{(r)}$ | The $j$-th substring under the tuned difference at $r$ |

| Term | Meaning |
|---|---|
| **Tuning** | The dial $r$ in $b - r\,a$; the geometric ratio the comparison is blind to |
| **Damage wedge** | The signed-binomial pattern a single corrupted term produces below itself |
| **Left edge** | The first entry of each level; the minimal data that rebuilds a tree |

| Result | Status |
|---|---|
| $h_r$ passes through a geometric and differences the polynomial | **Theorem** (§2.3) |
| Tuned Root Theorem: termination at depth $k+1$ | **Theorem** (§2.4), checked at $n2^n$ and $(n{+}1)3^n$ |
| $h_1$ is Module 1; degree-zero $h_r$ is Module 2 | **Theorem** (§3.1–§3.2) |
| $h_r$ is total where the ratio lineage was partial | **Theorem** (§3.3) |
| $c-b-a$ annihilates Fibonacci at depth 1 | **Theorem** (§4.2), checked at five triples |
| $h_\varphi \circ h_\psi$ = the integer three-term rule | **Theorem** (§4.4) |
| Damage wedge is signed binomial, ends at the corrupted index | **Theorem** (§5.3), checked at all three depths |
| Wedge reading fails for multiple or edge errors | **Stated limit** (§5.5), not a proved bound |
| Left edge rebuilds the tree; $k+1$ is minimal | **Theorem** (§6.1–§6.2), checked at $n^3$ |

---

# 10. Looking Ahead

Three threads remain open, and they are named here rather than promised.

**Composite tunings in general.** §4.4 composed two tuned differences and got an integer rule. Any linear recurrence factors the same way, over its characteristic ratios. **What has not been established here is what happens when a ratio repeats** — whether the depth grows the way §2.4 suggests, and what the analogue of the damage wedge becomes.

**Correction, not merely location.** §5 locates a single error and gives its size, which is enough to *repair* it. **Whether more than one error can be corrected, and how many, is a bound this module does not attempt** — and §6.3 says where the answer must come from, since correction is paid for out of redundancy.

**The non-terminating strings.** Module 2 §8 established that non-termination cannot be seen in finite data. **Every instrument in this syllabus so far assumes a string that terminates under *something*.** The strings that terminate under nothing are the ones left.

---

*End of Module 3, Version 2.*
