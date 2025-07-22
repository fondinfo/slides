![](http://fondinfo.github.io/images/comp/walle-eve.png)
# Automata
## Introduction to Computer Science <br> Michele Tomaiuolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/comp/executor.svg) ![](http://fondinfo.github.io/images/comp/automata-theory.svg) ![](http://fondinfo.github.io/images/hist/1942-human-computers.jpg)
# 💡️ Automata and Computation

- **Automaton**: *abstract machine*
- Implements a certain algorithm, according to a *computational model*
- Algorithm defined in the automaton's "machine language"
- Receives and processes input data
- Finiteness constraints
    - Finite number of components
    - Finite cardinality of I/O alphabets

> In 1942 the computer was not a thing, it was a person.

[Top Secret Rosies The Female Computers of WWII Documentary](https://youtu.be/IXtb4fA65qE?t=450)

---

![](http://fondinfo.github.io/images/comp/c3po.png) ... 6M languages
# ⭐ Language Recognition

- *Membership* problem
    - Given string `$x$`, determine if `$x \in L$`
- **Type 3** languages: recognized by **FSM**, *finite state machines*
    - Ex.: `$\{a^n b : n \geq 0\}$`, from `$S \to aS|b$`
- **Type 2** languages: **NPDA**, *non-deterministic pushdown automata*
    - Ex.: `$\{a^n b^n : n \geq 1\}$` from `$S \to aSb|ab$`
- **Type 1** languages: **LBA**, *linearly bounded automata*
    - Ex.: `$\{a^n b^n c^n : n \geq 1\}$`
- **Type 0** languages: **TM**, *Turing machines*
    - However, semi-decidable: if `$x \notin L$`, the process may not terminate!

---

# Finite State Machine (FSM)

---

![large](http://fondinfo.github.io/images/comp/pacman.svg) Pac-Man Ghost States
# 💡️ Games as FSM

- Internal state of each character
- Different behaviors in different states
- Events determine transitions

![small](http://fondinfo.github.io/images/comp/apple-fsm-jump.png)

>

[developer.apple.com](https://developer.apple.com/library/archive/documentation/General/Conceptual/GameplayKit_Guide/StateMachine.html)

---

# 💡️ GUI States

![large](http://fondinfo.github.io/images/comp/apple-fsm-gui.png)

---

# 💡️ Finite State Machine (FSM)

- Finite State Automaton, or Machine (FSA, or FSM)
- `$M := <\Sigma, Q, \delta, q_0, F>$`
- `$\Sigma := \{\sigma_1,\dots,\sigma_m\}$`: input alphabet
- `$Q := \{q_0, \dots, q_n\}$`: finite non-empty set of states
- `$q_0 \in Q$`: initial state
- `$F \subseteq Q$`: set of accepting final states
- `$\delta: Q \times \Sigma \to Q$`: transition function
    - Based on the current *state*…
    - and the current *input* symbol…
    - → determines the next *state*

>

[Computer Science Field Guide (NZ)](https://www.csfieldguide.org.nz/en/chapters/formal-languages/finite-state-automata/)

---

![](http://fondinfo.github.io/images/comp/fsm4.svg) Strings with <br> even number of `a` and <br> even number of `b`
# 🧪 FSM Example

- Representation of the transition function
    - *Transition table*
    - *State diagram*
- `$M := <\{a, b\}, \{q_0,q_1,q_2,q_3\}, \delta, q_0, \{q_0\}>$`

$\delta$      | $a$   | $b$
--------------|-------|---
**$\to q_0$** | $q_1$ | $q_2$
$q_1$         | $q_0$ | $q_3$
$q_2$         | $q_3$ | $q_0$
$q_3$         | $q_2$ | $q_1$

>

<https://fondinfo.github.io/play/?c19_fsm.py>

---

![](http://fondinfo.github.io/images/comp/fsm4.svg) <br> `$S \to aA | bB | \varepsilon \\ A \to aS | bC \\ B \to aC | bS \\ C \to aB | bA$`
# 💡️ Language Recognized by FSM

- Transition function extended to strings: `$\delta: Q \times \Sigma^\star \to Q$`
    - `$\delta(q_i, \varepsilon) := q_i, \forall q_j \in Q$`
    - `$\delta(q_i, \sigma_j x) := \delta(\delta(q_i, \sigma_j), x) \\ \forall \sigma_j \in \Sigma, \forall x \in \Sigma^\star$`
- Language recognized by a machine `M`:
    - `$L(M) = \{x \in \Sigma^\star : \delta(q_0, x) \in F\}$`
- FSMs recognize all and only *REG languages*
- Grammar equivalent to example FSM:
    - Each state corresponds to a non-terminal symbol <br>
    `$q_0: S, q_1: A, q_2: B, q_3: C$`
    - *$\varepsilon$-productions* for final states

---

![](http://fondinfo.github.io/images/comp/fsm-trap.svg)
# Trap State

- If the input sequence is `$x := ababa…$`
    - The automaton alternates states `$q_0, q_1$`
- Otherwise, it remains *trapped* in state `$q_2$`
    - From there, no input can be accepted
- Trap state often used for error conditions
    - But often remains *implicit*
    - Unexpected input symbol → `$x$` rejected

---

![large](http://fondinfo.github.io/images/comp/nfa-compute.svg)
# 💡️ Non-deterministic FSM

- `$M := <\Sigma, Q, \delta, q_0, F>$`
- `$Σ := \{\sigma_1, \dots, \sigma_m\}$`: input alphabet
- `$Q := \{q_0, \dots, q_n\}$`: finite non-empty set of states
- `$F \subseteq Q$`: set of accepting final states
- `$q_0 \in Q$`: initial state
- `$\delta: Q \times \Sigma \to P(Q)$`: transition function<br>Determines the *set* of next states
    - `$P(Q)$`: power set of `$Q$`
    - Set of all possible subsets of `$Q$`

---

![large](http://fondinfo.github.io/images/comp/nfa-tree.svg)
# 💡️ Non-deterministic <br> Computation

![small](http://fondinfo.github.io/images/comp/nfa.svg)

- Sometimes a symbol can activate multiple transitions
- In this case, the automaton develops *all* possible computation branches
- The string is accepted if *at least one* of the computations ends in an accepting final state

---

![](http://fondinfo.github.io/images/comp/nfsm.svg) ![](http://fondinfo.github.io/images/comp/nfsm-eq.svg) Accepts strings <br> ending with b
# 🧪 NFSM Example

- `$M := <\{a, b\}, \{q_0, q_1\}, \delta, q_0, \{q_1\}>$`

$δ$   | $a$           | $b$
------|---------------|----
$q_0$ | `$\{q_0\}$`   | `$\{q_0, q_1\}$`
$q_1$ | $\varnothing$ | $\varnothing$

- `$\{q_0\} \leftrightarrow q'_0, \{q_0, q_1\} \leftrightarrow q'_1$`

$\delta'$        | $a$        | $b$
-----------------|------------|----
`$\{q_0\}$`      | `$\{q_0\}$` | `$\{q_0, q_1\}$`
`$\{q_0, q_1\}$` | `$\{q_0\}$` | `$\{q_0, q_1\}$`

- `$M' := <\{a, b\}, \{q'_0, q'_1\}, δ', q'_0, \{q'_1\}>$`

>

<https://fondinfo.github.io/play/?c19_nfsm.py>

---

# ⭐ FSM / NFSM Equivalence

- For each state / input, multiple next states are defined
- *Non-determinism*
    - Computation = tree of autonomous computations
    - Instead of a trajectory in a state space
- In the case of FSM, non-determinism does not add computational power
- FSM / NFSM: **equivalent** formalisms
    - FSM is a special case of NFSM
    - Conversely, each element of `$P(Q)$` of an NFSM becomes a state of an FSM
    - `$P(Q)$` contains `$2^n$` (`$n=|Q|$`) elements: FSM can have an **exponentially larger** number of states than the equivalent NFSM

>

<http://www.cs.odu.edu/~toida/nerzic/390teched/regular/fa/nfa-2-dfa.html>

---

# Transition Dictionary

- Tuple to index FSM (finite state machine) transitions
- Tuple with current state and current input symbol
- Value associated with the key: new state

``` py
transition = {("Q0", "a"): "Q1", ("Q0", "b"): "Q2",
              ("Q1", "a"): "Q0", ("Q1", "b"): "Q3",
              ("Q2", "a"): "Q3", ("Q2", "b"): "Q0",
              ("Q3", "a"): "Q2", ("Q3", "b"): "Q1"}
```

- Operation cycle

``` py
new_state = transition.get((state, symbol), None)
```

---

# Non-deterministic Machine

- NFSM, non-deterministic, is in a *set* of states
- Outer curly braces: *dictionary* of transitions
    - Key: tuple of current state and symbol
- Inner curly braces: new *set* of states

``` py
states = {"Q0"}
transition = {("Q0", "a"): {"Q0"},
              ("Q0", "b"): {"Q0", "Q1"}}
```

- Operation: `new_states` is the *union* of all new states

``` py
new_states = set()
for state in states:
    new_states |= transition.get((state, symbol), set())
```

---

# Pushdown Automaton (PDA)

---

![](http://fondinfo.github.io/images/comp/pda.svg)
# ⭐ Pushdown Automaton (PDA)

- Pushdown Automaton (PDA)
- Similar to FSM, but equipped with infinite memory, organized as a stack
    - Only the top of the stack can be accessed
    - Reading the top symbol
    - Replacing the top symbol with a new string (even ε)
- In non-deterministic form, it allows recognizing *context-free languages*
- In deterministic form, it only recognizes *deterministic context-free languages* (a subclass)
    - Basis of common programming languages

---

# 💡️ PDA Definition

- `$M := <\Sigma, \Gamma, z_0, Q, q_0, F, \delta>$`
- `$\Sigma := \{\sigma_1, \dots, \sigma_n\}$`: input alphabet
- `$\Gamma := \{z_0, \dots, z_m\}$`: stack symbols
- `$z_0 \in \Gamma$`: initial stack symbol
- `$Q := \{q_0, \dots, q_k\}$`: finite non-empty set of states
- `$q_0 \in Q$`: initial state; `$F \subseteq Q$`: accepting final states
- `$\delta: Q \times \Sigma \times \Gamma \to Q \times \Gamma^\star$`: transition function
    - Based on state, input symbol, symbol at top of stack …
    - Determines next state and symbols pushed onto the stack
    - To remove the top symbol from the stack, write `$\varepsilon$`

---

![](http://fondinfo.github.io/images/comp/pda3.svg)
# 🧪 PDA Example

- PDA that recognizes `$L:=\{a^n b^n, n \geq 1\}$`
- `$M := <\{a, b\}, \{Z, Y, A\}, Z, Q, q_0, \{q_2\}, \delta>$`
- `$Q := \{q_0, q_1, q_2\}$`
    - `$q_0$`: count `$a$`'s (by pushing `$A$` on `$Y$`)
    - `$q_1$`: count `$b$`'s (by removing `$A$`)
    - `$q_2$`: accepting state

$δ$   | $a,Z$   | $a,Y$    | $a,A$    | $b,Z$ | $b,Y$             | $b,A$
------|---------|----------|----------|-------|-------------------|------
$q_0$ | $Y,q_0$ | $AY,q_0$ | $AA,q_0$ |       | $\varepsilon,q_2$ | $\varepsilon,q_1$
$q_1$ |         |          |          |       | $\varepsilon,q_2$ | $\varepsilon,q_1$
$q_2$ |         |          |          |       |                   |

>

<https://fondinfo.github.io/play/?c19_pda.py>

---

![](http://fondinfo.github.io/images/comp/nfa-compute.svg)
# ⭐ Non-deterministic PDA (NPDA)

- `$A := <\Sigma, \Gamma, z_0, Q, q_0, F, \delta_n>$`
- `$\delta_n: Q \times \Sigma_\varepsilon \times \Gamma \to P(Q \times \Gamma^\star)$`: transition function, determines the next states and stack symbols
- Ex. `$\delta(p, a, A) := \{(q, BA), (r, \varepsilon)\}$`, <br> two transitions:
    - ➊ Symbol `$A$` at the top of the stack replaced by the string `$BA$`, new internal state `$q$`
    - ➋ Symbol `$A$` at the top of the stack removed (`$\to\varepsilon$`), new internal state `$r$`
- ⭐ NPDA: **greater computational power** than PDA
    - `$L = \{a^n b^n\} \cup \{a^n b^{2n}\}, n \geq 0$`
    - `$S \to A|B, A \to aAb|\varepsilon, B \to aBbb|\varepsilon$`

---

# Turing Machine (TM)

---

![](http://fondinfo.github.io/images/hist/turing.jpg)
# 💡️ Turing Machine (TM)

- Automaton with a read/write head on a "unlimited" bidirectional tape
- At each step:
    - It is in a certain state
    - Reads a symbol from the tape
- Based on the transition function (deterministic):
    - Writes a symbol on the tape
    - Moves the head one position
    - Changes state
- Can simulate every other known computational model!

>

[A. Turing (1936). “On Computable Numbers, with an Application to the Entscheidungsproblem.” Proceedings of the London Mathematical Society, s2-42 (1): 230–265.](https://www.dropbox.com/s/w5zmu8s0vhuo75q/Turing_Paper_1936.pdf?dl=1)

---

![](http://fondinfo.github.io/images/comp/tm.png)
# 💡️ Deterministic TM

- `$M := <\Sigma, Q, q_0, F, \delta>$`
- `$\Sigma := \{σ_1, ..., σ_n, \$\}$`: tape alphabet
    - With *blank*, **`$\$$`**
- `$Q := \{q_0, \dots, q_m\}$`: finite set of states
- `$q_0 \in Q$`: initial state
- `$F \subseteq Q$`: accepting final states
- `$\delta: Q \times \Sigma → Q \times \Sigma \times \{L, R, N\}$`: transition function
    - Determines the next configuration: <br> state; symbol written on tape; head movement

---

![large](http://fondinfo.github.io/images/comp/tm-aaabbbccc.svg)
# 🧪 TM for aⁿbⁿcⁿ

- ① Mark `$a$` with `$X$`
    - Scroll right to the first `$b$`
    - Passing `$a$`'s and `$Y$`'s
- ② Mark `$b$` with `$Y$`
    - Scroll right to the first `$c$`
    - Passing `$b$`'s and `$Z$`'s
- ③ Mark `$c$` with `$Z$`
- ④ Scroll left to the first `$X$`
    - Passing `$Z$`, `$b$`, `$Y$`, `$a$`'s
- ⑤…⑨ Repetitions of ①…④
- ⑩ Symbol `$Y$` to the right of `$X$`: `$a$`'s are finished
    - Scroll right to `$\$$`
    - Passing `$Y$`'s and `$Z$`'s

---

# 🧪 Diagram for aⁿbⁿcⁿ

![](http://fondinfo.github.io/images/comp/tm-anbncn.png)

>

<https://fondinfo.github.io/play/?c19_lba.py>

---

![](http://fondinfo.github.io/images/comp/nfa-compute.svg)
# ⭐ Non-deterministic TM (NTM)

- `$M := <\Sigma, Q, q_0, F, \delta_n>$`
- `$δₙ: Q \times \Sigma \to P(Q \times \Sigma \times \{L, R, N\})$`: transition function
    - Determines one or more subsequent configurations
- *Degree of non-determinism* `$n$`
    - Max alternative transitions
    - Max children of a node in a computation tree
- ⭐ NTM: **same computational power as TM**
    - Given `$M$` NTM, `$\exists M'$` equivalent TM (`$M'$` simulates `$M$`)
- ⭐ But NTM **more efficient** (so far…)
    - `$k$` steps of `$M$` ⇒ `$k'$` steps of `M'`, `$k' \propto k n^k$`
    - `$M'$` requires exponentially more time

---

# ⭐ Linearly Bounded Automaton (LBA)

- NTM with a limit on memory size
- The tape is limited to only the cells containing the input
- LBAs recognize all and only *context-sensitive languages*, type 1

![](http://fondinfo.github.io/images/comp/lba.svg)

---

# 💡 Universal Turing Machine (UTM)

- UTM performs the computation:
    - `$(q'_0, D_m \#x) \to^\star (\alpha, q'_h, \beta)$` …
    - `$q'_0$`, initial state; `$q'_h$`, final state
    - `$D_m\#x$`: input
    - (`$D_m$`: description of `$M$`'s transition function)
- `$\iff M$` performs the computation: `$(q_0, x) \to^\star (\alpha, q_h, \beta)$`
    - `$q_0$`, initial state; `$q_h$`, accepting state; `$x$`, input
- `$M$`'s transition rules → Sequence of quintuples
    - `$D_m := d_1\#\#d_2\#\# \dots \#\#d_n$`
    - `$q_i\#\sigma_j\#q_h\#\sigma_k\#t_l \iff \delta(q_i, \sigma_j) = (q_h, σ_k, t_l)$`
- Turing's intuition: *the program is data*
    - Transition function on tape

---

# 💡 UTM Operation

- UTM **interprets** an arbitrary program on tape
    - Given the same input, UTM produces the same output as `$M$`
    - For each symbol read in `$x$` (input of `$M$`), it scrolls through the list of rules to choose the correct transition

![](http://fondinfo.github.io/images/comp/utm.svg)

---

# Computability

---

![](http://fondinfo.github.io/images/hist/church.jpg)
# 💡️ Church-Turing Thesis

- $\forall$ "effectively" computable problem, $\exists$ TM to compute it
    - TM: so far the *most powerful computational model*
    - Along with recursive functions, lambda calculus, register machines…
- But there are **unsolvable problems** (in the general case)
    - ⚠️ Attention: nothing is said about a single instance!
- *Gödel's incompleteness theorems*
    - $\forall$ formalization of mathematics that axiomatizes $\mathbb{N}$
    - $\Rightarrow \exists$ proposition neither provable nor refutable

---

![](http://fondinfo.github.io/images/comp/pinocchio-paradox.png)
# 💡️ Classic Paradoxes

- *Liar paradox*
    - This sentence is false
    - Epimenides of Crete states: "Cretans are liars"
- *Barber paradox*
    - If a barber shaves all and only those who do not shave themselves, who shaves the barber?
- *Russell's paradox*
    - Sets of sets; suppose a set can contain itself
    - Let T be the set of all sets that do not contain themselves; can we determine if T contains T?

---

# 💡️ Halting Problem

- Halting predicate, **uncomputable** (`$∀M ∀x$`)
    - `$h(D_m,x)=1$`, if `$M$` with input `$x$` halts
    - `$h(D_m,x)=0$`, if `$M$` with input `$x$` does not halt
- Let's construct *by contradiction* `$H$`, a TM that computes `$h$`, `$∀M ∀x$`
- Then let's construct `$K$`
    - If `$h(D_m,D_m)=0 \implies k(D_m)=0$`
    - Otherwise, undefined (`$K$` loops infinitely, if `$h=1$`)
- But this is absurd: `$H$` must work `$\forall M$`, even `$M=K$`
    - If `$k(Dₖ)$` is defined ⇒ `$h(D_k,D_k)=1 \implies k(D_k)$` is undefined
    - If `$k(Dₖ)$` is undefined ⇒ `$h(D_k,D_k)=0 \implies k(D_k)=0$` is defined

>

`M`: Turing machine; `Dₘ`: representation of `M` as a string

---

# More informally...

- Function `k` defined in `paradox.py` (Python is *Turing complete*)

``` py
from absurd import halt  # 😲
def k(file):
    if halt(file, file):
        while True: pass
    else:
        return False
k("paradox.py")  # this very file!
```

- Other undecidable problems (corollaries)
    - Correctness: does the program compute the desired function?
    - Reachability: will a procedure (or instruction) be executed?
    - Equivalence, ambiguity of CF grammars …
