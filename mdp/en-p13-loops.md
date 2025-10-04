![](http://fondinfo.github.io/images/draw/red-squares.svg)
# Loops
## Introduction to Programming

---

# Loops and Strings

---

# 🧪 String Comparison

- String comparison, in *lexicographical* order
    - `<, <=, >, >=, ==, !=`
    - Comparison decided by the first differing character
- First 128 *Unicode* codes == *ASCII*
    - Digits first, then uppercase, then lowercase
- Operator **`in`**: membership test (substring)

``` py
>>> "art" < "arc"
False
>>> "arT" < "arc"
True
>>> "Py" in "Monthy Python"
True
>>> chr(83)
"S"
>>> ord("S")
83
```

---

# ASCII Table

![large](http://fondinfo.github.io/images/repr/ascii-large.svg)

---

![](http://fondinfo.github.io/images/misc/characters.png)
# Loops on Strings

- The `for` loop iterates over the values of any *sequence*
- A string is a *sequence* of characters
- Each character is still of type `str`, length 1

``` py
for c in "Python":
    print(ord(c))
```

``` py
line = input("Text? ").lower()
digits, vowels = 0, 0
for c in line:
    if "0" <= c <= "9":  # char comparison
        digits += 1
    elif c in "aeiou":  # membership test
        vowels += 1
```

>

<https://fondinfo.github.io/play/?c03_vowels.py>

---

![](http://fondinfo.github.io/images/algo/words.svg)
# 🧪 Order between two strings

- The user provides two strings → 3 alternatives
    - They are in order
    - They are inverted
    - They are equal

``` py
a = input("First word? ")
b = input("Second word? ")

if a < b:
    print("The words are ordered")
elif a > b:
    print("The words are inverted")
else:
    print("The words are equal")
```

---

![](http://fondinfo.github.io/images/algo/words.svg)
# 🧪 Without elif

- If the first string does not precede the second...
    - There is another condition, nested `if`
    - More complicated, less readable code
    - Many conditions → increasing nesting

``` py
a = input("First word? ")
b = input("Second word? ")

if a < b:
    print("The words are ordered")
else:
    if a > b:
        print("The words are inverted")
    else:
        print("The words are equal")
```

---

![](http://fondinfo.github.io/images/algo/calc.svg)
# 🧪 Arithmetic Operations

``` py
a = float(input())
b = float(input())
op = input()

if op == "+":
    print(a + b)
elif op == "-":
    print(a - b)
elif op == "*":
    print(a * b)
elif op == "/" and b != 0:
    print(a / b)
else:
    print("Operation not allowed")
```

---

# Print Control

- Special characters in strings
    - `\n` : newline (code 10 dec)
    - `\t` : horizontal tab (code 9 dec)

``` py
>>> print("one\ttwo\tthree\nfour\tfive\tsix")
one     two     three
four    five    six
```

- Optional parameters for `print`
    - `end` : ending sequence, default `\n`
    - `sep` : separator between parameters, default *space*

``` py
>>> for i in range(3):
        print(1, 2, 3, sep=".", end=";")
1.2.3;1.2.3;1.2.3;
```

---

# Formatted Strings

- String concatenation : op. `+`
    - Complex to compose strings with many data
- Alternative : *formatted strings*, or *f-strings*
    - `f` before quotes
    - Expressions in string, inside curly braces
    - Replaced by their textual representation

``` py
radius = 2.5
area = math.pi * radius**2
# msg = ("The circle with radius " + str(radius) +
#        " has area " + str(area) + ".")
msg = f"The circle with radius {radius} has area {area}."
print(msg)
```

---

# Loops and Linearity

---

![](http://fondinfo.github.io/images/algo/linearity.svg)
# 💡 Linearity

- In a `for i in range(n)…` loop
- Linear relationship between a quantity $v$ and $i$

$$v = m \cdot i + q$$

- If you know the first and last values: $v_{first}, v_{last}$
    - `$\begin{cases}v_{first} = m \cdot 0 + q, (i = 0) \\ v_{last} = m \cdot (n-1) + q, (i = n-1)\end{cases}$`
    - `$\implies \begin{cases}q = v_{first} \\ m = \frac{v_{last} - v_{first}}{n-1}\end{cases}$`
- Since $i$ is an integer, $m$ is the difference between two instances
    - E.g., if $v$ is the position of squares drawn in sequence
    - ⇒ $m$ is the distance between two successive squares

>

<https://fondinfo.github.io/play/?c03_linearity.py>

---

![](http://fondinfo.github.io/images/draw/n-squares.svg)
# 🧪 Sequence of n Squares

- Draw a sequence of $n$ squares
    - $L$: known canvas side, $l$: known square side
    - ⇒ Positions of first and last square: $v_{first} = 0, v_{last} = L - l$

``` py
pos_fst, pos_lst = 0, L - l
pos_m = (pos_lst - pos_fst) / max(n - 1, 1)  # ⚠️ div by 0
for i in range(n):
    pos = pos_m * i + pos_fst
    g2d.draw_rect((pos, pos), (l, l))
```

- ❓ Color from black to red
- ❓ 10-pixel margin around the drawing

>

<https://fondinfo.github.io/play/?c03_squares.py>

---

![](http://fondinfo.github.io/images/fun/times-table.svg)
# Loops and Nesting

- Print the multiplication table
- First step: print a single row

``` py
y = int(input("Insert a value: "))
for x in range(1, 11):
    print(x * y, end="\t")  # keep printing on the same line
print()  # print just a `newline`
```

- Then, repeat everything for the 10 rows

``` py
for y in range(1, 11):
    for x in range(1, 11):
        print(x * y, end="\t")
    print()
```

>

<https://fondinfo.github.io/play/?c03_tables.py>

---

![](http://fondinfo.github.io/images/draw/color-grid.svg) ![](http://fondinfo.github.io/images/repr/raster-tile.svg)
# Color Grid

- Show a `rows×cols` grid of rectangles
    - Horizontally, blue increases from 0 to 255
    - Vertically, green increases from 0 to 255
- Two nested loops, like times tables
    - Values linear with respect to `x` or `y`

``` py
w, h = CANVAS_W / max(cols, 1), CANVAS_H / max(rows, 1)
g, b = 255 / max(rows - 1, 1), 255 / max(cols - 1, 1)
for y in range(rows):
    for x in range(cols):
        g2d.set_color((0, g * y, b * x))
        g2d.draw_rect((w * x, h * y), (w, h))
```

>

<https://fondinfo.github.io/play/?c03_grid.py>

---

# Loops with Sentinel

---

![](http://fondinfo.github.io/images/misc/rock-cubes.png)
# Sentinel

- Acquire input values, in a loop
    - Each value is processed
- Until values different from the *sentinel* value
    - The *sentinel* value should not be processed
    - Here it is `-1`, but it's important that it's distinct from data

``` py
v = int(input("Value (-1 to end)? "))
while v != -1:
    print(v ** 3)  # <-- in general, process v here
    v = int(input("Value (-1 to end)? "))
```

- Input code present twice
    - Before starting the loop
    - After processing the current value

---

# For and While Loops

- Use `for` for all sequences and iterables
    - `range, tuple, str, list`… Simpler and clearer!
- Use `while` with a sentinel or in more specific cases
- E.g., counting from `0` to `n-1`
    - `while`: counter initialized and incremented manually

``` py
n = int(input("n? "))
for count in range(n):
    print(count)
```

``` py
n = int(input("n? "))
count = 0
while count < n:
    print(count)
    count += 1
```

---

# Sentinel with Counting

``` py
count = 0
v = int(input("Value (-1 to end)? "))
while v != -1:
    count += 1
    print(v ** 3)  # <-- process here v as needed
    v = int(input("Value (-1 to end)? "))
print("Number of processed values:", count)
```

---

![](http://fondinfo.github.io/images/algo/sentinel.svg)
# Partial Sum

- Sum all input values, up to sentinel
- Variable for partial sum
    - New value acquired → added to total
- Like when we update the cost of a *shopping cart*

``` py
total = 0
v = int(input("Value (-1 to end)? "))
while v != -1:  # -1 is the sentinel
    total += v
    v = int(input("Value (-1 to end)? "))
print("Sum of all values:", total)
```

- ❓ Count values and calculate the average

>

<https://fondinfo.github.io/play/?c03_sentinel.py>

---

![](http://fondinfo.github.io/images/algo/sum1n.svg)
# 🧪 Gauss Sum

- Sum all natural numbers from $1$ to $n$, given
- *Partial sum*, but `for` over `range` is better
- Verify result with Gauss's formula

`$$\sum_{k=1}^n k = \frac{n(n+1)}{2}$$`

``` py
n = int(input("n? "))
total = 0
for i in range(1, n + 1):
    total += i
```

>

<https://it.wikipedia.org/wiki/Carl_Friedrich_Gauss#Biografia>
<br>
<https://fondinfo.github.io/play/?c03_gauss.py>

---

# Finding the Maximum

- Find the maximum in a sequence of values
- Variable for temporary maximum
    - Initial value: `-math.inf` (`$-\infty$`)
    - Updated every time a better value is found

``` py
from math import inf
largest = -inf  # -∞
for v in [3, 7, 5, 6]:
    if v > largest:
        largest = v
print(largest)
```

💡 The `max` and `min` functions accept a sequence as a parameter
<br><br>
❓ How to adapt to the loop with sentinel?

---

# Acquisition into List

- Acquire values of unknown number
- *Sentinel* to terminate: e.g., empty line

``` py
values = []  # list of floats
val = input("Val? (empty line to finish) ")

while val != "":
    values.append(float(val))  # float values
    val = input("Val? (empty line to finish) ")
```

- Avoid storing all data when possible
    - Efficiency, scalability to *Big Data*
    - Example: calculating the average, without a list

---

# 🏊 Exercises

---

# Sum of Powers of 2

- Ask the user for a number $n$
- Sum the first $n$ powers of 2
    - $2^0 + 2^1 + ... + 2^{n-1}$
- Keep track of a *partial sum*
- Verify result with this formula (also by Gauss)

`$$\sum_{k=0}^{n-1} 2^k = 2^n - 1$$`

>

Prefer `for` or `while`?

---

![](http://fondinfo.github.io/images/draw/blue-row.svg)
# Circles in a Row

- Ask the user for a number $n$
- In an $L\times L$ canvas, with $L=500$ predefined
- Draw a horizontal row of $n$ circles
    - All of equal size
    - Cover the entire canvas width
- Color gradually changes from black to saturated blue
    - From left to right

---

![](http://fondinfo.github.io/images/draw/red-circles.svg)
# Concentric Circles

- Ask the user for a number $n$
- In an $L\times L$ canvas, with $L=500$ predefined
- Draw $n$ circles at the center of the canvas
    - Decreasing diameter, from $L$ down to $\frac{L}{n}$
    - Color from red (outer circle) to black

---

![](http://fondinfo.github.io/images/draw/red-squares.svg)
# Diagonal Squares

- Ask the user for a number `n`
- On a 500×500 canvas, draw $n$ squares
    - All of equal size
    - Arranged along the diagonal, always sharing a vertex
    - Each with a random color
- Optionally, determine the side to occupy the entire diagonal

>

Review similar example: analysis still valid but need to calculate $l$
<br>
In $L$, there must be exactly $n+1$ half-sides ($l/2$)

---

# Distance from Corners

- Ask the user for two numbers $w$ and $h$ (number of columns and rows)
- Show two tables, for each cell $(x, y)$ calculate Manhattan distance
    1. Relative to the top-left corner $(x_0, y_0) = (0, 0)$
    2. Relative to the bottom-left corner: $(x_0, y_0) = (0, h - 1)$

``` txt
0 1 2 3
1 2 3 4
2 3 4 5
3 4 5 6

3 4 5 6
2 3 4 5
1 2 3 4
0 1 2 3
```

>

Manhattan distance: how many cells to move horizontally and vertically, $|\Delta x| + |\Delta y|$

---

![](http://fondinfo.github.io/images/misc/resistors.png)
`$R_s = \Sigma R_i$` <br>
`$\frac{1}{R_p} = \Sigma \frac{1}{R_i}$`

# Resistors with Sentinel

- Read, through a loop, a sequence of electrical resistance values
- The sequence ends when the user enters the value 0
- Finally, display the equivalent resistance, both for resistors arranged in series and in parallel

---

![](http://fondinfo.github.io/images/misc/bingo-balls.png)
# Secret Number

- Generate a random "secret" number between 1 and 90 at the beginning of the program
- Repeatedly ask the user to enter a number until they guess the generated one
- For each attempt, say whether the entered number is greater than or less than the secret number

---

![](http://fondinfo.github.io/images/misc/monster.png)
# The Monster's Room

- The player moves on a 5x5 grid, starting from a corner
    - Rows and columns are numbered from 0 to 4
- A treasure and a monster are hidden in two *different* random positions at the beginning of the game
    - They do not overlap with each other, nor with the player's corner
- At each turn:
    - Ask the player for a direction (`w/a/s/d`)
    - If they land on the treasure cell, they win
    - If they land on the monster cell, they lose

>

Just store three pairs of Cartesian coordinates
<br>
No graphics required

---

![](http://fondinfo.github.io/images/games/climbing.svg)
# Free Climbing

- Competition between two climbers, in text format
- Repeatedly generate two random numbers
    - Each number $∈ [-1, 3]$
    - Each competitor's jump up (or small descent)
    - A competitor's level never goes below $< 0$
- The first one to reach the top (a constant `TOP`) wins
