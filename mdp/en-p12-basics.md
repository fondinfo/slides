![](http://fondinfo.github.io/images/algo/rubik-cube.png)
# Basics
## Introduction to programming

---

![large](http://fondinfo.github.io/images/dev/python-cases.png) Web, data science, machine learning, scripting, teaching, games, hardware, multiplatform…
# 💡️ Python is fun!

![](http://fondinfo.github.io/images/algo/antigravity.png)

>

<https://xkcd.com/353/>

---

# 🧪 Interactive Shell

- Install [Thonny](https://thonny.org/) or use the online [Playground](https://fondinfo.github.io/play/)
    - At the bottom, interactive *REPL* (Read-Eval-Print Loop) interface
- **Data type**: set of *values* + allowed *operations*
- Numeric types: **`int`** or **`float`**, for integers or rational numbers
    - Basic operations: `+, -, *, /`
    - Integer division, remainder, power: `//, %, **`
- Descriptive comments, after `#`: not evaluated

``` py
>>> 7 / 2
3.5
>>> 7 // 2  # floor division: ⌊7/2⌋, try also -7 // 2
3
>>> 7 % 2  # reminder positive, try also -7 % 2
1
>>> 2 ** 1000  # no limits (but memory)
107150860718626[…]837205668069376
```

---

`a` | `b` | `a and b` | `a or b` | `not a`
----|-----|-----------|----------|--------
F   | F   | F         | F        | T
F   | T   | F         | T        | T
T   | F   | F         | T        | F
T   | T   | T         | T        | F

# 🧪 Boolean values and None

- Type **`bool`**, for boolean values: `True, False`
    - Logical operators: `and, or, not` (→ [Logic](t11-logica.html))
- Comparisons: `==, !=, <, <=, >, >=`
    - Only between homogeneous values; boolean result
    - Chainable comparisons, `and` implicit
- Value **`None`**, unique of type `NoneType`: *nothing*

``` py
>>> 4 == 5
False
>>> 4 != 5 and not False
True
>>> 3 < 5 < 7
True
>>> 3 < 5 and 5 < 7  # idem
True
```

---

![large](http://fondinfo.github.io/images/algo/assign.svg)
# ⭐ Assignment

- A **variable** is used to remember a useful result
- *Assignment*: operator **`=`**
    - On the left a *name*
    - On the right an expression (→ *value*)
- **⚠️ Do not confuse**
    - *Equality* comparison: operator **`==`**

``` py
>>> pi = 3.14  # assignment
>>> radius = 2.5
>>> area = pi * (radius ** 2)
>>> area
19.625
>>> radius = radius + 1  # guess radius… and area!
```

---

![](http://fondinfo.github.io/images/algo/var-label.svg)
# 🔬 Variable

- **Name** associated with a certain **value**
    - 🏷️ *Label* → *object*
- Object assigned to multiple variables
    - Not copied, but receives multiple labels
- The **type** depends on the currently assigned value
    - A var does not have to be *declared*
    - But it must be *initialized* before use
- *Reassignment*: new value to an existing var

``` py
>>> x = None           # no actual value, yet…
>>> x = 100            # variables: all_lower_case
>>> next_position = x  # use explicative names!
>>> DELTA_X = 5        # constants: ALL_UPPER_CASE
>>> x += DELTA_X       # shortcut for: `x = x + DELTA_X`
>>> a, b = 5, 8        # multiple assignments
```

---

# 🧪 Text Strings

- Type **`str`** for character sequences
- Enclosed in double or single quotes
- Concatenation: `+` operator
- Membership test (substring): `in` operator
- Length: `len` *function*

``` py
>>> str1 = "Monty Python's "
>>> str2 = 'Flying Circus'
>>> result = str1 + str2
>>> result
"Monty Python's Flying Circus"
>>> "Py" in result
True
>>> len(result)
28
```

---

# ⭐ Built-in Functions

- [Built-in](https://docs.python.org/3/library/functions.html) functions: `max, min, abs, len, round`…
- Type conversion functions (*cast*): `int, float, str`…
- Parameters between *parentheses*, separated by *comma*
- Typically, result assigned to variable

``` py
>>> max(3, 5)
5
>>> m = min(6, 4)
>>> m
4
>>> "5" + 3
TypeError: can only concatenate str (not "int") to str
>>> int("5") + 3
8
>>> "5" + str(3)
"53"
```

---

# ⭐ Methods

- In Python all values are *objects*
    - Different types → different operations, like *methods*
- Activating an object's method
    - Object and method separated by “`.`”
    - Then parameters in parentheses
    - Typically, result assigned to variable
- [Methods of `str` objects](https://docs.python.org/3/library/stdtypes.html#string-methods): `upper`, `lower`, `count`…

``` py
>>> txt = "Monty Python"
>>> shout = txt.upper()  # new string returned, `txt` unchanged
>>> shout
"MONTY PYTHON"
>>> txt.count("y")
2
```

---

![](http://fondinfo.github.io/images/fun/shopping-list.png) [Spam…](https://www.youtube.com/watch?v=Gxtsa-OvQLA)
# ⭐ List

- **Mutable** sequence of *homogeneous* values
- Elements between *square brackets*, separated by *commas*
- Add, remove: `append, remove`
- Length: `len` – Membership test: `in`

``` py
>>> groceries = ["spam", "egg", "beans"]
>>> groceries.append("sausage")  # add "sausage" at the end
>>> len(groceries)  # size has grown
4
>>> "egg" in groceries  # membership test
True
>>> groceries.remove("egg")  # remove "egg"
>>> len(groceries)  # size has shrunk
3
>>> groceries
["spam", "beans", "sausage"]
```

---

![large](http://fondinfo.github.io/images/algo/holy-grail.jpg) [The Bridge of Death](https://www.youtube.com/watch?v=Xel0c6mpqPA)

# 🧪 Read and Write

- **`input`** reads a line of *text*, entered by the user, into a *variable*
    - First shows a message
    - Result of type `str`
- **`print`** writes a series of values on a line
    - Inserts space between values (parameters)

``` py
>>> knight = input("What is your name? ")
What is your name? Lancelot
>>> print("Right. Off you go,", knight, ".")
Right. Off you go, Lancelot .
```

---

![](http://fondinfo.github.io/images/algo/sum3.svg)
# 🧪 Sum of three numbers

- Save the following program as “`sum3.py`”
- Run, by clicking the ▶️ button
    - Or from the command line: `python sum3.py`

``` py
a = float(input("Insert 1st val: "))
b = float(input("Insert 2nd val: "))
c = float(input("Insert 3rd val: "))

total = a + b + c

print("The sum is", total)
```

- **⚠️ Attention to types**
    - ❓ What happens without conversion to `float`?

>

<https://fondinfo.github.io/play/?c02_sum3.py>

---

# Modules

---

![large](http://fondinfo.github.io/images/repr/raster-coords.svg) ![large](http://fondinfo.github.io/images/repr/color-mixing.svg)
# ⭐ Drawing on canvas

- **Raster coordinates**
    - Origin at top-left
- **Additive color synthesis**
    - Primaries: *Red, Green, Blue*
- We will use an *ad-hoc* module: `g2d`
    - Defines drawing functions
- In the [playground](https://fondinfo.github.io/play/?c02_draw.py), integrated version
- *Local execution*
    - Copy the `g2d.py` file from the [fondinfo repository](https://github.com/fondinfo/fondinfo/archive/master.zip) into your working folder
- [**g2d Documentation**](https://github.com/fondinfo/fondinfo#g2d)

---

![large](http://fondinfo.github.io/images/repr/pixel-grid.png)
# ⭐ Tuple

- **Immutable** sequence of values
    - Even of *different types*
- Often in parentheses
    - To separate it from other code
- Also useful for graphics:
    - *Position*: `(x, y)`
    - *Dimension*: `(width, height)`
    - *Color*: `(red, green, blue)` <br> Each component in the range `0..255`

``` py
center_pt = (320, 240)  # packing
window_size = (640, 480)
bluette_color = (47, 102, 207)
x, y = center_pt  # sequence unpacking
```

---

# 🧪 Rectangles and Circles

``` py
import g2d

g2d.init_canvas((600, 400))  # width, height

g2d.set_color((255, 255, 0))  # red + green = yellow
g2d.draw_rect((150, 100), (250, 200))  # left-top, size

g2d.set_color((0, 0, 255))
g2d.draw_circle((400, 300), 20)  # center, radius

g2d.main_loop()  # manage the window/canvas
```

---

![](http://fondinfo.github.io/images/repr/draw.svg)
# 🧪 Lines and Text

``` py
import g2d

g2d.init_canvas((600, 400))

# draw_rect, draw_circle…

g2d.set_color((0, 255, 0))
g2d.draw_line((150, 100), (400, 300))   # pt1, pt2

g2d.set_color((255, 0, 0))
g2d.draw_text("Hello", (150, 100), 40)  # text, center, font-size

g2d.main_loop()
```

>

<https://fondinfo.github.io/play/?c02_draw.py>

---

# 🧪 Dialog Boxes

- `g2d.prompt`: *input* request, in a window, `str` result
- `g2d.alert`: *message* display, single `str` parameter
- `g2d.confirm`: *confirmation* request, `bool` result

``` py
import g2d

g2d.init_canvas((600, 400))

name = g2d.prompt("What's your name?")
g2d.alert("Hello, " + name + "!")

g2d.main_loop()
```

- [**g2d Documentation**](https://github.com/fondinfo/fondinfo#g2d)

---

![](http://fondinfo.github.io/images/algo/calculator.svg) [☞ `math`](https://docs.python.org/3/library/math.html)
# 🧪 Battery included 🔋

- [`math`](https://docs.python.org/3/library/math.html) module in *Python Standard Library*
    - No installation required
    - `sqrt, log, sin, pi, e, inf`…

``` py
import math  # use namespace `math` as prefix
y = math.sqrt(4)
print(y)  # 2.0
```

``` py
from math import sqrt  # no prefix for `sqrt`
print(sqrt(4))
```

- `import` at the beginning, to highlight dependencies
    - **`import …`**: entire module *namespace*
    - **`from … import …`**: only some names

---

![](http://fondinfo.github.io/images/algo/red-dice.svg) [☞ `random`](https://docs.python.org/3/library/random.html)
# 🧪 Random 🎲

- [`random`](https://docs.python.org/3/library/random.html) module in *Python Standard Library*
    - No installation required
    - `randint, randrange, random, choice, shuffle`…

``` py
from random import randint, randrange, choice

die1 = randint(1, 6)  # like rolling a die
die2 = randint(1, 6)  # like rolling a die

one_of_three = randrange(3)  # 0, 1, or 2

prime = choice([2, 3, 5, 7, 11, 13])  # one from a sequence
```

---

# ⭐ Control Structures

---

![](http://fondinfo.github.io/images/algo/if.svg)
# ⭐ Selection: if

- `if` or `else` body: **indentation**
    - Required for *syntax*, not optional
    - Can contain any statement
    - Also other nested `if` or `while` blocks!

> Readability counts *(The Zen of Python)*

``` py
r = int(g2d.prompt("Radius? [50-99]"))

if 50 <= r and r <= 99:
    g2d.set_color((0, 0, 255))
    g2d.draw_circle((200, 200), r)

g2d.set_color((255, 255, 0))
g2d.draw_circle((200, 200), 25)
```

---

![](http://fondinfo.github.io/images/algo/if-else.svg)
# ⭐ Selection: else

- `else` clause: optional
    - Executed if and only if the condition is not met

``` py
r = int(g2d.prompt("Radius? [50-99]"))

if 50 <= r <= 99:  # i.e.: 50 <= r and r <= 99
    g2d.set_color((0, 0, 255))
    g2d.draw_circle((200, 200), r)
else:
    g2d.alert("Out of range!")

g2d.set_color((255, 255, 0))
g2d.draw_circle((200, 200), 25)
```

>

<https://fondinfo.github.io/play/?c02_ifelse.py>

---

![](http://fondinfo.github.io/images/algo/dice.svg)
# ⭐ Selection: elif

- `elif`: contraction of `else if`
    - Selection among *multiple* alternatives
    - If no condition is true, `else` is executed
- Ex. Rolling *two dice* → 3 alternatives
    - 1st die wins, 2nd die wins, or a tie

``` py
from random import randint
a, b = randint(1, 6), randint(1, 6)  # roll 2 dice
if a > b:
    print("The first die wins.")
elif a < b:
    print("The second die wins.")
else:
    print("The dice are equal. It's a tie.")
```

---

![](http://fondinfo.github.io/images/algo/while.svg)
# ⭐ Iteration: while

- *Looping* condition
    - *Preliminary* check
    - Possible that the body is never executed

``` py
r = int(g2d.prompt("Radius? [50-99]"))

while r < 50 or r > 99:
    g2d.alert("Out of range!")
    r = int(g2d.prompt("Radius? [50-99]"))

g2d.set_color((0, 0, 255))
g2d.draw_circle((200, 200), r)
```

>

<https://fondinfo.github.io/play/?c02_while.py>

---

![](http://fondinfo.github.io/images/misc/rock-cubes.png)
# ⭐ Iteration: for

- Operates only on **sequences and iterables**
    - `list, tuple, str, range`…
    - Num. iterations = sequence length
- Iteration variable
    - At each iteration, new value from sequence

``` py
values = [2, 3, 5, 7, 11]
for val in values:  # list
    print(val ** 3)  # 8 27 125 343 1331
```

``` py
for r in (200, 175, 150):  # tuple
    color = (randrange(256), randrange(256), randrange(256))
    g2d.set_color(color)
    g2d.draw_circle((200, 200), r)
```

---

# ⭐ Value Range

- **`range`**: right-open value range
    - Extremes: lower *included* (0), upper *excluded*
    - If lower extreme ≠ 0, two parameters are needed
- *`reversed`*: reversed sequence

``` py
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)
```

``` py
for i in reversed(range(5)):  # 4, 3, 2, 1, 0
    print(i)
```

---

![](http://fondinfo.github.io/images/misc/red-squares.svg)
# 🧪 Sequence of Squares

``` py
import g2d

g2d.init_canvas((500, 500))

for i in range(4):  # 0, 1, 2, 3
    red = i * 85    # proportional to i
    g2d.set_color((red, 0, 0))

    pos = i * 100   # proportional to i
    g2d.draw_rect((pos, pos), (200, 200))

g2d.main_loop()
```

- ❓ What happens if we use `reversed` in the `for` loop?

>

<https://fondinfo.github.io/play/?c02_squares.py>

---

# 🏊 Exercises

---

![](http://fondinfo.github.io/images/misc/handshake.svg)
# Hello, admin!

- Write a program in a file `hello.py`
- Ask the user for their name
- Insert the name into a greeting message, e.g.:

``` txt
What's your name? Adam
Hello, Adam!
```

- If the user's name is “`admin`”…
    - Also show the special message “`At your command`”

---

![](http://fondinfo.github.io/images/misc/greek-pi.png)
# Circle

- Ask the user for the radius `r` of a circle
    - `r` rational number between 0 and 200
- If `r` is valid
    - Display the circle, in the center of the canvas
    - Just above the circle, write the value of its area
    - Just below the circle, write the value of its circumference
- If `r` is out of range
    - Show an error message

---

![](http://fondinfo.github.io/images/games/dragon.svg)
# The Year of the Dragon

- The program asks the user for their birth year
- Then it communicates whether that year was under the sign of the dragon, or not
- We know that, according to Chinese tradition, 2024 is the year of the dragon
- We also know that the sign repeats every 12 years

---

![large](http://fondinfo.github.io/images/algo/holy-grail.jpg)
# The Bridge of Death

- Ask the user three questions:
    - `"What is your name?"`
    - `"What is your quest?"`
    - `"What is your favorite color?"`
- If the answers are `"Lancelot"`, `"Holy Grail"`, and `"Blue"`, print:
    - `"Right. Off you go."`
- Otherwise, print:
    - `"Down into the Gorge of Eternal Peril!"`

>

First version: ask and check only the name

---

![](http://fondinfo.github.io/images/misc/calendar-cols.jpg)
# Age Calculation

- Ask the user for their birth date
    - Year, month, and day
- Ask the user for today's date
    - Year, month, and day
- Communicate the exact current age
    - Number of birthdays already passed

>

In the current year, has the user already had their birthday?
<br>
Boolean expression composed with `and`, `or`, `not`…

---

![](http://fondinfo.github.io/images/misc/three-brothers.png)
# Minimum and Maximum

- Generate and print three random integers: `a`, `b`, `c`
- Each between 1 and 6
- Determine and show which is the smallest of the three

>

First check if `a` is smaller than the other two
<br>
Otherwise check if `b` is smaller than `c`
<br>
Otherwise…

---

![](http://fondinfo.github.io/images/misc/random-squares.svg)
# Random Squares

- Ask the user for a number `n`
- Draw `n` squares
    - All with a side of 100 pixels
    - Each in a random position
    - Each with a random color

>

Start by drawing only one gray square, in a random position

---

![](http://fondinfo.github.io/images/misc/diagonal-squares.svg)
# Diagonal Squares

- Ask the user for a number `n`
- On a 500×500 canvas, draw `n` squares
    - All with a side of 50 pixels
    - Arranged along the diagonal, so they always share a vertex
    - Each with a random color
- Optionally, determine the side so that it occupies the entire diagonal

---


![large](http://fondinfo.github.io/images/misc/segments-1.svg)
# Random Segments

- Ask the user for the number of segments to draw
- Draw the segments
    - All with the same color, black
    - Each with both ends in a random position
    - But entirely contained within the canvas

---

![large](http://fondinfo.github.io/images/misc/segments-2.svg)
# Polyline

- Ask the user for the number of segments to draw
- Draw the segments as a polyline, in black
    - Start from a random point and connect it to a subsequent random point
    - Continue connecting the last point to a new random point
- The line must be entirely contained within the canvas
