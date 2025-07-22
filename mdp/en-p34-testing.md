![](http://fondinfo.github.io/images/dev/bug-feature.png)
# Software Development
## Introduction to Programming

---

# ⭐ Testing

> Testing operations can detect the presence of errors in software but cannot prove its correctness. *(E. Dijkstra)*

> Executing a program with the intent of finding errors. *(Glen Myers, The Art of Software Testing)*

- Verify the system in a sufficiently large set of cases...
- → plausible similar behavior in remaining situations as well

---

![large](http://fondinfo.github.io/images/dev/v-model.svg)
# ⭐ Test Classification

- Types of tests
    - **White box** (*in the small*)
    - **Black box** (*in the large*)
- Levels of tests
    - *Unit test*
    - *Integration test*
    - *System test*
- Test repetition
    - *Regression test*

>

<http://people.cs.aau.dk/~normark/oop-csharp/html/notes/test-book.html>

---

# ⭐ Testability

- Software *quality* that facilitates error detection
    - **Observability** – Test results are available
    - **Controllability** – Possibility to set program inputs and state before running a test
    - **Decomposability** – Program divided into parts that can be tested individually
    - **Understandability** – The correct (desired) behavior of the program is understood
- → Development for testability
    - Tests can be written even before the program
    - *Test driven development, TDD*

---

# White-box testing

---

# ⭐ White-box testing

- Tests based on knowledge of the internal code structure
- An error cannot be discovered if the code part containing it is never executed
- **Statement test**
    - A set of tests T such that, by executing program P on all cases of T, every instruction of P is executed at least once (utopian test?)
    - **Branch test** (decision coverage)
    - **Branch & condition test** (… conditions)

---

# ⭐ Basic path testing

- Objective: cover all instructions and conditions (*white box*)
- Choose minimum set of paths for coverage
    - Draw flow diagram
    - Abstract the diagram into a flow graph
    - Cyclomatic complexity `n` = test metric
    - Find `n` test cases that follow each independent path
- *Path*: sequence of commands, from beginning to end
- *Independent path*: adds at least one new instruction compared to already identified paths

---

![large](http://fondinfo.github.io/images/dev/flow-chart.png)
# 🛠️ Flow Diagram

``` py
def f():
    # entry
    while a:
        x()
        if b:
            if c: y()
            else: z()
            # p
        else:
             v()
             w()
        # q
    # exit: r
```

---

![large](http://fondinfo.github.io/images/dev/flow-graph.png)
# ⭐ Flow Graph

- From flow diagram, small abstraction
- **Cyclomatic complexity**
    - Number of possible independent paths
- From graph theory
    - Number of predicate nodes + 1, or...
    - Number of regions of the flow graph
- `A, r`
- `A, X, B, C, Y, p, q… A, r`
- `A, X, B, C, Z, p, q… A, r`
- `A, X, B, V, W, q… A, r`

---

# Black box testing

---

![large](http://fondinfo.github.io/images/dev/black-box.svg)
# ⭐ Black box testing

- White-box testing:
    - Impossible for large systems
- ⇒ System = black box
    - Test cases from requirements specifications
    - Verification of correspondences between input and output
- Desired: find errors...
    - *Functional*: correct results for given method inputs?
    - *Interface*: data correctly passed between methods?
    - *Efficiency*: is the method fast enough?

---

# ⭐ Equivalence Partitions

- Partitioning inputs into **equivalence classes**
    - Unrealistic to test all possible inputs (e.g., `sqrt`)
    - Hypothesis: sufficient to test only one case per class
    - Includes boundary cases and invalid values
    - Preconditions: reduce the number of test cases

``` py
def swap_elements(v: list, i: int, j: int):
    '''
    Exchange element i and j in list v
    v: empty, one element, more elements
    i, j: one or both indexes out of range...
          or both in range: i < j, i > j, i = j
    '''
    # ...
```

---

# 🧪 Testing Ball

- Equivalence classes for movement
    - Inside the arena
    - Against each of the edges
    - Against each of the corners
    - Beyond each of the edges
- Collision tests
    - Against ghost
    - Against turtle
    - Against another ball
    - For each character, consider its position relative to the ball <br> top / bottom / right / left

---

# ⭐ Regression testing

- Purpose: find regression errors
    - Errors in a program that was previously correct and has been recently modified
    - A regression error is an error that was not there before
- After modifying part `P` in program `Q`
    - Test that part `P` functions correctly
    - Test that the entire program `Q` has not been damaged by the modification

---

# Testing in Python

---

# 🧪 How to Test Code?

- Use a *debugger* to evaluate expressions at runtime
    - You can decide what to evaluate depending on the execution flow and generated values, without recompiling
- *Print* statements within the program
    - Expression value written to console or log file
- Both styles are poorly *automated*
    - Requires active intervention during tests
    - User judgment of results
    - Which values to analyze? Are they consistent?
- Poorly *composable*
    - Difficult to control many expressions in the debugger
    - “*Scroll blindness*”: too many print statements ⇒ less readable code

---

# 🧪 Unittest Library

- `unittest` tests do not require continuous user intervention or judgment
- Easy to run many tests together on a given project
- How to define a test?
    - Create a subclass of `unittest.TestCase`
    - Write test methods, named with the `test` prefix
    - To check the validity of an expression, use `assertTrue(bool)`

---

# 🧪 Test Example

- Check that a ball bounces correctly at the corner

``` py
import unittest
from c06_ball import Ball, ARENA_W, ARENA_H, BALL_W, BALL_H

MAX_X, MAX_Y = ARENA_W - BALL_W, ARENA_H - BALL_H

class SimpleTest(TestCase):

    def test_corner(self):
        b = Ball(MAX_X, MAX_Y)  # dx = 4, dy = 4
        b.move()
        self.assertTrue(b.pos() == (MAX_X - 4, MAX_Y - 4))

if __name__ == "__main__":
    unittest.main()
```

>

<https://fondinfo.github.io/play/?c21_simpletest.py>

---

# 🧪 Parameterized Tests

- Repeat a test with different parameters
    - One test case for each group of parameters?
    - In some applications, a huge number of tests!
- Simplistic solution: test containing a loop
    - At each iteration, a different group of parameters is prepared
    - Instructions to be tested are executed on the new parameters
    - Problem: the test stops at the first error

---

# 🧪 Parameterized Test, Simplistic

- If a test fails, all subsequent ones are not executed

``` py
class ParamBallTest(unittest.TestCase):

    def test_move(self):
        test_values = [ (40, 80, 44, 84),
                        (40, MAX_Y - 4, 44, MAX_Y),
                        (40, MAX_Y, 44, MAX_Y - 4),
                        (MAX_X - 4, 80, MAX_X, 84),
                        (MAX_X, 80, MAX_X - 4, 84) ]

        for param in test_values:
            x0, y0, x1, y1 = param
            b = Ball(x0, y0)
            b.move()
            self.assertTrue(b.pos() == (x1, y1))
```

---

# 🧪 Subtests, Python 3.4

- All subtests are executed, even if one fails

``` py
class ParamBallTest(unittest.TestCase):

    def test_move(self):
        test_values = [ (40, 80, 44, 84),
                        (40, MAX_Y - 4, 44, MAX_Y),
                        (40, MAX_Y, 44, MAX_Y - 4),
                        (MAX_X - 4, 80, MAX_X, 84),
                        (MAX_X, 80, MAX_X - 4, 84) ]

        for param in test_values:
            with self.subTest(param=param):
                x0, y0, x1, y1 = param
                b = Ball(x0, y0)
                b.move()
                self.assertTrue(b.pos() == (x1, y1))
```

---

![](http://fondinfo.github.io/images/oop/strawman.png)
# 🧪 Mock Object

- *Unit test*: test *only one object* at a time
- If another object is needed, a **mock** is created
- Mock: methods with predefined responses

``` py
class TurtleTest(TestCase):
    def test_collide_ball(self):
        arena = Mock()  # from unittest.mock
        ball = Mock(spec=Ball)  # to fool isinstance
        arena.size.return_value = (480, 360)
        arena.current_keys.return_value = []
        arena.collisions.return_value = [ball]
        turtle = TurtleHero((230, 170))
        turtle.move(arena)  # hit
        turtle.move(arena)  # no effect
        self.assertEqual(turtle.lives(), 2)
```

>

<https://fondinfo.github.io/play/?c21_bouncetest.py>

---

# 🥷 Checking Exceptions

- Programmer's job
    - Code that correctly completes execution in normal cases...
    - But also shows expected behavior in exceptional situations
- How to verify that an expected exception is actually raised?
    - Use the `assertRaises` method directly, passing a function and parameters
    - Or create a *context* with `with`
- Example: Does `sqrt` actually raise an expected exception?

``` py
def test_sqrt_domain(self):
    with self.assertRaises(ValueError):
        sq = math.sqrt(-1)
```

---

# 🥷 Fixture

- Two or more tests operate on identical or similar sets of objects
    - This common initial configuration is called a *fixture*
- If there are several tests with a common fixture...
    - Add fields for the various parts of the fixture
    - Initialize these fields in the `setUp` method
    - Release any allocated resources in the `tearDown` method
- Once the fixture is created, it can be used by all test cases
    - Add test methods to the class
    - `setUp` and `tearDown` are executed before and after each test

---

# 🥷 Fixture Example

- Numerous test methods operating on the same initial data
    - Example, a configuration of balls in predefined positions

``` py
class SimpleBallTest(unittest.TestCase):

    def setUp(self):
        self.b1 = Ball((80, 40))
        self.b2 = Ball((40, 80))
        self.b3 = Ball((120, 20))
```

---

# 🧪 Running Tests

- Mechanisms for defining tests to execute and organizing results
- Running tests from the command line
    - Inclusion of module tests, class tests, or specific test methods
    - Simple form of *test discovery*, for "`test*.py`" modules

``` sh
python -m unittest test_module1 test_module2
python -m unittest *test.py
python -m unittest test_module.TestClass
python -m unittest test_module.TestClass.test_method
python -m unittest discover
```

- Annotation `@unittest.skip("reason for skipping")`
    - Instructs the framework to ignore a specific test method
    - Message to document the decision

---

# 🥷 Test Suite

- Mechanism to logically *group* tests and *run them together*
- The `TestSuite` class represents a test suite
    - List of test classes added with the `addTest` method
- The `TestRunner` class represents a test runner
    - For the console, `TextTestRunner` is used, already included in the framework

``` py
suite = unittest.TestSuite()
suite.addTest(SimpleBallTest())
runner = unittest.TextTestRunner()
runner.run(suit)
```
