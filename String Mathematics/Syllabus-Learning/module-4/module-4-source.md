---
title: "String Mathematics — Module 4"
subtitle: "Number Without a Base: Counting, Registers, and Where Carrying Actually Lives"
author: "Prime Framework — Syllabus-Learning Series"
date: "Module 4 of the String Mathematics syllabus — Version 2"
---

# Module 4 — Number Without a Base

## Counting, Registers, and Where Carrying Actually Lives

**Version 2.** Prerequisite: Module 1. Modules 2 and 3 are helpful but not assumed.

---

# 0. How to Use This Module

## 0.1 What you need

**Module 1 only** — the Prime String, the Base String, substrings, the String Tree, and the Root. If you can difference a string down to its Root, you have enough.

Modules 2 and 3 are referred to twice, both times in passing. Nothing here depends on them.

## 0.2 What this module is about

The first three modules built an instrument and pointed it at sequences of numbers. **They never once asked what a number is.** Every value in them was an ordinary base-ten integer, written the way you have written integers since primary school, and no module remarked on it.

**This module removes that assumption**, and finds that the instrument does not need it. Along the way it reaches a result that is not obvious and is worth the whole module:

> **Carrying and borrowing are not part of arithmetic. They belong to *presentation*.** You can run an entire String Tree, in any base, and never carry once.

## 0.3 A warning about one word

**The word "base" is used in this syllabus for two completely different things**, and this is the module where they meet. §12 states the distinction formally; here is the short version so it never trips you:

- The **Base String** is the second layer of a String Tree — each Prime value raised to a power. This has nothing to do with number bases.
- A **number base** is how many symbols you write numbers with — ten for us, two for a computer.

They share a word by accident of English. **Where confusion is possible this module says "number base" in full.**

---

# 1. The Assumption Three Modules Never Questioned

Open Module 1 at any page. The cubes are written 0, 1, 8, 27, 64, 125. The Root of the fourth-order tree is written 24. The alternating sum for 10! runs to 3,628,800.

**Every one of those is written in base ten, and not one module says so.** It was never a decision — it was the water the syllabus was swimming in.

**Ask what would break if we changed it.** Write the cubes in base two:

```
   0        1     1000    11011   1000000   1111101
```

Difference them. Do you get the same tree? **The answer is yes, and the reason is worth the rest of this module.**

---

# 2. Counting Is the Prime String

Before there is a number to write down, there is the act of counting.

Module 1 §3 defines the Prime String as a seed and a rule applied over and over:

```
P^f^  =  P~0~,  f(P~0~),  f(f(P~0~)),  …
```

With the standard choice — start at zero, and let f add one — **that recursion is literally the act of counting.** Nothing is being represented yet. There are no digits, no columns, no symbols. There is a starting point and a step.

> **The Prime String is counting made into an object.** Everything else in String Mathematics is built on top of that act, and none of it needs a way of *writing* the results.

**This matters for what follows:** the numbers in a String Tree are quantities, not spellings. Whether we then write a quantity as `12`, `1100` or `110` is a separate decision, made afterwards, by somebody who wants to read it.

---

# 3. What a Number Base Actually Is

A number base is not a property of a number. **It is a choice of alphabet.**

Pick a set of symbols:

```
binary       0 1                          -> 2 symbols
ternary      0 1 2                        -> 3 symbols
decimal      0 1 2 3 4 5 6 7 8 9          -> 10 symbols
```

> ### The number base is the size of the alphabet.
> Count the symbols and you have the base. **Nothing else about the alphabet matters** — the symbols could be letters, colours or tally marks. Only how many there are.

**This is the whole of it.** "Base ten" is not a fact about the number twenty-five; it is a fact about the ten symbols we happen to have fingers for.

---

# 4. The Register

To write a quantity down, we express it as a list of positions, each holding one symbol from the alphabet, each position carrying a weight.

> ### Register
> **A value written as a list of positions over a chosen alphabet, where position *i* carries weight (base)^i^.**

The value is recovered by multiplying and adding:

```
value  =  d~0~ · base^0^  +  d~1~ · base^1^  +  d~2~ · base^2^  +  …
```

## 4.1 Written least-significant-first

**This syllabus writes registers with the smallest weight first** — the opposite of the way you were taught to write numbers.

So the quantity twenty-five, in base ten, is the register

```
(5, 2)          meaning   5·1  +  2·10   =  25
```

and in base two it is

```
(1, 0, 0, 1, 1)  meaning   1·1 + 0·2 + 0·4 + 1·8 + 1·16  =  25
```

**Check the second one:** 1 + 8 + 16 = 25. ✔

## 4.2 Why least-significant-first, and it is not arbitrary

Three reasons, and the third is the one that matters.

**One — the index is the exponent.** In this ordering, position *i* carries weight base^i^, always. Position 3 means base cubed, in every register, forever.

**Two — it is how you build one.** To encode a value you divide repeatedly by the base and keep the remainders. **Those remainders come out smallest-weight-first**, in exactly this order. Writing them the other way round means computing them in one order and then reversing them.

**Three — and this is the structural argument — a register can grow without renumbering.** Write twenty-five as `(5, 2)` and then let it become a hundred and twenty-five: `(5, 2, 1)`. **The 5 is still at position 0 and the 2 is still at position 1.** Nothing already written has moved.

Now try it in the familiar ordering. `25` becomes `125`: the digit 2 was in the tens column and is now in the tens column, but *counted from the left* it moved from position 1 to position 2. **In most-significant-first ordering, a position's meaning depends on how long the whole number is** — so it changes whenever the number grows.

> **Least-significant-first gives each position a permanent meaning. Most-significant-first gives it a meaning that depends on the length of the number it happens to be sitting in.** For a system built on strings that grow, the first is the honest ordering. Display can reverse it at the very last moment, for human eyes.


## 4.3 One edge case, because it fixes the definition

**The alphabet must have at least two symbols.**

Try one. An alphabet of `{0}` gives every position exactly one possible digit, zero, so every register decodes to

```
0·1 + 0·1 + 0·1 + … = 0
```

**Only zero is expressible, and there is no way to write anything else.** So "base one" is not a number base in this sense at all — tally marks work by a different principle entirely, counting marks rather than weighting positions.

**Base two is therefore the smallest genuine number base**, and everything in this module holds from two upward.

---

# 5. Encoding and Decoding Are Exact Inverses

The two operations — value to register, register to value — undo each other perfectly. No information is created or lost.

**Worked, in three bases, on the quantity forty-five:**

```
base 10 :  45  ->  (5, 4)              5 + 40                    = 45
base  2 :  45  ->  (1,0,1,1,0,1)       1 + 4 + 8 + 32            = 45
base  3 :  45  ->  (0, 0, 2, 1)        0 + 0 + 18 + 27           = 45
```

**Check base 3:** positions carry 1, 3, 9, 27. So 2·9 + 1·27 = 18 + 27 = 45. ✔

Three different registers. **One quantity.**

> **The register is a spelling. The value is the word.** Three spellings of forty-five are three spellings, not three numbers.

---

# 6. The Same String, Three Alphabets

Take the squares — Module 1's second-order Base String — and write each term as a register in three different number bases.

```
value     0     1     4     9    16    25

base 10  (0,0) (1,0) (4,0) (9,0) (6,1) (5,2)
base  2  (0…)  (1,0,0,0,0) (0,0,1,0,0) (1,0,0,1,0) (0,0,0,0,1) (1,0,0,1,1)
base  3  (0,0,0) (1,0,0) (1,1,0) (0,0,1) (1,2,1) (1,2,2)
```

**Spot-check three of them.** Base 2: 25 = 1 + 8 + 16 ✔. Base 3: 16 = 1 + 2·3 + 1·9 = 1 + 6 + 9 ✔. Base 3: 25 = 1 + 2·3 + 2·9 = 1 + 6 + 18 ✔.

Nothing about the *string* has changed. Only the spelling of each term.

---

# 7. ⭐ The Lineage Commutes With Encoding

Here is the central result of the module, and it is stronger than "the base does not matter."

## 7.1 The claim

> ### THEOREM
> Take any string. Encode every term as a register in any number base. Now compute the substring lineage **position by position on the registers** — subtracting digit from digit, **allowing digits to be negative, and never carrying.**
>
> **Decode any level, and you get exactly the lineage computed on the values.**

## 7.2 Why it is true, in two lines

The value of a register is

```
value  =  d~0~·base^0^  +  d~1~·base^1^  +  d~2~·base^2^  +  …
```

**Everything on the right is multiplication and addition of the digits.** So if you subtract two registers position by position, and then work out the value, you get:

```
(a~0~ − b~0~)·base^0^ + (a~1~ − b~1~)·base^1^ + …
   =  (a~0~·base^0^ + a~1~·base^1^ + …)  −  (b~0~·base^0^ + b~1~·base^1^ + …)
   =  value of A  −  value of B
```

**That is the whole proof.** Subtracting the digits and then adding up gives the same answer as adding up and then subtracting, because addition and multiplication rearrange freely. ∎

**And notice what the proof did not need.** It never asked that the digits stay inside the alphabet. A digit of −7, or of 13 in base ten, does no harm at all — it still gets multiplied by its weight and added in.

## 7.3 Worked in base ten — the Root recovered without a single carry

The squares, as base-ten registers, differenced digit by digit:

```
B      (0,0)  (1,0)  (4,0)  (9,0)  (6,1)  (5,2)

1S       (1,0)  (3,0)  (5,0)  (-3,1)  (-1,1)
decodes:   1      3      5     7        9

2S         (2,0)  (2,0)  (-8,1)  (2,0)
decodes:     2      2      2       2      <- ROOT = 2 = 2!
```

**Read the arithmetic on two of those.** At the fourth entry of 1S: `(6,1) − (9,0) = (−3, 1)`, and its value is −3·1 + 1·10 = **7** ✔, which is exactly the fourth term of the value-level 1S in Module 1. At the third entry of 2S: `(−3,1) − (5,0) = (−8, 1)`, value −8 + 10 = **2** ✔.

**The Root of 2 has been recovered from digit arithmetic alone, and no carry was performed anywhere in that table.**

## 7.4 The same tree in base two and base three

```
BASE 2, first substring
(1,0,0,0,0)          ->  1
(-1,0,1,0,0)         ->  -1 + 4                =  3
(1,0,-1,1,0)         ->   1 - 4 + 8            =  5
(-1,0,0,-1,1)        ->  -1 - 8 + 16           =  7
(1,0,0,1,0)          ->   1 + 8                =  9
```

```
BASE 3, first substring          BASE 3, second substring
(1,0,0)   ->  1                  (-1,1,0)   ->  -1 + 3          = 2
(0,1,0)   ->  3                  (-1,-2,1)  ->  -1 - 6 + 9      = 2
(-1,-1,1) ->  -1 - 3 + 9  = 5    (2,3,-1)   ->   2 + 9 - 9      = 2
(1,2,0)   ->   1 + 6      = 7    (-1,-2,1)  ->  -1 - 6 + 9      = 2
(0,0,1)   ->  9                                       ROOT = 2 = 2!
```

**Three alphabets. One tree. One Root.**

**And look at the base-three entry `(2, 3, -1)`.** It contains a digit of 3, which does not exist in base three, and a digit of −1, which does not exist anywhere. **It is still exactly right** — it decodes to 2, like every other entry in that row. A register whose digits have left the alphabet is not broken. It is simply not yet written down for a reader.


## 7.5 Where the theorem stops — and it stops somewhere useful

**A result is only as good as its boundary**, so here is this one's.

The proof in §7.2 used exactly one property: **the value of a register is its digits multiplied by weights and added up.** That makes the value depend on the digits in a particularly simple way — scale every digit and the value scales; add two registers digit by digit and the values add.

**Any operation built only from adding and scaling therefore passes straight through the encoding.** The difference lineage is built from subtraction, so it qualifies, and that is the whole of §7.

**Operations not built that way do not get the same guarantee**, and it is worth knowing which:

| Operation | Passes through digit-wise? | |
|-----------------------------------|-----------------------------|------------------------------------|
| difference `b − a` | **yes** | position by position (§7) |
| sum `a + b` | **yes** | position by position (§8.4) |
| scaling by a whole number | **yes** | multiply every digit |
| **product `a × b`** | **not position-wise** | but still carry-free — see §8.5 |
| **ratio `b / a`** | **no** | division is not built from adding and scaling |
| comparison, ordering | **no** | see §8.6 |

**So Module 2's ratio lineage does not inherit §7.** That is not a defect in either module — it is the same asymmetry Module 2 §4 recorded when it found the ratio lineage was partial where the difference lineage was total. **The ratio keeps turning out to be the harder of the two, for reasons that keep turning out to be the same reason.**

---

# 8. Where Carrying Actually Lives

If the arithmetic never needed a carry, what is carrying *for*?

## 8.1 A worked subtraction with no borrowing at all

One hundred take away thirty-seven, in base ten, least-significant-first:

```
   (0, 0, 1)          100
 - (7, 3, 0)           37
 = (-7, -3, 1)
```

Decode it: −7·1 − 3·10 + 1·100 = −7 − 30 + 100 = **63**. ✔

**That is the right answer, obtained without borrowing once.** The register merely looks unfamiliar.

## 8.2 Normalisation — what borrowing actually is

To *write* 63 for a reader, every digit must come back inside the alphabet, 0 to 9. That is a separate pass:

```
(-7, -3, 1)
   position 0:  -7  is below 0, so add 10 and take 1 from position 1   ->  3
   position 1:  -3 - 1 = -4, below 0, so add 10 and take 1 from position 2  ->  6
   position 2:   1 - 1 = 0                                             ->  0
(3, 6, 0)   =   63       same value, alphabet-legal digits
```

> ### Carrying and borrowing are NORMALISATION, not arithmetic.
> The arithmetic was finished at `(-7, -3, 1)`. Everything after that was **tidying the answer into the alphabet so a human can read it.** The quantity never changed.

## 8.3 Why this is the module's real result

Normalisation has a property the arithmetic does not: **it is sequential.** Position 1 cannot be tidied until position 0 has been tidied, because it may receive a borrow. That dependency runs the whole length of the register.

**The digit-wise arithmetic has no such dependency.** Every position is independent of every other.

> **So the chain in long arithmetic — the thing that makes you work right to left and wait — comes entirely from the demand that the answer be readable.** Drop that demand and the chain disappears.

**A boundary, stated because it is not mine to cross.** That fact plainly has consequences for machines that do arithmetic. **Those consequences are compute architecture and are not developed in this syllabus** — this module establishes the mathematical statement and stops there.


## 8.4 Addition behaves identically

Nothing above was special to subtraction. Adding two registers position by position works the same way and needs no carry either:

```
   (7, 4)          47
 + (8, 3)          38
 = (15, 7)
```

Decode: 15·1 + 7·10 = 15 + 70 = **85**. ✔ And 47 + 38 = 85.

Normalise only when a reader is waiting: position 0 holds 15, so subtract 10 and carry 1, giving 5; position 1 becomes 7 + 1 = 8. Result `(5, 8)` = **85**. ✔

## 8.5 Multiplication is carry-free too — but not position-wise

**This is the case that shows the boundary in §7.5 is a real one, and it has a satisfying answer.**

Multiplying two registers cannot be done position by position, because a digit of one meets *every* digit of the other. Position *k* of the product collects **every pair of positions whose weights multiply to weight k**:

```
digit k of the product  =  sum of  a~i~ · b~j~  over all i + j = k
```

**Worked on 27 × 14, in base ten:**

```
27 = (7, 2)     14 = (4, 1)

  k = 0 :  7·4                = 28
  k = 1 :  7·1  +  2·4        = 15
  k = 2 :  2·1                =  2

  product register = (28, 15, 2)
```

Decode: 28·1 + 15·10 + 2·100 = 28 + 150 + 200 = **378**. ✔ And 27 × 14 = 378.

**Those digits are wildly outside the alphabet** — 28 and 15 in base ten — **and the answer is exact anyway.** Normalise only to write it down: position 0 holds 28, leave 8 and carry 2; position 1 becomes 15 + 2 = 17, leave 7 and carry 1; position 2 becomes 2 + 1 = 3. Result `(8, 7, 3)` = **378**. ✔

> **So multiplication is carry-free as well.** What it is not is *position-independent* — each product digit needs several input digits, where each difference digit needed only one. **Those are two different properties and it is worth not conflating them:** §7 gives the difference lineage both; multiplication gets the second only.

## 8.6 What actually forces normalisation

If arithmetic never needs it, what does?

**Comparison does.** Ask whether the register `(-3, 1)` holds a positive value. It does — it is 7 — but **you cannot see that by looking at the digits.** The leading digit is positive and the trailing one is negative, and only working out the value settles it.

Worse: `(-3, 1)` and `(7, 0)` are **the same quantity written two ways**, and they disagree in every position. So two registers can be equal in value and share no digit.

> ### Computation defers normalisation. Comparison forces it.
> **You may add, subtract and multiply for as long as you like without ever tidying a digit. The moment you ask which of two results is larger — or whether one is negative — you must normalise, or evaluate, or both.**

**And that lands exactly on Module 1's principle.** The Comparative Split keeps *which way* on its own axis — and §9 below shows the signed digit is that split, one position at a time. **Normalisation is precisely the operation that recovers "which way" from a register that has been allowed to hold it loosely.**


---

# 9. The Signed Digit Is the Comparative Split

Module 1 §6 made a principle of keeping **how far** and **which way** on separate axes, and showed that collapsing them is irreversible. That was about whole values. **It applies to digits, and it is exactly what §7 relied on.**

A digit that has left the alphabet carries two pieces of information:

```
   -7      ->     [ − | 7 ]        direction and size
```

**This is the Comparative Split, one position at a time.** And it is precisely what makes carrying unnecessary: a register that may hold signed digits can absorb any difference without adjustment, because **the sign lives on its own axis instead of being forced into the magnitude by a borrow.**

> **Borrowing is what you must do when a digit is forbidden to be negative.** Permit the sign and the borrow has nothing to fix.

*Module 1 introduced the split as a fact about comparisons. Module 2 showed it survives the move from difference to ratio. Here it turns out to be the thing that lets arithmetic run without carries. It has now earned its place three times, in three different settings.*

---

# 10. The Operation Ladder

Counting, adding, multiplying and raising to a power are not four unrelated operations. **Each is the previous one done repeatedly.**

| Rung | Operation | Built from the rung below by |
|------------|----------------------------------------|------------------------------------------------|
| 1 | **succession** | — the primitive act: take the next one |
| 2 | **addition** | repeating succession *b* times |
| 3 | **multiplication** | repeating addition *b* times |
| 4 | **raising to a power** | repeating multiplication *b* times |

**Worked at rung 3, so the claim is not just asserted.** Three multiplied by four is four repetitions of an addition:

```
3 × 4   =   3 + 3 + 3 + 3   =   12
```

and each of those additions is itself repetitions of succession — adding 3 means taking the next one, three times.

## 10.1 Where the String Tree sits on the ladder

The three layers of a String Tree are three rungs of that ladder:

| Layer | Operation | Rung |
|----------------------------------|--------------------------------------------------|----------------|
| **Prime String** | succession — counting | 1 |
| **Base String** | raising to the power *k* | 4 |
| **Substrings** | comparison — difference or ratio | 2 and 3 |

> **The String Tree is not an arbitrary construction. It is the operations of arithmetic, stacked in the order they are built from one another.**

And the order *k* of a Base String is **not a choice of which operation to use** — it is a count of how many times to repeat one. B^3^ means multiply the Prime value by itself three times, and each of those multiplications is repeated addition, and each addition is repeated counting. **One act, applied at four depths.**

## 10.2 What this says about the number base

Notice that the ladder never mentions a base. **Succession does not need one.** Neither does repeating it.

> **The number base enters only at the moment somebody wants to read the answer.** It is a property of the writing, not of the counting — which is why §7's theorem could be true at all.

---

# 11. Exercises

## 11.1 Problems

**Exercise 1.** Write the quantity thirty in base ten, base two and base three, least-significant-first. Check each by decoding.

**Exercise 2.** Decode the base-ten register `(4, -2, 1)`. Then normalise it into alphabet-legal digits and confirm the value is unchanged.

**Exercise 3.** Take the string 1, 3, 9, 27 in **base three**, least-significant-first, and compute the first substring digit-wise without carrying. Decode it. Check against the value-level answer.

**Exercise 4.** A register in base five reads `(2, 7, 1)`. Is it wrong? Decode it, then normalise it, and say precisely what was and was not defective about it.

**Exercise 5.** Explain in one sentence why the difference lineage never needs a carry, and in one further sentence why a *human reader* still does.

**Exercise 6.** In most-significant-first ordering, the number 25 becomes 125. Describe what happens to the position index of the digit `2`, and say why least-significant-first avoids it.

**Exercise 7.** Add 68 and 55 in base ten as registers, without carrying. Decode to check, then normalise.

**Exercise 8.** Multiply 23 by 12 in base ten using the convolution rule of §8.5. Show the un-normalised product register, decode it to check, then normalise it.

**Exercise 9.** The registers `(-3, 1)` and `(7, 0)` hold the same value and agree in no position. **What does that tell you about deciding whether two registers are equal?**

**Exercise 10.** Module 1's Root Law says the Root of a polynomial string is its leading coefficient times *k*!. **Does that law depend on the number base?** Answer, and justify from §7 rather than by trying examples.

## 11.2 Answers

**Exercise 1.**

```
base 10 :  (0, 3)          0 + 30                = 30   OK
base  2 :  (0,1,1,1,1)     0 + 2 + 4 + 8 + 16    = 30   OK
base  3 :  (0, 1, 0, 1)    0 + 3 + 0 + 27        = 30   OK
```

**Exercise 2.** Value: 4·1 + (−2)·10 + 1·100 = 4 − 20 + 100 = **84**.

Normalising: position 0 is 4, already legal. Position 1 is −2, below zero, so add 10 and take 1 from position 2, giving 8; position 2 becomes 1 − 1 = 0. Result `(4, 8, 0)` = 4 + 80 = **84**. ✔ Same value, legal digits.

**Exercise 3.** In base three: 1 = `(1,0,0)`, 3 = `(0,1,0)`, 9 = `(0,0,1)`, 27 = `(0,0,0,1)`.

```
(0,1,0)   - (1,0,0)   = (-1, 1, 0)      ->  -1 + 3          =  2
(0,0,1)   - (0,1,0)   = ( 0,-1, 1)      ->  -3 + 9          =  6
(0,0,0,1) - (0,0,1)   = ( 0, 0,-1, 1)   ->  -9 + 27         = 18
```

First substring: 2, 6, 18. Value-level check: 3−1 = 2, 9−3 = 6, 27−9 = 18. ✔ (And note this string is geometric, so by Module 2 it will never reach a Root under difference — the digit-wise method reproduces that faithfully too.)

**Exercise 4.** It is **not wrong, and it is not normalised** — those are different things.

Decode: 2·1 + 7·5 + 1·25 = 2 + 35 + 25 = **62**. The value is perfectly well defined.

Normalise: position 1 holds 7, which is ≥ 5, so subtract 5 and carry 1 to position 2, giving 2; position 2 becomes 1 + 1 = 2. Result `(2, 2, 2)` = 2 + 10 + 50 = **62** ✔.

**What was defective:** nothing about the quantity. The register was simply **not yet written in the alphabet a base-five reader expects.** The digit 7 does not exist in base five, and the register was still correct.

**Exercise 5.** The lineage needs no carry because the value of a register is just its digits multiplied by their weights and added, so subtracting digit by digit and then adding up gives the same answer as adding up and then subtracting. A human reader still needs the carry because the alphabet has only so many symbols, and a digit of −7 or 13 cannot be written with them.

**Exercise 6.** Counted from the left, the digit `2` moves from position 1 to position 2 — **its index changed although the digit did not.** In most-significant-first ordering a position's meaning depends on the total length of the number, so growing the number renumbers everything already written. Least-significant-first ties position 0 to weight 1 permanently, so growth only ever appends.

**Exercise 7.**

```
   (8, 6)          68
 + (5, 5)          55
 = (13, 11)
```

Decode: 13 + 110 = **123** ✔ (68 + 55 = 123). Normalise: position 0 holds 13, leave 3 carry 1; position 1 becomes 11 + 1 = 12, leave 2 carry 1; position 2 becomes 1. Result `(3, 2, 1)` = 3 + 20 + 100 = **123** ✔.

**Exercise 8.** 23 = `(3, 2)`, 12 = `(2, 1)`.

```
  k = 0 :  3·2              =  6
  k = 1 :  3·1  +  2·2      =  7
  k = 2 :  2·1              =  2

  product register = (6, 7, 2)
```

Decode: 6 + 70 + 200 = **276** ✔ (23 × 12 = 276). Here every digit happens to be alphabet-legal already, so normalisation has nothing to do — **which is a reminder that normalisation is sometimes a no-op, not that it was never needed.**

**Exercise 9.** That **equality cannot be decided by comparing digits.** Two registers hold the same value exactly when they *decode* to the same value, and they may do so while disagreeing everywhere. To compare by inspection you must first normalise both, because normalisation is what makes the representation unique. This is §8.6: computation defers normalisation, comparison forces it.

**Exercise 10.** **No — and it cannot, by §7.**

The Root Law is a statement about the values in a lineage. §7 establishes that the lineage computed on registers in any base decodes to exactly the lineage computed on values. So every level of the tree — including the Root — holds the same quantity whatever alphabet it is written in. **The Root of the cubic tree is six whether you write it `6`, `110` or `20`.**

*Note that this argument settles all bases at once. Trying examples could only ever have settled the bases you tried — which is Module 2 §8's rule about stating the region a check covers.*

---

# 12. Two Vocabularies — A Note on the Corpus

**This concerns the surrounding Prime Framework material rather than the mathematics, and it is recorded here because this is the module where the two collide.**

The terms *Prime String* and *Base String* are used with **different meanings** in two places:

| Term | This syllabus, and the Foundations documents | The reference implementation |
|------------------|------------------------------------|----------------------------------------------|
| **Prime String** | a generated sequence: a seed and a rule *f* | the **alphabet** — the symbols, whose count is the number base |
| **Base String** | each Prime value raised to the power *k* | the ordered list of **registers** for 0 up to N |

**By ruling of the principal investigator, this syllabus keeps the Foundations meanings**, which are the ones Module 1 published. **Where the implementation's meanings must be referred to, they are marked `_OLD`** — `Prime String_OLD`, `Base String_OLD` — so the two can never be silently exchanged.

**`_OLD` marks the usage this syllabus does not adopt.** It is a disambiguation marker. **It is not a claim about which came first**, which has not been established.

**Why the collision matters here specifically:** this module's §3 and §4 are *about* the alphabet and the registers — exactly the two objects the implementation names `Prime String_OLD` and `Base String_OLD`. A reader moving between the two documents will meet both meanings within a page of each other. **This syllabus calls them the alphabet and the register**, and never calls either one a Prime String.

---

# 13. Glossary, Notation, and Status

## 13.1 Terms

| Term | Meaning |
|---------------------------------------|-------------------------------------------------------------|
| **Number base** | The size of the alphabet — how many symbols are available |
| **Alphabet** | The set of symbols used to write values |
| **Register** | A value written as positions over an alphabet, position *i* carrying weight base^i^ |
| **Least-significant-first** | Writing the register with the smallest weight at position 0 |
| **Normalisation** | Returning a register's digits to the alphabet's legal range; carrying and borrowing |
| **Signed digit** | A digit outside the alphabet's range; carries direction and size on separate axes |
| **Operation ladder** | succession → addition → multiplication → powers, each repeating the one below |

## 13.2 Status of claims

| Result | Status |
|----------------------------------------------------|------------------------------------------------|
| The number base is the size of the alphabet | **Definition** |
| Encoding and decoding are exact inverses | **Theorem**; checked in three bases on 45 |
| The lineage commutes with encoding, digit-wise, no carrying | **Theorem** (§7.2); checked in bases 10, 2 and 3 on the squares |
| A register with digits outside the alphabet is still exact | **Theorem** — follows from §7.2 |
| Carrying and borrowing are normalisation, not arithmetic | **Theorem** (§8.2) |
| Normalisation is sequential; digit-wise arithmetic is not | **Theorem** (§8.3) |
| The signed digit is the Comparative Split per position | **Theorem** (§9) |
| Each rung of the operation ladder repeats the rung below | **Definition**, with rung 3 worked |
| The Root Law is independent of the number base | **Theorem** — corollary of §7 (§11.2 Ex. 7) |
| Addition is carry-free, position-wise | **Theorem** (§8.4); checked on 47 + 38 |
| Multiplication is carry-free but **not** position-wise — it convolves | **Theorem** (§8.5); checked on 27 × 14 and 23 × 12 |
| The ratio lineage does **not** inherit §7 | **Theorem** (§7.5) — division is not built from adding and scaling |
| Comparison and equality require normalisation | **Theorem** (§8.6); two registers may share a value and no digit |
| A number base must have at least two symbols | **Theorem** (§4.3) |
| Machine consequences of carry-free arithmetic | **Out of scope** — compute architecture, not developed here |

---

# 14. Looking Ahead

**The value domain is the next assumption to fall.** This module removed the assumption that a number must be written in a particular base. It left standing a larger one: **that the values are ordinary integers at all.**

Module 1's Comparative Split factors a value into a sign and a magnitude — over the integers, that means a choice from `{+1, −1}` and a size. **Change the values and the sign axis changes with them.** In a number system built on the golden ratio there are infinitely many "signs", they form a group, and the split survives — but only for a reason that has to be earned rather than assumed.

**Two threads stay open from earlier modules**, named again so they are not lost: composite tunings where a ratio repeats (Module 3 §10), and whether more than one error can be corrected rather than merely located (Module 3 §5.5, §6.3).

# Revision History

**Version 2.** **Notation rendering.** Notation written inside code spans was displaying as raw markup — a superscript marker appearing as a literal character instead of raising the symbol — and the escape before a vertical bar was visible as a backslash. **A code span suppresses exactly the formatting the notation needs.** All affected notation now renders as true superscripts and subscripts. Verified in the document's own markup rather than in a text extraction, because a text extraction flattens a superscript and cannot tell a rendered one from a broken one.


**Version 1.** Initial issue.

---

*End of Module 4, Version 2.*
