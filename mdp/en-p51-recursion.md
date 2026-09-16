![](http://fondinfo.github.io/images/fun/matryoshka.png)
# Recursion
## Introduction to Programming

---

# 💡️ Recursive Programming

- Many languages allow a function (or procedure) to call itself
- Recursive call, direct or indirect

![](http://fondinfo.github.io/images/fun/recursion.svg)

---

`$$\begin{cases}0! = 1 \\ n! = n · (n-1)!, n>0\end{cases}$$` ![](http://fondinfo.github.io/images/fun/stack.svg)
# ⭐ Factorial, recursion

``` py
def factorial(n: int) -> int:
    if n == 0:
        result = 1
    else:
        result = n * factorial(n - 1)
    return result

```

- At each invocation of a function, a new record is created on the **stack**
- **Local context** specific to that particular activation of the function
- Execute using the *Thonny* debugger

>

<https://fondinfo.github.io/play/?c11_factorial.py>

---

# 💡️ Thinking Recursively

- ① Find some *base case*
    - Result obtained without recursion
- ② Find a solution for the *general case*
    - Requires solving a problem of the same type
    - But of reduced size
- Thus, progressively smaller problems are solved
    - Getting closer and closer to the base case
    - Recursion terminates

---

![](http://fondinfo.github.io/images/fun/books-stack.png)
# 🔬 Application Stack

- Stack: *LIFO (Last In First Out)* dynamic memory
    - Fixed maximum size
- The program automatically stores in it:
    - **Return address** for the function <br> Pushed at the call, popped at exit
    - **Parameters** of the function <br> Pushed at the call, removed at exit
    - **Local variables**, defined in the function <br> Removed outside the scope of visibility

>

In early days (Fortran 66, etc.) only static allocation <br> Fixed and unique space for data local to a function → no recursion

---

# 🔬 Simplified Stack View

![large](http://fondinfo.github.io/images/fun/stack-content.svg)

---

# 🔬 Activation Record

![large](http://fondinfo.github.io/images/fun/records.svg)

---

# 🔬 Variable Scope

- Set of instructions from which a variable is accessible
    - *Lifetime*: existence in memory of the variable (label)
    - Values (objects) in Python are all managed dynamically
- **Global** scope
    - Variables outside any function - *Best avoided!*
    - *Static* allocation in some languages
- **Local** scope to the function
    - Local variables and parameters
    - *Automatic* allocation of space on the *stack* at each function activation (enabling recursion)
- Block scope (e.g., `if`): not in Python!

---

# 🧪 Fibonacci's Rabbits

![large](http://fondinfo.github.io/images/fun/fib-rabbits.png)

---

# 🧪 Fibonacci, recursion

``` py
def fibonacci(n: int) -> int:
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

![](http://fondinfo.github.io/images/fun/fib-calls.svg)

>

<https://fondinfo.github.io/play/?c11_fibonacci.py>

---

# 🧪 Fibonacci, memoization

``` py
def fibonacci(n: int, _cache=[0, 1]) -> int:
    if n < len(_cache):
        return _cache[n]
    result = fibonacci(n - 1) + fibonacci(n - 2)
    _cache.append(result)
    return result
```

``` py
from functools import lru_cache
@lru_cache()  # function decoration
def fibonacci(n: int) -> int:
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```
---

# 🧪 Fibonacci, iteration

``` py
def fibonacci(n: int) -> int:
    val, nxt = 0, 1

    for i in range(n):
        val, nxt = nxt, val + nxt

    return val
```

>

<https://fondinfo.github.io/play/?c11_fibonacci.py>

---

# 🧪 Contiguous Area

- Find a contiguous and homogeneous area in a matrix

``` py
def find_area(board, x, y, val, area=None):
    if area is None:
        area = set()
    h, w = len(board), len(board[0])
    if 0<=x<w and 0<=y<h and board[y][x] == val and (x, y) not in area:
        area.add((x, y))  # area is a set of points
        for dx, dy in ((1, 0), (0, 1), (-1, 0), (0, -1)):
            find_area(board, x + dx, y + dy, val, area)
    return area
```

>

<https://fondinfo.github.io/play/?c11_findarea.py>

---

# 💡️ Recursive Data Type

- A value can *contain* values of the same type
- *Linked list*
    - Empty / `None`, or...
    - Head node, followed by a *linked list*

![](http://fondinfo.github.io/images/fun/linked-list.svg)

``` py
class ListNode:
    def __init__(self, data, next=None):
        self.data = data
        self.next = next  # ListNode | None

    def __str__(self) -> str:
        return f"<{self.data} {self.next}>"
```

---

![](http://fondinfo.github.io/images/comp/binary-tree.svg)
# Binary Tree

- *Tree*
    - Empty / `None`, or...
    - Head node, followed by multiple trees
- *Binary tree*
    - Two children for each node

``` py
class TreeNode:
    def __init__(self, data, left=None, right=None):
        self.data = data
        self.left = left    # TreeNode | None
        self.right = right  # TreeNode | None

    def __str__(self) -> str:
        return f"<{self.data} {self.left} {self.right}>"
```

---

![](http://fondinfo.github.io/images/comp/sorted-tree.svg)
# Sorted Tree

``` py
def insert(tree, val) -> TreeNode:
    if tree == None:
        tree = TreeNode(val)
    elif val < tree.data:
        tree.left = insert(tree.left, val)
    elif val > tree.data:
        tree.right = insert(tree.right, val)
    return tree

def flatten(tree) -> list:
    if tree == None:
        return []
    return flatten(tree.left) + [tree.data] + flatten(tree.right)
```

- Sorted tree like a `set`, *without duplicates*

---

![](http://fondinfo.github.io/images/comp/sorted-tree.svg)
# Binary Search

``` py
def contains(tree, val) -> bool:
    if tree == None:
        return False
    if val == tree.data:
        return True
    subtree = tree.left if val < tree.data else tree.right
    return contains(subtree, val)
```

``` py
t = None
for v in [7, 5, 5, 9, 6, 2, 3, 11]:
    t = insert(t, v)
print(t)
print(flatten(t))
print(contains(t, 4))
print(contains(t, 5))
```

---

![](http://fondinfo.github.io/images/repr/file-system.svg)
# Documents and Folders

- A tree representing a hierarchy of documents
- Tree node
    - A `Document` (*leaf*)
    - Or a `Folder`, with various child nodes

``` py
class Node:
    pass
class Document(Node):
    def __init__(self, name: str, data: str):
        self._name = name
        self._data = data
class Folder(Node):
    def __init__(self, name: str, children: list[Node]):
        self._name = name
        self._children = children
```

---

![](http://fondinfo.github.io/images/comp/list-tree.svg)
# Nested Lists

- Simple cases of trees: nested lists

``` py
type T = int | list[T]

def count_tree(t: T) -> int:
    if not isinstance(t, list):
        return 1
    # return sum(count_tree(v) for v in t)
    count = 0
    for v in t:
        count += count_tree(v)
    return count

tree = [[1, 2, [3, 4], [5]], 6]
print(count_tree(tree))
```

---

# 🏊 Exercises

---

# Recursion, Palindrome

- *Palindrome*: text that remains the same when read backward
- Write a recursive function to recognize palindromes
    - Parameter: text to check
    - Result: `bool`

>

Palindrome string: if it has length 0 or 1, or...
<br>
First letter == last letter and...
<br>
Remaining string (without first and last letter) is a palindrome

---

![](http://fondinfo.github.io/images/fun/sierpinski-triangle.svg)
# Sierpinski Triangle

- Draw on a rectangular area (black): `x`, `y`, `w`, `h`
    - Initially, the entire canvas
- If the area is sufficient, divide it into `4` sub-quadrants
    - Color the top-left quadrant (white)
    - Recursively apply the pattern to the other `3` quadrants
- As an enhancement, allow the user to choose the *level of detail* (recursion depth), to color...
    - Level `0`: nothing
    - Level `1`: only `1` quadrant
    - Level `2`: `1` large quadrant and `3` smaller ones
    - Level `3`: `1+3+9` quadrants, etc.

---

![](http://fondinfo.github.io/images/fun/fractal-tree.png)
# Fractal Tree

- Recursive function to draw a tree
    - Parameters: initial position, trunk length, angle
- If trunk is less than 5 pixels
    - Draw only a segment (green)
- Otherwise:
    - Segment for trunk (brown)
    - At its tip, two branches with the same pattern
    - 1st branch, with rotation of -30°
    - 2nd branch, with rotation of +30°
    - Branch length reduced to 4/5 of the parameter

---

![](http://fondinfo.github.io/images/hist/euclid.jpg)
# Greatest Common Divisor

- Read two numbers
- Compute their Greatest Common Divisor inside a function
- Display the result of the function

>

Try using both iteration and recursion
<br>
Euclid: GCD(a, b) = a, if b = 0;
<br>
GCD(a, b) = GCD(b, a mod b), if b > 0

---

![](http://fondinfo.github.io/images/misc/cubic-function.png)
# Bisection, Recursion

- Find the zero of the following mathematical function
    - $f(x) = x^3 - x - 1$, for $1 \leq x \leq 2$
    - Find *x* such that *$|f(x)| < 0.001$*
- Define a recursive bisection function
    - Required parameters: *start of search interval*, *end of search interval*
    - At each level, call the function on a halved interval

>

<https://en.wikipedia.org/wiki/Bisection_method>

---

![](http://fondinfo.github.io/images/fun/bike-lock.png)
# Password Generation

- Generate all passwords of a given length (*arrangements with repetition*)
    - Parameter: length `n` of the passwords
    - Parameter: `str` containing possible symbols
    - Result: a list of strings
- Algorithm:
    - Length `0`: the only password is the empty string: `['']`
    - Otherwise: for each symbol chosen as the first character...
    - Concatenate it with all passwords of length `n - 1` (recursion)

>

Only recursive solutions will be accepted

---

![](http://fondinfo.github.io/images/fun/elvis-lives.svg)
# Anagrams

- Generate all anagrams (permutations) of a string
- Result: a list of strings
- Algorithm:
    - Empty string: only itself
    - Otherwise: for each character...
    - Concatenate it with all permutations of the remaining characters (*recursion*)

---

![](http://fondinfo.github.io/images/fun/hanoi-tower.png) ![](http://fondinfo.github.io/images/fun/hanoi.svg)
# Tower of Hanoi

- Three pegs + N disks of decreasing diameter
- Move all disks from the first to the last peg
- Only one disk can be moved at a time
- A disk cannot be placed on top of a smaller disk
- Use recursion

>

Moving a single disk is immediate.
<br><br>
N disks: move N-1 disks to the peg that is neither source nor dest.,
<br>
move the last disk to the target peg,
<br>
move the remaining N-1 disks again.

---

# Polish Notation

- Read a line of text into a string
- Write a function that evaluates the string as an expression, in the form:
    - `"+ 2 7"` (=9)
- Operands can themselves be expressions:
    - `"+ * 3 4 15"` (=27)
- Write a second function that transforms the expression into standard infix notation:
    - `"((3 * 4) + 15)"`
- Use recursion

>

Assume all "tokens" are separated by spaces and that all operators have fixed arity

---

![](http://fondinfo.github.io/images/repr/file-system.svg)
# Documents and Folders

- A hierarchical document management system consists of two types of *nodes* (base class)
    - *Documents*, characterized by a name and textual content (derived class)
    - *Folders*, characterized by a name and a list of contained nodes (derived class)
- Create a hierarchy for the three classes: `Node`, `Document`, `Folder`
- In the main program body, instantiate and structure various nodes (without user input)
    - Recreate with objects the structure shown alongside

---

![](http://fondinfo.github.io/images/repr/file-system.svg)
# Folder Size

- `size` method for all nodes (previous exercise)
    - Abstract in base class
    - For a document, length of content
    - For a folder, sum of sizes of contained nodes
- Calculate size for the previous exercise
    - Make up content for the documents present
- Additionally, `print(indent: int)` method for nodes
    - To display the tree structure in the terminal
    - Abstract method in base class
    - Displays the name of documents and folders
    - Indents nodes appropriately relative to their containing folder

---

![](http://fondinfo.github.io/images/comp/expression.svg)
# Expressions

- Define a class hierarchy to represent mathematical expressions
- *Base class* **`Expression`** with abstract method `eval`
    - Takes no parameters, returns the `float` value of the expression
- Concrete *subclasses* of an expression are:
    - **`Literal`**, containing a constant `float` value
    - **`Sum`**, containing two operands, both expressions
    - **`Product`**, containing two operands, both expressions
- Instantiate objects (without parsing!) to represent this expression:
    - `5 * (3 * 2 + 4)`
- Calculate final value by calling `eval` on the root node

---

![](http://fondinfo.github.io/images/comp/expression.svg)
# Prefix Expressions

- Add a `prefix` method to `Expression` (previous exercise)
    - Generates a string in prefix notation (operator followed by operands)
- Result from example expression:
    - `"* 5 + * 3 2 4"`

``` py
prod1 = Product(Literal(3), Literal(2))
sum1 = Sum(prod1, Literal(4))
prod2 = Product(sum1, Literal(5))
print(prod2.eval())
print(prod2.prefix())
```

>

<https://en.wikipedia.org/wiki/Polish_notation>

---

![](http://fondinfo.github.io/images/comp/expression.svg)
# Tree from String

- Parse a string provided by the user
    - The string contains an expression in Polish prefix notation
    - Construct an object tree in memory of type **Expression**
- Show expression value using `eval`
- Show infix representation using `infix`
    - Add an `infix` method to **Expression**

---

# Strings in Nested Lists

- Create a tree of strings
    - Nested list structure

``` py
tree = [["spam"], [["egg", "sausage"], [], "spam"]]
```

- Write a function that finds the longest string
    - In tree, passed as parameter
    - In case of empty list, return `""`
