![](http://fondinfo.github.io/images/misc/tic-tac-toe.svg)
# Minimax
## Introduction to Programming

---

# Minimax Algorithm

- Used in games, but also for decision-making problems
- Finds the optimal move for one player (called *Max*)
- Assuming that the opponent (called *Min*) also plays optimally
- Each of the two makes the most favorable move for themselves

---

# Minimax Steps

1. Generate the complete game state tree
2. Apply the utility function to all terminal states (leaves of the tree)
3. Starting from the leaves, assign a value to intermediate states
    - Maximum of the children if the move is made by player *Max*
    - Minimum of the children if the move is made by player *Min*
4. Finally, a value is assigned to the first move, by *Max*
    - Maximum utility at the first level of the tree
    - Corresponds to the best move for the player

---

![large](http://fondinfo.github.io/images/fun/tictactoe-minimax.png)
# Full Exploration

- Each node is labeled with *+1* or *-1*
- *Max*'s goal: reach *+1* nodes
- *Min*'s goal: reach *-1* nodes
- Nodes where it's *Max*'s turn to move
    - Label = maximum value of children
- Nodes where it's *Min*'s turn to move
    - Label = minimum value of children

---

![large](http://fondinfo.github.io/images/comp/minimax1.png)
# Min and Max Strategies

- The *Minimax* algorithm traverses the complete game tree
    - Assigns a utility value to every possible *leaf* of the game tree
    - Then recursively updates the utility value of higher nodes
    - The utility value propagates upwards
- *Minimax* ensures the best possible choice
    - Assuming the opponent plays optimally
    - Player *Min* will always make the worst move for player *Max*

---

![large](http://fondinfo.github.io/images/comp/minimax3.png)
# Non-Binary Utility

- In some cases, the result is not binary
    - Result as a numerical score
    - Or, evaluation of a certain game position
- *Max* chooses states with maximum value
- *Min* chooses states with minimum value

---

![large](http://fondinfo.github.io/images/comp/minimax4.png)
# Recursion

- The *Minimax* algorithm calculates the optimal choice for a given game state
- Uses a simple recursive calculation of the utility value of each subsequent state
- Directly implements the mathematical operation `$min$`, or `$max$`
- The recursion proceeds to the bottom of the game state tree
- After reaching the leaf nodes…
    - Values propagated backward, upwards
    - As recursive calls conclude

---

# Minimax Complexity

- *Minimax* algorithm calculates the optimal move for *Max* (first player)
    - Assuming *Min* (opponent) plays a perfect game
- Provides the model for a mathematical analysis of games
    - Basis for developing more practical algorithms
- *Minimax* assumption: possible to generate all terminal states
- Complete depth-first exploration of the game tree
- *Minimax* time complexity: `$O(b^n)$`
    - `$n$`: maximum tree depth
    - `$b$`: legal moves in each state

---

# Search Space

- There are games much more complex than Tic-Tac-Toe
- For example, the game of *chess*
- Branching factor of approximately `$35$`
- Often, games with over `$50$` moves per player
- Search space of `$35^{100}$`
- In reality, only `$10^{40}$` legal positions

---

# Minimax with Heuristics

- Searching for the best move across the entire game tree
    - Not efficient, not practicable
    - Even for games that are not too complicated
    - Reasonably, ~ a few minutes to get a response
- A criterion is needed to make *Minimax* capable of moving
    - Without having to explore the entire game tree
- Possible, by introducing two elements
- ① **Heuristic** evaluation function, which also evaluates the utility of non-terminal states
- ② **Cutoff-Test** to decide at what move level to stop the search

---

# Heuristics

- More interesting and complex games: full exploration impossible
- The utility function is calculated with the help of some heuristic evaluation
- Heuristics are specific to each type of game
- Provide an *estimate* of a configuration's utility
- In the absence of a certain final result

---

# Limited Minimax

- Strategy: look *k* moves ahead (Shannon, 1949)
- The game tree is expanded to depth *k* (level limit)
- Compatible with available time and space
- Reached states are evaluated
- The result is propagated backward using the usual rules

$$
MinimaxValue(n) = \begin{cases}
f(n), level(n) = k \\
max_{s\in succ(n)} MinimaxValue(s), n = MAX \\
min_{s\in succ(n)} MinimaxValue(s), n = MIN
\end{cases}
$$

---

# Evaluation for Chess

- The **evaluation function** provides an estimate of a move's goodness
- For example, for chess: value of the two players' pieces
    - *Pawn*: 1
    - *Knight and Bishop*: 3
    - *Rook*: 5
    - *Queen*: 9
- The termination test tries to stop the search
    - Level that respects the available time limit
- However, abrupt termination of the search can yield poor results
    - Especially if associated with a not very sophisticated evaluation function

---

# More Careful Evaluation

- Piece value
    - Importance of a piece, not constant
    - Depends on its position
    - Depends on the phase of the game
- For example, for a *knight*
    - Central positions more advantageous than corners
    - Positions that threaten enemy pieces are more advantageous
    - Distance from the king has a negative weight
    - Importance decreases as the game progresses

---

# Evaluation Function

- Estimate of expected utility, starting from a certain position in the game
- Fundamental qualities of the function:
- ① Consistent with utility, if applied to terminal states
    - That is, it induces the same *ordering*
- ② Reflects real chances of winning
    - Degree of *confidence* in the winning estimate
    - A has a greater value than B
    - `$\iff$` In A there are more chances of winning than in B
- ③ *Efficient* to calculate

---

# Minimax Code

``` code
function minimax( node, depth, maximizingPlayer ) is
    if depth = 0 or node is a terminal node then
        return the heuristic value of node
    if maximizingPlayer then
        value := −∞
        for each child of node do
            value := max( value, minimax( child, depth − 1, FALSE ) )
        return value
    else (* minimizing player *)
        value := +∞
        for each child of node do
            value := min( value, minimax( child, depth − 1, TRUE ) )
        return value
```

>

<https://en.wikipedia.org/wiki/Minimax>

---

# Negamax Code

``` code
(* color ∈ {-1, 1} *)

function negamax(node, depth, color) is
    if depth = 0 or node is a terminal node then
        return color × the heuristic value of node
    value := −∞
    for each child of node do
        value := max(value, −negamax(child, depth − 1, −color))
    return value
```

<https://en.wikipedia.org/wiki/Negamax>

---

# Cut-off Test

- Facilitate the calculation of *f*
    - *Minimax* algorithm stopped in quiescent configurations
    - First subsequent moves don't change the value much
- Horizon
    - Difficult prediction of very relevant moves
    - Unreachable due to search space limits
    - Invisible to the algorithm
- The *cut-off* is a difficult task

---

# Alpha-Beta

---

# Minimax Optimizations

- Minimax with *limited time*
    - Evaluation function
    - Cut-off
- But it might still not be acceptable
- Possible *ad-hoc* solutions
    - Ordering of possible moves
    - Secondary search to eliminate some branches
    - Focused and in-depth search on certain moves
- Simple, *general* applicability solution
    - *Alpha-Beta Pruning*

---

# Alpha-Beta Pruning

- *Minimax*: search in the tree based on mathematical properties
- But branches that will never be chosen are explored
- The right move can be found…
    - Without trying all moves in the game tree
- Trick to calculate the correct *Minimax* decision…
    - Without fully exploring every branch of the tree
- *Alpha-Beta Pruning* technique
    - If a player can make a move towards a node `$n$`
    - But at a higher level in the tree can make a better choice
    - Then node `$n$` will never be reached

---

# Idea for Pruning

- Game position `$n$`
- If a player has a better choice at the level of node `$m$`
    - With `$m$` being a parent node of `$n$`
    - Or any ancestor node of `$n$`
- `$\implies$` `$n$` will never be reached in a real game
- So, if we eventually discover enough about `$n$`
    - By examining only some of its descendants
    - Then we can immediately prune the entire branch of `$n$`
    - We remove node `$n$` from those to evaluate

---

![large](http://fondinfo.github.io/images/comp/alphabeta-prune.png)
# Nodes Not Actually Useful

- Consider a node `$n$` in the tree
- Will the player move towards that node?
- If there is a better choice
    - At the parent node level
    - At every higher level...
- Then `$n$` will never be reached during the game

---

# α and β Thresholds

- Alpha-Beta pruning is named after the following two parameters
    - They describe the limits recorded for values appearing along the path
- **`$\alpha$`** = highest value found so far by *Max*
    - At any point on the path where *Max* plays
- **`$\beta$`** = lowest value found so far by *Min*
    - At any point on the path where *Min* plays

---

# Updating α and β

- The Alpha-Beta algorithm continuously updates the values of `$\alpha$` and `$\beta$`
- Prunes the branches of a node (i.e., stops recursive calls)
- As soon as the current node's value proves worse
    - Than the `$\alpha$` threshold, for *Max*
    - Than the `$\beta$` threshold, for *Min*
- *Minimax* search is depth-first
    - Only one path is considered at a time
    - Only nodes on that path are in memory

---

# How Alpha-Beta Works

- Let *Max* be the player and *Min* be the opponent
- **`$\alpha$`** is the minimum score obtainable by *Max*
    - Starting from the given position
    - At the beginning of the algorithm, it is `$−\infty$`
    - During the search, `$α :=$` best value obtained by Max
- **`$\beta$`** is the maximum score obtainable by *Min*
    - Starting from the same position
    - At the beginning of the algorithm, it is `$+\infty$`
    - During calculations, `$β :=$` best value obtained by Min

---

# Depth-First Search

- The search is similar to normal *Minimax*
- However, the values of `$\alpha$` and `$\beta$` are updated for each node
    - As the search deepens
- *Minimax* search: depth-first
    - Consider only nodes along a single path in the tree
    - Parameters `$\alpha$` and `$\beta$` calculated for each point on the path
- ⇒ `$α < β$` must always hold
    - When they contradict, prune

---

# Pruning Conditions

- A leaf node has `$\alpha = \beta = f$`
    - Value of the utility function `$f$`
- For a *Max* node
    - `$\alpha$` = greater utility value among child nodes
    - `$\beta$` = `$\beta$` of the parent node
- For a *Min* node
    - `$\alpha$` = `$\alpha$` of the parent node
    - `$\beta$` = smaller utility value among child nodes
- For each node, it should hold that
    - `$\alpha \leq f \leq \beta$`
    - Otherwise, it can be pruned

---

# Utility and Thresholds

- Alpha-beta search updates the values of `$\alpha$` and `$\beta$` at each node
- Prunes branches
- That is, it terminates recursive calls
- When it determines that the value of the current node
- Is worse than `$\alpha$`, for *Max*, or...
- Is worse than `$\beta$`, for *Min*

---

# Search with Pruning 1/4

![large](http://fondinfo.github.io/images/comp/alphabeta1.png)

---

# Search with Pruning 2/4

![large](http://fondinfo.github.io/images/comp/alphabeta2.png)

---

# Search with Pruning 3/4

![large](http://fondinfo.github.io/images/comp/alphabeta3.png)

---

# Search with Pruning 4/4

![large](http://fondinfo.github.io/images/comp/alphabeta4.png)

---

# Alpha-Beta Code for Max

``` code
function alphabeta(node, depth, α, β, maximizingPlayer) is
    if depth = 0 or node is a terminal node then
        return the heuristic value of node
    if maximizingPlayer then
        value := −∞
        for each child of node do
            value := max(value, alphabeta(child, depth − 1, α, β, FALSE))
            if value ≥ β then
                break (* β cutoff *)
            α := max(α, value)
        return value
    else
        (* … *)
```

---

# Alpha-Beta Code for Min

``` code
function alphabeta(node, depth, α, β, maximizingPlayer) is
    if depth = 0 or node is a terminal node then
        return the heuristic value of node
    if maximizingPlayer then
        (* … *)
    else
        value := +∞
        for each child of node do
            value := min(value, alphabeta(child, depth − 1, α, β, TRUE))
            if value ≤ α then
                break (* α cutoff *)
            β := min(β, value)
        return value
```

---

# Negamax Code with α-β

``` code
function negamax(node, depth, α, β, color) is
    if depth = 0 or node is a terminal node then
        return color × the heuristic value of node

    childNodes := generateMoves(node)
    childNodes := orderMoves(childNodes)
    value := −∞
    foreach child in childNodes do
        value := max(value, −negamax(child, depth − 1, −β, −α, −color))
        α := max(α, value)
        if α ≥ β then
            break (* cut-off *)
    return value
```

---

# Effectiveness of Alpha-Beta Pruning

- Effectiveness highly dependent on the order of node analysis
- Advantageous to try examining the most promising nodes first
- *If* nodes can be ordered, then…
    - Alpha-beta needs to examine only `$O(b^{d/2})$` nodes
    - Instead of `$O(b^d)$`, for *Minimax*
    - That is, the effective branching factor becomes `$b^{1/2}=\sqrt{b}$`
- Node reduction
    - From a certain complexity, to its square root
    - The search depth `$d$` can be doubled
- In chess, for example
    - It goes from ~ `$b=35$` to `$b=6$`
    - Sequences of moves of double length are explored
