# Relations

## Introduction to programming

-----

# 💡️ Composition

  - **Has-a**, **part-of** association between objects
      - An *arena* can *contain* several *balls*

<!-- end list -->

```py
class BallArena:  # ...
    def __init__(self):
        self._balls = []
    def spawn(self, b: Ball):
        self._balls.append(b)
    def tick(self):
        for b in self._balls:
            b.move()

arena = BallArena()
arena.spawn(Ball(40, 80))
arena.spawn(Ball(80, 40)) # ...
arena.tick()
```

-----

# 💡️ Is-a relationship

  - **Classification**, e.g., in biology
      - *Vertebrates* subclass of *animals*
      - *Mammals* subclass of *vertebrates*
      - *Carnivores* subclass of *mammals*
      - *Felines* subclass of *carnivores*
      - *Cats* subclass of *felines*
  - **Is-a** relationship between classes: each subclass...
      - Inherits characteristics of the base class
      - But introduces specializations

-----

# 🧪 Speaking Farm

  - We will define a *base class* as an **abstract interface**
  - E.g., `Animal`
      - All animals make a sound (*interface*)
      - Each animal makes a different sound (*polymorphism*)

<!-- end list -->

```py
class Animal:
    def speak(self):
        raise NotImplementedError("Abstract method")
```

>

[https://fondinfo.github.io/play/?c07\_animals.py](https://fondinfo.github.io/play/?c07_animals.py)

-----

# 🧪 Concrete Classes

```py
class Dog(Animal):
    def __init__(self, name):
        self._name = name
    def speak(self):
        print("I am", self._name, "Dog.",
              "I say: WOOF!")

class Cat(Animal):
    def __init__(self, name):
        self._name = name
    def speak(self):
        print("I am", self._name, "Cat.",
              "I say: MEOW!")
```

-----

# 🧪 List of objects

```py
d = Dog("Danny")
c = Cat("Candy")
p1 = Pig("Peppa")
p2 = Pig("George")

# a list of Animal objects
animals = [d, c, p1, p2]
for a in animals:
    a.speak()
```

```text
I am Danny Dog. I say: WOOF!
I am Candy Cat. I say: MEOW!
I am Peppa Pig. I say: OINK!
I am George Pig. I say: OINK!
```

-----

# ⭐ Actor Interface

  - `Actor`: *abstract interface*
      - Declares a `move` method, without implementing it
      - `arena` parameter, for context data
      - Other methods: `pos, size, sprite`
  - Various actors: *concrete classes*
      - Implement `Actor` methods, defining specific behaviors
      - Can define additional methods

<!-- end list -->

```py
class Actor:  # …
    def move(self, arena: Arena):
        raise NotImplementedError("Abstract method")
```

>

[https://fondinfo.github.io/play/?actor.py](https://fondinfo.github.io/play/?actor.py)

-----

# 💡️ Generalization and Reuse

```py
class Arena:  # …
    def __init__(self, size):
        self._w, self._h = size
        self._actors = []
    def spawn(self, a: Actor):
        self._actors.append(a)
    def tick(self):
        for a in self._actors:
            a.move(self)
    def size(self):
        return self._w, self._h
```

  - Code dependent only on *abstract interfaces*
  - `Arena` reusable by creating new *concrete classes* that implement `Actor`

-----

# ⭐ Polymorphic Method

  - Can be declared in an *abstract interface*
  - Implemented in different forms in *concrete classes*
  - Different actors can move in different ways

<!-- end list -->

```py
class Ghost(Actor):  # ...
    def move(self, arena: Arena):
        dx = random.choice([-4, 0, 4])
        dy = random.choice([-4, 0, 4])
        arena_w, arena_h = arena.size()
        self._x = (self._x + dx) % arena_w
        self._y = (self._y + dy) % arena_h
```

>

[https://fondinfo.github.io/play/?c07\_bounce.py](https://fondinfo.github.io/play/?c07_bounce.py)
\<br\>\<br\>
[https://docs.python.org/3/library/random.html\#random.choice](https://docs.python.org/3/library/random.html#random.choice)

-----

# 💡️ Substitution

```py
arena = Arena((480, 360))
arena.spawn(Ball((40, 80)))
arena.spawn(Ball((80, 40)))
arena.spawn(Ghost((120, 80)))
arena.spawn(Turtle((80, 80)))
```

  - Liskov **substitution** principle
      - An object of a *derived class* can always be used in place of an object of the *base class*
  - *Has-a* relationship between an `Arena` object and the `Actor` objects it contains
  - *Is-a* relationship between concrete classes (`Ball` and `Ghost`) and interface (`Actor`)

>

[https://en.wikipedia.org/wiki/Liskov\_substitution\_principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)

-----

# Character Animation

-----

# 🧪 Bounce Animation

```py
def tick():
    g2d.clear_canvas()
    for a in arena.actors():
        # Foreground; cut an area from a larger image
        g2d.draw_image("sprites.png", a.pos(),
                            a.sprite(), a.size())

    arena.tick()  # Game logic, move actors
```

>

[https://fondinfo.github.io/play/?c07\_bounce.py](https://fondinfo.github.io/play/?c07_bounce.py)

-----

# 🧪 Keyboard Control

```py
class Turtle(Actor): # ...
    def move(self, arena: Arena):
        keys = arena.current_keys()
        if "ArrowUp" in keys:
            self._y -= self._speed
        elif "ArrowDown" in keys:
            self._y += self._speed
        if "ArrowLeft" in keys:
            self._x -= self._speed
        elif "ArrowRight" in keys:
            self._x += self._speed
```

>

[https://fondinfo.github.io/play/?c07\_bounce.py](https://fondinfo.github.io/play/?c07_bounce.py)

-----



# 🧪 Collisions

  - Many *collision detection* algorithms
      - Simple cases: rectangle intersection
  - `Arena`'s `collisions` method
      - List of colliding characters
  - Possible errors in bounce calculation
      - Usually acceptable
      - Otherwise, apply corrections

-----

# ⭐ Collisions with balls

```py
class Turtle(Actor):
    # ...
    def move(self, arena: Arena):
        for other in arena.collisions():
            if isinstance(other, Ball):
                arena.kill(self)
```

  - `isinstance(obj, cls)`
      - Checks if object `obj` is an instance of class `cls`
      - ... or one of its subclasses
      - Returns a `bool`

-----

# Bounce, game and GUI

  - `BounceGame` : subclass of `Arena` to manage the *Bounce* game
      - Initializes characters
      - Controls positive or negative game conclusion
  - `BounceGui` : class for game representation
      - Drawing images and `g2d`-related functionalities
      - Keyboard and input management, `tick` method, etc.

> [Separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)

[https://fondinfo.github.io/play/?c07\_bouncegame.py](https://fondinfo.github.io/play/?c07_bouncegame.py)

-----

# 🏊 Exercises

-----

# Frog in the arena

  - Make the `Vehicle` class an `Actor`
      - [c05\_vehicle.py](https://fondinfo.github.io/play/?exs/c05_vehicle.py)
      - Add the character to the arena
  - `Frog` class from `Turtle` of `bounce` exercise
  - Count the frames of a frog jump
      - E.g., 4px for 8 frames, then it stops
      - While jumping, it does not accept other commands
  - If it collides with a vehicle, the frog dies
      - Or returns to the starting position

-----

# Aliens in the arena

  - Make the `Alien` class an `Actor`
      - [c05\_alien.py](https://fondinfo.github.io/play/?exs/c05_alien.py)
      - Add the character to the arena
  - Create a `Bullet` actor
      - Starts from the bottom and moves upwards
      - If it goes off-screen, it is removed from the game
      - If it collides with an alien, both are removed from the game
  - In the `tick` function, randomly generate `Bullet`s

-----

# Mario in the arena

  - `Mario` class from `Turtle` of `bounce` exercise
  - Consider gravity acceleration
      - With each move, add a *constant* `g` to `dy` (e.g., `0.5`)
      - Allow `Mario` to jump only when on the ground
  - Add `Wall`, an immobile character
  - When `Mario` collides with a platform...
      - He moves to the nearest edge of the platform
      - If he lands on the top edge, he can jump from there
