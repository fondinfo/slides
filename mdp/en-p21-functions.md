![](http://fondinfo.github.io/images/fun/juicer.svg)
# Functions
## Introduction to programming

---

![](http://fondinfo.github.io/images/fun/function.png)
# ⭐ Function Definition

- *Operator*, applied to *operands*, to obtain a *result*
    - **`def`** to define a function
    - **`return`** to terminate and return a result

``` py
from math import sqrt

def hypotenuse(a, b):
    c = sqrt(a ** 2 + b ** 2)
    return c
```

- Subdivision of a problem into sub-problems
    - Abstraction from implementation
    - Generalization and separation of the solution
    - Calculation based on parameters, model

---

# ⭐ Function Call

- **`def`** defines a function, but does not execute it!
- It must be *called*
- When executed, a function creates a new *namespace*
    - Parameters and variables have **local scope**
    - Not visible in the rest of the program
    - Identical names, defined in different scopes, remain distinct
- ⚠️ Remember to assign the result to a variable
    - ~ glass to collect the juice 🥤

``` py
side1 = float(input("1st side? "))
side2 = float(input("2nd side? "))
side3 = hypotenuse(side1, side2)  # call the function, get the result
print("3rd side:", side3)
```

---

![](http://fondinfo.github.io/images/fun/fun-hypotenuse.svg)
# 💡 Main Function

- Preferable, to limit **global variables**
- *Procedure*, without `return` (`None` result)

``` py
def hypotenuse(a, b):
    c = sqrt(a ** 2 + b ** 2)
    return c

def main():
    side1 = float(input("1st side? "))
    side2 = float(input("2nd side? "))
    side3 = hypotenuse(side1, side2)
    print("3rd side:", side3)

main()  # remove, if importing the module elsewhere
```

>

<https://fondinfo.github.io/play/?c04_hypotenuse.py>

---

![](http://fondinfo.github.io/images/fun/fun-inc.svg)
# ⭐ Function Parameters

- **Formal parameters**: names used in the *definition*
- **Actual parameters**: values passed at the *call*
- Parameters passed “*by object*”
    - External variables: not reassigned
    - Actions on mutable objects: permanent

``` py
def inc(a):
    a += 1  # what's `a` now? print it

def main():
    x = 10
    inc(x)  # what's `x` now? print it

main()
```

---

![](http://fondinfo.github.io/images/oop/anim-right.png)
# ⭐ Animation

``` py
x, y, dx = 50, 50, 4  # sequence unpacking
ARENA_W, ARENA_H = 480, 360

def tick():
    global x, dx
    g2d.clear_canvas()  # Draw background
    g2d.draw_image("ball.png", (x, y))  # Draw foreground
    ##if g2d.mouse_clicked(): ...
    ##if x + dx > ARENA_W: ...
    x += dx  # Update ball's position

g2d.init_canvas((ARENA_W, ARENA_H))
g2d.main_loop(tick)  # call tick 30 times/second
```

>

<https://fondinfo.github.io/play/?c05_anim.py>

---

# 💡 Tick, keyboard and mouse

- **`g2d.main_loop`**: *event handling loop*
    - Optional parameter: function that will be called periodically
- **`g2d.mouse_clicked`**: *check if the left mouse button has been clicked*
    - Result: `bool`
- **`g2d.mouse_pos`**: *mouse position*
    - Result: `Point`
- **`g2d.current_keys`**: *all currently pressed keys*
    - Result: sequence of `str` – [Possible values](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values)
    - Ex.: `"q", "1", "ArrowLeft", "Enter", "Spacebar", "LeftButton"`
- **`g2d.close_canvas`**: *closes the canvas, terminates execution*

>

[**g2d Documentation**](https://github.com/fondinfo/fondinfo#g2d)

---

![](http://fondinfo.github.io/images/hist/mcnulty.png) Kay McNulty <br> Subroutine for ENIAC
# 💡 Function Documentation

- **Annotations**: useful for documenting the type of parameters and result
    - But no verification!
- **Docstring**: textual description of a function
- **`help`**: function to display documentation

``` py
def hypotenuse(leg1: float, leg2: float) -> float:
    '''
    Return the hypotenuse of a right triangle,
    given both its legs (catheti).
    '''
    return sqrt(leg1 ** 2 + leg2 ** 2)

---

# 💡 Functions in Modules

- Each Python file is a *module*: file name, without `.py`
- If imported elsewhere, `main` execution under condition

``` py
# file `mymath.py`
def hypotenuse(leg1: float, leg2: float) -> float:
    return sqrt(leg1 ** 2 + leg2 ** 2)

def main():  # Use or test the hypotenuse function
    print(hypotenuse(3, 4))

if __name__ == "__main__":  # file executed directly, or imported?
    main()  # `main` not called, if file imported as module
```

``` py
>>> import mymath  # nothing printed
>>> mymath.hypotenuse(4, 3)
5
```

---

# 💡 Error Conditions

- Preconditions for activation not met
- ⇒ Error, **`raise`** statement
- Ex. Invalid triangle

``` py
def triangle_perimeter(a: float, b: float, c: float) -> float:
    if a > b + c or b > a + c or c > a + b:
        raise ValueError("Not a triangle")
    return a + b + c

print(triangle_perimeter(4, 2, 1))
```

---

# 🧪 Result in Tuple

``` py
def divmod_(a: int, b: int) -> tuple[int, int]:
    quotient = a // b
    reminder = a % b
    return (quotient, reminder)  # ❗ return a tuple

result = divmod_(5, 2)  # a tuple
q, r = result  # ❗ sequence unpacking
```

>

<https://docs.python.org/3/library/functions.html#divmod>

---

# 🧪 Multiple Returns

- A function can have multiple `return` statements
- At the first one encountered, execution terminates and control returns to the calling code
- Acceptable violation of structured programming

``` py
def exceeds(data: list[int], limit: int) -> bool:
    for v in data:
        if v > limit:
            return True
    return False
```

- Conversely, if no explicit `return` with a result is encountered…
- Implicit result `None`: “*no value*”

---

![](http://fondinfo.github.io/images/oop/anim-bounce.png)
# 🧪 Bounce Function

- Functions provide limited abstraction
    - Encapsulate behavior
    - ❗ But expose data

``` py
def move_ball(x: int, y: int,
              dx: int, dy: int) -> tuple[int, int, int, int]:
    if not 0 <= x + dx <= ARENA_W - BALL_W:
        dx = -dx
    if not 0 <= y + dy <= ARENA_H - BALL_H:
        dy = -dy
    x += dx
    y += dy
    return (x, y, dx, dy)
```

>

<https://fondinfo.github.io/play/?c05_move.py>

---

# 💡 Side Effects

- Modification of objects passed as parameters or global variables, read/write operations...
- Nullify **referential transparency**
    - Impossible to simplify by replacing a function call with its return value (e.g., if I/O operations are present)
- Make the function **non-idempotent**
    - Called multiple times with the same parameters, it returns different results
- → Difficult to perform mathematical verifications
    - `z = f(sqrt(2), sqrt(2))`
    - `s = sqrt(2)` <br> `z = f(s, s)`

---

# 💡 Non-Idempotent Functions

- Example of simplification
    - `p = g(x) + g(y) * (g(x) - g(x))`
    - `p = g(x) + g(y) * (0)`
    - `p = g(x) + 0`
    - `p = g(x)`
- But if `g` has side effects, it cannot be done!

``` py
base_value = 0  # global variable

def g(x: int) -> int:
    global base_value
    base_value += 1
    return x + base_value
```

>

For example, with `x = 3` and `y = 4` the two results are `-2` and `4`

---

# Trigonometric Functions

---

![](http://fondinfo.github.io/images/fun/sin-cos-tan-1.svg) ![](http://fondinfo.github.io/images/fun/sin-cos-tan-2.svg)
# 🧪 Polar Coordinates

- Given hypotenuse and angle of a right triangle
    - With `cos` and `sin` the legs can be derived
- On the Cartesian plane (or *raster*)
    - $x$ adjacent leg, $y$ opposite, $r$ hypotenuse
- **Polar coordinates** of a point: `$(r, \theta)$`
    - Distance from origin and angle
- Polar coords `$(r, \theta)$` ⇒ Cartesian `$(x, y)$`
    - `$\begin{cases}x = r\cdot cos\theta \\ y = r\cdot sin\theta\end{cases}$`
- Cartesian coords `$(x, y)$` ⇒ Polar `$(r, \theta)$`
    - `$\begin{cases}r = \sqrt{x^2 + y^2} = hypot(x, y) \\ \theta = atan2(y, x)\end{cases}$`

>

<https://github.com/tomamic/fondinfo/wiki/P03-Funzioni#coordinate-polari>

---

![](http://fondinfo.github.io/images/fun/move-around.svg)
# 🧪 Rays on Canvas

- Displacement `$(r, \theta)$` relative to `$(x_0, y_0)$`
    - *Translation*
- In `math` module, useful functions and constants
    - `sin, cos, radians, pi`
    - `hypot, atan2, dist`
- Ex. 4 rays: same center, same radius, different angles

``` py
def draw_rays(x0: int, y0: int, r: int):
    for angle in [0, 15, 30, 45]:
        x = x0 + r * cos(radians(angle))
        y = y0 + r * sin(radians(angle))
        g2d.draw_line((x0, y0), (x, y))
```

>

<https://fondinfo.github.io/play/?c04_angles.py>

---

![](http://fondinfo.github.io/images/fun/move-around.svg)
# Functions on Polar Coordinates

- More general functions, better abstraction

```
Point = tuple[float, float]  # Pt in cartesian coords (x, y)
Polar = tuple[float, float]  # Pt in polar coords (r, angle)

def from_polar(plr: Polar) -> Point:
    r, angle = plr
    a = polar(angle)
    return (r * cos(a), r * sin(a))

def move_around(start: Point, length: float, angle: float) -> Point:
    x0, y0 = start
    dx, dy = from_polar((length, angle))
    return (x0 + dx, y0 + dy)
```

- ❓ Rewrite `draw_rays` using `move_around`

>

<https://fondinfo.github.io/play/?polar.py>

---

# 🏊 Exercises on Functions

---

![](/images/misc/thermometer.png)
# Function, Fahrenheit

- Define a function `cels_to_fahr`
    - Parameter: Celsius temperature, as `float`
    - Result: Fahrenheit temperature, as `float`
- Invoke the function from the interactive shell
- Then define a `main` function
    - *Procedure, without parameters and without result*
    - Ask the user for the Celsius temperature
    - Then call `cels_to_fahr`
    - Finally show the user the result

>

Start from the formula `fahr = cels * 1.8 + 32`

---

![](http://fondinfo.github.io/images/misc/ellipse.svg)
# Area of an Ellipse

- Define an *ellipse_area* function that:
    - Receives the semi-axes of an ellipse as *parameters*: <br>`a`, `b`
    - Returns the area of the ellipse as a result: <br>`π⋅a⋅b`
- Define a *main* function that:
    - Asks the user for two values
    - Invokes the `ellipse_area` function with these parameters
    - Prints the obtained result

---

![](http://fondinfo.github.io/images/misc/triangle-notations.svg)
# Perimeter of a Triangle

- Define a *triangle_perimeter* function that:
    - Receives the three sides of a triangle as *parameters*: <br>`a`, `b`, `c`
    - Returns the perimeter of a triangle as a result
    - If the three sides do not form a triangle, it raises a `ValueError` <br> (if one of the sides is greater than the sum of the other two)
- Define a *main* function that, cyclically:
    - Asks the user for three values
    - Shows the result of `triangle_perimeter` with these parameters
    - Asks the user if they want to process more data, or terminate

---

# Groups of Letters

- Define a function `count_groups`
    - Text parameter (`str`)
- Result: two values
    - How many letters in the text are in the *A-M* group
    - How many letters in the text are in the *N-Z* group
- The `count_groups` function does not distinguish between uppercase and lowercase letters
- Call the `count_groups` function with user-provided text and show the results

---

![](http://fondinfo.github.io/images/fun/comb-lock.svg)
# Three-Letter Words

- Write a function with a `str` type parameter
    - The string represents an alphabet of valid characters
- Generates the list of all words
    - Exactly 3 characters long
    - Composed only of those characters
- If the alphabet contains repeated letters, raise a `ValueError`

---

![](http://fondinfo.github.io/images/misc/perfect-squares.svg)
# Perfect Square

- Write a function `perfect_square`
    - Parameter: a number
    - Checks if it is a *perfect square*
    - Is its square root a natural number?
- Result: boolean, followed by a number
    - Perfect root of the number, if it exists
- `main` function to run `perfect_square`
    - On a number provided by the user
    - Show the result

>

Do not use `math.sqrt` and similar — Solve with iteration

---

# Common Divisors

- Define a function `common_divisors`
    - Takes two natural numbers as parameters
    - Returns a list with all common divisors of the two numbers
- `main` function to run `common_divisors`
    - On numbers provided by the user
    - Show the result

---

![](http://fondinfo.github.io/images/fun/polygon.svg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# Drawing a Polygon

- Define a function `draw_polygon`
    - Parameters: number of sides, center and radius of the circumscribed circle
    - Find the vertices around the center with `move_around`
    - Connect the vertices to draw the polygon

---

![](http://fondinfo.github.io/images/misc/classical-watch.jpg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# Classic Clock

- Define a function `draw_clock`
    - Draw 12 radial marks, like on a classic clock
    - Improvement: also draw smaller minute marks

---

# 🏊 Exercises on Animations

---

![](http://fondinfo.github.io/images/draw/random-circles.svg)
# Circles on Click

- Define a `tick` function
- When the mouse is clicked…
- If the mouse is near the center of the canvas…
    - Ask the user for confirmation
    - If confirmed, close the application
- Otherwise…
    - Draw a circle at the click position
    - With fixed radius and random color

---

![](http://fondinfo.github.io/images/misc/frogger.png)
# Horizontal Vehicle

- Show a turtle moving horizontally
    - Var. `dx`: displacement per frame
- When it exits one edge, it reappears from the opposite edge, after a while
    - Allow crossing the side edges
    - If it crosses 100px past the right edge, it reappears 100px before the left edge and vice versa
- On mouse click, the turtle reverses direction
- Crop the image from `sprites.png`

``` py
g2d.draw_image("sprites.png", (x, y), (0, 20), (20, 20))
```

>

<https://github.com/fondinfo/fondinfo#images-and-sounds>

---

![](http://fondinfo.github.io/images/misc/space-invaders-school.png)
# Alien

- Show an alien moving in a serpentine pattern
- Normally it moves only horizontally
- When it reaches a side edge…
    - The alien drops a few pixels
    - Reverses its horizontal direction
- Avoid diagonal movements
    - When the alien descends, it does not move horizontally
    - When it moves horizontally, it does not descend
- Crop the ghost image from `sprites.png`

``` py
g2d.draw_image("sprites.png", (x, y), (20, 0), (20, 20))
```

---

![](http://fondinfo.github.io/images/misc/bouncing-ball.jpg)
# Bounces with Gravity

- Using the `tick` function and global variables, show a ball moving and bouncing off the edges
    - The ball undergoes constant downward acceleration
    - At each frame, add a small constant to `dy`
    - Similar to the effect of gravity

---

![](http://fondinfo.github.io/images/misc/frogger.png)
# Movement for 5 Frames

- Show a ball moving vertically
    - Variable `dy` indicates the displacement to be made at each frame
- The ball moves only after a mouse click
    - It moves only for 5 frames
    - Then it stops until a new press
- Reverse direction at each start of movement

>

Increment (or decrement) a counter at each call to `tick`

---

![](http://fondinfo.github.io/images/fun/polygon.svg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# Rotating Polygon

- Asks the user for a number $n$
- Show a regular polygon of $n$ sides rotating in the center of the canvas
- Hint
    - Reuse the `draw_polygon` function, already requested in a function exercise
    - Rotation, by varying the last parameter of the function (angle of the first vertex)

---

![](http://fondinfo.github.io/images/games/climbing.svg)
# Free Climbing

- Race between two climbers, in graphic form
- Two competitors, starting from the bottom of the canvas
- The first to reach the top of the canvas wins
- In the periodic `tick` function, generate two random numbers
    - Each number $∈ [-1, 3]$
    - Jump up (or small descent) for each competitor
    - Competitors' positions always within canvas limits
- Draw a circle or an image at each competitor's position
