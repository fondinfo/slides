![](http://fondinfo.github.io/images/fun/matryoshka.png)
# Recursion
## Introduction to Programming

---

# 💡️ Recursive Programming

- Many languages allow a function (or procedure) to call itself
- Direct or indirect recursive call

![](http://fondinfo.github.io/images/fun/recursion.svg)

---

`$$\begin{cases}0! = 1 \\ n! = n \cdot (n-1)!, n>0\end{cases}$$` ![](http://fondinfo.github.io/images/fun/stack.svg)
# ⭐ Factorial, recursion

§ py
def factorial(n: int) -> int:
    if n == 0:
        result = 1
    else:
        result = n * factorial(n - 1)
    return result

§

- At each invocation of a function, a new record is created on the **stack**
- **Local context** to the particular activation of the function itself
- Execute with the *Thonny* debugger

>

<https://fondinfo.github.io/play/?c11_factorial.py>

---

# 💡️ Thinking Recursively

- ① Find some *base case*
    - Result obtained without recursion
- ② Find a solution in the *general case*
    - Requires solving a problem of the same type
    - But of reduced size
- Thus, increasingly smaller problems are solved
    - Getting closer and closer to the base case
    - Recursion terminates

---

![](http://fondinfo.github.io/images/misc/tree.svg)
# ⭐ Binary Tree

- A tree is a data structure, in which each node can have "children" nodes
- A *binary* tree has at most two children
- Recursive definition:
    - Base case: empty tree (no nodes)
    - General case: a node (value) + two children (subtrees)

---

# 🧪 Tree (node) class

§ py
class Node:
    def __init__(self, val, left=None, right=None):
        self.value = val
        self.left = left
        self.right = right
§

- Each `Node` can contain any value
- `left` and `right` fields point to other `Node` objects
    - Or to `None` if they are empty

---

# 🧪 Creating a tree

- A small example of a binary tree
- Built explicitly, without using a complex algorithm
- It is a balanced tree
    - On level 0: one node
    - On level 1: two nodes
    - On level 2: four nodes

§ py
# Nodes on the last level (leaves)
n7 = Node(7)
n4 = Node(4)
n2 = Node(2)
n6 = Node(6)

# Nodes on the intermediate level
n3 = Node(3, n2, n4)
n5 = Node(5, n6, n7)

# Root node
root = Node(1, n3, n5)
§

---

# ⭐ Traversing a tree

- How can we access all the nodes of a tree?
- Using a *recursive algorithm*
- It passes from the current node...
    - To its left child, then recursively to its children
    - To its right child, then recursively to its children
- The depth of the recursion is the height of the tree

---

# 🧪 Printing a tree

§ py
class Node:  # …
    def print_tree(self):
        if self.left is not None:
            self.left.print_tree()
        print(self.value, end=" ")
        if self.right is not None:
            self.right.print_tree()

root.print_tree()
§

§ text
2 3 4 1 6 5 7
§

- This traversal method is called *inorder*
    - First left subtree, then root, then right subtree
- The result of the print is the *sorted sequence* of values
    - If it is a Binary Search Tree (BST)
        - Values in left subtree < root < values in right subtree

---

# 🧪 Summing values

- How to sum all values in a tree?
- Sum of `root.value` + sum of `left_subtree` + sum of `right_subtree`

§ py
class Node:  # …
    def sum_values(self) -> int:
        s = self.value
        if self.left is not None:
            s += self.left.sum_values()
        if self.right is not None:
            s += self.right.sum_values()
        return s

print(root.sum_values())  # 28
§

---

# 🧪 Tree height

- Maximum level reachable from the root
- How to calculate it?
    - If the node is a leaf (no children), its height is 1
    - Otherwise, it is 1 + maximum height of children

§ py
class Node:  # …
    def height(self) -> int:
        if self.left is None and self.right is None:
            return 1
        h_left, h_right = 0, 0
        if self.left is not None:
            h_left = self.left.height()
        if self.right is not None:
            h_right = self.right.height()
        return 1 + max(h_left, h_right)

print(root.height())  # 3
§

---

# 🧪 Is the tree balanced?

- A tree is balanced if, for each node, the heights of its subtrees differ by at most 1
    - And its subtrees are themselves balanced
- The `is_balanced` method, if defined on the `Node` class, returns a `bool`

§ py
class Node:  # …
    def is_balanced(self) -> bool:
        if self.left is None and self.right is None:
            return True
        h_left, h_right = 0, 0
        if self.left is not None:
            h_left = self.left.height()
        if self.right is not None:
            h_right = self.right.height()
        return abs(h_left - h_right) <= 1 and \
               (self.left is None or self.left.is_balanced()) and \
               (self.right is None or self.right.is_balanced())
§

---

# 🏊 Exercises

---

# Fibonacci, recursive

- Implement `fibonacci(n)`
    - If `n` is 0 or 1, the result is `n`
    - Otherwise, `fibonacci(n-1) + fibonacci(n-2)`
- Print `fibonacci(8)` (which is 21)

>

[https://en.wikipedia.org/wiki/Fibonacci_number](https://en.wikipedia.org/wiki/Fibonacci_number)

---

# Palindrome

- Implement `is_palindrome(s)`
    - A string is a palindrome if it reads the same forwards and backward
    - E.g., `otto`, `anna`, `radar`, `madam`, `rotor`
- Recursive definition:
    - Base cases: empty string or single-character string
    - General case: first char == last char, AND inner string is palindrome

---

# String reverse

- Implement `reverse(s)`
    - Returns the reversed string
- Recursive definition:
    - Base cases: empty string or single-character string
    - General case: last char + reverse of inner string + first char

---

# Sum of digits

- Implement `sum_digits(n)`
    - Sums all digits of a number
    - E.g., `sum_digits(1234) == 10`
- Recursive definition:
    - Base case: `n < 10`
    - General case: last digit + sum of remaining digits

---

# Binary representation

- Implement `to_binary(n)`
    - Returns the string representation of the number in binary
    - E.g., `to_binary(10) == "1010"`
- Recursive definition:
    - Base case: `n < 2`
    - General case: `to_binary(n // 2)` + `n % 2`

---

# Max in list

- Implement `max_in_list(l)`
    - Returns the maximum value in a list
- Recursive definition:
    - Base case: list with one element
    - General case: maximum of `first` vs `max_in_list(rest)`

---

# `n_th` in list

- Implement `n_th_in_list(l, n)`
    - Returns the `n_th` element (0-indexed) of list `l`
- Recursive definition:
    - Base case: `n == 0`
    - General case: `n_th_in_list(rest, n-1)`

---

# Search in list

- Implement `search_in_list(l, x)`
    - Returns `True` if `x` is in `l`, `False` otherwise
- Recursive definition:
    - Base case: empty list
    - General case: `x == first` or `search_in_list(rest, x)`

---

# Tree properties

- Add to the `Node` class
    - `count_nodes()`: number of nodes in the tree
    - `sum_leaves()`: sum of values in leaf nodes
    - `count_leaves()`: number of leaf nodes

---

# Tree methods

- Add to the `Node` class
    - `level(val)`: returns the level (0-indexed) of the node containing `val`
    - `depth(node)`: returns the depth (0-indexed) of the specified `node`
        - The root has depth 0
        - This should be a function (not a method)

---

![](http://fondinfo.github.io/images/comp/expression.svg)
# Expression evaluation

- Define an abstract base class `Expression`
    - With an abstract method `eval`
- Then define concrete subclasses, derived from `Expression`
    - **`Literal`**, containing a single number (value)
    - **`Sum`**, containing two operands, both expressions
    - **`Product`**, containing two operands, both expressions
- Instantiate (without *parsing*!) objects to represent this expression:
    - `5 * (3 * 2 + 4)`
- Calculate the final value, calling `eval` on the root node

---

![](http://fondinfo.github.io/images/comp/expression.svg)
# Prefix expressions

- Add a `prefix` method to `Expression` (previous ex.)
    - Generates a string in prefix notation (operator followed by operands)
- Result from example expression:
    - `"* 5 + * 3 2 4"`

§ py
prod1 = Product(Literal(3), Literal(2))
sum1 = Sum(prod1, Literal(4))
prod2 = Product(sum1, Literal(5))
print(prod2.eval())
print(prod2.prefix())
§

>

<https://it.wikipedia.org/wiki/Polish_notation>

---

![](http://fondinfo.github.io/images/comp/expression.svg)
# Tree from string

- Analyze a string, provided by the user
    - The string contains an expression in Polish, prefix notation
    - Generate an object tree of type **Expression** in memory
- Show the value of the expression, using `eval`
- Show the infix representation, using `infix`
    - Add an `infix` method to **Expression**

---

# Strings in nested lists

- Create a tree of strings
    - Structure with nested lists

``` py
tree = [["spam"], [["egg", "sausage"], [], "spam"]]
```

- Write a function to find the longest string
    - In a tree, passed as parameter
    - In the case of an empty list, return `""`
