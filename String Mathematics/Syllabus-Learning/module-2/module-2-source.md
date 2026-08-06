---
title: "String Mathematics — Module 2"
subtitle: "The Ratio Lineage, and the Sequence Between"
author: "Prime Framework — Syllabus-Learning Series"
date: "Module 2 of the String Mathematics syllabus — Version 3"
---

# Module 2 — The Ratio Lineage

## Two Lineages, One Idea, and the Object That Sits Between Them

**Version 3.** Prerequisite: Module 1, §1–§11. See §16 for the revision history.

---

# 0. How to Use This Module

## 0.1 What you need before starting

You need **Module 1**, and specifically: the Prime String, the Base String, substrings, the String Tree, and the Root. If you can build a difference lineage down to its Root and read off a degree, you are ready.

**You do not need to have read Module 1's proofs.** §9.5 and §9.6 there are not assumed here.

## 0.2 A deliberate difference from Module 1

Module 1 opened with a six-position symbol before any mathematics had been done. **Two readers reported that this — not the algebra — was the hardest part of that module**, and they were right.

**This module introduces exactly two new pieces of notation**, and both arrive *after* the idea they name, not before. Everything else is Module 1's vocabulary.

## 0.3 Where this module is going

Module 1 ended on a promise: difference lineages terminate on polynomials, ratio lineages terminate on geometrics, and **there is a sequence that sits between them, closed under neither but almost closed under both, with the gap measurable exactly at every step.**

This module keeps that promise. The sequence is the **Fibonacci string**, the gap is exact, and the number that falls out of it is **φ**.

**But two things happen on the way that are worth more than the destination:**

- The two lineages turn out **not to be two theories.** They are one theory in two coordinate systems, and the thing connecting them is a fact you already know about arithmetic.
- We find a question the String Tree **cannot answer**, and the reason it cannot is important enough to be a result in its own right (§8).

---

# 1. Where Module 1 Ran Out

Module 1's Exercise 5 handed you a tree that refuses to terminate. Take the geometric string $1, 2, 4, 8, 16, 32$ and difference it:

```
B      1    2    4    8   16   32
1S        1    2    4    8   16
2S           1    2    4    8
3S              1    2    4
```

**Every substring is a copy of its parent.** There is no Root, no Terminator, and no depth at which the descent goes constant. Differencing this string achieves nothing at all.

That is not a defect in the string. **It is a mismatch between the string and the instrument.** Module 1's difference lineage is built to strip degree away, and a geometric string has no degree to strip.

> **The response is not a better difference lineage. It is a different comparison.**

---

# 2. The Ratio Lineage

## 2.1 Definition

Module 1 §5.3 already permits it. A comparative substring may use any relationship $h$, and among the ones listed is the **ratio**:

$$ h(a, b) = b / a $$

We write a ratio substring as $jS^{\,k\,|\,f}_{\div}$ when it must be distinguished, and simply "the ratio lineage" otherwise. **This is the first of the module's two new notations.**

## 2.2 The geometric string, done right

Apply the ratio to the same string that defeated differencing:

```
B      1    2    4    8   16   32
1S        2    2    2    2    2      <- ROOT = 2, at depth 1
2S           1    1    1    1        <- TERMINATOR
```

**Depth 1.** The string that had no difference-Root at any depth has a ratio-Root immediately, and the Root value is the common ratio itself.

## 2.3 The general result

> ### The Ratio Root Theorem
> For a geometric Base String $B_n = c\,r^{\,n}$ with $r \neq 0$:
> $$ 1S_{\div} = r \quad\text{(constant)}, \qquad 2S_{\div} = 1 $$
> **The ratio lineage of a geometric string reaches its Root at depth 1, and the Root is the common ratio.**

**Proof.** $B_{n+1}/B_n = c\,r^{\,n+1} / c\,r^{\,n} = r$, for every $n$. One step, and the constant $c$ cancels — **the ratio Root cannot see the leading constant**, exactly as the difference Root cannot see lower-order terms. $\blacksquare$

**Note how short that proof is.** Module 1 needed a lemma and an induction to reach $k!$. Here one line suffices, because we have matched the instrument to the object.

---

# 3. The Terminator Pair

Module 1's Terminator was the **zero** string. This module's is the **one** string. That is not a coincidence and it is worth naming.

| Lineage | Comparison | Terminates at | Because that value is |
|----------------|----------------|--------------------|------------------------------------------------|
| Difference | $b - a$ | $0$ | the **additive** identity |
| Ratio | $b / a$ | $1$ | the **multiplicative** identity |

> **A lineage terminates at the identity of the operation it is built from.** Two equal adjacent values differ by $0$ and divide to $1$. **The Terminator is not a special construction — it is what "no change" looks like in whichever arithmetic you are using.**

This is the first sign that the two lineages are the same idea wearing different clothes. §6 makes that precise.

---

# 4. Ratio Is Partial — and Difference Is Not

**This section exists because the very first example a reader will try does not work**, and a syllabus that lets that happen without warning has failed.

## 4.1 The problem

Module 1's standard Prime String begins at $P_0 = 0$. So every Standard Power Base String begins at $0^k = 0$:

$$ B^{\,3\,|\,f} = (0,\; 1,\; 8,\; 27,\; 64,\; 125, \ldots) $$

The first ratio comparison is $1 / 0$. **Undefined.** The ratio lineage cannot even start on the module's own standard example.

## 4.2 This is structural, not an inconvenience

It would be easy to patch this by quietly starting at $n = 1$. **We are not going to, because the failure is informative:**

> ### Difference is **total**; ratio is **partial**.
> $b - a$ is defined for every pair of numbers without exception. $b / a$ is undefined whenever $a = 0$. **The two lineages are not equally applicable, and no change of notation will make them so.**

**Where a lineage is undefined is information about the lineage.** The ratio lineage lives on strings that avoid zero — and, as §6 will show, that restriction is exactly the restriction its logarithm requires.

## 4.3 The working convention

For the remainder of this module, ratio lineages are taken over strings whose terms are **strictly positive**. Where a Prime String would introduce a zero, we start the index at $n = 1$ **and say so at the time.**

---

# 5. The Comparative Split Under Ratio

Module 1 §6 is its load-bearing idea: a comparison carries **how far** and **which way**, and collapsing them into one number is irreversible. That was established for differences. **Does it survive the move to ratio?**

It does, and the translation is exact.

| What the comparison carries | Difference | Ratio |
|-----------------------------------|---------------------------|--------------------------------------|
| **"Which way"** | sign: $+$ or $-$ | $> 1$ or $< 1$ |
| **"No change"** | $0$ | $1$ |
| **"How far"** | $\lvert b - a \rvert$ | how far the ratio sits from 1 |

So the split becomes

$$ [\;\text{direction}\;|\;\text{factor}\;] $$

where direction records **growth or decay** and factor records **by how much**.

**Worked example.** Take $(4,\; 1,\; 7)$ from Module 1 §6.2 and compare by ratio instead:

| Pair | Ratio | Split form |
|------------------------|---------------|-------------------------------------------------------------|
| $(4, 1)$ | $1/4$ | $[\downarrow\;|\;4]$ |
| $(1, 7)$ | $7/1$ | $[\uparrow\;|\;7]$ |

**And the same irreversibility argument applies unchanged.** Keep only the factors $(4, 7)$ and you cannot tell $(4, 1, 7)$ from $(1, 4, 28)$ — both give the same factors with different directions. **The direction channel is as necessary here as the sign channel was there.**

> **So the Comparative Split is a fact about comparison, not a fact about subtraction.** Module 1's framing was broader than its worked examples, and this is the evidence.

---

# 6. The Two Lineages Are One — and a Direct Substring Carries the Bridge

## 6.1 The observation that connects them

Here is a fact from ordinary arithmetic:

$$ \log(b/a) \;=\; \log b - \log a $$

**A ratio becomes a difference when you take logarithms.** That is the whole of the connection, and it is not a new idea — it is the reason slide rules worked.

## 6.2 Saying it in String Mathematics' own vocabulary

Module 1 §5.2 defines a **Direct Substring**: a unary function $g$ applied to each value in place, at the same index. Module 1 never used one for anything.

**Here is its work.** Take $g = \log$ as a Direct Substring, then difference the result:

$$ {}^{D}\!jS \;\text{with}\; g = \log \quad\longrightarrow\quad (\log B_0,\; \log B_1,\; \log B_2,\; \ldots) $$

$$ \text{then difference} \quad\longrightarrow\quad (\log B_1 - \log B_0,\; \ldots) \;=\; \left(\log \tfrac{B_1}{B_0},\; \ldots\right) $$

which is the logarithm of the ratio substring. Undoing the logarithm:

> ### The Bridge
> $$ \text{ratio lineage} \;=\; \exp \;\circ\; (\text{difference lineage}) \;\circ\; \log $$
> **The ratio lineage is the difference lineage performed in logarithmic coordinates.** A Direct Substring gets you in; a Direct Substring gets you out.

## 6.3 Three consequences, immediately

**(a) Everything from Module 1 transfers.** A ratio lineage reaches its Root at depth $k$ exactly when the *logarithm* of the string is a polynomial of degree $k$ in the index. Geometric strings have $\log B_n = n \log r$ — degree 1 — which is why §2.2 terminated at depth 1 and not at some other depth.

**(b) The partiality of §4 is explained rather than merely observed.** The logarithm requires positive inputs. **The ratio lineage is undefined exactly where its bridge is undefined** — the two restrictions are the same restriction, not two coincidental ones.

**(c) The Direct Substring earns its place in the notation.** Module 1 defined Direct Substrings, reserved a symbol for them, and never used one. **They are what carries a lineage between coordinate systems**, and without them the bridge above cannot be written in the framework's own terms at all.

## 6.4 And this is your own arithmetic, restated

The bridge looks like a piece of machinery. It is not. It is this:

> **Multiplication is addition done a specific way.**

Repeated multiplication *is* repeated addition of logarithms. **The ratio lineage is not a second theory sitting beside the difference lineage — it is the same theory, seen from the rung of the operation ladder one step up.**

---

# 7. Why Geometrics Never Terminate Under Difference

Module 1 asserted that a geometric string's difference tree reproduces itself forever. **Here is why**, and the reason is one line.

$$ \Delta\!\left(r^{\,n}\right) \;=\; r^{\,n+1} - r^{\,n} \;=\; r^{\,n}\,(r - 1) $$

**Differencing a geometric string returns the same string, scaled by $(r-1)$.** Not reduced, not simplified — *scaled*.

**Check it at $r = 2$**, which is Module 1's Exercise 5: the factor is $2 - 1 = 1$, so each substring is **identical** to its parent. That is exactly the self-reproducing tree the exercise shows, and now it is explained rather than observed.

**Check it at $r = 3$**, where the factor is $2$:

```
B      1    3    9   27   81
1S        2    6   18   54
2S           4   12   36
3S              8   24
```

Every level is the one above it doubled. Verified term by term.

> ### The two behaviours of one operation
> Differencing does **two completely different things** depending on what you hand it:
>
> - On a **polynomial**, it *reduces* — degree drops, and after $k$ steps there is nothing left to reduce.
> - On a **geometric**, it *scales* — the shape is preserved exactly and only the size changes.
>
> **Termination requires the first behaviour.** A geometric string terminates under differencing only if its scaling factor is zero, i.e. $r = 1$ — the constant string.

**That is the honest reason the two lineages exist.** Not that one is better, but that each is blind to what the other sees.

---

# 8. ⭐ A Question the String Tree Cannot Answer

**This section is the most important in the module, and it is a negative result.**

## 8.1 The question

You are handed a string. You difference it. Depth 3, no Root. Depth 4, no Root. Depth 5, no Root.

**Are you in a tree that will never terminate, or one you have not differenced far enough?**

## 8.2 The uncomfortable answer

**You cannot tell, and not because the method is weak. From finitely many terms, the question has no answer.**

Here is why. Every substring is one term shorter than its parent (Module 1 §5.3). So a string of $N$ terms produces:

```
N terms
     N-1 terms
          N-2 terms
               ...
                    1 term
```

**At depth $N-1$ you are left with a single value — and a row of one value is constant.** Trivially, vacuously, always.

**So every finite string terminates.** Take Module 1's Exercise 5, the geometric string that "never terminates", and give it only five terms:

```
B      1    2    4    8   16
1S        1    2    4    8
2S           1    2    4
3S              1    2
4S                 1        <- one value. "Constant". Root?
```

**No.** That is not a Root. It is the table running out of string.

## 8.3 What this means

> **Non-termination is a property of the infinite string. It is not visible in any finite sample of it.**

Given $N$ terms, there is **always** a polynomial of degree at most $N-1$ passing through them — so any finite data whatsoever is consistent with a terminating difference lineage. **A descent that has not gone constant has told you nothing except that it has not gone constant yet.**

## 8.4 The rule this forces

> ### A Root claim must state the region it was established over.
> "The descent went constant at depth $j$" is only meaningful if the constant row has **enough entries to be non-trivially constant**. One entry is not constancy. Two is barely evidence. **Say how many terms were in the row, and how many terms you started with.**

**This is Module 1 §9.4 in a new setting.** There the rule was *a sample can prove presence, never absence*. Here: **the absence of a Root in your data is not the absence of a Root.** You have looked at a region; say which region.

## 8.5 The honest procedure

When you *do* know the generating rule, the question is settled by §7 and §6.3 rather than by looking:

| If you know the string is… | then the difference lineage… | and the ratio lineage… |
|--------------------------------------|-----------------------------------|---------------------------|
| polynomial of degree $k$ | terminates at depth $k$ | does not terminate |
| geometric with ratio $r \neq 1$ | never terminates | terminates at depth 1 |
| neither | see §9 | see §9 |

**Knowledge of the rule settles it. Inspection of finitely many terms never does.**

---

# 9. The Sequence Between

We now have two instruments. **Difference** sees polynomials and is blind to geometrics. **Ratio** sees geometrics and is blind to polynomials.

**Is there a string that neither one closes?**

## 9.1 The Fibonacci string

$$ P = (1,\; 1,\; 2,\; 3,\; 5,\; 8,\; 13,\; 21, \ldots), \qquad P_{n+1} = P_n + P_{n-1} $$

## 9.2 Under difference — it reproduces itself

```
B      1    1    2    3    5    8   13
1S        0    1    1    2    3    5
2S           1    0    1    1    2
```

**The first substring is the Fibonacci string again, shifted back one place.** So is the second. So is every one after it.

**Why:** $\Delta F_n = F_{n+1} - F_n = F_{n-1}$, directly from the defining rule. **Differencing a Fibonacci string walks backwards along it.** There is no Root at any depth.

## 9.3 Under ratio — it approaches but never arrives

```
n:            1        2        3        4        5        6
F(n+1)/F(n):  1     2.0      1.5   1.6667   1.6000   1.6250
```

The ratios do not go constant. **But they are visibly closing on something** — and they alternate above and below it.

That something is

$$ \varphi \;=\; \frac{1 + \sqrt 5}{2} \;=\; 1.6180339887\ldots $$

**Neither lineage closes the Fibonacci string.** Difference gives back the string itself; ratio gives a sequence that converges without ever becoming constant.

> ### The Fibonacci string is the object Module 1 promised: **exactly closed under addition, only asymptotically closed under multiplication.**

---

# 10. The Gap, Measured Exactly

"Approaches but never arrives" is a description. **Here is the exact quantity, at every step.**

## 10.1 The ratio's distance from φ

$$ \frac{F_{n+1}}{F_n} - \varphi \;=\; \frac{(-1)^{\,n}}{\varphi^{\,n} F_n} $$

**Verified by hand at four consecutive steps:**

| $n$ | $F_{n+1}/F_n$ | gap, computed | $(-1)^n / (\varphi^n F_n)$ |
|----|---------------------|-------------------|--------------------------------------------------------|
| 1 | $1$ | $-0.6180339887$ | $-1/(1.6180339887 \cdot 1) = -0.6180339887$ ✔ |
| 2 | $2$ | $+0.3819660113$ | $+1/(2.6180339887 \cdot 1) = +0.3819660113$ ✔ |
| 3 | $1.5$ | $-0.1180339887$ | $-1/(4.2360679775 \cdot 2) = -0.1180339887$ ✔ |
| 4 | $1.6\overline{6}$ | $+0.0486326780$ | $+1/(6.8541019662 \cdot 3) = +0.0486326780$ ✔ |

**Three things are visible in that column and all three matter:**

- **The sign alternates** — $(-1)^n$ — which is why the ratios straddle φ rather than creeping up to it.
- **The magnitude shrinks by roughly a factor of $\varphi^2 \approx 2.618$ each step**, because $\varphi^{\,n} F_n$ grows like $\varphi^{2n}$.
- **It is never zero.** For any finite $n$, $\varphi^{\,n} F_n$ is finite, so the gap is a nonzero number. **The ratio lineage cannot terminate, and this is the proof rather than the observation.**

## 10.2 The same gap as an exact integer identity

The measurement above uses φ, an irrational number. **There is a version using no irrationals at all.**

Take the quantity $L(x) = x^2 - x - 1$, which is zero exactly at $x = \varphi$, and evaluate it at each ratio:

$$ L\!\left(\frac{F_{n+1}}{F_n}\right) \;=\; \frac{F_{n+1}^2 - F_{n+1}F_n - F_n^2}{F_n^2} \;=\; \frac{(-1)^{\,n}}{F_n^{\,2}} $$

**by Cassini's identity** $F_{n+1}F_{n-1} - F_n^2 = (-1)^n$.

**Checked exactly, no decimals:**

| $n$ | ratio $x$ | $L(x) = x^2 - x - 1$ | $(-1)^n / F_n^2$ |
|------|-----------------|-----------------------------------------------|------------------------------|
| 2 | $2/1$ | $4 - 2 - 1 = 1$ | $+1/1 = 1$ ✔ |
| 3 | $3/2$ | $9/4 - 3/2 - 1 = -1/4$ | $-1/4$ ✔ |
| 4 | $5/3$ | $25/9 - 5/3 - 1 = 1/9$ | $+1/9$ ✔ |
| 5 | $8/5$ | $64/25 - 8/5 - 1 = -1/25$ | $-1/25$ ✔ |

> ### The gap between the two lineages is $(-1)^n / F_n^2$ — an exact rational number at every step, with no approximation anywhere.
> **This is what "measurable exactly at every step" meant.** The alternating sign is not an observation about the pattern; it is $(-1)^n$, and it is a theorem.

## 10.3 Where φ actually comes from

Notice what did **not** happen. **φ was not introduced, assumed, or looked up.** It arrived as the answer to a question about two lineages:

> *For which value does the ratio lineage of an additively-closed string want to terminate?*

A string that is exactly additive and asymptotically multiplicative must satisfy both closures at once. Write $x$ for the ratio it is heading toward: adding gives $F_{n+1} = F_n + F_{n-1}$, and dividing through by $F_n$ gives

$$ x \;=\; 1 + \frac{1}{x} \qquad\Longleftrightarrow\qquad x^2 - x - 1 = 0 \qquad\Longleftrightarrow\qquad x = \varphi $$

> **φ is the fixed point where the difference lineage and the ratio lineage agree.** It is the number at which "add the previous term" and "multiply by a constant" become the same instruction.

That is a considerably better reason to care about φ than being told it is the golden ratio.

---

# 11. Exercises

## 11.1 Problems

**Exercise 1.** Build the ratio lineage of $3, 12, 48, 192, 768$. Give the Root, its depth, and the Terminator.

**Exercise 2.** The string $2, 6, 18, 54$ is geometric with $r = 3$. Predict its **difference** lineage using §7 before computing it, then compute it and check.

**Exercise 3.** Why can the ratio lineage not be applied to $B^{2|f} = (0, 1, 4, 9, 16)$ as written? State the fix and the cost of the fix.

**Exercise 4.** Take the mixed string $n \cdot 2^{\,n}$ for $n = 1 \ldots 5$: $\;2,\; 8,\; 24,\; 64,\; 160$. Difference it, then take ratios. **Does either lineage terminate?** What does that tell you about strings built from a polynomial *times* a geometric?

**Exercise 5.** A colleague differences a string of six terms, reaches a single value at depth 5, and reports "Root found, degree 5". **What is wrong with the claim, and what would you need to see instead?**

**Exercise 6.** Compute $L(x) = x^2 - x - 1$ at $x = 13/8$ exactly, and check it against $(-1)^n / F_n^2$.

## 11.2 Answers

**Exercise 1.**

```
B      3   12   48  192  768
1S        4    4    4    4      <- ROOT = 4, at depth 1
2S           1    1    1        <- TERMINATOR
```

Root 4 at depth 1; Terminator the string of 1s. The leading value 3 is invisible to the ratio Root, per §2.3.

**Exercise 2.** Prediction from §7: differencing scales by $(r-1) = 2$, so each substring should be its parent doubled, and the descent should never terminate.

```
B      2    6   18   54
1S        4   12   36
2S           8   24
3S             16
```

Confirmed — each level is the one above doubled. (Note the descent bottoms out at one value only because the string was four terms long; that is §8.2, not a Root.)

**Exercise 3.** The first term is $0$, so the first comparison is $1/0$ — undefined. **Fix:** start the index at $n = 1$, giving $1, 4, 9, 16$. **Cost:** you have discarded a term, and with it any information the tree held about index 0. The difference lineage would have needed no such concession — §4.2.

**Exercise 4.**

```
B      2    8   24   64  160
1S        6   16   40   96
2S          10   24   56
3S             14   32
4S                18
```

```
ratios:  4,  3,  2.667,  2.5   -> heading toward 2, never constant
```

**Neither terminates.** The difference lineage leaves a geometric factor behind at every level; the ratio lineage leaves a polynomial factor behind. **A product of a polynomial and a geometric is closed by neither instrument** — each strips away only its own half. This is the natural motivation for a composite lineage, and it is taken up in Module 3.

**Exercise 5.** Six terms differenced to depth 5 leaves **one value**, and one value is trivially constant (§8.2). **The colleague has observed the table running out of string, not a Root.** To claim a Root at depth 5 you would need a constant row with several entries in it — which means starting with several more terms — and the claim should state how many terms were in the row and how many the descent began with (§8.4).

**Exercise 6.** $x = 13/8$, which is $F_8/F_7$, so $n = 7$.

$$ L(13/8) = \frac{169}{64} - \frac{13}{8} - 1 = \frac{169 - 104 - 64}{64} = \frac{1}{64} $$

Hmm — the sign is positive while $(-1)^7$ is negative. **Check the indexing:** with $F_1 = 1, F_2 = 1, F_3 = 2, F_4 = 3, F_5 = 5, F_6 = 8, F_7 = 13$, the ratio $13/8$ is $F_7/F_6$, so $n = 6$, not 7. Then $(-1)^6/F_6^2 = +1/64$ ✔.

*This exercise is included precisely because the indexing is easy to slip on, and because the check catches the slip.*

---

# 12. Glossary and Notation Additions

**Only two new notations, as promised in §0.2:**

| Symbol | Meaning |
|------------------------------------|----------------------------------------------------------------|
| $jS_{\div}$ | A ratio substring — comparative substring with $h(a,b) = b/a$ |
| $[\,\text{direction}\,|\,\text{factor}\,]$ | The Comparative Split in multiplicative form: growth/decay, and by how much |

**New terms:**

| Term | Meaning |
|--------------|--------------------------------------------------------------------------------------|
| **Ratio lineage** | The substring lineage generated by $h(a,b) = b/a$ |
| **Terminator pair** | That difference lineages end at $0$ and ratio lineages end at $1$ — the identities of their respective operations |
| **The Bridge** | $\text{ratio} = \exp \circ\, \text{difference} \circ \log$ — the two lineages are one theory in two coordinate systems |
| **Total / partial** | A lineage is *total* if defined on every pair (difference) and *partial* if not (ratio, undefined at zero) |

## 12.1 Status of claims

| Result | Status |
|-------------------------------------------------------|---------------------------------------------|
| Ratio Root of a geometric is $r$, at depth 1 | **Theorem** (§2.3) |
| Terminators are the operation's identity | **Theorem** (§3) |
| Ratio is partial; difference is total | **Theorem** (§4.2) |
| The Comparative Split survives to ratio | **Theorem** (§5) |
| The Bridge: ratio $=\exp\circ$ difference $\circ\log$ | **Theorem** (§6.2) |
| $\Delta(r^n) = r^n(r-1)$; geometrics scale, never reduce | **Theorem** (§7) |
| Non-termination is invisible in finite data | **Theorem** (§8.2–§8.3) |
| Fibonacci closed by neither lineage | **Theorem** (§9) |
| Gap $= (-1)^n/(\varphi^n F_n)$ | **Theorem**; checked at $n = 1,2,3,4$ |
| Gap $= (-1)^n/F_n^2$ via Cassini | **Theorem**; checked exactly at $n = 2,3,4,5$ |
| φ is the fixed point of $x = 1 + 1/x$ | **Theorem** (§10.3) |
| Polynomial × geometric closed by neither | **Observation** (§11.2 Ex. 4); Module 3 |

---

# 13. A Note on Two Vocabularies

**This concerns the corpus rather than the mathematics, and it is recorded so no reader is caught by it.**

The names *Prime String* and *Base String* are used with **different meanings** in two places in the Prime Framework material:

| Term | This syllabus (following the Foundations documents) | The reference implementation |
|-------------|-----------------------------------------|----------------------------------------------|
| **Prime String** | a generated sequence: a seed and a rule $f$ | the atomic **alphabet**, whose length is the numeric base |
| **Base String** | each Prime value raised to the $k$-th power | the ordered sequence of **registers** for $0 \ldots N$ |

**By ruling of the principal investigator, this syllabus keeps the Foundations meanings**, which are the ones Module 1 published. **Where the implementation's meanings are referred to, they are marked `_OLD`** — `Prime String_OLD`, `Base String_OLD` — so that the two can never be silently interchanged.

**`_OLD` marks the usage this syllabus does not adopt. It is a disambiguation marker and not a claim about which was written first**, which has not been established.

---

# 14. Looking Ahead — Module 3

Two threads are left deliberately open.

**The composite lineage.** Exercise 4 showed a string — polynomial times geometric — that neither instrument closes, because each strips away only its own half. The natural response is a lineage that does both, and the natural question is whether the order matters.

**Reading the damage.** Module 1 §9.2.3 observed that the Root row is its own error detector: corrupt one term and the constancy breaks. **But a detector is not a locator.** A single corrupted term propagates downward in a structured, binomial-weighted wedge — and a structured pattern may carry the position of its own cause. Whether a String Tree can tell you *where* an error was, and not merely *that* there was one, is the question Module 3 opens with.

---

# 15. Acknowledgements

Module 1 was tested by two readers who were not mathematicians and who returned thirteen defects between them, including an unstated lemma beneath its primary proof and an overstated claim about its own certainty. **This module was written with those returns open on the desk**, and §0.2, §4, §5, §6.3(c) and §8 exist because of specific things they asked for.

**Their strongest single contribution was not a defect but a method:** report where you *went back*, not whether you understood — and treat a reader who never fatigues as a lower bound on difficulty rather than a measure of it.

---

# 16. Revision History

**Version 3.** **Column widths.** The table audit in the previous version corrected blank headings but left a second fault untouched, because it examined the *source* rather than the *rendered document*. **Every table was being given equal column widths** — a uniform separator row carries no width information, so the converter divided the page evenly regardless of content. A column holding one symbol received the same space as one holding a full sentence, which crushed the long columns and left equations without room to display. **All 35 tables now carry separator widths proportional to their actual content.**

*The source was correct throughout. What was wrong was the space the content was given to appear in — which is why a check on the source could not find it.*


**Version 2.** **Table audit.** Every table in this module was checked for blank cells and for rows whose width did not match their header. **The fault found was blank column headings** — a column with no heading reads as missing information, and in a rendered document it simply appears empty. All are now labelled.

*Method note, since it matters more than the fix:* the first hypothesis was that a `|` inside mathematics was splitting cells, which would have been a serious and silent corruption. **That was checked against the rendered document and proved false** — the converter's cell-splitter is mathematics-aware. Had the fix been applied on the hypothesis rather than on the evidence, it would have mangled every notation in the syllabus to solve a problem that did not exist.

One table corrected: §5's comparison of the two lineages had an unlabelled first column, now **What the comparison carries**.

---

*End of Module 2, Version 3.*
