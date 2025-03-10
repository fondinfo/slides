![](http://fondinfo.github.io/images/oop/lego-blocks.png)
# Relazioni
## Introduzione alla programmazione

---

![](http://fondinfo.github.io/images/oop/ball-arena.svg)
# 💡️ Composizione

- Associazione **has-a**, **part-of** tra oggetti
    - Una *arena* può *contenere* diverse *palline*

``` py
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

---

![large](http://fondinfo.github.io/images/oop/carnivora.png)
# 💡️ Relazione is-a

- **Classificazione**, es. in biologia
    - *Vertebrati* sottoclasse di *animali*
    - *Mammiferi* sottoclasse di *vertebrati*
    - *Carnivori* sottoclasse di *mammiferi*
    - *Felini* sottoclasse di *carnivori*
    - *Gatti* sottoclasse di *felini*
- Relazione **is-a** tra classi: ogni sottoclasse...
    - Eredita i caratteri della classe base
    - Ma introduce delle specializzazioni

---

![large](http://fondinfo.github.io/images/oop/animals.png)
# 🧪 Fattoria parlante

- Noi definiremo una *classe base* come **interfaccia astratta**
- Es. `Animal`
    - Tutti gli animali fanno un verso (*interfaccia*)
    - Ogni animale fa un verso diverso (*polimorfismo*)

``` py
class Animal:
    def speak(self):
        raise NotImplementedError("Abstract method")
```

>

<https://fondinfo.github.io/play/?c07_animals.py>

---

![large](http://fondinfo.github.io/images/oop/farm.svg)
# 🧪 Classi concrete

``` py
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

---

![large](http://fondinfo.github.io/images/oop/peppa.png)
# 🧪 Lista di oggetti

``` py
d = Dog("Danny")
c = Cat("Candy")
p1 = Pig("Peppa")
p2 = Pig("George")

# a list of Animal objects
animals = [d, c, p1, p2]
for a in animals:
    a.speak()
```

``` text
I am Danny Dog. I say: WOOF!
I am Candy Cat. I say: MEOW!
I am Peppa Pig. I say: OINK!
I am George Pig. I say: OINK!
```

---

![](http://fondinfo.github.io/images/oop/actor.svg)
# ⭐ Interfaccia dei personaggi

- `Actor`: *interfaccia astratta*
    - Dichiara un metodo `move`, senza implementarlo
    - Parametro `arena`, per dati del contesto
    - Altri metodi: `pos, size, sprite`
- Vari attori: *classi concrete*
    - Realizzano i metodi di `Actor`, definendo i comportamenti specifici
    - Possono definire ulteriori metodi

``` py
class Actor:  # …
    def move(self, arena: Arena):
        raise NotImplementedError("Abstract method")
```

>

<https://fondinfo.github.io/play/?actor.py>

---

# 💡️ Generalizzazione e riuso

``` py
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

- Codice dipendente solo da *interfacce astratte*
- `Arena` riutilizzabile creando nuove *classi concrete*, che implementano `Actor`

---

# ⭐ Metodo polimorfo

- Può essere dichiarato in una *interfaccia astratta*
- Implementato in forme diverse nelle *classi concrete*
- Attori diversi possono muoversi in modo diverso

``` py
class Ghost(Actor):  # ...
    def move(self, arena: Arena):
        dx = random.choice([-4, 0, 4])
        dy = random.choice([-4, 0, 4])
        arena_w, arena_h = arena.size()
        self._x = (self._x + dx) % arena_w
        self._y = (self._y + dy) % arena_h
```

>

<https://fondinfo.github.io/play/?c07_bounce.py>
<br><br>
<https://docs.python.org/3/library/random.html#random.choice>

---

![](http://fondinfo.github.io/images/oop/actors.svg)
# 💡️ Sostituzione

``` py
arena = Arena((480, 360))
arena.spawn(Ball((40, 80)))
arena.spawn(Ball((80, 40)))
arena.spawn(Ghost((120, 80)))
arena.spawn(Turtle((80, 80)))
```

- Principio di **sostituzione** di Liskov
    - Si può sempre usare un oggetto di una *classe derivata*, al posto di uno della *classe base*
- Relazione *has-a* tra un oggetto `Arena` e gli oggetti `Actor` che contiene
- Relazione *is-a* tra classi concrete (`Ball` e `Ghost`) e interfaccia (`Actor`)

>

https://en.wikipedia.org/wiki/Liskov_substitution_principle

---

# Animazione dei personaggi

---

![](http://fondinfo.github.io/images/oop/bounce.png)
# 🧪 Animazione dei rimbalzi

``` py
def tick():
    g2d.clear_canvas()
    for a in arena.actors():
        # Foreground; cut an area from a larger image
        g2d.draw_image("sprites.png", a.pos(),
                            a.sprite(), a.size())

    arena.tick()  # Game logic, move actors
```

>

<https://fondinfo.github.io/play/?c07_bounce.py>

---

# 🧪 Controllo da tastiera

``` py
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

<https://fondinfo.github.io/play/?c07_bounce.py>

---

![](http://fondinfo.github.io/images/oop/collision.svg) ![](http://fondinfo.github.io/images/oop/reflection.png)
# 🧪 Collisioni

- Molti algoritmi di *collision detection*
    - Casi semplici: intersezione di rettangoli
- Metodo `collisions` di `Arena`
    - Lista di personaggi in collisione
- Possibili errori nel calcolo del rimbalzo
    - Di solito accettabili
    - Altrimenti, applicare correzioni

---

# ⭐ Urti con palline

``` py
class Turtle(Actor):
    # ...
    def move(self, arena: Arena):
        for other in arena.collisions():
            if isinstance(other, Ball):
                arena.kill(self)
```

- `isinstance(obj, cls)`
    - Controlla se l'oggetto `obj` è istanza della classe `cls`
    - ... o di una sua sottoclasse
    - Restituisce un `bool`

---

![](http://fondinfo.github.io/images/oop/bounce.png)
# Bounce, gioco e GUI

- `BounceGame` : sottoclasse di `Arena` per gestire il gioco *Bounce*
    - Inizializza i personaggi
    - Controlla la conclusione della partita, positiva o negativa
- `BounceGui` : classe per la rappresentazione del gioco
    - Disegno immagini e funzionalità legate a `g2d`
    - Gestione della tastiera e dell'input, metodo `tick` etc.

> [Separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)

<https://fondinfo.github.io/play/?c07_bouncegame.py>

---

# 🏊 Esercizi

---

![](http://fondinfo.github.io/images/misc/frogger.png)
# Rana nell'arena

- Rendere la classe `Vehicle` un `Actor`
    - [c05_vehicle.py](https://fondinfo.github.io/play/?exs/c05_vehicle.py)
    - Aggiungere il personaggio all'arena
- Classe `Frog` da `Turtle` dell'es. `bounce`
- Conteggiare i frame di un salto della rana
    - Es. 4px per 8 frame, poi si ferma
    - Mentre è in salto, non accetta altri comandi
- Se si scontra con un veicolo, la rana muore
    - Oppure torna alla posizione di partenza

---

![](http://fondinfo.github.io/images/misc/space-invaders-school.png)
# Alieni nell'arena

- Rendere la classe `Alien` un `Actor`
    - [c05_alien.py](https://fondinfo.github.io/play/?exs/c05_alien.py)
    - Aggiungere il personaggio all'arena
- Creare un attore `Bullet`
    - Parte dal fondo e si muove verso l'alto
    - Se esce dallo schermo, si rimuove dal gioco
    - Se si scontra con un alieno, entrambi si rimuovono dal gioco
- Nella funzione `tick`, generare casualmente dei `Bullet`

---

![](http://fondinfo.github.io/images/misc/super-mario.jpg)
# Mario nell'arena

- Classe `Mario` da `Turtle` dell'es. `bounce`
- Considerare l'accelerazione di gravità
    - A ogni mossa, aggiungere *costante* `g` a `dy` (es. `0.5`)
    - Permettere a `Mario` di saltare solo quando è sul fondo
- Aggiungere `Wall`, personaggio immobile
- Quando `Mario` collide con una piattaforma...
    - Si sposta al bordo più vicino della piattaforma
    - Se atterra sul bordo superiore, da lì può saltare
