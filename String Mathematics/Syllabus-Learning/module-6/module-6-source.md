---
title: "String Mathematics — Module 6"
subtitle: "Digit Sets: Redundancy, Carry-Free Arithmetic, and Why Three"
author: "Prime Framework — Syllabus-Learning Series"
date: "Module 6 of the String Mathematics syllabus — Version 2"
---

# Module 6 — Digit Sets

## Redundancy, Carry-Free Arithmetic, and Why Three

**Version 2.** Prerequisite: Modules 1 and 4.

---

# 0. How to Use This Module

## 0.1 What you need

**Module 4** — registers, weights, signed digits, and the result that carrying is normalisation rather than arithmetic. **Module 1** for the String Tree and the Root, since §8 rebuilds one from scratch.

Modules 2, 3 and 5 are not assumed.

## 0.2 The question this module answers

Module 4 established that you can difference a whole String Tree digit by digit, in any number base, **allowing digits to go negative and never carrying once.** That result is correct and it is proved there.

**But it left a hole, and this module exists because of it.** Module 4 said "allow signed digits" without ever asking:

- **Which** signed digits? How far outside the alphabet are we allowed to go?
- Does the answer of a digit-wise operation **stay** inside whatever set we chose, or does it drift wider at every step?
- If digits may be signed, **can two different registers be the same value** — and if so, how would we ever recognise a Terminator?

**Those three questions have one answer**, and it turns out to select a number base rather than merely permit one.

## 0.3 Attribution, stated up front

**The carry-free signed-digit scheme in §5 is not new and is not this framework's.** It is due to **Avizienis (1961)** and is standard in computer arithmetic. What this module does is derive its constraint alongside a second, independent requirement — unique representation of zero — and show that **the two are the same inequality**, which is the part worth having.

---

# 1. The Hole Module 4 Left

Module 4 §7 differenced the squares digit by digit in base ten and produced entries like `(−3, 1)`, decoding to 7. In base three it produced `(2, 3, −1)`, decoding to 2 — **containing a digit of 3, which does not exist in base three.**

Module 4 was right that this costs nothing in exactness. **It never asked whether it costs anything in principle.**

**It does, in two ways.**

**Growth.** Subtract two base-ten registers whose digits run 0 to 9 and the result runs −9 to 9. Subtract two of *those* and it runs −18 to 18. **Left unchecked, the digits get wider at every level of the tree**, and a machine holding a fixed number of symbols per position eventually cannot hold them.

**Recognition.** Module 4 §8.6 noted that `(−3, 1)` and `(7, 0)` are the same value with no digit in common. Extend that worry to zero and it becomes serious: **if a Terminator can be spelled in more than one way, no machine can recognise one by looking.**

> **A String Tree that cannot recognise its own Terminator has no way of reporting an answer.**

---

# 2. Digit Sets

A register is a list of positions over a base, and until now the digits were whatever they happened to be. **Fix them deliberately.**

> ### Digit set
> For a radix *r*, the **digit set** `{−a, …, −1, 0, 1, …, a}` is the range of values a single position is permitted to hold. The number *a* is the **digit bound**.

Two familiar cases:

| System | radix *r* | digit bound *a* | digits |
|-------------------------------|----------------|--------------------------------|----------------------|
| ordinary decimal | 10 | — (unsigned, 0 to 9) | 0 … 9 |
| balanced ternary | 3 | 1 | −1, 0, +1 |
| **the system this module reaches** | **3** | **2** | **−2, −1, 0, +1, +2** |

**The digit bound is the whole design.** Choose it too small and arithmetic will not close; choose it too large and, as §4 shows, something important breaks.

---

# 3. Redundancy Is Real

When the digit set holds more than *r* values, **some quantities have more than one spelling.**

At radix 3 with bound 2 the digit set holds five values against a radix of three, so redundancy is guaranteed. **Two worked cases:**

```
1  =  (1, 0)      1
1  =  (-2, 1)    -2 + 3   =  1        same value, no digit in common

2  =  (2, 0)      2
2  =  (-1, 1)    -1 + 3   =  2        same value, no digit in common
```

**This is not a defect.** Redundancy is what buys carry-freedom in §5 — a position that may overshoot can absorb a difference without asking its neighbour for help. **But it is exactly what makes the recognition problem of §1 look fatal**, and that is what §4 settles.

---

# 4. ⭐ But Zero Has Only One Spelling

**This is the result that makes the whole scheme usable**, and it is not obvious: a redundant system in which almost every value has several spellings can still have **exactly one spelling for zero.**

## 4.1 The claim

> ### THEOREM (uniqueness of zero)
> If the digit bound satisfies `a ≤ r − 1`, then a register has value zero **if and only if every one of its digits is zero.**

## 4.2 The proof, and it is three lines

Suppose some digit is not zero. Let *p* be the **highest** position holding a nonzero digit. That digit contributes at least r^p^ in size. Everything beneath it contributes at most

```
a·r^0^  +  a·r^1^  +  …  +  a·r^(p−1)^   =   a·(r^p^ − 1)/(r − 1)
```

and since `a ≤ r − 1`, that whole tail is at most r^p^ − 1.

**So the top digit outweighs everything below it, with at least 1 to spare:**

```
|value|   ≥   r^p^  −  (r^p^ − 1)   =   1   >   0
```

**A single nonzero digit anywhere forces the value away from zero.** ∎

## 4.3 Why this settles §1's recognition problem

> **Terminator detection becomes local.** To decide whether a register is zero you look at its digits and nothing else — no evaluation, no normalisation, no carry chain, no comparison with a neighbour.
>
> **And it costs no loss of redundancy anywhere else.** §3's two spellings of 1 and of 2 are untouched. **The system is redundant for every nonzero value and unique exactly at zero** — which is precisely, and only, where uniqueness was needed.

*It is worth noticing how narrow the hypothesis is: `a ≤ r − 1`. Nothing about signs, nothing about the base being three. §6 shows this same inequality arriving from a completely different direction.*

---

# 5. Carry-Free Addition

## 5.1 The problem with adding digit by digit

Add two registers position by position and the sums run from `−2a` to `+2a`, **which is outside the digit set.** Module 4 allowed exactly this and simply let the digits grow. **To keep them bounded, each position must hand something to its neighbour** — and the danger is that the hand-off cascades the length of the register, which is the sequential chain Module 4 §8.3 identified.

## 5.2 The two-step that stops the cascade

**Split each position's sum before adding anything in.** For each position independently:

```
step 1:   s = x + y            the raw digit sum, from -2a to 2a
          write   s  =  r·c  +  w        with  |c| <= 1  and  |w| <= a - 1

step 2:   z  =  w  +  (the c produced by the position below)
```

**The point is what step 1 does not depend on.** The carry `c` leaving a position is computed from that position's own two input digits **and nothing else** — in particular, not from the carry arriving from below. So no carry can trigger another carry.

> ### Every position finishes in two steps, whatever the length of the register.
> **The depth is constant. Nothing propagates.**

## 5.3 Worked: 5 + 7 in radix 3

```
5  =  (-1, -1,  1)      -1 - 3 + 9  =  5
7  =  ( 1, -1,  1)       1 - 3 + 9  =  7

raw sums  s  =  ( 0, -2,  2)

  s = 0  ->  c = 0,  w =  0
  s = -2 ->  c = -1, w =  1        since  -2 = 3(-1) + 1
  s = 2  ->  c = 1,  w = -1        since   2 = 3(1) - 1

  z0 = 0 + 0    =  0
  z1 = 1 + 0    =  1
  z2 = -1 + -1  = -2
  z3 = 0 + 1    =  1

result  ( 0, 1, -2, 1)   =   0 + 3 - 18 + 27   =   12
```

**5 + 7 = 12.** ✔ Every digit landed inside `{−2 … 2}`, and **no carry moved more than one position.**

---

# 6. ⭐ Two Conditions, One Inequality

**Now put the two requirements side by side**, because they were reached independently and they turn out to be the same constraint.

## 6.1 What each one demands

**Uniqueness of zero** (§4.2) demanded

```
a  <=  r - 1
```

**Carry-freedom** (§5.2) demands two things. First, the final digit `z = w + c` must stay inside the digit set: since `|w| ≤ a−1` and `|c| ≤ 1`, that gives `|z| ≤ a` automatically — **but only if the split of step 1 is possible at all**, which requires the largest raw sum to be reachable:

```
2a  <=  r  +  (a - 1)          that is,        a  <=  r - 1
```

**The same inequality.** And second, *every* raw sum in the range must be splittable, which requires the choices of `w` to cover a complete set of residues:

```
2(a - 1) + 1  >=  r            that is,        a  >=  (r + 1)/2
```

## 6.2 What they force together

Both must hold, so:

```
(r + 1)/2   <=   a   <=   r - 1
```

**A digit bound exists only when the two ends do not cross:**

```
(r + 1)/2  <=  r - 1     =>     r + 1  <=  2r - 2     =>     r  >=  3
```

> ### THEOREM
> **Requiring both unique representation of zero and carry-free addition forces the radix to be at least three.**
> **And at radix three the digit bound is `2 ≤ a ≤ 2` — a single possible value.** The digit set is `{−2, −1, 0, +1, +2}`, uniquely.

## 6.3 What that means

**Three is not chosen here. It is the smallest number that survives two independent requirements**, and at that value there is no design freedom left at all — the digit set is determined.

| radix | required bound | available bound | verdict |
|---------------|-------------------------|----------------------------|-------------------------------|
| 2 | `a ≥ 1.5` | `a ≤ 1` | **impossible** |
| **3** | `a ≥ 2` | `a ≤ 2` | **exactly one system** |
| 4 | `a ≥ 2.5` | `a ≤ 3` | `a = 3` |
| 10 | `a ≥ 5.5` | `a ≤ 9` | several |

---

# 7. Why Binary Cannot

**Radix two deserves its own paragraph**, because it is the one everybody expects to work.

At `r = 2` the bound must satisfy `a ≤ 1`, so the only signed digit set available is `{−1, 0, +1}`. Then `|w| ≤ a − 1 = 0`, which forces `w = 0`, and step 1 becomes

```
s  =  2c        with   |c| <= 1
```

**That can only represent even values of `s`.** A raw sum of 1 — which arises the moment you add `1` and `0` — has no split at all.

> **Binary admits no carry-free signed-digit addition.** Not because the technique is unavailable but because there is no room: with only three digits, once you reserve the interim range you have nothing left to reserve.

*Binary arithmetic can of course be made fast by other means. What it cannot be made is carry-free in the sense of §5.2, where each position's outgoing carry depends only on that position's own inputs.*

---

# 8. A Complete String Tree in Signed Ternary

**The test that matters: build a whole String Tree, never leave the digit set, never normalise, and see whether the Root survives.**

Take Module 1's squares — 0, 1, 4, 9, 16, 25 — and write each as a radix-3 register, least-significant-first:

```
 0 = (0, 0, 0, 0)      1 = (1, 0, 0, 0)      4 = (1, 1, 0, 0)
 9 = (0, 0, 1, 0)     16 = (1,-1,-1, 1)     25 = (1,-1, 0, 1)
```

**Checks:** 16 is `1 − 3 − 9 + 27` ✔; 25 is `1 − 3 + 27` ✔.

## 8.1 The descent

Each level: subtract digit-wise, then apply §5.2's two-step to bring digits back inside `{−2 … 2}`.

```
B     (0,0,0,0)  (1,0,0,0)  (1,1,0,0)  (0,0,1,0)  (1,-1,-1,1)  (1,-1,0,1)
         0          1          4          9           16          25

1S      (1,0,0,0)  (0,1,0,0)  (-1,-1,1,0)  (1,-1,1,0)  (0,0,1,0)
            1          3           5           7           9

2S        (-1,1,0,0)  (-1,1,0,0)  (2,0,0,0)  (-1,1,0,0)
              2           2           2           2          <- ROOT = 2 = 2!

3S          (0,0,0,0)  (0,0,0,0)  (0,0,0,0)                  <- TERMINATOR
```

**Decode the Root row to check it:** `−1 + 3 = 2` for three of them, and `2` for the fourth. **All four are the value 2**, which is `2!`, exactly as Module 1's second-order tree requires.

## 8.2 Two things to notice in that table

**The Root row is redundant, visibly.** Three entries read `(−1, 1, 0, 0)` and one reads `(2, 0, 0, 0)`. **Same value, no digit in common.** The tree does not care, and neither does §4 — because the Root is not zero, and only zero needed uniqueness.

**The Terminator row is not redundant.** Every entry is all-zeros, because §4.1 leaves it no alternative. **That is what makes the answer readable by inspection.**

---

# 9. The Reduction Does Not Cascade

**This is worth seeing explicitly**, because the naive way of tidying digits does cascade and it is easy to assume the fast way must too.

Take the raw subtraction that produced the second Terminator entry:

```
2S~2~ − 2S~1~   =   (2, 0, 0, 0)  −  (-1, 1, 0, 0)   =   (3, -1, 0, 0)
```

**Every digit there is legal-looking nonsense** — a 3 in radix three — and the value is `3 − 3 = 0`.

**Tidied the naive way**, position by position: the 3 becomes 0 and hands 1 upward; position 1 becomes `−1 + 1 = 0`. **Two steps, and the second could not begin until the first had finished.** On a long register that chain runs the whole length.

**Tidied by §5.2**, every position at once:

```
  s0 = 3   ->  c = 1,  w = 0
  s1 = -1  ->  c = 0,  w = -1

  z0 = 0 + 0   = 0
  z1 = -1 + 1  = 0
  z2 = 0 + 0   = 0

  (0, 0, 0, 0)      zero, in one parallel step
```

**Same answer. No chain.** And the same for the third entry, from `(−3, 1, 0, 0)`: `c = −1, w = 0` at position 0 and `w = 1` at position 1 give `z1 = 1 − 1 = 0`, all zero again.

---

# 10. What the Whole Tree Costs

With §4 and §5 in hand the accounting is straightforward, and it is worth stating because Module 4 could not.

| Stage | Depth |
|--------------------------------------------------|--------------------------------------------------|
| one subtraction at one position | **constant** |
| the two-step reduction | **constant** — it never cascades (§9) |
| one whole level of the tree | **constant**, all positions in parallel |
| a descent of depth *k* | **proportional to *k*** |
| deciding a register is zero | **constant per position** (§4) |
| deciding a whole level is the Terminator | **logarithmic** in the number of digits |
| normalising | **never performed** |

> **The only part that is not constant-depth is asking a question about *all* positions at once** — and that cost is unavoidable in any system whatever, because it is the cost of a global question rather than of this representation.
>
> **What the signed digit set removes is the sequential carry chain**, which would otherwise sit inside every single operation rather than once at the end.

**A boundary held deliberately:** these are depths of a mathematical procedure. **What a machine built on this would cost is compute architecture and is not developed in this syllabus.**

---

# 11. Normalisation Is For Readers

Module 4 §8.2 concluded that carrying and borrowing are normalisation rather than arithmetic. **This module sharpens that to something stronger than it could then support.**

Module 4 still expected normalisation *eventually* — to write an answer down. **§4 removes even that, for the only question a String Tree actually asks.**

> ### A String Tree reports its answer by reaching its Terminator, and a Terminator is recognisable **without normalising anything.**
> **So a process that answers by termination never normalises at all.** Normalisation is required at exactly one moment: **when a human wants to read a number.**

*Module 4 arrived at "normalisation is for readers" as a description. Here it becomes a design principle with a proof behind it: the arithmetic never needs it, the reduction of §5 is not it, and the answer does not require it.*

---

# 12. Exercises

## 12.1 Problems

**Exercise 1.** Give two different radix-3 registers, digits in `{−2 … 2}`, both equal to 4. Confirm both by decoding.

**Exercise 2.** Is `(1, −2, 1)` in radix 3 equal to zero? Decide by §4 **without decoding**, then decode to confirm your reasoning was sound.

**Exercise 3.** Add 4 and 5 in radix 3 using the two-step of §5.2. Show the raw sums, the split, and the result, and confirm no carry travelled more than one position.

**Exercise 4.** Apply §6.2 to radix 5. What digit bounds are permitted? Is the system unique?

**Exercise 5.** Explain in one sentence why a digit bound of `a = r` — one larger than §4 allows — would break Terminator detection. Give a radix-3 example.

**Exercise 6.** Take the cubes 0, 1, 8 as radix-3 registers and compute the first two entries of the first substring digit-wise. Decode to check against Module 1.

**Exercise 7.** Module 4 allowed digits to grow without bound. **What goes wrong across a deep tree if you never reduce?** Answer in terms of what a position must hold.

**Exercise 8.** Why does the Root row in §8.1 not need to be unique, when the Terminator row does?

## 12.2 Answers

**Exercise 1.** `4 = (1, 1, 0)` since `1 + 3 = 4` ✔, and `4 = (−2, 2, 0)` since `−2 + 6 = 4` ✔. Two spellings, no digit in common.

**Exercise 2.** **No.** By §4.1 a register in a system with `a ≤ r − 1` is zero only if every digit is zero, and this one has nonzero digits. Decoding confirms it: `1 − 6 + 9 = 4`, and 4 is not 0. ✔

*The point of the exercise is that the first sentence settled it and the decoding was only a check on the reasoning.*

**Exercise 3.** `4 = (1, 1, 0)` and `5 = (−1, −1, 1)`.

```
raw sums  s = (0, 0, 1)

  s = 0  ->  c = 0, w = 0
  s = 0  ->  c = 0, w = 0
  s = 1  ->  c = 0, w = 1

  z0 = 0,  z1 = 0,  z2 = 1 + 0 = 1

result (0, 0, 1) = 9
```

**4 + 5 = 9** ✔. No carry was generated at all here, which is the easy case — but the structure is the same, and no position consulted any other.

**Exercise 4.** At `r = 5` the constraint is `(5+1)/2 = 3 ≤ a ≤ 4`. **So `a = 3` or `a = 4` — two systems, not one.** Radix 5 has design freedom; radix 3 has none.

**Exercise 5.** With `a = r` the tail can exactly cancel the leading digit, so a register of nonzero digits can have value zero — and a Terminator would then be unrecognisable by inspection. In radix 3 with `a = 3` the register `(3, −1)` is `3 − 3 = 0` **while containing no zero digit at all.**

**Exercise 6.** `0 = (0,0,0)`, `1 = (1,0,0)`, `8 = (−1, 0, 1)` since `−1 + 9 = 8` ✔.

```
1S~0~ = 1 - 0  =  (1, 0, 0)            =  1
1S~1~ = 8 - 1  =  (-2, 0, 1)           =  -2 + 9  =  7
```

Module 1's cubic tree has first substring 1, 7, 19, … ✔ — and note `−2` is inside the digit set, so no reduction was needed.

**Exercise 7.** **A position must hold a wider and wider range of values.** Each level of differencing can double the digit bound, so after *k* levels a position may need to hold values of order 2^k^ times the original bound — and any real register with a fixed number of symbols per position eventually cannot. **Reduction is what makes the depth of the tree independent of the width of a position.**

**Exercise 8.** Because **uniqueness is only ever needed where recognition is needed.** The Root is a value to be read once, at the end, by whoever wants it; the Terminator is a condition the process must test for itself, repeatedly, without reading anything. §4 supplies uniqueness exactly at zero and nowhere else — which is exactly the distribution required.

---

# 13. Glossary, Notation, and Status

## 13.1 Terms

| Term | Meaning |
|-------------------------------------|---------------------------------------------------------------|
| **Digit set** | The values one position may hold: `{−a … a}` for digit bound *a* |
| **Digit bound** | The number *a*; the largest magnitude a single position may carry |
| **Redundant** | A system in which some values have more than one register |
| **Carry-free** | Each position's outgoing carry depends only on that position's own inputs |
| **The two-step** | Split each raw sum into carry and interim, then add the carry from below |
| **Reduction** | Returning digits to the digit set by the two-step; constant depth |
| **Normalisation** | Returning digits to an *unsigned* alphabet for a human reader; sequential |

## 13.2 Status of claims

| Result | Status |
|-----------------------------------------------|-----------------------------------------------------|
| Redundancy is real at radix 3, bound 2 | **Fact**; two spellings each shown for 1, 2 and 4 |
| **Zero is unique whenever `a ≤ r − 1`** | **Theorem** (§4.2), proved by top-digit dominance |
| Carry-free addition requires `(r+1)/2 ≤ a ≤ r−1` | **Theorem** (§6.1) — the scheme is Avizienis (1961) |
| **Both conditions together force `r ≥ 3`** | **Theorem** (§6.2) |
| At `r = 3` the digit set is `{−2 … 2}`, uniquely | **Theorem** (§6.2) |
| Binary admits no carry-free signed-digit addition | **Theorem** (§7); the raw sum 1 has no split |
| A full String Tree runs in `{−2 … 2}` and reaches its Root | **Verified** (§8.1), by hand, on the squares |
| The reduction does not cascade | **Theorem** (§5.2); demonstrated against the naive method (§9) |
| Terminator detection is digit-local | **Corollary** of §4 |
| A process answering by termination never normalises | **Theorem** (§11) |
| Machine cost of any of this | **Out of scope** — compute architecture, not developed here |

## 13.3 A note on provenance

**The radix-3 conclusion in §6 is derived here from two stated requirements.** It is a consequence of those requirements and of nothing else.

**This module does not claim that any surrounding framework document specifies radix three**, and no such document has been consulted for this purpose. **If a corpus source states it independently, that would be a separate and stronger fact than anything proved here** — and it would need citing, not assuming.

---

# 14. Looking Ahead

**Two threads open directly from this module.**

**Multiplication in a bounded digit set.** Module 4 §8.5 showed multiplication convolves rather than acting position by position, and that its product digits can run far outside any alphabet. **What digit bound a convolution needs, and whether it can be reduced in constant depth the way §5 reduces a sum, is not settled here.**

**And the join that is still missing.** Everything in this module concerns digits and positions. **None of it touches the carrier** — the vertex topology the surrounding framework is built on. The arithmetic here would run identically on any parallel arrangement whatever. **Connecting a digit layer to a vertex layer is the open problem, and it is named rather than promised.**

**Older threads still open**, restated so they do not drift: composite tunings where a ratio repeats (Module 3 §10), and whether more than one error can be corrected rather than merely located (Module 3 §5.5, §6.3).

# Revision History

**Version 2.** **Notation rendering.** Notation written inside code spans was displaying as raw markup — a superscript marker appearing as a literal character instead of raising the symbol — and the escape before a vertical bar was visible as a backslash. **A code span suppresses exactly the formatting the notation needs.** All affected notation now renders as true superscripts and subscripts. Verified in the document's own markup rather than in a text extraction, because a text extraction flattens a superscript and cannot tell a rendered one from a broken one.


**Version 1.** Initial issue.

---

*End of Module 6, Version 2.*
