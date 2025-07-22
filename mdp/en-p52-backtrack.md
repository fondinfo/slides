![](http://fondinfo.github.io/images/misc/tic-tac-toe.svg)
# Backtracking
## Introduction to Programming

---

![](http://fondinfo.github.io/images/fun/8-queens.svg)
# Constraint Satisfaction Problem

- *Constraint Satisfaction Problem* (CSP), characterized by:
    - **Set of variables**, which can take values from a certain *domain*
    - **Set of constraints**, which must be respected by the variable values
- Example: *Eight Queens Puzzle*
    - Place `8` queens on an `8x8` chessboard
    - So that none of them can capture another
    - No queen should share a column, row, or diagonal with another queen

---

![](http://fondinfo.github.io/images/fun/generate-and-test.png)
# Generate & Test

- Technique for solving constraint satisfaction problems
- A *value* is assigned to each variable
- It is checked if all *constraints* are satisfied
    - If constraints are *satisfied* ⇒ a *solution* is found
    - Otherwise, try with different values
- The process *continues*
    - Until there are no new assignments to test
    - All solutions are tested

>

<https://fondinfo.github.io/play/?c11_words.py>

---

![](http://fondinfo.github.io/images/fun/8-queens.svg) ![](http://fondinfo.github.io/images/fun/k-comb.svg)
# 8 Queens: G&T

- *Generate*
    - Place `8` queens in all possible *combinations* on an `8x8` chessboard
    - We need to choose `8` (*k*) squares out of `64` (*n*), without considering the order
    - `~ 4 billion`
- *Test*
    - For each combination, check if no queen can capture another
    - Only `92` solutions

>

Example of the more general `N` queens problem on an `N×N` chessboard
<br>
<https://en.wikipedia.org/wiki/Combination>

---

![](http://fondinfo.github.io/images/fun/queens-sol.svg)
# 8 Queens: Reduced G&T

- From the constraints, it is clear that *each row*
    - Can contain at most 1 queen
    - Must contain exactly 1 queen
- It is therefore possible to represent a *list*
    - The values represent the column where the queen is placed on the row
    - `8` elements with indices `0..7` and values `0..7`
    - (`N` elements with indices `0..N-1` and values `0..N-1`)
- *Generate*
    - All configurations of 8 values: `8⁸ = ~ 16 million`
- *Test*
    - For each configuration, check the constraints

---

![large](http://fondinfo.github.io/images/fun/backtracking.png)
# Standard Backtracking

- Immediately discards assignments that do not satisfy the constraints
- After *each assignment*, the constraints are checked
- If there are no *already violated constraints*, proceed with assigning the remaining variables
- Otherwise, check if the newly assigned variable still has values to try
    - If yes, try a new value
    - Otherwise, go back and modify an already assigned variable
- For the *8 Queens* (`92` solutions)
    - `15720` cells checked, `2056` attempted placements

---

# N Queens, Backtracking

![large](http://fondinfo.github.io/images/fun/queens.svg)

---

![](http://fondinfo.github.io/images/fun/queens-sol.svg)
# N Queens, Verification

``` py
def print_board(board: list):
    for v in board:
        print("•" * v + "♛" + "•" * (len(board)-v-1))

def under_attack(board: list, x: int, y: int) -> bool:
    for r in range(y):  # for each row above y
        # directions: ↖↑↗ (no queens below)
        if board[r] in (x - (y-r), x, x + (y-r)):
            return True
    return False
```

>

`board` is a list of `int`: for each row of the chessboard, it stores the queen's `x` position

---

# N Queens, Recursion

``` py
def place_queens(board: list, y=0) -> bool:
    if y == len(board):
        return True  # all queens already placed
    for x in range(len(board)):
        if not under_attack(board, x, y):
            board[y] = x  # (x, y) is safe: place a queen

            # try and place queens in the following rows
            if place_queens(board, y + 1):
                return True

            board[y] = None  # no luck, backtrack
    return False
```

>

<https://github.com/tomamic/backtracking/blob/main/queens.py>

---

![](http://fondinfo.github.io/images/misc/artificial-intelligence.png)
# Games and AI

---

# Games and AI

- Games: the first field to which artificial intelligence was applied
- Interesting characteristic of games: enormous search space
- Presence of the opponent: uncertainty
- Finding the solution: more complicated

---

![](http://fondinfo.github.io/images/comp/chess.jpg)
# Perfect Knowledge

- For AI, games with the following two characteristics are interesting
- ① Two-player games, with alternating moves
- ② Games with perfect knowledge
    - Players have the same information
    - Deterministic and observable environment
- Typical classical AI games are checkers, chess, etc.
    - Not typical card games: poker, bridge, etc.

---

# Two Opponents

- Typically, only two players, who play alternately
    - Presence of two agents whose actions alternate
- *Zero-sum* games
    - One player's advantage is equivalent to the other's disadvantage
    - Both utility functions are always equal
    - But with opposite signs
    - For example +1 for the winner and -1 for the loser

---

# Game Elements

- Game as a search problem, characterized by:
    - Initial state
    - Operators: legal moves
    - Termination condition
    - Utility function (payoff): indicates the outcome of the game
- Game development interpreted as a tree
    - Root: starting point
    - Leaves: final positions
- Game tree determined by
    - Initial state
    - Legal moves of each player

---

![](http://fondinfo.github.io/images/misc/tic-tac-toe.svg)
# Tic-Tac-Toe Game

- “*Tic-tac-toe*”, “*Noughts and crosses*”, “*Xs and Os*”
- Paper and pencil game
- Two players who alternate
    - The first always has "X", the other "O"
- Each puts their mark in a cell of a 3×3 grid
- The first to get three of their marks in a row wins
    - Horizontally, vertically, or diagonally
- Toy problem
    - If played well, a game always ends in a draw
    - This makes it a futile game

---

# Strategies

- On the empty matrix (initial state) *X* has 9 possible moves
- *X* and *O* play in turns, until a final state is reached
- States good for *X* are bad for *O*
- *X* must find contingent strategies
    - Specify its initial moves
    - And those to make after the opponent's responses
- *Optimal strategy*
    - → Result no worse than any other strategy
    - Assumes playing against an infallible opponent

---

# Solution 1

- Complete database of **pre-calculated moves**
- Game state (Python-like data structures)
    - `matrix = [0] * 9`
    - `matrix[i] == 0` if empty
    - `matrix[i] == 1` if it contains *X*
    - `matrix[i] == 2` if it contains *O*
- Complete strategy
    - `moves: list[int] = [0] * 19683`
    - Game state: number in *base 3*, to convert to base 10
    - This is the index for the `moves` array
    - The element is the new move (or the new game state)

$$
n = c_0 × b^0 + c_1 × b^1 + \dots + c_8 × b^8; b=3
$$

---

![small](http://fondinfo.github.io/images/comp/tictactoe-x.png) ![small](http://fondinfo.github.io/images/comp/tictactoe-o.png)
# Solution 2

- **Decision rules**, with priority
    - ~ Expert system
- *X* opening: in a corner (the opponent has more chances to make a mistake)
- *O* opening: in the center if available, otherwise a corner
- *Win*: complete own tic-tac-toe
- *Block*: block opponent's tic-tac-toe
- *Fork*: prepare a double possible tic-tac-toe
- *Block fork*: block opponent's double possible tic-tac-toes
- Then: center, corner opposite to opponent, corner, side

>

<https://en.wikipedia.org/wiki/Tic-tac-toe#Strategy>
<br>
<https://www.wikihow.com/Win-at-Tic-Tac-Toe>
<br>
For convenience of sum: 2 = empty, 3 = X, 5 = O

---

![](http://fondinfo.github.io/images/comp/tictactoe-tree.png)
# Solution 3

- **Exploration of the move tree**
- *Algorithm*: generate all *reachable configurations* in one move and choose the best
- If a configuration is immediately winning, then it is the best
- Otherwise, all possible opponent moves must be considered
- Each player seeks their best move
- This determines the value of the configuration

``` py
class Position:
    matrix: list[int] = [0] * 9
    next_positions: list[Position] = []
    value: int = 0
```

---

# Evaluation Solution 1

- *Advantages*
    - Time efficient
    - Plays optimally
- *Disadvantages*
    - Not very space efficient
    - A lot of time to define the values of the `moves` vector
    - Errors are probable when entering values
    - Difficult to apply to other games
- *Does not* meet the requirements of a good AI technique

---

![small](http://fondinfo.github.io/images/comp/tictactoe-x.png) ![small](http://fondinfo.github.io/images/comp/tictactoe-o.png)
# Evaluation Solution 2

- *Advantages*
    - Space efficient
    - Plays optimally
    - The game strategy is more understandable
- *Disadvantages*
    - Less time efficient
    - Difficult to apply to other games
- *Does not* meet the requirements of a good AI technique

---

![](http://fondinfo.github.io/images/comp/tictactoe-tree.png)
# Evaluation Solution 3

- *Advantages*
    - Reasonably space efficient
    - Plays optimally
    - Approach extensible to other games
- *Disadvantages*
    - Time inefficient
- Example of a *good AI technique*

---

# 🏊 Exercises

---

![](http://fondinfo.github.io/images/misc/cindy1.png) ![](http://fondinfo.github.io/images/misc/cindy2.png)
# Cindy's Puzzle

- Game board: `2n+1` aligned cells
    - Start with `n` red pawns on the left, `n` green pawns on the right
    - Red pawns can only move to the right, green pawns only to the left
- With each move, any pawn can:
    - Move one position forward, if there is a free cell in front
    - Or jump exactly one pawn of the other color, if there is a free cell immediately after
- The application must *automatically* find the moves to reverse the position of all pawns

>

<http://www.cis.upenn.edu/~matuszek/cit594-2012/Pages/backtracking.html>
<br>
<https://github.com/tomamic/backtracking/blob/main/cindy.py>

---

![](http://fondinfo.github.io/images/fun/queens-sol.svg)
# 8 Queens Solutions

- Find all possible solutions using *backtracking*
    - Modify the proposed code
    - Display the number of attempts made and the number of solutions found
- Find all solutions using the *Generate & Test* methodology
    - Simplified version – only one queen per row
    - Display the number of attempts made and the number of solutions found

>

<https://github.com/tomamic/backtracking/blob/main/queens.py>

---

![](http://fondinfo.github.io/images/fun/knights.svg)
# Knight's Domination

- Place knights on the chessboard
- All cells are either *occupied* or *attacked*
- Minimize the number of pieces used
- Solve for different board sizes

>

[Domination problems](https://en.wikipedia.org/wiki/Mathematical_chess_problem#Domination_problems)
<br>
<http://www.contestcen.com/knight.htm>
<br>
<http://oeis.org/A006075/b006075.txt>
