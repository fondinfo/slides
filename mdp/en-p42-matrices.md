![]([http://fondinfo.github.io/images/misc/tic-tac-toe.svg](http://fondinfo.github.io/images/misc/tic-tac-toe.svg))
# Matrices
## Introduction to Programming

---

![large](http://fondinfo.github.io/images/repr/matrix.svg)
# ⭐ Matrix in a single list

- Rows concatenated into a single list
- Single index: `i = x + y * cols`

``` py
>>> data = ["A", "B", "C", "D",
            "E", "F", "G", "H",
            "I", "J", "K", "L"]
>>> cols, rows = 4, 3
>>> x, y = 1, 2
>>> data[x + y * cols]
"J"
```

- Conversely: `x, y = i % cols, i // cols`
- `y` counts how many full rows precede an element
- `x` counts how many cells precede the element on its row

---

# Print a matrix

- Print a row, from left to right
- Everything must be repeated for each row, from top to bottom

``` py
for y in range(rows):
    for x in range(cols):
        end_ = "\n" if x == cols - 1 else "\t"
        print(data[x + y * cols], end=end_)
```

- Initialize matrix, as a single list: *list repetition*
- All elements to `0` (or another value…)

``` py
matrix = [0] * (rows * cols)
```

---

# 🧪 Matrix operations

- Sum, column by column
- Besides the list, you need to know at least `cols` (or `rows`)

``` py
matrix = [2, 4, 3, 8,
          9, 3, 2, 7,
          5, 6, 9, 1]
cols, rows = 4, 3
# rows = len(matrix) // cols

for x in range(cols):
    total = 0
    for y in range(rows):
        val = matrix[x + y * cols]   # 2D -> 1D
        total += val
    print("Col #", x, "sums to", total)
```

---

# List of lists

---

# 🧪 Matrix in list of lists

- Possible representation of a *matrix*: list of lists
- ⚠️ Often, management is more complex
    - In general, a simple list is preferable
- Accessing elements: two indices (`y` and `x`)
    - ⚠️ *First index* selects the row: `y`
    - *Second index* selects the column: `x`

``` py
>>> a = [["A", "B", "C", "D"],
         ["E", "F", "G", "H"],
         ["I", "L", "M", "N"]]
>>> a[2]
["I", "L", "M", "N"]
>>> a[2][1]  # x, y = 1, 2
"L"
```

---

# 🧪 Operations on lists of lists

- Sum, column by column
- From the list of lists, you can derive `rows` and `cols` 👍

``` py
matrix = [[2, 4, 3, 8],
          [9, 3, 2, 7],
          [5, 6, 9, 1]]
rows = len(matrix)
cols = len(matrix[0])

for x in range(cols):
    total = 0
    for y in range(rows):
        val = matrix[y][x]
        total += val
    print("Col #", x, "sums to", total)
```

---

# 🔬 Create rows x cols matrix

- Initialize matrix, as a single list: *list repetition*
- Initialize a list of lists: two nested *comprehensions* ⚠️
    - Also pay attention to copy operations ⚠️
    - [Python FAQ: multidimensional list](https://docs.python.org/3/faq/programming.html#faq-multidimensional-list)

``` py
unidim = [0] * (rows * cols)  # suggested way

multidim = [[0 for x in range(cols)] for y in range(rows)]

# multidim = []
# for y in range(rows):
#     new_row = []
#     for x in range(cols):
#         new_row.append(0)
#     multidim.append(new_row)
```

---

# 🧪 Flattened and nested lists

- From flattened structure `data` to nested structure `matrix`
    - In comprehension, rows taken as *slices* from the simple list
    - All slices of size `w` (which must be known)

``` py
matrix = [data[i * w : i * w + w] for i in range(h)]
```

- From nested structure `matrix` to flattened structure `data`
    - Comprehension with two `for`
    - Iterate the structure row by row
    - Iterate the elements of each row

``` py
data = [v for row in matrix for v in row]
```

---

# Matrix games

---

# ⭐ Abstract game

``` py
def abstract():
    raise NotImplementedError("Abstract method")

class BoardGame:
    def play(self, x: int, y: int, action: str): abstract()
    def read(self, x: int, y: int) -> str: abstract()
    def finished(self) -> bool: abstract()
    def status(self) -> str: abstract()
    def cols(self) -> int: abstract()
    def rows(self) -> int: abstract()
```

>

*BoardGame*: [https://fondinfo.github.io/play/?boardgame.py](https://fondinfo.github.io/play/?boardgame.py)

---

# ⭐ Game loop

``` py
def print_game(game: BoardGame):
    for y in range(game.rows()):
        for x in range(game.cols()):
            end_ = "\n" if x == game.cols() - 1 else "\t"
            print(game.read(x, y), end=end_)
    print(game.status())

def console_play(game: BoardGame):
    print_game(game)
    while not game.finished():
        x, y, action = input("x y action?\n").split()
        game.play(int(x), int(y), action)
        print_game(game)
```

>

*Gui*: [https://fondinfo.github.io/play/?boardgamegui.py](https://fondinfo.github.io/play/?boardgamegui.py)

---

![]([http://fondinfo.github.io/images/qt/fifteen-puzzle.jpg](http://fondinfo.github.io/images/qt/fifteen-puzzle.jpg))
# 🧪 Fifteen - Constructor

``` py
class Fifteen(BoardGame):
    def __init__(self, w: int, h: int):
        # init board with sorted tiles: [1 2 ... 14 15 0]
        self._bd = list(range(1, w * h)) + [0]
        self._x0, self._y0 = w - 1, h - 1  # blank
        self._w, self._h = w, h

        # then, random walk of the blank tile, until most tiles change
        while w * h > 1 and self._bd[-1] != 1:
            dx, dy = choice([(0, -1), (1, 0), (0, 1), (-1, 0)])
            self.play(self._x0 + dx, self._y0 + dy, "")
```

>

[https://en.wikipedia.org/wiki/15_puzzle#Solvability](https://en.wikipedia.org/wiki/15_puzzle#Solvability)

---

# 🧪 Fifteen - Moves

``` py
class Fifteen(BoardGame):
    #...
    def play(self, x: int, y: int, action: str):
        w, h, bd, x0, y0 = self._w, self._h, self._bd, self._x0, self._y0
        if 0 <= x < w and 0 <= y < h and abs(x - x0) + abs(y - y0) == 1:
            bd[y0 * w + x0] = bd[y * w + x]  # swap tiles
            bd[y * w + x] = 0
            self._x0, self._y0 = x, y  # blank

    def finished(self) -> bool:
        for i in range(self._w * self._h - 1):
            if self._bd[i] != i + 1:
                return False
        return True
```

---

# 🧪 Fifteen - Getter methods

``` py
class Fifteen(BoardGame):
    #...
    def read(self, x: int, y: int) -> str:
        w, h, bd = self._w, self._h, self._bd
        if 0 <= x < w and 0 <= y < h and bd[x + y * w]:
            return str(bd[x + y * w])
        return ""

    def status(self) -> str:
        if self.finished():
            return "Puzzle solved!"
        return "Playing"
```

>

<https://fondinfo.github.io/play/?c09_fifteen.py>

---

# Data streams

---

![](http://fondinfo.github.io/images/fun/cassette-tape.png)
# 💡️ Stream

- Abstraction for information flows
    - Reading or writing information to *any* I/O device (*file, but not only*)
- **Text files**
    - Various encodings (*UTF-8* or other)
    - Automatic conversions, e.g. `"\n"` → `"\r\n"`
- **Binary files**
    - Precise byte-by-byte I/O, without any conversion
    - Any file... even text!

>

[docs.python.org/tutorial](https://docs.python.org/3/tutorial/inputoutput.html#tut-files)

---

![]([http://fondinfo.github.io/images/hist/typewriter.png](http://fondinfo.github.io/images/hist/typewriter.png))
# ⭐ Writing to file

- Function **`open`** to access a (text) file
    - *Write* or *read* mode: `"w"`, or `"r"` (default)
- **`with`** block: *closes* the file at the end
    - Even in case of error
    - File available again for other apps.
- Writing to file: **`print`** function

``` py
with open("squares.txt", "w") as squares:
    for x in range(10):
        print(x, x ** 2, file=squares)
```

---

![]([http://fondinfo.github.io/images/fun/shopping-list.png](http://fondinfo.github.io/images/fun/shopping-list.png))
# ⭐ File reading loop

- Open file for reading with **`open`**
- **`with`** block: always closes the file on exit
- File *iterable* line by line with a **`for`** loop
    - *Similarly* to a list of strings

``` py
with open("shopping_list.txt") as groceries_file:
    for line in groceries_file:
        # process line
        # line = line.strip()
        print(line, ":", len(line))
```

- ⚠️ Each line is of type `str`, ending with `"\n"`
    - `strip()` removes leading and trailing whitespace

---

# 🔬 Reading a line

- **`read`** reads the entire file as a single string
- **`readline`** reads and “*consumes*” a single line
- Subsequent reads skip already “*consumed*” lines
    - The file “*tape*” advances under the “*read head*”
- At the end of the file, an empty string is read
    - *Sentinel* value
- For better compatibility, set `utf-8` encoding

``` py
with open("some_file.txt", encoding="utf-8") as f:
    first_line = f.readline()
    second_line = f.readline()
    remaining_text = f.read()
    # read lines contain "\n" at the end
```

---

# 🧪 Simple CSV reading

``` py
def read_csv(filename: str) -> tuple[list[int], int, int]:
    data, rows = [], 0
    with open(filename) as f:
        for line in f:
            row = [int(v) for v in line.split(",")]
            data += row  # or, data.append(row)
            rows += 1
    return data, len(data) // (rows or 1), rows
```

---

# 🧪 CSV module

- [`csv` module]([https://docs.python.org/3/library/csv.html](https://docs.python.org/3/library/csv.html)) for more complex files (quoted text etc.)

``` py
import csv
matrix = []
with open("some.csv") as f:
    reader = csv.reader(f)
    column_names = next(reader)  # 1st row
    for row in reader:  # each row is a `list[str]`
        matrix.append(row)
print(matrix)

with open("some.csv", "w") as f:
    writer = csv.writer(f)
    for row in matrix:
        writer.writerow(row)  # quotes are added, where needed
```

---

# 🧪 Top100 from IMDB

- Columns
    - `rank (0), name (1), year (2), rating (3), genre (4), certificate (5), run_time (6), tagline (7), budget (8), box_office (9), casts (10), directors (11), writers (12)`
- Objectives
    - List genres in descending order by number of films
    - List the 10 director-actor pairs with the most collaborations
    - List actors who have participated in all "Star Wars" films present here

>

[https://fondinfo.github.io/data/movies.csv](https://fondinfo.github.io/data/movies.csv) <br>
[https://fondinfo.github.io/play/?c10_movies.py](https://fondinfo.github.io/play/?c10_movies.py)

---

# 🥷 Error handling

- **Exceptions**: to handle unexpected cases separately
- In case of error inside `try`
    - `try` execution stops immediately
    - `except` block is executed

``` py
x = None
while x is None:
    try:
        x = int(input("Please enter a number: "))  # ValueError?
        print("That's fine")
    except:
        print("Oops! That was no valid number. Try again...")
print("The square is", x ** 2)
```

---

![]([http://fondinfo.github.io/images/fun/tape-pencil.png](http://fondinfo.github.io/images/fun/tape-pencil.png))
# 🥷 File errors

- For a `try`, various `except` blocks are possible
    - Each handles only one type of error
    - Otherwise, the program terminates
- `with`: file closed even in case of error

``` py
try:
    with open("file.txt", "r") as f:   # OSError?
        whole_text = f.read()          # OSError?
        print(int(whole_text[10:15]))  # IndexError? ValueError?
except OSError as e:
    print("Ouch!\n", e)
except IndexError:
    print("Oh, my!")
# if ValueError is raised: unhandled, abrupt termination
```

---

# 🥷 Console as stream

- Console as *input* stream: `sys.stdin`
- Console as *output* stream: `sys.stdout`, `sys.stderr`
- File **`write`** method, alternative to `print`
    - A single `str` value as parameter
    - Does not add implicit `\n`

``` py
import sys

sys.stdout.write("CTRL-D (Lin) or CTRL-Z (Win) ")
sys.stdout.write("to close the input\n")  # print("...")
for line in sys.stdin:
    print(len(line))  # line includes a trailing '\n'
```

---

# 🥷 Formatted strings

- Strings with `f` before quotes
- Can include expressions, inside curly braces
- Formatting specifications, after `:`

``` py
for a in [0, 45, 90, 135]:
    v = math.sin(a * math.pi / 180)
    print(f"Angle: {a:3}; Sin: {v:4.2f}")
```

``` text
Angle:   0; Sin: 0.00
Angle:  45; Sin: 0.71
Angle:  90; Sin: 1.00
Angle: 135; Sin: 0.71
```

>

[docs.python.org/tutorial](https://docs.python.org/3/tutorial/inputoutput.html#tut-f-strings)

---

# 🏊 Exercises

---

# Data alignment

- Display two tables with ASCII characters
    - 4 rows x 24 columns, codes from 32 to 126
- Table 1: show characters in order, column by column
- Table 2: show characters in order, row by row

``` text
 $(,048<@DHLPTX\`dhlptx|
!%)-159=AEIMQUY]aeimquy}
"&*.26:>BFJNRVZ^bfjnrvz~
#'+/37;?CGKOSW[_cgkosw{
```

>

Always use two nested `for` loops: outer on `y`, inner on `x`
<br>
In each position, calculate the character to display: `x * ROWS + y`...

---

![]([http://fondinfo.github.io/images/repr/neighborhood4.svg](http://fondinfo.github.io/images/repr/neighborhood4.svg))
# Smooth function

- Write a `smooth` function
    - Parameter: initial matrix, of floats
    - Result: new smoothed matrix
- **Smooth**: for each cell in the initial matrix
    - The result is the *average* of the neighborhood
    - 5 values: the cell itself and 4 adjacent ones
- Pay attention to outer cells
    - Sum and count only available values
    - 4 values at the borders, 3 values at the corners
- Test the function with some test matrices
- Provide two implementations
    - Matrix in simple list
    - Matrix in list of lists

---

![]([http://fondinfo.github.io/images/repr/matrix-spiral.svg](http://fondinfo.github.io/images/repr/matrix-spiral.svg))
# Spiral

- Write a function to fill a square (or rectangular) matrix with increasing numbers
- Follow the spiral path suggested in the figure on the side
- Matrix dimensions indicated by the user at runtime

>

Keep track of the current direction (∆y, ∆x)
<br>
Advance to the edge or an already visited cell,
<br>
then change direction clockwise
<br><br>
Raster coordinates, 90° clockwise rotation: `(x', y') = (-y, x)`
<br>
In general: `(x', y') = (x⋅cos(θ) - y⋅sin(θ), x⋅sin(θ) + y⋅cos(θ))`

---

![]([http://fondinfo.github.io/images/games/lightsout.svg](http://fondinfo.github.io/images/games/lightsout.svg))
# Lights out

- Game based on a grid of lights
- At startup, some random lights are on
- If you click on a light
    - It changes state
    - Along with the 4 adjacent lights (**✣**)
- The goal is to turn off all lights
    - Possibly with the minimum number of moves

>

<[https://en.wikipedia.org/wiki/Lights_Out_(game](https://en.wikipedia.org/wiki/Lights_Out_(game))>

---

![]([http://fondinfo.github.io/images/games/ogre.svg](http://fondinfo.github.io/images/games/ogre.svg))
# The monster's room

- `BoardGame` game on a $w×h$ matrix
- A certain number of ogres and treasures hidden randomly
    - All in different positions
- Cell at $(0, 0)$ left as the player's starting position
- With each move, the player moves to one of the 4 adjacent cells (**✣**)
    - Without exiting the matrix
- If they discover an ogre, they lose
- If they discover all treasures, they win

---

# Bishops

- On an $8×8$ chessboard (or generally $w×h$)
    - Randomly place $n$ bishops
    - So that they do not overlap
    - Parameters requested from the user at startup
- Display the chessboard with the bishops on the console
- Also highlight all *safe* cells
    - Cells that no bishop can reach

>

Bishops move any number of steps diagonally

---

![]([http://fondinfo.github.io/images/misc/resistors.png](http://fondinfo.github.io/images/misc/resistors.png)) `$$R_{ser} = \sum_i R_i$$` `$$\frac{1}{R_{par}} = \sum_i \frac{1}{R_i}$$`
# Resistors from file

- Read a sequence of electrical resistance values from a file
- Each line contains a value
- At the end, display the equivalent resistance, both for series and parallel resistors

---

![]([http://fondinfo.github.io/images/misc/histogram.svg](http://fondinfo.github.io/images/misc/histogram.svg))
# Sequence of values

- Ask the user for a file name
- Each line of the file contains a `float` value
- Find the minimum and maximum value in the file
- Display the two values

---

![]([http://fondinfo.github.io/images/misc/merge-sign.png](http://fondinfo.github.io/images/misc/merge-sign.png))
# Merge

- Two text files contain sequences of numbers
    - One value per line
    - In each file, values are already sorted
- Write the values from both files to output
    - Output sequence all in order

>

Cyclically, compare the pair of first values (each coming from one of the two streams)
<br>
Write the smaller of the two to the output file
<br>
Do not extract a new value from a stream, if the previous one has not yet been written to output

---

# Diagonal in CSV

- Read an integer matrix from a CSV text file
    - *Comma Sep. Values*: row by row values, separated by comma

``` text
5,7,2,11
1,3,12,9
4,6,10,8
```

- Store the data in a simple list
    - Count: num. rows in file, num. values in a row
- Square values on diagonal, from bottom right
    - In the example: `8`, `12`, `7` (cells where `cols-x == rows-y`)
- Save the modified matrix to CSV

---

![]([http://fondinfo.github.io/images/misc/pac-man.png](http://fondinfo.github.io/images/misc/pac-man.png))
# Maps for Pac-Man

- `PacMan` class from `Turtle` of `bounce` example
    - `PacMan` size: 16×16 pixels
- Walls are indicated in a map
    - List of strings (rows)
    - Each character of the map: 8×8 pixel block
- Prevent passage through walls
    - Check before movement
- Ignore keyboard commands that move to a wall
