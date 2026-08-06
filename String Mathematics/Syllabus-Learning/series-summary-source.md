---
title: "String Mathematics — Series Summary"
subtitle: "Modules 1 to 6: the arc, the results, the dependencies, and what remains open"
author: "Prime Framework — Syllabus-Learning Series"
date: "Series Summary — covering Modules 1 through 6"
---

# String Mathematics — Series Summary

## Modules 1 to 6

**This document is a map, not a module.** It teaches nothing new. It exists so that a reader arriving at the series can see its shape, find a result without hunting, and know what has been proved from what.

---

# 1. The Arc

The series is built on one principle, which was not planned and became visible only in retrospect:

> ### Each part questions something the part before it took for granted.

| Modules | What they build | What they leave unquestioned |
|-------------------|--------------------------------------|-------------------------------------------|
| **1 – 3** | the instrument: lineages, Roots, tuning | what the *values* are — every one an ordinary base-ten integer |
| **4 – 6** | the number itself: registers, bases, digit sets | what the values are *made of* — still ordinary integers |
| **next** | the value domain | — |

**Modules 1–3 build an instrument** and point it at sequences. Difference, ratio, and the tuned comparison that contains both. Roots, Terminators, depth, and what a String Tree knows about its own damage.

**Modules 4–6 turn the instrument on number itself.** A base is a choice of alphabet, not a property of a quantity; carrying is presentation rather than arithmetic; and once you ask which digit set actually works, the answer forces a radix rather than permitting one.

---

# 2. Reading Map

**Modules should be read in order the first time.** Afterwards, this is what actually depends on what:

```
   Module 1  Foundations
      |  \
      |   \______________________
      |                          \
   Module 2  Ratio Lineage      Module 4  Number Without a Base
      |                              |
      |                              |
   Module 3  Tuned Comparisons   Module 6  Digit Sets
      |
   Module 5  Sum and Product
```

| Module | Requires | Does not require |
|-------------------------|--------------------------------|-------------------------------------------|
| **1** | — | — |
| **2** | 1 | 3, 4, 5, 6 |
| **3** | 1, 2 | 4, 5, 6 |
| **4** | 1 | 2, 3, 5, 6 |
| **5** | 1, 2, 3 | 4, 6 |
| **6** | 1, 4 | 2, 3, 5 |

**Two independent tracks run from Module 1** — the *lineage* track (2, 3, 5) and the *representation* track (4, 6). They do not depend on each other and may be read in either order after Module 1.

---

# 3. What Each Module Establishes

## 3.1 Module 1 — Foundations

**Builds:** the Prime String, the Base String, substrings, the String Tree, the Root and the Terminator. Notation and the indexing convention.

**Central result — the Root Theorem.** For the Standard Power Base of order *k*, the descent goes constant at depth exactly *k*, and the constant is *k*!. **Two logically independent proofs**: a descent-of-degree argument, and a counting argument over surjections that never mentions polynomials.

**Also:** the **Root Law**, `R = A·k!` — the Root sees the degree and the leading coefficient and is blind to everything else; reading a tree backwards to recover a polynomial's top-order structure from numbers alone; and the **Comparative Split**, keeping *how far* and *which way* on separate axes.

**And a strand that runs through the whole series:** the difference between a check and a proof. A sample proves presence and never absence. Verification must vary the *question*, not merely the method.

## 3.2 Module 2 — The Ratio Lineage

**Central result:** a geometric string reaches its ratio-Root at depth 1, and the Root is the common ratio.

**The Bridge.** `ratio = exp ∘ difference ∘ log` — the two lineages are one theory in two coordinate systems, carried between them by a Direct Substring.

**Two honest limits, both kept rather than patched.** Ratio is **partial** where difference is **total** — division by zero is not an inconvenience but a structural asymmetry. And **non-termination cannot be seen in finite data**: `N` terms always bottom out at a single value by depth `N−1`, and one value is trivially constant, so any finite sample is consistent with termination.

**The destination:** the Fibonacci string is closed by neither lineage — differencing reproduces it shifted, ratios converge without arriving — and the gap is exact at every step, `(−1)ⁿ/(φⁿFₙ)`, or in pure integers `(−1)ⁿ/Fₙ²` by Cassini's identity. **φ arrives as the fixed point of `x = 1 + 1/x`**, the value at which "add the previous term" and "multiply by a constant" become the same instruction.

## 3.3 Module 3 — Tuned Comparisons

**Central result:** the tuned difference `h_r(a,b) = b − r·a` passes through a geometric factor and differences the polynomial underneath it, annihilating `p(n)·rⁿ` at depth `k+1`.

**And it contains both earlier lineages.** Dial at 1 is Module 1; constant polynomial is Module 2's ratio test. **It also repairs Module 2's partiality** — `b − r·a` is total where `b/a` was not.

**Two results about what a tree knows about itself.** A single corrupted term produces a **signed-binomial damage wedge** whose right edge is the corrupted index and whose outermost entry gives the error's size — so a String Tree reports *where*, not merely *that*. And the **left edge** — one entry per level — rebuilds the whole tree, in `k+1` numbers, which is minimal.

**Also:** the right comparison for a family is that family's own recurrence, so `c − b − a` kills Fibonacci at depth 1; and composing two tuned differences at φ and ψ gives exactly that integer rule, the irrationals entering and cancelling.

## 3.4 Module 4 — Number Without a Base

**Central result:** the lineage **commutes with encoding.** Write every term as a register in any base, difference the registers position by position with signed digits and never carrying, decode any level — and you get exactly the value-level lineage. Verified in bases 10, 2 and 3.

**The corollary the module is named for:** **carrying and borrowing are normalisation, not arithmetic.** The arithmetic finishes with digits still outside the alphabet; tidying them is a separate pass, and it is the *sequential* part.

**Where the theorem stops**, stated because a result is only as good as its boundary: it needs only adding and scaling. Difference and sum pass through position-wise; **multiplication is carry-free too but convolves** rather than acting position by position; division inherits none of it.

**And what forces normalisation: comparison.** Two registers can hold one value and share no digit, so equality cannot be decided by inspection. **Computation defers normalisation; comparison forces it.**

## 3.5 Module 5 — Sum and Product

**Completes an enumeration** Module 1 §5.3 made and the series left two-thirds undone.

**Central discovery:** the **sum lineage is Module 3's dial at `r = −1`.** It had been covered four modules before it was named — nobody had turned the dial to a negative number.

**Difference and sum are one triangle** — the same closed form over Pascal, read with alternating signs or with all signs positive. That is why one annihilates by cancellation and the other doubles.

**The second bridge:** `product = exp ∘ sum ∘ log`, exactly parallel to Module 2's, for the same reason. **And the dial exists multiplicatively too**, `b / aʳ`, killing doubly-exponential strings at depth 1.

**The family:** two arithmetics by two directions. Additive relationships terminate at 0, multiplicative ones at 1 — **each is the identity of its own arithmetic.**

**And the sum lineage earns its keep:** the stride-two difference **factors** as difference composed with sum, in either order — which also answers a question Module 1 never asked, namely why comparisons are defined on *adjacent* terms at all. They need not be.

## 3.6 Module 6 — Digit Sets

**Closes a hole Module 4 created** by saying "allow signed digits" without asking which.

**Two requirements, reached independently, that turn out to be one inequality.**

**Uniqueness of zero:** if the digit bound satisfies `a ≤ r − 1`, a register is zero if and only if every digit is zero — by top-digit dominance. **The system stays redundant for every nonzero value and is unique exactly at zero**, which is precisely where uniqueness was needed. Terminator detection becomes digit-local.

**Carry-free addition** (Avizienis, 1961) requires `(r+1)/2 ≤ a ≤ r−1`.

**Together they force `r ≥ 3`**, and at radix three the bound is `2 ≤ a ≤ 2` — a single possible value, digit set `{−2 … 2}`, no design freedom left. **Binary admits no carry-free signed-digit addition at all.**

**Verified end to end:** a complete String Tree run in signed ternary, reaching Root `= 2 = 2!` and an all-zero Terminator, **never normalising once.**

**And Module 4's principle is sharpened to a proof:** a process that answers by termination never normalises at all. **Normalisation is for readers.**

---

# 4. Consolidated Results

**Every theorem in the series, with its home.** Results marked *verified* were checked numerically as well as proved.

| Result | Module |
|-----------------------------------------------------------------------------|-----------------------|
| Root Theorem — descent goes constant at depth *k*, constant is *k*! | 1 §9 |
| Two independent proofs of it — degree descent, and counting surjections | 1 §9.5, §9.6 |
| Root Law — `R = A·k!`, the Root sees only degree and leading coefficient | 1 §10 |
| Reading a tree backwards to recover degree and leading coefficient | 1 §11 |
| Comparative Split is irreversible if the sign channel is discarded | 1 §6.3 |
| Ratio Root Theorem — geometric roots at depth 1, value *r* | 2 §2.3 |
| The Bridge — `ratio = exp ∘ difference ∘ log` | 2 §6.2 |
| Difference is total; ratio is partial | 2 §4.2 |
| `Δ(rⁿ) = rⁿ(r−1)` — differencing *scales* geometrics, never reduces them | 2 §7 |
| Non-termination is invisible in finite data | 2 §8 |
| Fibonacci gap exact at every step — `(−1)ⁿ/(φⁿFₙ)` and `(−1)ⁿ/Fₙ²` | 2 §10 |
| φ is the fixed point of `x = 1 + 1/x` | 2 §10.3 |
| Tuned Root Theorem — `p(n)rⁿ` dies at depth `k+1` | 3 §2.4 |
| The tuned difference contains Modules 1 and 2 as special cases | 3 §3 |
| Damage wedge — signed binomial, right edge is the corrupted index | 3 §5.3 |
| Left edge rebuilds the tree; `k+1` numbers is minimal | 3 §6 |
| `h_φ ∘ h_ψ` equals the integer three-term Fibonacci rule | 3 §4.4 |
| The lineage commutes with encoding, digit-wise, no carrying | 4 §7 |
| Carrying and borrowing are normalisation, not arithmetic | 4 §8.2 |
| Multiplication is carry-free but convolves | 4 §8.5 |
| Comparison forces normalisation; computation defers it | 4 §8.6 |
| A number base must have at least two symbols | 4 §4.3 |
| The sum lineage is the tuned difference at `r = −1` | 5 §4.1 |
| Difference and sum are one triangle, signed and unsigned | 5 §5.2 |
| `product = exp ∘ sum ∘ log` | 5 §7 |
| The terminator is the identity of its arithmetic — across all four | 5 §8.1 |
| Stride-two difference factors as difference ∘ sum | 5 §8.2 |
| All four relationships rebuild from one anchor | 5 §9 |
| A Direct Substring commutes with the lineage iff it is linear | 5 §10.1 |
| Zero is unique whenever `a ≤ r − 1` | 6 §4 |
| Unique zero and carry-free together force `r ≥ 3` | 6 §6.2 |
| At radix 3 the digit set is `{−2 … 2}`, uniquely | 6 §6.2 |
| Binary admits no carry-free signed-digit addition | 6 §7 |
| A process answering by termination never normalises | 6 §11 |

---

# 5. Notation Across the Series

| Symbol | Meaning | Introduced |
|---------------------------|----------------------------------------------|---------------------------|
| P^f^ | Prime String — a seed and a rule applied repeatedly | 1 §3 |
| B^k\|f^ | Base String — each Prime value raised to the power *k* | 1 §4 |
| jS^k\|f^ | The *j*-th substring | 1 §5 |
| `0S = B` | The Base String is the substring of depth zero | 1 §2.3 |
| `ᴰjS` , `ᶜjS` | Direct and Comparative substrings | 1 §5.2, §5.3 |
| [ sign \| magnitude ] | The Comparative Split | 1 §6 |
| R^k^ | The Root String value | 1 §8 |
| jS~÷~ | A ratio substring | 2 §2.1 |
| [ direction \| factor ] | The Split in multiplicative form | 2 §5 |
| h~r~(a,b) = b − r·a | The tuned difference, tuning *r* | 3 §2.1 |
| jS~(r)~ | Substring under the tuned difference | 3 §2.1 |
| *r* , *a* | Radix and digit bound | 6 §2 |

**One known weakness, recorded rather than hidden.** The Base String symbol carries the Prime-generating function in every occurrence, and in practice that function almost never varies. **Both readers who tested Module 1 stalled on the six-position symbol and neither stalled on the mathematics.** Dropping to B^k^ and naming the generating function in prose would cost nothing and remove the series' single largest source of reader friction. **That is a change to the framework's notation and is not made unilaterally here.**

---

# 6. Open Threads

**Named rather than promised**, and carried forward so they do not drift.

| Thread | Where it was opened |
|---------------------------------------------------------------------------|-------------------------|
| Composite tunings where a ratio repeats | 3 §10 |
| Whether more than one error can be **corrected**, not merely located | 3 §5.5, §6.3 |
| Multiplication inside a bounded digit set — what bound a convolution needs | 6 §14 |
| Relationships outside the four — `max`, `min`, `gcd` — an **extension**, not a completion | 5 §13 |
| **The join between the digit layer and the carrier** | 6 §14 |

**The last of these is the significant one.** Everything in Modules 4–6 concerns digits and positions and would run identically on any parallel arrangement whatever. **Nothing in the series so far touches the vertex topology the surrounding framework is built on.**

---

# 7. Where the Series Goes Next

**The next assumption to fall is the value domain.** Modules 1–6 removed the assumption that a number must be written in a particular base. They left standing a larger one: **that the values are ordinary integers at all.**

Two directions open, and they are different sizes.

**The golden ring.** Over the integers, the Comparative Split factors a value into a unit and a magnitude, and the unit group is just `{+1, −1}` — which is exactly the `±a` of Module 6's digit set. **Over `ℤ[φ]` the unit group is infinite**, and the split survives for a reason that has to be earned. This is the smaller step and it is directly continuous with Module 6.

**The quaternion packing.** A quaternion holds four components; a lineage of a cubic holds four orders. **The registration `q = (W, ΔW, Δ²W, Δ³W)` packs one into the other**, and this is where String Mathematics meets the framework's own carrier.

**A warning about that second direction, stated in advance.** The obvious question — whether the carrier's own rotation can advance such a registration — **has a negative answer.** The lineage operator is unipotent and of infinite order; a rotation in the carrier is an isometry of finite order; **nilpotency and periodicity are different closure laws.** Any module on the packing will have that theorem at its centre, and it is a genuine result rather than a difficulty to be worked around.

---

# 8. On Method

**The series carries a discipline as well as a subject**, and it is worth stating in one place because it is unusual in a mathematics text.

- **A sample proves presence and never absence.** A check that finds nothing has established nothing about what it did not examine. *(1 §9.4)*
- **Verification must vary the question, not merely the method.** Two calculations sharing an unexamined assumption agree whether or not it is true. *(1 §9.7)*
- **State the region a check covered**, or it cannot be told apart from one that covered everything. *(2 §8.4)*
- **Independent observations add weight; independent mechanisms explaining one observation add robustness only.** *(3 §7.1)*
- **A result is only as good as its boundary** — say where it stops. *(4 §7.5)*

**These are not decoration.** Every one of them was earned by an error found in this series during its own writing, and several were found by readers who were not mathematicians. The revision histories record which.

---

*End of Series Summary.*
