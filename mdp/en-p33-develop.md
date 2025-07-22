![](http://fondinfo.github.io/images/dev/bug-feature.png)
# Software Development
## Introduction to Programming

---

![large](http://fondinfo.github.io/images/dev/waterfall-model.svg) Waterfall model
# 🌱 Waterfall Life Cycle

- **Analysis**
    - Model, requirements, feasibility
- **Design and Implementation**
    - Architectural components... class details
- **Testing**
    - Requirements compliance, software quality
- **Release and Maintenance**
    - 40%-80% of total cost (DoD, HP)
    - Requirements not known or not correctly understood
    - Changing operating conditions…

>

[Winston W. Royce, 1970](https://univpr-my.sharepoint.com/:b:/g/personal/michele_tomaiuolo_unipr_it/EQfW_uuaEK1CqznE8JhlhPYB_0to41SqFooYximIZLitxw?e=Znuk0A) - [Robert L. Glass, 2001](http://www.eng.auburn.edu/~kchang/comp6710/readings/Forgotten_Fundamentals_IEEE_Software_May_2001.pdf)

---

![large](http://fondinfo.github.io/images/dev/rup-cycle.png)
# 🌱 Software Evolution

- Ineliminable evolution for many systems
    - Performance, quality, functionality (perfective maintenance, ~60%)
    - Anomalies and errors (corrective maintenance, ~20%)
    - Environmental changes (adaptive maintenance, ~20%)
- Iterative development and agile methodologies
    - Frequent and incremental release
    - <http://agilemanifesto.org/>

---

![large](http://fondinfo.github.io/images/dev/programmer.svg)
# 🌱 Software Quality

- The qualities on which a software system is evaluated can be:
    - **Internal**, concerning characteristics related to the development **process** and not directly visible to users
    - **External**, concerning the functionalities provided by the software **product** and directly visible to users
- Categories are linked:
    - *Product quality is process quality*

---

# ⭐ External Qualities

- **Correctness and reliability**: the system meets specifications, absolutely or with a certain probability
- **Robustness**: the system behaves reasonably even outside specifications
- **Efficiency**: makes good use of computing resources
- **Scalability**: better performance with more resources
- **Security**: confidentiality, authentication, authorization, accounting
- **Usability**: user interface allows natural interaction

---

# ⭐ Internal Qualities

- **Verifiability**: system based on formal model
- **Reusability**: parts for building new systems
- **Maintainability**: repairability, evolvability (new specifications), adaptability (environmental changes)
- **Interoperability**: ability to cooperate with other systems, even from other manufacturers
- **Portability**: suitable for multiple hw/sw platforms
- **Understandability**: readable, documented code
- **Modularity**: interaction between cohesive components

---

![](http://fondinfo.github.io/images/dev/gearwheel.png)
# 🌱 Specifications

- Against what do we evaluate the **correctness** or **reliability** of a program?
- Programmer's idea
    - Not formulated, not documented
    - Incomplete, mutable, easily forgotten
- Specifications (formal or informal)
    - Formulated, written, studied and shared <br> → Part of the design and the program
    - Axiomatic specifications: logical expressions or assertions <br> → **Preconditions, postconditions, and invariants**

---

# 🌱 Pre- and Post-conditions

- **Preconditions**
    - Establish whether a method can be called
    - Prerequisites for activation
- **Postconditions**
    - Establish whether the method returns the expected value, i.e., whether it produces the desired effect
    - … In relation to parameters (which satisfy the preconditions)
    - Define the meaning of the method
- **Division of responsibilities** between modules
    - Error of the *calling* code (*client*) if preconditions not met
    - Error of the *called* code (*server*), if postconditions not met

---

# 🌱 Responsibilities and Contracts

- **Preconditions + postconditions = contract**
    - … between calling module and called module
- Infringement of a contract: serious problem
    - Error with respect to specifications
    - Exception and/or termination
- No **division of responsibility** → overlaps
    - All modules assume many responsibilities
    - *Defensive programming*: all parts of the program check all conditions
    - Large program → even larger

---

# 🛠️ Contract Example

``` py
def sqrt(x: float) -> float
```

- Preconditions: `x >= 0`
- Postconditions: `abs(result * result - x) <= 0.00001`
- Calling code
    - Obligations: must pass a non-negative number
    - Benefits: receives the square root of the number
- Called code
    - Obligations: returns a number `r` such that `r * r ≃ x`
    - Benefits: can assume `x` is not negative

---

![](http://fondinfo.github.io/images/qt/fifteen-puzzle.jpg)
# 🛠️ Class Invariant

- Constraint on the internal state of an object
    - Throughout its life cycle, for every *stable* state
    - Satisfied by the constructor and public methods
    - But not necessarily by private methods
- "Sanity criterion" of the object
    - Strengthening of pre- and post-conditions
- E.g.: class for the *Fifteen Puzzle*
    - Position `x` of the empty cell: always between `0` and `cols-1`
    - Position `y` of the empty cell: always between `0` and `rows-1`
    - The value `0` is always stored in that position

---

# ⭐ Inheritance and Contracts

![](http://fondinfo.github.io/images/dev/contract-inherit.svg)

- ❓ *What is the relationship between the assertions of a class and those of its descendants?*

---

# ⭐ Substitutability Principle

- Polymorphism: possible execution of a method of a subclass, instead of the base class
    - Subclass methods can redefine base class methods... but not arbitrarily
- Subclass contracts must *respect base class contracts* ("subcontracts")
    - *Preconditions*: must not be stronger
    - *Postconditions*: must not be weaker
    - *Class invariants*: must not be weaker

> Require no more, promise no less

---

# 💡 Design by Contract

- Paradigm proposed in the *Eiffel* language (Bertrand *Meyer*, 1986)
- Use of assertions in various development phases
    - *Design*: pragmatic approach to specifications
    - *Implementation*: guide for programming
    - *Documentation*: interfaces with additional info
    - *Testing*: DbC delimits test cases (for reliability)
    - *Maintenance*: DbC helps uncover errors earlier
    - *End-use*: exceptions raised if violations occur

---

# 🛠️ Python Assertions

- Boolean expressions, similar to mathematical predicates
- Express semantic properties of classes and methods
- Useful for testing and debugging, but also documentation
    - Express the programmer's intention
- Violation → **AssertionError**
    - Normally: *abort*, program termination

``` py
assert age > 0
```

---

# 🛠️ Assertions and Contracts

- Assertions are generally useful for:
    - Preconditions, postconditions, class invariants
    - Internal and control flow invariants
- Incorrect public method arguments → exception
    - `ValueError` or `TypeError`
- Usually, assertions are used for debugging, but disabled in production
    - `python -O some_code.py`

---

# 🛠️ Pre- and Post-conditions

``` py
def sqrt(x: float) -> float:
    '''
    Precondition: x >= 0
    Postcondition: abs(result * result - x) <= 0.00001
    '''
    if x < 0:
        raise ValueError("sqrt: arg < 0")

    # ...

    assert abs(result * result - x) <= 0.00001
    return result
```

---

# 🛠️ Exceptions

- Besides incorrect parameters, various unexpected situations
- **try** to handle these situations separately
- In case of an error in `try`, execution stops immediately
- The `except` block is executed

``` py
x = None
while x is None:
    try:
        x = int(input("Please enter a number: "))  # ValueError?
        print("That's fine")
    except:
        print("Oops! That was not a valid number. Try again...")
print("The square is", x ** 2)
```

---

# 🥷 Different Exceptions

- In `try`, different types of errors are possible
- Followed by various `except` blocks
- If an error handler is missing, the program terminates abruptly

``` py
try:
    x = float(input("Please enter a number: "))  # ValueError?
    y = 1 / x
    print("Inverse: ", y)
except ValueError:
    print("Oops! That was not a valid number.")
except ZeroDivisionError:
    print("Oops! Cannot divide by 0.")
```

---

# Verification and Validation

---

![large](http://fondinfo.github.io/images/dev/v-model.svg)
# 🌱 Verification and Validation

- Show that the system...
    - Conforms to specifications
    - Meets user needs

> Verification: Are we building the product right? <br> Validation: Are we building the right product? <br> *(Barry Boehm)*

- Includes system review and testing
- **Test cases**, derived from specifications

---

![large](http://fondinfo.github.io/images/dev/first-bug.jpg) Report of the first "bug" <br> Grace Hopper's group
# 🌱 Cost of Bugs

- Finding bugs, difficult and frustrating 😫
    - Testing: ~ 20-40% of project costs
    - Time and resources
- B. Boehm: **bring out** bugs in early development stages!
    - If finding a problem during requirements specification costs 1$...
    - 5$ in design
    - 10$ in programming
    - 20$ in unit testing
    - Up to 200$ after delivery
    - Many errors already in requirements specification

>

[nationalgeographic.org](https://www.nationalgeographic.org/thisday/sep9/worlds-first-computer-bug)
–
[newyorker.com](https://www.newyorker.com/magazine/2018/12/10/the-friendship-that-made-google-huge)

---

# 💡 Formal Proofs

- Mathematical demonstration of a program
    - Alternative (~ academic) to testing
    - Annotation of the program with mathematical assertions: expected behavior
    - Properties valid for the various constructs of the program
    - Often for *functional languages* (without side effects)
- Proof that post-conditions are verified, if:
    - Preconditions are verified
    - Program terminates
- Automatic proofs
    - If manual → errors (more than in the program?)

>

<https://coq.inria.fr/about-coq>

---

# ⭐ Software Review

- Code analysis by *colleagues* 🧐
    - To evaluate its characteristics and functionalities
- **Code walk-through**
    - Selection of code portions and input values
    - Paper simulation of system behavior
- **Code inspection**, more formal and focused
    - Use of uninitialized variables
    - Infinite loops
    - Reads from unallocated memory portions
    - Improper memory release
