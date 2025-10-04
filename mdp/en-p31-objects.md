![](http://fondinfo.github.io/images/oop/basic-object.svg)
# Objects
## Introduction to Programming

---

![](http://fondinfo.github.io/images/dev/abstraction.png)
# 💡️ Abstract Thinking

- **Abstraction**, from "*ab trahere*" = to pull away ✂️
    - Disregarding inessential, accidental details
    - Reasoning on a concept or *model*, instead of on reality
    - E.g., maps do not represent every stone or leaf
- → *Generalization*
    - Attributing common characteristics of the concept to all instances
- Fundamental for describing and realizing *complex software systems*
    - Levels of abstraction, to encapsulate details 📦
    - Generic, reusable structures and algorithms ♻️

>

https://it.wikipedia.org/wiki/Astrazione_(filosofia)
<br>
https://thevaluable.dev/abstraction-type-software-example/

---

# 💡️ The map is not the territory

![large](http://fondinfo.github.io/images/dev/map-levels.png)

---

![](http://fondinfo.github.io/images/oop/basic-object.svg)
# 💡️ Object

- Represents a *physical object* or a *concept* from the domain
- Stores its internal **state** in *private fields*
    - *Encapsulation (black box)*
- Offers a set of **services**, as *public methods*
    - Implements an *abstract data type (ADT)*

---

![](http://fondinfo.github.io/images/oop/cookie-cutter.png)
# 💡️ Classes and objects

- Every *object* has an **origin class**
    - The class gives the same initial form (fields and methods) to all its objects
- But every *object* has its own **identity**
    - State and memory location distinct from those of other objects
    - Both instances of different classes and of the same class

---

![](http://fondinfo.github.io/images/oop/ball-object.svg) ![](http://fondinfo.github.io/images/oop/ball-uml.svg) UML Class diagram
# ⭐ Class Definition

- Data **Encapsulation**: *naming convention*
    - `_` prefix for *private field* names

> We're all consenting adults here. *(GvR)*

``` py
class Ball:  # …
    def __init__(self, x0: int, y0: int):
        self._x = x0
        self._y = y0
        self._dx, self._dy = 4, 4
```

- We define all the fields necessary for the ball
    - Complete representation of its state
    - ⇒ `self._x, self._y, self._dx, self._dy`

---

![](http://fondinfo.github.io/images/oop/bob-builder.jpg)
# ⭐ Object Construction

- **`__init__`** : *constructor* method
    - Automatically executed upon object creation
    - *Instantiation is initialization*
- **`self`** : first parameter of all methods
    - Represents the *object* on which to perform the operation
    - Allows methods to access fields
    - No explicit value needs to be passed
- Other parameters, after `self` : we decide them
    - We don't want to create all balls in the same position
    - ⇒ Parameters `x0, y0`

``` py
ball = Ball(40, 80)  # Allocation and initialization
```

---

![](http://fondinfo.github.io/images/oop/anim-bounce.png)
# ⭐ Methods

- Expose *services* to other objects
- *Getter* methods : do not modify state

``` py
ARENA_W,ARENA_H, BALL_W,BALL_H = 480,360, 20,20

class Ball:  # …
    def move(self):
        if not 0 <= self._x + self._dx <= ARENA_W - BALL_W:
            self._dx = -self._dx
        if not 0 <= self._y + self._dy <= ARENA_H - BALL_H:
            self._dy = -self._dy
        self._x += self._dx
        self._y += self._dy

    def pos(self) -> (int, int):  # getter
        return self._x, self._y
```

---

![](http://fondinfo.github.io/images/oop/balls.png)
# ⭐ Using Objects

``` py
# Create two objects, instances of Ball class
b1 = Ball(140, 180)
b2 = Ball(180, 140)

b1.move()
b2.move()

print("b1 @", b1.pos())
print("b2 @", b2.pos())
```

- In its *private fields*, each object stores all its state
    - We use fields instead of global variables
    - `self._x, self._y, self._dx, self._dy`

>

<https://fondinfo.github.io/play/?c06_ball.py>

---

# 🔬 The first parameter, self

- The first parameter of every method is called `self` (by convention)
- The value of `self` is *automatically* assigned
- It represents the *object* on which the method is invoked
- In Python, a method call is interpreted as follows:

``` py
b1 = Ball(140, 180)
b1.move()
```

``` py
# ⚠️ Python internals, DON'T do this!
b1 = object.__new__(Ball)
Ball.__init__(b1, 140, 180)
Ball.move(b1)
```

---

# 🧪 Animation of two balls

``` py
b1 = Ball(140, 180)
b2 = Ball(180, 140)

def tick():
    g2d.clear_canvas()
    g2d.draw_image("ball.png", b1.pos())
    g2d.draw_image("ball.png", b2.pos())
    b1.move()
    b2.move()

def main():
    g2d.init_canvas((ARENA_W, ARENA_H))
    g2d.main_loop(tick)
```

>

<https://fondinfo.github.io/play/?c06_ball.py>

---

# 🧪 Methods with parameters

- Method for multiple consecutive movements
- `n`: method parameter
    - Not a characteristic of the ball
    - But a choice of who uses the object
- The call requires an actual parameter

``` py
class Ball:
    # …
    def multiple_move(self, n: int):
        for i in range(n):
            self.move()

b1 = Ball(40, 40)
b1.multiple_move(3)
b1.multiple_move(2)
```

---

# 💡️ Local variables, parameters, fields

- *Fields*: store the characteristic data of an instance
    - Each ball has its position `(self._x, self._y)` <br> and its velocity `(self._dx, self._dy)`
- *Parameters*: pass other values to a method
    - If some necessary data is not in the fields
- *Local variables*: store partial results
    - Generated during method processing
    - Names deleted after method exit
- *Global variables*: defined outside all functions
    - Use only if strictly necessary
    - Better to have a few more parameters for functions

---

![](http://fondinfo.github.io/images/misc/slope.svg)
# 🧪 Linear Model

``` py
class LinearModel:
    def __init__(self, slope: float,
                 intercept: float):
        self._a = slope
        self._b = intercept

    def predict(self, x: float) -> float:
        return self._a * x + self._b
```

---

# 🧪 Using the model

``` py
def main():
    slope = float(input("Slope? "))
    intercept = float(input("Intercept? "))
    model = LinearModel(slope, intercept)

    line = input("x? ")
    while line != "":
        x = float(line)
        y = model.predict(x)
        print("y:", y)
        line = input("x? ")
```

<https://fondinfo.github.io/play/?c06_linmodel.py>

---

![](http://fondinfo.github.io/images/misc/hiccup.png)
# 🧪 D&D Character

- Let's consider a fantasy character
- Has a distinctive name
- Starts the game with a random number of "hit points"

``` py
class Fighter:
    def __init__(self, name: str):
        self._name = name
        self._hp = randint(15, 30)  # hit points

    def describe(self) -> str:
        return f"I'm {self._name}. I have {self._hp} hit points."
```

---

# 🧪 Managing points

- When hit, the character loses some points
- When healed, they regain some
- The character dies when they run out of hit points
- Cannot be healed anymore

``` py
class Fighter: # …
    def hit(self, damage: int) -> None:
        self._hp = max(self._hp - damage, 0)

    def heal(self, cure: int) -> None:
        if self.alive():
            self._hp = min(self._hp + cure, 30)

    def alive(self) -> bool:
        return self._hp > 0
```

---

# Using the character

- The constructor only requires the name
- We inflict three random hits and one random cure

``` py
c = Fighter("Hero")
print(c.describe())

for _ in range(3):
    c.hit(randint(5, 10))
    print(c.describe())

c.heal(randint(5, 10))
print(c.describe())

print(c.alive())
```

<https://fondinfo.github.io/play/?c06_dnd.py>

---

![](http://fondinfo.github.io/images/fun/shopping-list.png)
# ⭐ List

- *Mutable* sequence of *homogeneous* values

``` py
groceries = ["spam", "eggs", "beans"]
groceries.append("sausage")  # add "sausage" at the end
print(len(groceries))  # 4
groceries.remove("eggs")  # remove "eggs"
print(len(groceries))  # 3

for product in groceries:
    print(product.capitalize())
```

- `for` statement for looping over sequences of values
- Each string is an object, of class `str`
- `capitalize` is a method of the `str` class

---

# 🧪 List of objects

- A list can contain any type of data
- Useful for managing numerous balls
- `move` call in a `for` loop

``` py
from p04_ball import Ball, ARENA_W, ARENA_H

def tick():
    g2d.clear_canvas()  # BG
    for b in balls:
        b.move()
        g2d.draw_image("ball.png", b.pos())  # FG

balls = [Ball(40, 80), Ball(80, 40), Ball(120, 120)]
g2d.init_canvas((ARENA_W, ARENA_H))
g2d.main_loop(tick)
```

>

<https://fondinfo.github.io/play/?c06_balls.py>

---

# Creating the list

``` py
balls = [Ball(40, 80), Ball(80, 40), Ball(120, 120)]
```

``` py
b1 = Ball(40, 80)
b2 = Ball(80, 40)
b3 = Ball(120, 120)
balls = [b1, b2, b3]
```

``` py
balls = []
balls.append(Ball(40, 80))
balls.append(Ball(80, 40))
balls.append(Ball(120, 120))
```

<https://fondinfo.github.io/play/?c06_balls.py>

---

![](https://raw.githubusercontent.com/fondinfo/fondinfo/master/sprites.png)
# Ghost Character

- Every now and then it disappears or reappears (changing *sprite*)

``` py
class Ghost:  # …
    def __init__(self):
        self._w, self._h = 20, 20
        self._x, self._y = ARENA_W // 2, ARENA_H // 2
        self._visible = True

    def sprite(self):
        if self._visible:
            return 20, 0
        return 20, 20
```

- `sprite` method: where the desired *sprite* is located
    - Within the overall image

---

# Random direction

- With each move, it chooses a completely random direction
    - Local variables `dx`, `dy`, *not fields*

``` py
class Ghost:  # …
    def move(self):
        dx = choice([-4, 0, 4])
        dy = choice([-4, 0, 4])
        self._x = (self._x + dx) % ARENA_W
        self._y = (self._y + dy) % ARENA_H

        if randrange(100) == 0:
            self._visible = not self._visible
```

- ❓ Why is the modulo operator `%` used?
- ❓ How to limit the choice to only the 4 main directions ↔↕?

---

# Choosing the sprite

``` py
ghosts = []
for _ in range(5):
    ghosts.append(Ghost())

def tick():
    g2d.clear_canvas()
    for g in ghosts:
        # Draw a clip from a larger image
        g2d.draw_image("sprites.png", g.pos(), g.sprite(), g.size())
        g.move()
```

<https://fondinfo.github.io/play/?c06_ghost.py>

- `g2d.draw_image` draws a portion of an image
    - Inefficient to load many separate images

---

# 🏊 Exercises

---


![](http://fondinfo.github.io/images/misc/ellipse.svg)
# Ellipse Class

- Class that models an ellipse
- Private fields (constructor parameters)
    - Semiaxes: `a, b`
- Public methods to get...
    - Area: `$A = \pi \cdot a \cdot b$`
    - Focus: `$c = \sqrt{|a^2 - b^2|}$`
- In the main program body...
    - Create an object with user-provided data
    - Display the area and focal distance of the ellipse

---

# Quadratic Model

- Create a class to represent a single-variable quadratic model
    - Of the type: $y = a \cdot x^2 + b \cdot x + c$
    - Initialize coefficients in the constructor
- Then define a `predict` method, which provides the output $y$ of the model
    - Corresponding to a certain value of $x$
    - $x$ passed as a parameter

>

Start from the linear model example

---

# Two-variable Model

- Create a class to represent a linear model with two variables
    - Of the type: $z = a \cdot x + b \cdot y + c$
    - Initialize coefficients in the constructor
- Then define a `predict` method, which provides the output $z$ of the model
    - Corresponding to certain values of $x$ and $y$
    - $x$ and $y$ passed as parameters

>

Start from the linear model example

---

![](http://fondinfo.github.io/images/misc/frogger.png)
# Vehicle Animation

- Create a `Vehicle` class
    - Start from the `Ball` class seen in the lesson
    - However, movement is only horizontal
- If the vehicle passes 100px beyond the right edge...
    - It reappears 100px before the left edge
- If the vehicle passes 100px beyond the left edge...
    - It reappears 100px after the right edge
- Animate two vehicles
    - One moving to the right (→)
    - The other to the left (←)
    - Represent each vehicle with a rectangle

---

![](http://fondinfo.github.io/images/misc/space-invaders-school.png)
# Alien Animation

- Create an `Alien` class
    - Start from the `Ball` class seen in the lesson
    - However, basic movement is only horizontal
- Upon reaching the edge, the character:
    - Moves a few pixels downwards
    - Then changes horizontal direction
- Ensure that, in each frame, the movement is only horizontal, or only vertical, but *not* diagonal

---

![](https://raw.githubusercontent.com/fondinfo/fondinfo/master/sprites.png)
# Ghost with Count

- Start from the `Ghost` class seen in the lesson
- The ghost is normally stationary
- Randomly, with probability $\frac{1}{100}$, it starts moving
    - Chooses a random direction <br> (horizontal, vertical, or diagonal)
    - Maintains the same direction for 10 frames
    - Then stops again
- While the ghost is moving, it is semi-transparent
    - Otherwise, it is visible
- Add counter and direction fields to the ghost

---

![](http://fondinfo.github.io/images/games/viewport.svg)
# View Scrolling

- Set a large space for character movements (`ARENA_W, ARENA_H`)
- Create a smaller drawing canvas (`VIEW_W, VIEW_H`)
    - Only a portion of the arena is shown
- Allow the user to move the *view* on the arena
    - Using arrow keys

---

![](http://fondinfo.github.io/images/draw/spiral-circles.svg)
# 🥷 Object Spiral

- Show a moving circle
- Spiral path, in $N$ steps
    - The circle rotates around the center of the canvas
    - At increasing distance from the center of the canvas
    - Circle radius: increasing
    - Color: from red to blue
- Create a class for the circle
    - `move` method for one-step movement
    - *Getter* methods for position, radius, and color
    - Counter field; if it exceeds limit $N$, it returns to 0
