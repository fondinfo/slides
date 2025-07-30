![](http://fondinfo.github.io/images/fun/hanoi-tower.png)
# Mathematical Logic
## Introduction to Computer Science <br> Michele Tomaiolo @ Engineering UniPR

---

![](http://fondinfo.github.io/images/repr/hair-logic.svg)
# Boolean Algebra

---

![](http://fondinfo.github.io/images/hist/boole.jpg) George Boole, 1815-1864
# 💡️ Boolean Algebra

- Boolean algebra is a formalism that operates on variables (called *Boolean variables*)
- Boolean variables can take only two values
    - `True`: 1
    - `False`: 0
- Functions (called *Boolean functions*) can be defined on Boolean variables
- Boolean functions can also take only the two values `true` and `false`

---

`$A$` | `$B$` | `$C$` | `$F_1$`
--|---|---|--
0 | 0 | 0 | 1
0 | 0 | 1 | 0
0 | 1 | 0 | 0
0 | 1 | 1 | 1
1 | 0 | 0 | 0
1 | 0 | 1 | 1
1 | 1 | 0 | 1
1 | 1 | 1 | 1

# 💡️ Function and Truth Table

- *Truth table* to define a *Boolean function*
- Resulting value for each configuration of input values

>

Sometimes, *incomplete specification*: certain input configurations cannot occur, so no value is specified

---

# 💡️ Logical Operators

- Boolean Algebra: based on a set of operators

Operator | Symbol    | Alternative Symbol
----------|-----------|---
**And** | `$\land$` | `$\cdot$`
**Or** | `$\lor$`  | `$+$`
**Not** | `$\lnot$` | Overline

- Simple functions, specified with truth tables

`$A$` | `$B$` | `$A \land B$` | `$A \lor B$` | `$\lnot A$`
------|-------|---------------|--------------|------------
0     | 0     | 0             | 0            | 1
0     | 1     | 0             | 1            | 1
1     | 0     | 0             | 1            | 0
1     | 1     | 1             | 1            | 0

---

# 💡️ Other Common Operators

Operator | Symbol | Alternative Symbol
----------|---------|---
Xor       | `$⊕$`     |
Nand      | `$\uparrow$`     | `$\bar\land$`
Nor       | `$\downarrow$`   | `$\bar\lor$`

`$A$` | `$B$` | `$A \oplus B$` | `$A \uparrow B$` | `$A \downarrow B$`
------|-------|----------------|------------------|-------------------
0     | 0     | 0              | 1                | 1
0     | 1     | 1              | 1                | 0
1     | 0     | 1              | 1                | 0
1     | 1     | 0              | 0                | 0

- Operators can be combined into *expressions*
    - Another form of defining Boolean functions
    - E.g. `$F_2(A, B, C) = A \cdot B + C$`

---

# ⭐ Properties of Operators

- Proof: compare the two truth tables

Property     | Not
-------------|--------
Complement   | `$\lnot \lnot A \equiv A$`

Property     | And                                                | Or
-------------|----------------------------------------------------|--------------------------
Commutative  | `$A \cdot B \equiv B \cdot A$`                     | `$A + B \equiv B + A$`
Associative  | `$(A \cdot B) \cdot C \equiv A \cdot (B \cdot C)$` | `$(A+B)+C \equiv A+(B+C)$`
Distributive | `$A+(B \cdot C) \equiv (A+B) \cdot (A+C)$`         | `$A \cdot (B+C) \equiv (A \cdot B)+(A \cdot C)$`
Idempotence  | `$A \cdot A \equiv A$`                             | `$A + A \equiv A$`
Identity     | `$A \cdot 1 \equiv A$`                             | `$A + 0 \equiv A$`
Of the limit | `$A \cdot 0 \equiv 0$`                             | `$A + 1 \equiv 1$`
Absorption   | `$A \cdot (A+B) \equiv A$`                         | `$A + (A \cdot B) \equiv A$`
Inverse      | `$A \cdot \lnot A \equiv 0$`                       | `$A + \lnot A \equiv 1$`
De Morgan    | `$\lnot (A \cdot B \cdot C \dots) \equiv \lnot A + \lnot B + \lnot C \dots$` | `$\lnot (A+B+C \dots) \equiv \lnot A \cdot \lnot B \cdot \lnot C \dots$`

---

# 🔬 Proofs

- De Morgan for And: `$\lnot (A \cdot B) \equiv \lnot A+ \lnot B$`

$A$ | $B$ | $\lnot A$ | $\lnot B$ | $A \cdot B$ | $\lnot (A \cdot B)$ | $\lnot A + \lnot B$
----|-----|-----------|-----------|-------------|---------------------|--------------------
0   | 0   | 1         | 1         | 0           | 1                   | 1
0   | 1   | 1         | 0         | 0           | 1                   | 1
1   | 0   | 0         | 1         | 0           | 1                   | 1
1   | 1   | 0         | 0         | 1           | 0                   | 0

- De Morgan for Or: `$\lnot (A+B) \equiv \lnot A \cdot \lnot B$`

$A$ | $B$ | $\lnot A$ | $\lnot B$ | $A + B$ | $\lnot (A+B)$ | $\lnot A \cdot \lnot B$
----|-----|-----------|-----------|---------|---------------|------------------------
0   | 0   | 1         | 1         | 0       | 1             | 1
0   | 1   | 1         | 0         | 1       | 0             | 0
1   | 0   | 0         | 1         | 1       | 0             | 0
1   | 1   | 0         | 0         | 1       | 0             | 0

---

# ⭐ De Morgan

- ⚠️ Caution with De Morgan: common error!

``` py
if x1 == x2 and y1 == y2:
    print("the points are equal")
```

``` py
if x1 != x2 or y1 != y2:  # not (x1 == x2 and y1 == y2)
    print("the points are different")
```

- Python allows comparing tuples

``` py
pt1 = x1, y1
pt2 = x2, y2
if pt1 != pt2:
    print("the points are different")
```

---

| `a`     | `a == True` || `not a` | `a == False`
|---------|-------------||---------|---
| `True`  | `True`      || `False` | `False`
| `False` | `False`     || `True`  | `True`

# 🤢️ Booleans and code smell

- ⚠️ Comparing boolean var `a` and `True`?
    - `a` already has the same value as the comparison!

``` py
if a: …  # instead of “if a == True: …”
```

``` py
if not a: …  # instead of “if a == False: …”
```

- ⚠️ Be careful with boolean results produced with `if`

``` py
if radius > 50:
    big_enough = True
else:
    big_enough = False  # Too verbose and convoluted!
```

``` py
big_enough = radius > 50  # rhs expression holds the value, already
```

---

| `$A$` | `$B$` | `$C$` | `$F$` | |
|---|---|---|---|-------------------|
| 0 | 0 | 0 | 1 | → *SP* |
| 0 | 0 | 1 | 0 |        |
| 0 | 1 | 0 | 0 |        |
| 0 | 1 | 1 | 1 | → *SP* |
| 1 | 0 | 0 | 0 |        |
| 1 | 0 | 1 | 1 | → *SP* |
| 1 | 1 | 0 | 1 | → *SP* |
| 1 | 1 | 1 | 1 | → *SP* |

# ⭐ Canonical Form SP

- **Sum of Products**: take rows with 1
    - `$F(A, B, C) := ( \lnot A \cdot  \lnot B \cdot  \lnot C) + \\ ( \lnot A \cdot B \cdot C) + (A \cdot  \lnot B \cdot C) + \\ (A \cdot B \cdot  \lnot C) + (A \cdot B \cdot C)$`
- *Principle*: which inputs make `F` true?

---

| `$A$` | `$B$` | `$C$` | `$F$` | `$\lnot F$` | |
|---|---|---|---|----|---|
| 0 | 0 | 0 | 1 | 0  | |
| 0 | 0 | 1 | 0 | 1  | → *PS* |
| 0 | 1 | 0 | 0 | 1  | → *PS* |
| 0 | 1 | 1 | 1 | 0  | |
| 1 | 0 | 0 | 0 | 1  | → *PS* |
| 1 | 0 | 1 | 1 | 0  | |
| 1 | 1 | 0 | 1 | 0  | |
| 1 | 1 | 1 | 1 | 0  | |

# ⭐ Canonical Form PS

- **Product of Sums**: take rows with 0, *negated*
    - `$F(A, B, C) := (A+B+ \lnot C) \cdot \\ (A+ \lnot B+C) \cdot ( \lnot A+B+C)$`
- *Principle*: which inputs make `$\lnot F$` true?
    - `$\lnot F(A, B, C) := ( \lnot A \cdot  \lnot B \cdot C) + \\ ( \lnot A \cdot B \cdot  \lnot C) + (A \cdot  \lnot B \cdot  \lnot C)$`
    - `$F(A, B, C) := \lnot (( \lnot A \cdot  \lnot B \cdot C) + \\ ( \lnot A \cdot B \cdot  \lnot C) + (A \cdot  \lnot B \cdot  \lnot C))$`
    - ... De Morgan twice and you get *PS*

---


# Propositional Logic

---

# 💡️ Proposition

- Declarative sentence (*statement*) with a complete meaning that can be recognized as “true” or “false”
    - **Principle of non-contradiction**: a statement cannot be simultaneously true and false
    - **Principle of excluded middle**: a statement is either true or false, there is no third possibility (*tertium non datur*)
- For example, these are propositions:
    - “A dog is an animal” - “2 = 1” - “Triangles have three sides”
- ... While these are not:
    - “The dog” - “What time is it?” - “If 2 = 1” - “No smoking!” - “I am lying” (*)

>

(*) Paradox: it cannot be determined whether the sentence is true or false

---

![](http://fondinfo.github.io/images/repr/logical-problem.png)
# 💡️ Logical Connectives

- In logic, Boolean operators to *link* propositions into a more complex form
    - “and” (*conjunction*, `$\land$`)
    - “or” (*disjunction*, `$\lor$`)
    - “not” (*negation*, `$\lnot$`)
    - The properties already seen apply
- Example of formalization
    - `$P_1 :=$` “Gold is in Chest1” <br> `$P_2 :=$` “Gold is in Chest2” <br> `$P_3 :=$` “Gold is in Chest3”
    - `$\lnot P_2 \land (P_1 \lor P_3) \land \lnot P_3 \equiv$` *(distributive property)* <br>
       `$\lnot P_2 \land (P_1 \land \lnot P_3 \lor P_3 \land \lnot P_3) \equiv$` *(inverse property)* <br>
       `$P_1 \land \lnot P_2 \land \lnot P_3$`

---

`$P$` | `$Q$` | `$P \implies Q$`
------|-------|---------
 F    |  F    |  T
 F    |  T    |  T
 T    |  F    |  F
 T    |  T    |  T

# 💡️ Logical Implication

- **Conditional connective**: expresses the “if ... then” relationship
    - `$P :=$` “I think” (*premise*, or *antecedent*)
    - `$Q :=$` “I exist” (*conclusion*, or *consequent*)
    - `$P \implies Q$`: “if I think then I exist”
- `$P \implies Q$` can also be read in the following ways:
    - From `$P$` follows `$Q$`
    - `$P$` is a *sufficient condition* for `$Q$` (if `$P$` is true, then `$Q$` is true)
    - `$Q$` is a *necessary condition* for `$P$` (if `$Q$` is false, then `$P$` is false)
- Examples of true implications:
    - “If 5 is a number then Rome is a city”
    - “If Paris is the capital of Italy, then 5 + 5 = 10”

---

# 🧪 Truth of Implication

`$P$` | `$Q$` | `$P \implies Q$` | `$Q \implies P$` | `$\lnot P \lor Q$`
------|-------|------------------|------------------|---
 F    |  F    |  T               | T                | T
 F    |  T    |  T               | F                | T
 T    |  F    |  F                | T                | F
 T    |  T    |  T               | T                | T

- `$P \implies Q$` is false in only one case: `$P$` is true and `$Q$` is false
    - `$\lnot (P \implies Q) \equiv (P \land \lnot Q)$`
    - `$P \implies Q \equiv \lnot (P \land \lnot Q) \equiv$` *[De Morgan]* <br> `$\lnot P \lor \lnot ( \lnot Q) \equiv $` *[Double negation]* <br> `$\lnot P \lor Q$` (implication true when: `$P$` is false, or `$Q$` is true)
- Implication **does not** satisfy the *commutative* property:
    - `$(P \implies Q) \neq (Q \implies P)$`

---

# 🧪 Double Implication

- **Logical equivalence**: read as “P if and only if Q”, <br> “P is a necessary and sufficient condition for Q”

`$P$` | `$Q$` | `$P \implies Q$` | `$Q \implies P$` | `$P \iff Q$` | `$(P \land Q) \lor ( \lnot P \land \lnot Q)$`
----|-----|---------|---------|---------|------------------
 F  |  F  |  T      |  T      |  T      |  T
 F  |  T  |  T      |  F      |  F      |  F
 T  |  F  |  F      |  T      |  F      |  F
 T  |  T  |  T      |  T      |  T      |  T

- `$P \iff Q$`: both implications hold, `$(P \implies Q) \land (Q \implies P)$`
    - `$P \iff Q$` true: `$P$` and `$Q$` both true, or both false
    - From distributive property and inverse property
    - `$(P \implies Q) \land (Q \implies P) \equiv ( \lnot P \lor Q) \land ( \lnot Q \lor P) \equiv \\ ( \lnot P \land \lnot Q) \lor ( \lnot P \land P) \lor ( \lnot Q \land Q) \lor (P \land Q) \equiv \\ (P \land Q) \lor ( \lnot P \land \lnot Q)$`

---

# 💡️ Logical Deduction

- A *theorem* can be reduced to the implication `$P \implies Q$`
    - `$P$` (*hypothesis*): proposition assumed to be true
    - `$Q$` (*thesis*): proposition whose truth is to be deduced
- The process of *logical deduction*, or *proof*, must follow precise reasoning schemes
    - Direct proof (*modus ponens*)
    - Proof by contradiction (*modus tollens*)

---

# ⭐ Direct Proof

- *Modus ponens*: reasoning scheme

Premises | Conclusion
---------|------------
`$(P \implies Q)$` true <br> `$P$` true | `$Q$` true

- `$P = T, P \implies Q = \lnot P \lor Q = F \lor Q = Q = T$`
- Example
    - If it's sunny, Ugo arrives by bike (implication, *inference rule*)
    - It's sunny (*fact*)
    - Ugo arrives by bike (*deduction*)
- **Observation**: the mere fact of knowing that `$P \implies Q$` is true does not allow concluding anything about `$P$` and `$Q$`

---

# 🧪 Intermediate Steps

- Proofs with multiple intermediate steps are possible
- If implications `$P \implies R, R \implies Q$` are true... <br> and if `$P$` is true... <br> then `$Q$` is also true
- `$((P \implies R) \land (R \implies Q) \land P) \implies Q$`
- Reasoning scheme

Premises | Conclusion
---------|------------
`$(P \implies R)$` true <br> `$(R \implies Q)$` true <br> `$P$` true | `$Q$` true

---

# 🧪 Equivalent Implication

`$P$` | `$Q$` | `$P \implies Q$` | `$\lnot Q$` | `$\lnot P$` | `$\lnot Q \implies \lnot P$`
----|-----|---------|------|------|----------
 F  |  F  |  T      |  T   |  T   |  T
 F  |  T  |  T      |  F   |  T   |  T
 T  |  F  |  F      |  T   |  F   |  F
 T  |  T  |  T      |  F   |  F   |  T

- These two implications are equivalent
    - `$P \implies Q$`
    - `$\lnot Q \implies \lnot P$`
    - In fact, `$\lnot P \lor Q \equiv \lnot ( \lnot Q) \lor \lnot P$`
- In proofs, we can use the second implication instead of the first

---

# ⭐ Proof by Contradiction

- If the implication `$( \lnot Q \implies \lnot P)$` is true and `$P$` is true, then `$Q$` is also true
- *Modus tollens*: reasoning scheme

| Premises | Conclusion |
|----------|-------------|
| `$( \lnot Q \implies \lnot P)$` true <br> `$P$` true | `$Q$` true |

- Example of theorem
    - `$P := m \cdot n ≠ 0$`
    - `$Q := (m ≠ 0) \land (n ≠ 0)$`
    - Proof by contradiction: `$\lnot Q \implies \lnot P$`
    - If `$(m = 0) \lor (n = 0)$`, then `$m \cdot n = 0$`

---


# Predicate Logic

---

# 💡️ Predicate, or Open Statement

- Sentence containing *variables*
    - The truth of the sentence depends on the value of the variables
    - If variables are replaced by values, it becomes a proposition
- Example
    - `$P(x) :=$` “x is an odd number”
- The *domain* of the variables must be defined
- *Truth set* of the predicate
    - Values of the variables that make the statement true
    - Subset of the domain of the variables

---

# 💡️ Predicates with Connectives

- `$P(x) \land Q(x)$` – True for `$x$` that make both `$P$` and `$Q$` true
- `$P(x) \lor Q(x)$` – True for `$x$` that make at least one of the predicates `$P$` and `$Q$` true
- `$\lnot P(x)$` – True for `$x$` that make `$P$` false
- `$P(x) \implies Q(x)$` – True for `$x$` that make `$P$` false or `$Q$` true
- `$P(x) \iff Q(x)$` – True for `$x$` that make `$P$` and `$Q$` both false or both true

---

# ⭐ Quantifiers

- A predicate can be transformed into a proposition in two ways
    - By substituting variables with values
    - Or, by *quantifying* its variables
- A variable bound to a quantifier is called *bound*, otherwise *free*
- There are two logical quantifiers
    - **Universal** quantifier
    - **Existential** quantifier

---

# 🧪 Universal Quantifier

- States that a given property holds for *all values* in the domain of the bound variable
- `$\forall x, P(x)$` – “For every x, P(x) is true”
- Examples
    - `$\forall n \in N, n \bmod 4 = 0 \implies even(n)$` – All multiples of 4 are even
    - `$\forall x \in R, \forall y \in R, (x + y)^2 = x^2 + 2xy + y^2$`

---

# 🧪 Existential Quantifier

- States that a given property holds for *at least one value* of the bound variable
- `$\exists x : P(x)$` -- “There exists at least one x such that P(x) is true”
- Examples
    - `$\exists n \in N : even(n)$` -- There exists at least one even number
    - `$\exists x \in R : 2x + 1 = 0$` -- The equation admits at least one solution
- Statements with `$\nexists$` reformulated with `$\forall$` and negating the predicate
    - `$\nexists x : x^2 < 0$`
    - `$\forall x, x^2 ≥ 0$`

---

# 🔬 Properties of Quantifiers

- Quantifiers are essentially *conjunctions* or *disjunctions* extended to all elements of a domain
    - For simplicity, domain `$D := {1, 2, 3}$`
    - `$\forall x \in D, P(x) \equiv P(1) \land P(2) \land P(3)$`
    - `$\exists x \in D : P(x) \equiv P(1) \lor P(2) \lor P(3)$`
- Two quantifiers of the same type *can* be swapped without altering the truth of the statement
- However, two quantifiers of different types *cannot* be swapped
- The following statements are very different
    - `$\forall x \in R, \exists y \in R : y \geq x$`
    - `$\exists y \in R : \forall x \in R, y \geq x$`

---

# ⭐ Negation with Quantifiers

- To negate a statement containing quantifiers, two modifications are required:
    - **➊** Replace all `$\forall$` with `$\exists$`, and vice versa
    - **➋** Negate the predicate
- Property analogous to *De Morgan*
    - In fact, quantifiers are essentially `$\land$` or `$\lor$` extended
- Examples
    - `$\lnot (\forall x, P(x)) \iff \exists x : \lnot P(x)$`
    - `$\lnot (\exists x : P(x)) \iff \forall x, \lnot P(x)$`

---

![](http://fondinfo.github.io/images/hist/plato-aristotle.jpg) Plato and Aristotle <br> ~350 BC
# 🧪 Aristotelian Syllogisms

- Modus ponens with quantifiers
    - *Major premise*: “All men are mortal” <br> `$\forall x, man(x) \implies mortal(x)$`
    - *Minor premise*: “Socrates is a man” <br> `$man(Socrates)$`
    - *Conclusion*: “Socrates is mortal” <br> `$mortal(Socrates)$`
- The quantifier can be eliminated by substituting a domain value for the variable
    - `$man(Socrates) \implies mortal(Socrates)$`
- Then apply modus ponens

---

# 🧪 Set Operations

- Let two truth sets be defined
    - `$A = \{x : P(x)\}, B = \{x : Q(x)\}$`
- *Union*
    - `$A \cup B = \{x : x \in A \lor x \in B\} = \{x : P(x) \lor Q(x)\}$`
- *Intersection*
    - `$A \cap B = \{x : x \in A \land x \in B\} = \{x : P(x) \land Q(x)\}$`
- *Complement*
    - `$A' = \{x : x \notin A\} = \{x : \lnot P(x)\}$`

---

# 🧪 Properties of Sets

- On the same sets: `A` and `B`

Property    | Set Operations           | Predicate Operations
------------|--------------------------|-------------------------
Commutative | `$A \cup B = B \cup A$` | `$P \lor Q \equiv Q \lor P$`
Commutative | `$A \cap B = B \cap A$` | `$P \land Q \equiv Q \land P$`
Associative | `$(A \cup B) \cup C = A \cup (B \cup C)$` | `$(P \lor Q) \lor R \equiv P \lor (Q \lor R)$`
Associative | `$(A \cap B) \cap C = A \cap (B \cap C)$` | `$(P \land Q) \land R \equiv P \land (Q \land R)$`
Distributive | `$(A \cup B) \cap C = (A \cap C) \cup (B \cap C)$` | `$(P \lor Q) \land R \equiv (P \land R) \lor (Q \land R)$`
Distributive | `$(A \cap B) \cup C = (A \cup C) \cap (B \cup C)$` | `$(P \land Q) \lor R \equiv (P \lor R) \land (Q \lor R)$`
Double neg. | `$(B')' = B$` | `$\lnot ( \lnot P) \equiv P$`
De Morgan   | `$(A \cup B)' = A' \cap B'$` | `$\lnot (P \lor Q) \equiv \lnot P \land \lnot Q$`
De Morgan   | `$(A \cap B)' = A' \cup B'$` | `$\lnot (P \land Q) \equiv \lnot P \lor \lnot Q$`

---

![large](http://fondinfo.github.io/images/comp/domino.svg)
# ⭐ Principle of Induction

- Let `$P(n)$` be a predicate defined on `$ℕ$`, such that:
    - **(1)** `$P(1)$` is true
    - **(2)** `$\forall n$`, assuming `$P(n)$` is true, <br> it follows that `$P(n+1)$` is also true
- Then `$P(n)$` is true `$\forall n$`

Premises | Conclusion
---------|------------
`$P(1)$` <br> `$\forall n, P(n) \implies P(n+1)$` | `$\forall n, P(n)$`

>

Some predicates are defined starting from a given `$k$`, rather than from 1

---

# 🧪 Example, Gauss's Formula

- For convenience, let `$G(n) = \frac{n \cdot (n+1)}{2}$`
- Define the predicate `$P(n)$` as: `$1 + 2 +  \cdot  \cdot  \cdot  + n = G(n)$`
- Let's prove *by induction* that the predicate is true `$\forall n$`
- **(1)** The predicate for `$n=1$` is true, in fact:
    - `$G(1) = \frac{1 \cdot (1+1)}{2} = 1$`
- **(2)** Assume `$P(n)$` is true, it follows that `$P(n+1)$` is true, in fact:
    - For the sum up to `$n+1$`, one term must be added:
    - `$1 + 2 + ... + n + n+1 = G(n) + n+1 = \\ \frac{n \cdot (n+1)}{2} + n+1 = \frac{n^2 + 3n + 2}{2} = \\ \frac{(n+1) \cdot (n+2)}{2} = G(n+1)$`
- Therefore the formula holds `$\forall n$`

---

![](http://fondinfo.github.io/images/fun/hanoi.svg)
# 🧪 Example, Tower of Hanoi

- *Rule 1*: Move only one disk at a time
- *Rule 2*: Place it only on a larger one
- *Strategy* for `$n+1$` disks
    - `$n$` disks → auxiliary peg, in `$R(n)$` moves
    - then last disk → destination
    - finally the others → destination, in `$R(n)$` moves
- Prove *by induction* that the number of moves to transfer `$n$` disks is `$R(n) = 2^n-1$`
- **(1)** For 1 disk, 1 move: `$1 = 2^1-1 = R(1)$`
- **(2)** Assume `$R(n)$` moves are needed for `$n$` disks...
    - Then for `$n+1$` disks:
    - `$R(n) + 1 + R(n) = 2 \cdot (2^n-1)+1 = 2^{n+1}-1 = R(n+1)$`
- Therefore the formula holds `$\forall n$`

---

![](http://fondinfo.github.io/images/repr/homer-genius.png)
# ⚠️ Incorrect Syllogisms and Quiz

- *Major premise*: “All geniuses are absent-minded”
    - `$\forall x, genius(x) \implies absent\_minded(x)$`
- *Minor premise*: “I am absent-minded”
    - `$absent\_minded(I)$`
- *Conclusion*: “I am a genius”
    - `$genius(I)$` – **Doh!** 😕
- Be careful to use the correct implication!
    - `$P \implies Q$`: sufficient condition, but not necessary
    - “All Swedes are blonde” …

>

<https://www.beniculturali.it/mibac/multimedia/MiBAC/documents/1228312182183_F1_Logica.pdf>
<br>
Questions 20, 22, 24, 27
