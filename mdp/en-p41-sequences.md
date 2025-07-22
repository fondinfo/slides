![](http://fondinfo.github.io/images/oop/lego-blocks.png)
# Sequences
## Introduction to Programming

---

# Lists and Indices

---

![](http://fondinfo.github.io/images/fun/shopping-list.png)
# ⭐ List

- Mutable sequence of homogeneous elements

``` py
groceries = ["spam", "egg", "beans"]
rainfall_data = [13, 24, 18, 15]
```

  - Sometimes a list of already known size is needed
  - Values will be calculated during execution

<!-- end list -->

```py
results_by_month = [0] * 12  # 12 times 0 (list repetition)
```

-----

# ⭐ Loops over lists: for

```py
values = [2, 3, 5, 7, 11]

print("Cubes:")

for val in values:
    cube = val ** 3
    print(cube, end="\t")
```

```text
8   27  125 343 1331
```

  - In each iteration, `val` is assigned an element from `values`
  - `for` loop for any type of sequence
      - `list`, `str`, `tuple`, `range`…

-----

# ⭐ Accessing Elements

  - **Be careful to use valid indices\!**
      - Current *length* of a list `s`: `len(s)`
      - Elements *numbered* from `0` to `len(s)-1`

<!-- end list -->

```py
groceries = ["spam", "egg", "beans", "bacon"]
n = len(groceries)           # 4
groceries[0]                 # "spam"
groceries[1]                 # "egg"
groceries[n-1]               # "bacon"
groceries[1] = "ketchup"     # replace a value, len is still 4
groceries.append("sausage")  # add to the end, len is 5
groceries                    # guess!
```

-----

# 🧪 Elements and slices

  - *Negative* indices count from the end
      - From `-1` (last) to `-len(s)` (first)

<!-- end list -->

```py
months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun",
          "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]
n = len(months)            # 12
months[3]                  # "Apr"
months[-2]                 # "Nov", same as n - 2
```

```py
spring = months[2:5]       # ["Mar", "Apr", "May"]
quart1 = months[:3]        # ["Jan", "Feb", "Mar"]
quart4 = months[-3:]       # ["Oct", "Nov", "Dec"]
whole_year = months[:]     # Copy of the whole list
```

-----

# 🧪 Insertion and removal

```py
groceries = ["spam", "egg", "beans"]

groceries[0] = "sausage"      # replace an element

groceries.append("bacon")     # add an element to the end
groceries.pop()               # remove (and return) last element

groceries.insert(1, "bacon")  # other elements shift
removed = groceries.pop(1)    # remove (and return) element at index

i = groceries.index("egg")    # 1, index of "egg" in groceries
if "egg" in groceries:        # True, groceries contains "egg"
    groceries.remove("egg")   # remove an element by value

groceries.clear()             # remove everything, groceries is empty now
```

-----

# 🔬 Equality and identity

```py
a = ["spam", "egg", "beans"]
b = a[:]         # new list!
b == a           # True, they contain the same values
b is a           # ❗ False, they are two objects in memory
                 # (try and modify one of them...)
c = a
c is a           # ❗ True, same object in memory
                 # (try and modify one of them...)
d = ["sausage", "tomato"]
groceries = c + d  # list concatenation --> new list!

# Lexicographical comparison of lists (or strings, tuples...)
# Compare the first two *different* elements
[2, 0, 0] > [1, 2, 0]  # True: 2 > 1
[2, 1, 0] > [2, 0, 1]  # True: 2 == 2, 1 > 0
```

-----

# 🧪 Functions on lists

  - Parameters passed *by assignment* (\~ labels)
      - ⇒ Modifications to objects: permanent

<!-- end list -->

```py
def append_fib(data: list[int]):
    val = len(data)
    if val >= 2:
        val = data[-2] + data[-1]
    data.append(val)

def main():
    values = []
    for _ in range(12):
        append_fib(values)
        print(values)  # let's see what's going on
```

>

[https://fondinfo.github.io/play/?c08\_fibonacci.py](https://fondinfo.github.io/play/?c08_fibonacci.py)

-----

# 🧪 Variables and values

  - ❓ What is the output of the following program?
  - ❓ And if we assign an empty list to `data` instead?
      - Instead of calling its `clear` method

<!-- end list -->

```py
def reset(data: list):
    data.clear()
    #data = []

def main():
    nums = [1, 2, 3]
    reset(nums)
    print(nums)

main()
```

>

[https://fondinfo.github.io/play/?c08\_reset.py](https://fondinfo.github.io/play/?c08_reset.py)

-----

# 🧪 Strings and lists

  - **String**: *immutable* sequence of characters
  - **`join`** and **`split`**: from list to string and vice versa

<!-- end list -->

```py
txt = "Monty Python's Flying Circus"
txt[3]    # "t"
txt[-2]   # "u"
txt[6:12] # "Python"
txt[-6:]  # "Circus"

days = ["tue", "thu", "sat"]
txt = "|".join(days)  # "tue|thu|sat"

days = "mon|wed|fri".split("|")  # ["mon", "wed", "fri"]
```

  - Without parameters, `split` separates based on sequences of whitespace characters
      - `" ", "\n", "\t"`…

-----

# 🧪 Loops over strings

  - The `for` loop iterates over the values of any sequence
  - A string is a sequence of characters

<!-- end list -->

```py
line = input("Text? ").lower()
digits, vowels = 0, 0

for c in line:
    if "0" <= c <= "9":  # char comparison
        digits += 1
    elif c in "aeiou":  # membership test
        vowels += 1
```

>

[https://fondinfo.github.io/play/?c03\_vowels.py](https://fondinfo.github.io/play/?c03_vowels.py)

-----

# 🧪 Text between markers

  - From a text, transcribe only parts enclosed between `<` and `>`
      - If `>` is missing after `<`, transcribe until the end

<!-- end list -->

```py
text = input("Text? ")
inside = False

for c in text:
    if c == "<" and not inside:
        inside = True
    elif c == ">" and inside:
        inside = False
        print()
    elif inside:
        print(c, end="")
```

>

[https://fonsinfo.github.io/pyodide/?c08\_brackets.py](https://fonsinfo.github.io/pyodide/?c08_brackets.py)

-----

# 🧪 List of counters

  - Count digits separately in a text
      - How many `0`s? How many `1`s? …
      - `10` conditions, `10` counter variables
      - Or a list of `10` elements

<!-- end list -->

```py
text = input("Text? ")
counters = [0] * 10

for c in text:
    if "0" <= c <= "9":
        counters[int(c)] += 1

print(counters)
```

>

[https://fondinfo.github.io/play/?c08\_counters.py](https://fondinfo.github.io/play/?c08_counters.py)

-----

# 🧪 Tuple

  - **Immutable** sequence of values, even of *different types*

<!-- end list -->

```py
# Tuple packing
pt = (5, 6, "red")
pt[0]  # 5
pt[1]  # 6
pt[2]  # "red"

# Sequence unpacking (from a list, string, tuple...)
x, y, colour = pt
a, b = 3, 4
a, b = b, a
```

-----

# ⭐ Set

  - Unordered collection and *without repetitions*
      - Without keys or indices
  - Methods `add` and `discard`
      - Addition and removal
  - Operators `in`, `|` and `&`
      - Membership, union and intersection

<!-- end list -->

```py
numbers = {1, 4, 5}
numbers.add(4)  # {1, 4, 5}
few = numbers & {4, 5, 6}  # {4, 5}, intersection
many = numbers | {3, 4}  # {1, 3, 4, 5}, union

empty_set = set()  # ⚠️ {} is an empty dict
```

>

[https://docs.python.org/3/library/stdtypes.html\#set](https://docs.python.org/3/library/stdtypes.html#set)

-----

# ⭐ Dictionary

  - Also called *map* or *associative array*
  - Collection of **key**-**value** pairs
  - Key: *index* to access the value
      - Keys are *unique* (\~ `list`)
      - Type *`str`*, or other immutable type

<!-- end list -->

```py
tel = {"john": 4098, "terry": 4139}  # dict[str, int]
if "john" in tel:
    print(tel["john"])  # 4098, ⚠️ error for a missing key
tel["graham"] = 4127
for k, v in tel.items():
    print(k, v)  # john 4098 ⏎ terry 4139 ⏎ graham 4127 ⏎
```

>

See: [get](https://docs.python.org/3/library/stdtypes.html#dict.get),
[keys](https://docs.python.org/3/library/stdtypes.html#dict.keys),
[values](https://docs.python.org/3/library/stdtypes.html#dict.values),
[items](https://docs.python.org/3/library/stdtypes.html#dict.items) \<br\>
[https://docs.python.org/3/library/stdtypes.html\#dict](https://docs.python.org/3/library/stdtypes.html#dict)

-----

`$\begin{pmatrix}5 & 0 & 0 & 0 \\ 0 & 8 & 0 & 0 \\ 0 & 0 & 3 & 0 \\ 0 & 6 & 0 & 0\end{pmatrix}$`

# 🧪 Sparse matrix

  - Matrix with many "empty" cells
  - Or sparse, non-numeric keys
  - Dictionary with *tuple* type keys
  - `dict.get` method with *default* value

<!-- end list -->

```py
values = {(0, 0): 5, (1, 1): 8,
          (2, 2): 3, (1, 3): 6}  # dict[(int, int), int]

x = int(input("Col? "))
y = int(input("Row? "))
val = values.get((x, y), 0)  # key not found → default 0
print(val)
```

>

[https://docs.python.org/3/library/stdtypes.html\#dict](https://docs.python.org/3/library/stdtypes.html#dict)

-----

# 🥷 Functions on sequences

-----

# 🥷 List comprehension

  - Concise way to create a list, by re-processing a given sequence
      - *Output* expression
      - *Iteration* variable
      - *Input* sequence
  - Optional condition on elements

<!-- end list -->

```py
squares = [x ** 2 for x in range(5)]  # [0, 1, 4, 9, 16]
# squares = []
# for x in range(5):
#    squares.append(x ** 2)
```

```py
nums = [int(c) for c in "h3ll0 w0rld" if "0" <= c <= "9"]
# [3, 0, 0]
```

-----

# 🥷 Zip

  - Pairs elements of two (or +) sequences
  - Generates a *lazy* sequence of pairs (tuples)
  - Length of the shortest sequence
  - **Laziness**: results calculated not immediately
      - Only when needed

<!-- end list -->

```py
groceries = ["spam", "egg", "beans"]
quantities = ["100 g", "6 pc", "200 g", "too much"]

for p, q in zip(groceries, quantities):  # unpacking
    print(p, q, end=" § ")
# spam 100 g § egg 6 pc § beans 200 g §

z = list(zip(groceries, quantities))  # if you *really* need a list
# [("spam", "100 g"), ("egg", "6 pc"), ("beans", "200 g")]
```

-----

# 🥷 Enumerate

  - Pairs an incrementing index with the values of a sequence
  - Generates a *lazy* sequence of pairs
  - Iterations with value and index together

<!-- end list -->

```py
groceries = ["spam", "egg", "bacon", "sausage"]

for i, val in enumerate(groceries):  # ~ zip(range(4), groceries)
    print(i, val, end=" § ")
# 0 spam § 1 egg § 2 bacon § 3 sausage §

e = list(enumerate(groceries))  # if you *really* need a list
[(0, "spam"), (1, "egg"), (2, "bacon"), (3, "sausage")]
```

-----

# 🥷 Sorted or reversed lists

  - Functions `sorted` and `reversed` do not alter the list
  - Methods `sort` and `reverse` alter the list (*in place*)
  - `key` parameter: comparison between results of a *function*

<!-- end list -->

```py
groceries = ["spam", "bacon", "egg"]
s1 = sorted(groceries)           # ["bacon", "egg", "spam"]
s2 = sorted(groceries, key=len)  # ["egg", "spam", "bacon"]
rev = list(reversed(groceries))  # ["egg", "bacon", "spam"]
print(groceries)                 # ["spam", "bacon", "egg"]
```

```py
groceries.sort()     # in-place
groceries.reverse()  # in-place
print(groceries)     # ["spam", "egg", "bacon"]
```

-----

# 🥷 Sorting keys

```py
vals = sorted([2, 4, -1, -5], key=abs)  # [-1, 2, 4, -5]
```

  - `itemgetter` function in `operator` module
      - Parameters: one or more integer indices
      - Result: function that extracts corresponding values
      - Useful for sorting lists of tuples, lists of lists etc.

<!-- end list -->

```py
from operator import itemgetter
records = [("Joe", 150), ("Rob", 310), ("Alb", 600), ("Din", 250)]
r1  = sorted(records, key=itemgetter(0))
# [("Alb", 600), ("Din", 250), ("Joe", 150), ("Rob", 310)]
r2 = sorted(records, key=itemgetter(1), reverse=True)
# [("Alb", 600), ("Rob", 310), ("Din", 250), ("Joe", 150)]
```

-----

# 🥷 Map

  - Parameters: function `f`, sequence `l`
      - *(Higher-order function)*
  - `f` applied to each value in `l`
  - Result: *lazy* sequence of results

<!-- end list -->

```py
vals = [-2, -1, 0, 1, 2]  # or, range(-2, 3)
for v in map(abs, vals):
    print(v, end="\t")
# 2    1    0    1    2
```

```py
vals = [1, 2]
vals += map(int, "3,4,5".split(","))  # [1, 2, 3, 4, 5]
```

>

Multiple sequences, if needed as parameters for `f`

-----

# 🥷 Filter

  - Parameters: *predicate* `p` (boolean function), sequence `l`
  - Result: *lazy* sequence with only values that satisfy `p`

<!-- end list -->

```py
def odd(x): return x % 2 == 1
def pos(x): return x > 0

vals = [4, 5, -6, 0, -7, 8]
for v in filter(odd, vals):
    print(v, end="\t")  # 5  -7
for v in filter(pos, vals):
    print(v, end="\t")  # 4  5  8
```

-----

# 🥷 Statements and expressions

  - **Expression**: code whose evaluation produces a value
      - Suitable for the right-hand side of an assignment (*rvalue*)
  - Many Python **statements** do not correspond to a value
      - `if`, `while`, `for`, `def`, `class` are *not* expressions
      - Assignments `=`, `+=` etc. are *not* expressions
  - There is a special `if`, as an expression

<!-- end list -->

```py
val = "boom" if 5 % 2 == 0 else "bang"
```

  - From v3.8: special *assignment* `:=`, as an expression

<!-- end list -->

```py
while (v := float(input("val? "))) >= 0:  # sentinel
    print(v ** .5)
```

-----

# 🥷 Truth value

  - Every object can be converted to `bool`
  - *Falsy* constants and numbers
      - `None`, `False`, `0`, `0.0` etc.
  - *Falsy* sequences
      - `""`, `()`, `[]`, `{}`, `set()`, `range(0)`
  - Other objects, normally *truthy*
      - Decided by `__bool__` method, or `__len__`

<!-- end list -->

```py
while v := input("val? "):  # sentinel, "" is falsy
    print(float(v) ** 2)
```

>

[https://docs.python.org/3/library/stdtypes.html\#truth](https://docs.python.org/3/library/stdtypes.html#truth)

-----

# 🥷 Aggregation functions

  - From sequence to single result
  - Logical operations
      - **`all`** : logical *AND* on all *truthiness* values
      - **`any`** : logical *OR* on all *truthiness* values
  - Numeric operations
      - **`sum`, `max`, `min`, `len`**
      - **count** method on sequence: number of occurrences of a value

<!-- end list -->

```py
>>> all((2, 1, 0, -1, ""))  # 0 and "" are falsy
False
>>> any([2, 1, 0, -1, ""])  # 2, 1 and -1 are truthy
True
>>> "abracadabra".count("a")
5
```

-----

# 🥷 Random values from sequences

  - **`choice`** : random extraction from sequence, uniform probability

<!-- end list -->

```py
>>> from random import choice, sample, shuffle
>>> choice("aeiou")
"e"
```

  - **`shuffle`** : random shuffling of a list (*in place*)

<!-- end list -->

```py
>>> vals = [2, 3, 5, 7, 11, 13]
>>> shuffle(vals)
>>> vals
[2, 11, 7, 3, 5, 13]
```

  - **`sample`** : *n* extractions, from non-repeated random positions

<!-- end list -->

```py
>>> sample("aeiou", 3)  # a sequence and an int
["e", "o", "i"]  # result is a list
```

-----

# 🏊 Exercises

-----

# Histogram with horizontal bars

  - Ask the user for a list of positive values
      - Until `0` is entered (sentinel)
  - Show a histogram
      - Horizontal length of each bar proportional to the corresponding value
      - The longest bar occupies all available horizontal space

-----

# Random results

  - Simulate `n` rolls of a pair of dice
      - `n` chosen by the user
  - Count how many times each result occurs
      - Possible results: from 2 to 12
      - Sum of the two dice

>

To count the various results, use a list of (at least) 11 values

-----

# Fill

  - Define `fill` function with two parameters
      - List of integers
      - Integer index $i$, a position in the list
  - Fills with 1s cells that initially contain 0, around the given index
      - Element with index $i$ ≠ 0: stops immediately
      - Element with index $i$ = 0: set to 1, fills right and left
      - Upon reaching element ≠ 0: filling stops
  - Ex.: caret indicates position $i$ in the list: start of filling

<!-- end list -->

```text
   0022000000002000
            ^
-> 0022111111112000
```

-----



# Merge

  - Define a `merge` function
  - Two `list` type parameters
      - Both lists are already sorted (❗)
      - Both lists will eventually be empty
  - Result `list`
      - Result contains all values from both lists
      - Result values are all in order
  - Do not use `sort`, `sorted`; do not sort the list
      - Just compare the values at the head of the two lists
      - The smallest absolute value is among those two
      - Remove the chosen value from its list

-----

# List Clamp

  - Define the `clamp` function with three parameters
      - A list of numbers
      - A minimum limit $a$
      - A maximum limit $b$
  - Modifies numbers in the list
      - If less than $a$, replaces them with $a$
      - If greater than $b$, replaces them with $b$

<!-- end list -->

```py
data = [3, 4, 6, 7, 3, 5, 6, 12, 4]
clamp(data, 5, 10)
# data = [5, 5, 6, 7, 5, 5, 6, 10, 5]
```

-----

# Shuffle

  - Define a `shuffle` function
      - Parameter: a list of values
      - Shuffles the list elements *in-place*
  - For each index $i$ in the list
      - Generates a random, valid index $j$
      - Swaps elements at $i$ and $j$

>

Naturally, *without* using the `random.shuffle` function

-----

# Occurrences

  - Given a string containing a sequence of words
      - Separated by a space
  - Count the occurrences of each word in the sequence

>

Use a dictionary

-----

# Common words

  - Given two strings `s1` and `s2` containing sequences of words
      - Separated by a space
  - Find the set of words belonging to both strings

<!-- end list -->

```
```
