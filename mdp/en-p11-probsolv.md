![](http://fondinfo.github.io/images/algo/bulb.svg)
# Problem solving
## Introduction to programming

---

# Problems and algorithms

---

![](http://fondinfo.github.io/images/hist/polya.jpg)
# 💡️ Problem solving

- George Polya, [“How to solve it”](https://www.dropbox.com/s/86ua0v7mbr6tkgm/Polya_How-to-solve-it.pdf?dl=1), 1945
- Solving (mathematical) problems: a rarely linear process

> Example. Find the diagonal of a rectangular parallelepiped, given its length, width, and height. *(Polya, p. 23)*

---

![](http://fondinfo.github.io/images/dev/problem-solving.svg) ![](http://fondinfo.github.io/images/algo/space-diagonal.svg)
# 💡 Problem analysis

- **➊ See.** Understand the problem
    - What are the data, the unknowns, the conditions?
    - Figures, notation… *model*

> Everything should be made as simple as possible, but not simpler. *(A. Einstein)*

> For every complex problem there is an answer that is clear, simple… and wrong! *(H.L. Mencken)*

For example, when calculating the diagonal of a parallelepiped, <br> a good figure can provide important hints

---

![](http://fondinfo.github.io/images/dev/problem-solving.svg)
# 💡 From problem to solution

- **➋ Plan.** Devise a plan
    - Relate data and unknowns
    - Reduction, analogy, divide and conquer, composition, abstraction… *Computational thinking*
    - Start by solving a *simpler* problem
- **➌ Do.** Carry out the plan
    - Build the system to be tested

> If you can't solve a problem, then there is an easier problem you can solve: find it. *(G. Polya)*

> [The answer is inside you… (Quelo)](https://www.youtube.com/watch?v=WGQ7JZRZ65M)

---

![](http://fondinfo.github.io/images/dev/problem-solving.svg) ![](http://fondinfo.github.io/images/hist/david-michelangelo.jpg) Michelangelo's David
# 💡 … And Looking Back

- **➍ Check.** Look back at the solution
    - Is it correct? Can it be obtained differently?
    - Is the method useful for other problems?

> I am writing you a long letter because I don't have time to write a short one. *(Voltaire)*

> Perfection is achieved not when there is nothing more to add, but when there is nothing left to take away. *(De Saint-Exupéry)*

> Sculpture is the art of taking away. *(Michelangelo)*

A shorter and clearer solution is obtained after several iterations

---

![large](http://fondinfo.github.io/images/algo/origami.svg) Origami are algorithms
# 💡️ Elements of an algorithm

- 🤖️ *Algorithm*: a procedure that solves a given problem through a finite number of elementary steps (al-Khwarizmi, ~800)
- **Data**: initial (problem instance), intermediate, final (solution)
- **Steps** elementary: atomic actions that cannot be broken down into simpler actions
- **Process**, or execution: an ordered sequence of steps
- *Properties*: finiteness, non-ambiguity, feasibility, efficiency…

>

<https://en.wikipedia.org/wiki/Muhammad_ibn_Musa_al-Khwarizmi>

---

![](http://fondinfo.github.io/images/algo/spaghetti-flowchart.svg)
# 💡️ Flowchart

- **Flowchart**: *directed graph*, nodes + edges
    - Steps of an algorithm + their sequence
- *Graphical* representation instead of verbal
    - More effective, less ambiguous
- Three types of nodes
    - I/O: reading and writing data
    - Arithmetic-logic operations
    - Control of the execution flow

![small](http://fondinfo.github.io/images/algo/nodes.svg)

---

![](http://fondinfo.github.io/images/algo/recipe.png)
# ⭐️ Structured programming

![](http://fondinfo.github.io/images/algo/structures.svg)

> Any algorithm can be implemented using only these structures *(Böhm-Jacopini, 1966)*

> Goto considered harmful *(Dijkstra, 1968)*

- ❗ Structures with: 1 entry, 1 exit
- 🧑‍🍳 Recipes: everyday algorithms, with `if` and `while`
    - “If there is no yeast, use two teaspoons of baking soda”
    - “Beat the egg whites until stiff”


---

# 🧪 Block-based programming

![](http://fondinfo.github.io/images/algo/blockly.png)

>

<https://blockly.games/maze?lang=en>
