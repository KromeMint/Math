---
title: "String Mathematics — Module 5"
subtitle: "Sum and Product: Completing the Four Relationships"
author: "Prime Framework — Syllabus-Learning Series"
date: "Module 5 of the String Mathematics syllabus — Version 2"
---

# Module 5 — Sum and Product

## Completing the Four Relationships, and the Family They Turn Out to Be

**Version 2.** Prerequisite: Modules 1, 2 and 3. Module 4 is not assumed.

---

# 0. How to Use This Module

## 0.1 What you need

**Module 1** for the String Tree and the Root. **Module 2** for the ratio lineage and the logarithmic bridge. **Module 3** for the tuned difference and its dial.

**Module 4 is not required.** Nothing here depends on registers or number bases.

## 0.2 What this module does — and what it does not

**It introduces no new machinery whatsoever.** There is no new operator, no new notation, and no new theorem-generating device. Everything below is built from tools already on the bench.

What it does instead is **finish an enumeration the syllabus has left two-thirds undone for four modules** — and discover that the four relationships were never four things.

> **This is a lateral module.** It does not climb; it fills in. Read it before anything that goes further up.

---

# 1. The Enumeration Left Unfinished

Module 1 §5.3 defines a comparative substring and lists the relationships it may use:

| Relationship | Definition | Where the syllabus has used it |
|----------------------------------|-------------------------------|-----------------------------------|
| **Difference** | h(a,b) = b − a | Module 1, and tuned in Module 3 |
| **Sum** | h(a,b) = a + b | **nowhere** |
| **Product** | h(a,b) = ab | **nowhere** |
| **Ratio** | h(a,b) = b / a | Module 2 |

**Two of the four have never been used.** They were listed in the first module and then quietly passed over, and no module since has said why.

**There is no good reason.** They are not harder, they are not degenerate, and they are not covered by what came before — although, as §5 will show, one of them turns out to have been covered all along without anybody noticing.

---

# 2. The Sum Lineage

## 2.1 Definition

```
h(a, b)  =  a + b
```

The substring at each level is formed by adding adjacent values instead of subtracting them. Everything else about a String Tree is unchanged — the same layers, the same shortening by one term per level, the same reading downward.

## 2.2 Worked on the squares

Take Module 1's second-order Base String and add instead of subtract:

```
B      0     1     4     9    16    25
1S        1     5    13    25    41
2S           6    18    38    66
3S             24    56   104
```

Each entry, so nothing is taken on trust: 0+1=1, 1+4=5, 4+9=13, 9+16=25, 16+25=41; then 1+5=6, 5+13=18, 13+25=38, 25+41=66; then 6+18=24, 18+38=56, 38+66=104.

**No Root. No Terminator. The values grow.**

## 2.3 The failure is informative, not embarrassing

Module 2 met a tree that would not terminate and treated it as a mismatch between instrument and object rather than a defect. **The same reading applies here**, but the mechanism is the opposite one.

- **Differencing strips** — it removes a degree at every level until nothing is left.
- **Summing accumulates** — it combines two values into a larger one at every level, so nothing is ever removed.

> **The difference lineage is subtractive and terminates by exhaustion. The sum lineage is additive and terminates only by cancellation.** They fail on opposite things for opposite reasons.

---

# 3. What the Sum Lineage Does Terminate On

A sum lineage reaches zero exactly when adjacent values cancel:

```
a + b = 0        that is,      b = −a
```

So it terminates on strings that **flip sign at every step.**

## 3.1 The simplest case

```
B      3    -3     3    -3     3
1S        0     0     0     0        <- TERMINATOR at depth 1
```

Every adjacent pair sums to zero. **Depth 1**, exactly as a geometric string of ratio 2 reached its ratio-Root at depth 1 in Module 2.

## 3.2 A case with structure underneath

Take an alternating string with a polynomial riding on it — B~n~ = n·(−1)^n^:

```
B      0    -1     2    -3     4    -5
1S       -1     1    -1     1    -1
2S          0     0     0     0        <- TERMINATOR at depth 2
```

Working: 0+(−1) = −1, (−1)+2 = 1, 2+(−3) = −1, (−3)+4 = 1, 4+(−5) = −1; then (−1)+1 = 0, four times.

**Depth 2** — one more than the degree of the polynomial riding on the alternation. **That number should look familiar**, and §5 explains why it must be so.

---

# 4. Two Names for One Instrument

## 4.1 The sum lineage is the tuned difference at minus one

Module 3 built a comparison with a dial on it:

```
h~r~(a, b)  =  b − r·a
```

**Set the dial to −1:**

```
h~−1~(a, b)  =  b − (−1)·a  =  b + a
```

> ### The sum lineage is not a new relationship. It is Module 3's tuned difference with the dial at minus one.

**Everything Module 3 proved therefore applies to it without a further word.** In particular the Tuned Root Theorem — a polynomial of degree *k* times a geometric of ratio *r* is annihilated at depth *k*+1 — becomes, at *r* = −1:

> **A polynomial of degree *k* riding on an alternating string is annihilated by the sum lineage at depth *k*+1.**

**Which is exactly what §3.2 observed by hand.** Degree 1, terminated at depth 2. It was not a coincidence and it did not need a new proof.

## 4.2 What that says about Module 3

Module 3 presented its dial as the instrument that closes polynomial-times-geometric strings, and demonstrated it at r = 2 and r = 3. **It never turned the dial to a negative number.**

> **The sum lineage was already covered by Module 3 four modules before it was named. Nobody had turned the dial that far.**

*This is worth pausing on. An enumeration can be incomplete not because a case is hard but because nobody tried the value. Module 3's dial has always ranged over every number; the syllabus only ever tested it on positive ones.*

---

# 5. One Triangle, Signed and Unsigned

Both lineages have a closed form, and they are the same closed form.

## 5.1 The sum lineage in one step

Instead of descending level by level, ask what the level-*j* substring is directly:

```
jS~n~  =  SUM over i  of   C(j, i) · B~n+i~
```

**Those are the binomial coefficients — Pascal's triangle.**

**Checked against §2.2 by hand.** At level 2, position 0: C(2,0)·B~0~ + C(2,1)·B~1~ + C(2,2)·B~2~ = 0 + 2·1 + 1·4 = **6** ✔, which is the first entry of 2S. At level 3, position 0: B~0~ + 3B~1~ + 3B~2~ + B~3~ = 0 + 3 + 12 + 9 = **24** ✔.

## 5.2 And the difference lineage

Module 1 §9.6.1 derived the corresponding formula for differences:

```
jS~n~  =  SUM over i  of   (−1)^(j−i)^ · C(j, i) · B~n+i~
```

**Identical, apart from the alternating sign.**

> ### The two lineages are one triangle. The difference lineage reads Pascal's triangle with alternating signs; the sum lineage reads the same triangle with all signs positive.
> **Nothing else distinguishes them.**

## 5.3 Why one annihilates and the other amplifies

Put the two formulas side by side and the behaviour follows immediately.

With alternating signs, the terms are set against one another, and for a polynomial of the right degree they cancel exactly — that cancellation *is* the Root Theorem. **With all signs positive nothing can ever cancel**, because every term is added to every other.

**A quick measure of the growth.** Apply the sum lineage to the constant string of value c: each level gives 2c, then 4c, then 8c.

> **The difference lineage annihilates by cancellation. The sum lineage doubles, because the row sums of Pascal's triangle are the powers of two.**

**Checked:** the row sums 1, 2, 4, 8 are exactly C(j,0)+C(j,1)+…+C(j,j) for j = 0, 1, 2, 3.

---

# 6. The Product Lineage

## 6.1 Definition and first example

```
h(a, b)  =  a · b
```

Take the geometric string of ratio 2:

```
B      2     4     8    16    32
1S        8    32   128   512
```

Working: 2·4 = 8, 4·8 = 32, 8·16 = 128, 16·32 = 512. **Growing fast, no Root.**

## 6.2 What it terminates on

A product lineage reaches **1** — the multiplicative identity — exactly when adjacent values are reciprocals:

```
a · b = 1        that is,      b = 1/a
```

So it terminates on strings that **invert at every step**:

```
B      2    1/2     2    1/2
1S        1      1      1        <- TERMINATOR at depth 1
```

---

# 7. The Second Bridge

Module 2 §6 showed that the ratio lineage is the difference lineage seen in logarithmic coordinates, because a logarithm turns division into subtraction. **The same bridge carries the product lineage onto the sum lineage**, for the same reason:

```
log(a · b)  =  log a  +  log b
```

## 7.1 Verified, not merely asserted

Take the product example of §6.1 and put it through logarithms base two.

```
B          2     4     8    16    32
log2 B     1     2     3     4     5

SUM lineage of the logarithms:   3     5     7     9
```

Working: 1+2 = 3, 2+3 = 5, 3+4 = 7, 4+5 = 9.

Now take logarithms of the product lineage from §6.1:

```
product 1S          8     32    128    512
log2 of it          3      5      7      9
```

**Identical.** ✔

> ### product lineage  =  exp ∘ (sum lineage) ∘ log
> **Exactly parallel to Module 2's bridge for ratio and difference, and true for exactly the same reason.**


## 7.2 The dial exists in the multiplicative world too

Module 3 put a dial on the difference. **The bridge says there must be one on the ratio, and there is:**

```
h~r~(a, b)  =  b / a^r^
```

Take logarithms and it becomes `log b − r·log a` — **Module 3's tuned difference exactly.** No separate theory is needed; the bridge carries the whole of Module 3 across.

**What it annihilates.** It gives 1 when b = a^r^, so it kills strings in which **each term is the previous one raised to a fixed power**:

```
B      2     4    16   256          each term is the previous one squared
1S        1     1     1             <- TERMINATOR at depth 1
```

Working: 4/2² = 1, 16/4² = 1, 256/16² = 1.

**Cross-checked through the bridge.** In logarithms base two the string is 1, 2, 4, 8, and Module 3's tuned difference at r = 2 gives 2−2·1 = 0, 4−2·2 = 0, 8−2·4 = 0 — terminating at depth 1 in the additive world, exactly as the ratio version did in the multiplicative one. ✔

> **Doubly-exponential strings are to the tuned ratio what polynomial-times-geometric strings are to the tuned difference.** They look formidable and they die at depth 1, because the instrument was built for them.

---

# 8. The Four Relationships Are One Family

Everything above assembles into a single picture.

|  | **opposing** — undo one from the other | **combining** — put the two together |
|--------------------------------------|--------------------------------|------------------------------|
| **additive world** | **difference** b − a *(Module 1)* | **sum** a + b *(§2)* |
| **multiplicative world** | **ratio** b / a *(Module 2)* | **product** ab *(§6)* |

**Read it two ways and both are informative.**

**Across the rows** — the logarithm carries the top row onto the bottom row. Difference becomes ratio; sum becomes product. **Two bridges, one mechanism**, because a logarithm turns adding into multiplying wherever it is applied.

**Down the columns** — the left column *removes* and can therefore terminate by exhaustion; the right column *accumulates* and can only terminate by exact cancellation.

> **There are not four relationships. There is one relationship, seen in two arithmetics and pointed in two directions.**

## 8.1 The terminator quartet

Module 2 §3 observed that the difference lineage terminates at 0 and the ratio lineage at 1, and named the reason: **each is the identity of the operation the lineage is built from.** With all four in hand, that rule holds across the board.

| Relationship | Terminates at | Because that value is | Terminates on |
|------------------------|--------------------|-----------------------------|--------------------------|
| difference b − a | **0** | the additive identity | polynomials |
| sum a + b | **0** | the additive identity | alternating strings |
| ratio b / a | **1** | the multiplicative identity | geometrics |
| product ab | **1** | the multiplicative identity | reciprocating strings |

**The terminator is decided by the arithmetic; the family annihilated is decided by the direction.** Neither choice affects the other, which is why the table has four entries and only two distinct terminators.


## 8.2 Composing two relationships — and why the sum lineage earns its keep

The sum lineage does not terminate on anything a working string is likely to be, which invites the question of what it is *for*. **Here is the answer, and it is structural.**

**Suppose you want to compare terms two apart** rather than adjacent — B~n~ against B~n+2~, skipping one. Call it the stride-two difference. On the squares:

```
B      0     1     4     9    16    25
stride-2:   4     8    12    16
```

Working: 4−0 = 4, 9−1 = 8, 16−4 = 12, 25−9 = 16.

**Now get there a different way — sum first, then difference:**

```
sum lineage    1     5    13    25    41
then difference   4     8    12    16
```

**Identical.** ✔ And doing it in the other order, difference first and then sum:

```
difference lineage   1     3     5     7     9
then sum                4     8    12    16
```

**Identical again**, so the two operations commute.

> ### The stride-two difference factors into the difference lineage composed with the sum lineage.
> **Neither order matters.** In the notation of Module 1 §9.6.1, where the difference is `E − I`, the sum is `E + I`, and the stride-two difference is `E² − I`, this is nothing more exotic than the difference of two squares:
>
> `(E − I)(E + I) = E² − I`

**So the sum lineage is a factor.** It is not a curiosity that fails to terminate — **it is one of the two pieces a wider comparison is built from**, and you cannot construct a stride without it.

*That also answers a question Module 1 never asked: why comparisons are defined on **adjacent** values. They need not be. A comparison at any stride is available, and it decomposes into adjacent ones.*

---

# 9. All Four Reconstruct From One Anchor

Module 1 §7.3 said a String Tree can be read upward to rebuild its parent, given one anchor value per level. **That property does not belong to differencing.** It belongs to all four.

Each relationship can be rearranged to give the next parent value:

| Relationship | Rebuild the parent by |
|----------------------------------------------------|------------------------------------------------|
| difference b − a | B~n+1~ = 1S~n~ + B~n~ |
| sum a + b | B~n+1~ = 1S~n~ − B~n~ |
| ratio b / a | B~n+1~ = 1S~n~ · B~n~ |
| product ab | B~n+1~ = 1S~n~ / B~n~ |

**Worked for the sum lineage**, which is the new one. Take B = 0, 1, 4, 9 with 1S = 1, 5, 13, and the anchor B~0~ = 0:

```
B~1~ = 1S~0~ − B~0~ =  1 − 0 =  1     OK
B~2~ = 1S~1~ − B~1~ =  5 − 1 =  4     OK
B~3~ = 1S~2~ − B~2~ = 13 − 4 =  9     OK
```

**Rebuilt exactly.**

> **Reversibility is a property of *being a two-input relationship you can solve for one input*, not a property of subtraction.** Every one of the four qualifies. **The two multiplicative ones carry the usual caveat: you cannot divide by zero, which is Module 2 §4's partiality appearing on schedule.**

---

# 10. The Unary Side — Direct Substrings

Module 1 §5.2 defined a **Direct Substring**: a function g applied to each value in place, at the same index, comparing nothing. Module 1 never used one. Module 2 §6 gave one real work, as the logarithm that carries a lineage between coordinate systems.

**Here is the general account, which is short and decides the matter.**

## 10.1 When does a Direct Substring commute with the lineage?

Two things you might do to a string: apply g to every value and then difference; or difference and then apply g. **When do they agree?**

**They agree when g is linear** — that is, when g just multiplies by a fixed number. If g(x) = cx then

```
difference of g(B)  =  c·B~n+1~ − c·B~n~  =  c·(difference of B)  =  g(difference of B)
```

**They do not agree otherwise, and absolute value is the example that matters.** Take B = 1, −2, 3:

```
difference first, then absolute value :  DB = −3, 5     ->  |DB| = 3, 5
absolute value first, then difference :  |B| = 1, 2, 3  ->  D|B| = 1, 1
```

**3, 5 against 1, 1.** Not remotely the same string.

> ### A Direct Substring commutes with the lineage exactly when it is linear.
> **This is Module 1 §6.4's warning stated exactly.** That section cautioned that iterating absolute differences while discarding sign is a different construction with different behaviour. **The reason is here: absolute value does not commute with differencing**, so applying it inside the lineage changes what the lineage is doing.

## 10.2 So what is the logarithm doing?

The logarithm is **not** linear, so by §10.1 it does not commute. **And that is exactly why it is useful.**

> **A Direct Substring that commutes changes nothing worth having. One that does not commute changes the lineage into a different lineage — and if the change is reversible, you have a bridge.**

The logarithm is invertible, so it does not destroy the tree; it **relocates** it, from the multiplicative world to the additive one. Absolute value is not invertible — it discards the sign — so it destroys instead of relocating.

**That is the whole distinction between a bridge and a loss**, and it puts Module 1's split, Module 2's bridge and Module 1's Ducci warning on one page as three faces of one fact.

---

# 11. Exercises

## 11.1 Problems

**Exercise 1.** Build three levels of the **sum** lineage for the cubes 0, 1, 8, 27, 64, 125. Does it terminate?

**Exercise 2.** Use the closed form of §5.1 to compute the level-2 sum substring at position 0 for the cubes, and check it against Exercise 1.

**Exercise 3.** Predict, using §4.1 and Module 3's Tuned Root Theorem and **without computing**, the depth at which the sum lineage annihilates B~n~ = n²·(−1)^n^. Then verify it.

**Exercise 4.** Build the product lineage of 3, 9, 81 and confirm it against the sum lineage of the logarithms base 3.

**Exercise 5.** A string has sum-lineage first substring 4, 10, 18 and anchor B~0~ = 1. Rebuild the string.

**Exercise 6.** Show by a single example that squaring — g(x) = x² — does not commute with the difference lineage.

**Exercise 7.** Which of the four relationships would you choose to detect a string that flips sign every step but is otherwise constant? Justify from §8.1 rather than by trying all four.

**Exercise 8.** Build the stride-two difference of the cubes 0, 1, 8, 27, 64, 125 directly. Then obtain it again by summing first and differencing second, and confirm the two agree.

**Exercise 9.** Using §7.2, find the relationship that annihilates the string 3, 9, 81, 6561 at depth 1, and verify it.

**Exercise 10.** Module 2 §3 called 0 and 1 the "terminator pair". After §8.1, is "pair" still the right word? Say precisely what is paired with what.

## 11.2 Answers

**Exercise 1.**

```
B      0     1     8    27    64   125
1S        1     9    35    91   189
2S          10    44   126   280
3S             54   170   406
```

Working: 0+1=1, 1+8=9, 8+27=35, 27+64=91, 64+125=189; then 1+9=10, 9+35=44, 35+91=126, 91+189=280; then 10+44=54, 44+126=170, 126+280=406.

**It does not terminate.** The cubes are a polynomial string, and §2.3 says the sum lineage terminates only by cancellation — a string of non-negative values can never cancel.

**Exercise 2.** C(2,0)·B~0~ + C(2,1)·B~1~ + C(2,2)·B~2~ = 1·0 + 2·1 + 1·8 = **10**, which is the first entry of 2S above. ✔

**Exercise 3.** By §4.1 the sum lineage is the tuned difference at r = −1. The string is a polynomial of degree 2 riding on an alternating string, so Module 3's theorem gives annihilation at depth k+1 = **3**.

Verify with B = 0, −1, 4, −9, 16, −25:

```
1S       -1     3    -5     7    -9
2S          2    -2     2    -2
3S            0     0     0            <- TERMINATOR at depth 3, as predicted
```

**Exercise 4.** Product lineage: 3·9 = 27, 9·81 = 729, so 1S = **27, 729**.

Logarithms base 3: the string becomes 1, 2, 4. Sum lineage: 1+2 = 3, 2+4 = 6. And log₃27 = 3, log₃729 = 6. ✔

**Exercise 5.** Using B~n+1~ = 1S~n~ − B~n~ from §9:

```
B~1~ =  4 − 1 =  3
B~2~ = 10 − 3 =  7
B~3~ = 18 − 7 = 11
```

The string is **1, 3, 7, 11**. Check forward: 1+3 = 4 ✔, 3+7 = 10 ✔, 7+11 = 18 ✔.

**Exercise 6.** Take B = 1, 2, 3.

```
difference first, then square :  DB = 1, 1    ->  squared = 1, 1
square first, then difference :  B² = 1, 4, 9 ->  D(B²)  = 3, 5
```

**1, 1 against 3, 5.** Squaring is not linear, so by §10.1 it cannot commute — and it does not.

**Exercise 7.** **The sum lineage.** §8.1 says each relationship terminates on the family its own arithmetic and direction select, and a string that flips sign every step while otherwise constant is exactly the alternating string — the family the sum lineage annihilates, at depth 1. **No other relationship kills it in one step:** difference doubles it, and the two multiplicative relationships are the wrong arithmetic for a sign flip.

**Exercise 8.** Direct: 8−0 = 8, 27−1 = 26, 64−8 = 56, 125−27 = 98 → **8, 26, 56, 98**.

By composition: the sum lineage of the cubes is 1, 9, 35, 91, 189 (from §11.2 Exercise 1); differencing that gives 9−1 = 8, 35−9 = 26, 91−35 = 56, 189−91 = 98 → **8, 26, 56, 98**. ✔ Identical.

**Exercise 9.** Each term is the previous one squared: 3² = 9, 9² = 81, 81² = 6561. So by §7.2 the tuned ratio at r = 2 — that is, h(a,b) = b/a² — annihilates it.

Check: 9/3² = 1, 81/9² = 1, 6561/81² = 1 → **1, 1, 1** at depth 1. ✔

**Exercise 10.** **"Pair" was right for what Module 2 could see and is now the wrong word for the whole picture.** There are four relationships and only **two** terminator values, so the terminators are not paired one-to-one with relationships. What is paired is **arithmetic with identity**: the additive relationships — difference and sum — both terminate at 0, and the multiplicative ones — ratio and product — both terminate at 1. **The pairing is between an arithmetic and its identity, and each member of the pair serves two relationships.**

---

# 12. Glossary, Notation, and Status

## 12.1 No new notation

**This module introduces none.** The sum and product lineages are written exactly as Module 1 §5.3 writes any comparative substring, and the sum lineage may equally be written as Module 3's jS~(−1)~.

## 12.2 Terms

| Term | Meaning |
|---------------------------------------|-------------------------------------------------------------|
| **Sum lineage** | Comparative lineage with h(a,b) = a + b; the tuned difference at r = −1 |
| **Product lineage** | Comparative lineage with h(a,b) = ab |
| **Alternating string** | A string that reverses sign at every step; geometric of ratio −1 |
| **Reciprocating string** | A string whose adjacent terms are reciprocals |
| **Opposing / combining** | Whether a relationship undoes one value from the other, or puts them together |

## 12.3 Status of claims

| Result | Status |
|----------------------------------------------------|------------------------------------------------|
| The sum lineage never terminates on a polynomial | **Theorem** (§2.3, §5.3) — positive terms cannot cancel |
| The sum lineage terminates on alternating strings, depth 1 | **Theorem** (§3.1) |
| **The sum lineage is Module 3's dial at r = −1** | **Theorem** (§4.1) — no new machinery |
| Depth k+1 for degree k on an alternation | **Corollary** of Module 3's Tuned Root Theorem; checked at k = 1 and k = 2 |
| Sum lineage closed form is unsigned Pascal | **Theorem** (§5.1); checked at levels 2 and 3 |
| Difference and sum are one triangle, signed and unsigned | **Theorem** (§5.2) |
| Sum lineage doubles per level on a constant | **Theorem** (§5.3) — row sums of Pascal are powers of two |
| product = exp ∘ sum ∘ log | **Theorem** (§7); checked base 2 and base 3 |
| Product terminates at 1 on reciprocating strings | **Theorem** (§6.2) |
| The terminator is the identity of the arithmetic | **Theorem** (§8.1), now across all four |
| All four rebuild from one anchor | **Theorem** (§9); worked for the sum lineage |
| A Direct Substring commutes with the lineage iff it is linear | **Theorem** (§10.1); counterexamples for absolute value and squaring |
| A useful Direct Substring is one that does **not** commute but **is** invertible | **Observation** (§10.2) — names bridge versus loss |
| The dial exists multiplicatively: h(a,b) = b/a^r^ | **Theorem** (§7.2); checked at r = 2 both sides of the bridge |
| Doubly-exponential strings die at depth 1 under the tuned ratio | **Theorem** (§7.2) |
| Stride-two difference = difference ∘ sum, in either order | **Theorem** (§8.2); checked on squares and cubes |
| Comparisons need not be adjacent; a stride decomposes into adjacent ones | **Theorem** (§8.2) |

---

# 13. Looking Ahead

**The lateral space at this level is now closed.** All four relationships named in Module 1 §5.3 have been built, their terminators identified, their closed forms given, and their family structure exhibited. The unary side has been characterised completely by one criterion.

**What remains unexplored at this level, and is named rather than promised:**

**Relationships outside the four.** Nothing forces a comparison to be arithmetic at all. Taking the larger of two values, or the smaller, or their greatest common divisor, are all two-input relationships on adjacent terms. **They are not in the framework's list**, and any treatment of them would be an extension rather than a completion — which is why this module stops here.

**Two threads stay open from earlier modules**, restated so they do not drift: composite tunings where a ratio repeats (Module 3 §10), and whether more than one error can be corrected rather than merely located (Module 3 §5.5 and §6.3).

# Revision History

**Version 2.** **Notation rendering.** Notation written inside code spans was displaying as raw markup — a superscript marker appearing as a literal character instead of raising the symbol — and the escape before a vertical bar was visible as a backslash. **A code span suppresses exactly the formatting the notation needs.** All affected notation now renders as true superscripts and subscripts. Verified in the document's own markup rather than in a text extraction, because a text extraction flattens a superscript and cannot tell a rendered one from a broken one.


**Version 1.** Initial issue.

---

*End of Module 5, Version 2.*
