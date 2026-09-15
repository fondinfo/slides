![](http://fondinfo.github.io/images/dev/python-logo.svg)
# Basi
## Introduzione alla programmazione

---

![large](http://fondinfo.github.io/images/dev/python-cases.png) Web, data science, machine learning, scripting, teaching, games, hardware, multiplatform…
# 💡️ Python is fun!

![](http://fondinfo.github.io/images/algo/antigravity.png)

>

<https://xkcd.com/353/>

---

# 🧪 Shell interattiva

- Installare [Thonny](https://thonny.org/) o usare il [Playground](https://fondinfo.github.io/play/) online
    - In basso, interfaccia interattiva *REPL* (Read-Eval-Print Loop)
- **Tipo di dato** : insieme di *valori* + *operazioni* ammesse
- Tipi numerici: **`int`** o **`float`**, per numeri interi o razionali
    - Operazioni di base: `+, -, *, /`
    - Divisione intera, resto, potenza: `//, %, **`
- Commenti descrittivi, dopo `#` : non valutati

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

# 🧪 Valori booleani e None

- Tipo **`bool`**, per valori booleani: `True, False`
    - Operatori logici: `and, or, not` (→ [Logica](t11-logica.html))
- Confronti: `==, !=, <, <=, >, >=`
    - Solo tra valori omogenei; risultato booleano
    - Confronti concatenabili, sottinteso `and`
- Valore **`None`**, unico del tipo `NoneType`: *niente*

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
# ⭐ Assegnamento

- Una **variabile** serve per ricordare un risultato utile
- *Assegnamento* : operatore **`=`**
    - Alla sinistra un *nome*
    - Alla destra una espressione (→ *valore*)
- **⚠️ Non confondere**
    - Confronto di *uguaglianza* : operatore **`==`**

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
# 🔬 Variabile

- **Nome** associato a un certo **valore**
    - 🏷️ *Etichetta* → *oggetto*
- Oggetto assegnato a più variabili
    - Non viene copiato, ma riceve più etichette
- Il **tipo** dipende dal valore attualmente assegnato
    - Una var non dev'essere *dichiarata*
    - Ma dev'essere *inizializzata* prima dell'uso
- *Riassegnamento* : nuovo valore a var già esistente

``` py
>>> x = None           # no actual value, yet…
>>> x = 100            # variables: all_lower_case
>>> next_position = x  # use explicative names!
>>> DELTA_X = 5        # constants: ALL_UPPER_CASE
>>> x += DELTA_X       # shortcut for: `x = x + DELTA_X`
>>> a, b = 5, 8        # multiple assignments
```

---

# 🧪 Stringhe di testo

- Tipo **`str`** per sequenze di caratteri
- Racchiuse tra apici doppi, o singoli
- Concatenazione: operatore `+`
- Test di appartenenza (sottostringa): operatore `in`
- Lunghezza: *funzione* `len`

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

# ⭐ Funzioni predefinite

- Funzioni [built-in](https://docs.python.org/3/library/functions.html): `max, min, abs, len, round`…
- Funzioni per conversione di tipo (*cast*): `int, float, str`…
- Parametri tra *parentesi*, separati da *virgola*
- Tipicamente, risultato assegnato a variabile

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

# ⭐ Metodi

- In Python tutti i valori sono *oggetti*
    - Tipi diversi → operazioni diverse, come *metodi*
- Attivazione di un metodo di un oggetto
    - Oggetto e metodo separati da “`.`”
    - Poi parametri tra parentesi
    - Tipicamente, risultato assegnato a variabile
- [Metodi di oggetti `str`](https://docs.python.org/3/library/stdtypes.html#string-methods): `upper`, `lower`, `count`…

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
# ⭐ Lista

- Sequenza **mutabile** di valori *omogenei*
- Elementi tra *quadre*, separati da *virgole*
- Aggiunta, rimozione: `append, remove`
- Lunghezza: `len` ­– Test di appartenenza: `in`

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

# 🧪 Leggere e scrivere

- **`input`** legge una riga di *testo*, inserita dall'utente, in una *variabile*
    - Prima mostra un messaggio
    - Risultato di tipo `str`
- **`print`** scrive una serie di valori su una riga
    - Inserisce spazio tra i valori (parametri)

``` py
>>> knight = input("What is your name? ")
What is your name? Lancelot
>>> print("Right. Off you go,", knight, ".")
Right. Off you go, Lancelot .
```

---

![](http://fondinfo.github.io/images/algo/sum3.svg)
# 🧪 Somma di tre numeri

- Salvare il programma seguente come “`sum3.py`”
- Eseguire, cliccando il bottone ▶️
    - Oppure da riga di comando: `python sum3.py`

``` py
a = float(input("Insert 1st val: "))
b = float(input("Insert 2nd val: "))
c = float(input("Insert 3rd val: "))

total = a + b + c

print("The sum is", total)
```

- **⚠️ Attenzione ai tipi**
    - ❓ Cosa succede, senza conversione in `float`?

>

<https://fondinfo.github.io/play/?c02_sum3.py>

---

# Moduli

---

![large](http://fondinfo.github.io/images/repr/raster-coords.svg) ![large](http://fondinfo.github.io/images/repr/color-mixing.svg)
# ⭐ Disegno su canvas

- **Coordinate raster**
    - Origine in alto a sinistra
- **Sintesi additiva dei colori**
    - Primari: *Red, Green, Blue*
- Useremo un modulo *ad-hoc*: `g2d`
    - Definisce funzioni di disegno
- Nel [playground](https://fondinfo.github.io/play/?c02_draw.py), versione integrata
- *Esecuzione locale*
    - ⬇️ Salvare nella cartella di lavoro <br> il file [`g2d.py`](https://github.com/fondinfo/fondinfo/blob/master/g2d.py)
- [**Documentazione g2d**](https://github.com/fondinfo/fondinfo#g2d)

---

![large](http://fondinfo.github.io/images/repr/pixel-grid.png)
# ⭐ Tupla

- Sequenza **immutabile** di valori
    - Anche di *tipo diverso*
- Spesso tra parentesi
    - Per separarla da altro codice
- Utili anche per grafica:
    - *Posizione*: `(x, y)`
    - *Dimensione*: `(width, height)`
    - *Colore*: `(red, green, blue)` <br> Ogni componente nel range `0..255`

``` py
center_pt = (320, 240)  # packing
window_size = (640, 480)
bluette_color = (47, 102, 207)
x, y = center_pt  # sequence unpacking -- also for lists and other iterables
```

---

# 🧪 Rettangoli e cerchi

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
# 🧪 Linee e testi

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

# 🧪 Finestre di dialogo

- `g2d.prompt`: richiesta di *input*, in finestra, risultato `str`
- `g2d.alert`: visualizzazione *messaggio*, singolo parametro `str`
- `g2d.confirm`: richiesta di *conferma*, risultato `bool`

``` py
import g2d

g2d.init_canvas((600, 400))

name = g2d.prompt("What's your name?")
g2d.alert("Hello, " + name + "!")

g2d.main_loop()
```

- [**Documentazione g2d**](https://github.com/fondinfo/fondinfo#g2d)

---

![](http://fondinfo.github.io/images/algo/calculator.svg) [☞ `math`](https://docs.python.org/3/library/math.html)
# 🧪 Battery included 🔋

- Modulo [`math`](https://docs.python.org/3/library/math.html) in *Python Standard Library*
    - Non necessita d'installazione
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

- `import` all'inizio, per evidenziare dipendenze
    - **`import …`** : intero *namespace* del modulo
    - **`from … import …`** : solo alcuni nomi

---

![](http://fondinfo.github.io/images/algo/red-dice.svg) [☞ `random`](https://docs.python.org/3/library/random.html)
# 🧪 Random 🎲

- Modulo [`random`](https://docs.python.org/3/library/random.html) in *Python Standard Library*
    - Non necessita d'installazione
    - `randint, randrange, random, choice, shuffle`…

``` py
from random import randint, randrange, choice

die1 = randint(1, 6)  # like rolling a die
die2 = randint(1, 6)  # like rolling a die

one_of_three = randrange(3)  # 0, 1, or 2

prime = choice([2, 3, 5, 7, 11, 13])  # one from a sequence
```

---

# ⭐ Strutture di controllo

---

![](http://fondinfo.github.io/images/algo/if.svg)
# ⭐ Selezione: if

- Corpo di `if` o `else`: **indentazione**
    - Richiesta per *sintassi*, non opzionale
    - Può contenere qualsiasi istruzione
    - Anche altri blocchi `if` o `while` annidati!

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
# ⭐ Selezione: else

- Clausola `else`: opzionale
    - Eseguita sse la condizione non è verificata

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
# ⭐ Selezione: elif

- `elif` : contrazione di `else if`
    - Selezione tra *molteplici* alternative
    - Se nessuna condizione vera, eseguito `else`
- Es. Lancio di *due dadi* → 3 alternative
    - Vittoria del 1° dado, del 2°, o pareggio

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
# ⭐ Iterazione: while

- Condizione di *permanenza* nel ciclo
    - Controllo *preliminare*
    - Possibile che il corpo non sia mai eseguito

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
# ⭐ Iterazione: for

- Opera solo su **sequenze e iterabili**
    - `list, tuple, str, range`…
    - Num. iterazioni = lunghezza sequenza
- Variabile di iterazione
    - A ogni iterazione, nuovo valore da sequenza

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

# ⭐ Intervallo di valori

- **`range`** : intervallo di valori aperto a destra
    - Estremi: inferiore *incluso* (0), superiore *escluso*
    - Se estremo inferiore ≠ 0, servono due parametri
- *`reversed`* : sequenza rovesciata

``` py
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)
```

``` py
for i in reversed(range(5)):  # 4, 3, 2, 1, 0
    print(i)
```

---

![](http://fondinfo.github.io/images/draw/red-squares.svg)
# 🧪 Sequenza di quadrati

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

- ❓ Cosa succede se usiamo `reversed` nel `for`?

>

<https://fondinfo.github.io/play/?c02_squares.py>

---

![large](http://fondinfo.github.io/images/misc/slope.svg)
# 🧪 Formule utili

- Distanza tra due punti

``` py
x1, y1 = 150, 400
x2, y2 = 550, 100
```

``` py
from math import dist
p1 = (x1, y1)
p2 = (x2, y2)
d = dist(p1, p2)
```

``` py
from math import sqrt
dx = x2 - x1
dy = y2 - y1
d = sqrt(dx ** 2 + dy ** 2)
```

---

# 🏊 Esercizi

---

![](http://fondinfo.github.io/images/misc/handshake.svg)
# Hello, admin!

- Scrivere un programma in un file `hello.py`
- Chiedere il nome all'utente
- Inserire tale nome in un messaggio di saluto, p.es.:

``` txt
What's your name? Adam
Hello, Adam!
```

- Se il nome dell'utente è “`admin`”…
    - Mostrare inoltre il messaggio speciale “`At your command`”

---

![](http://fondinfo.github.io/images/misc/greek-pi.png)
# Cerchio

- Chiedere all'utente il valore del raggio `r` di un cerchio
    - `r` razionale compreso tra 0 e 200
- Se `r` è valido
    - Visualizzare il cerchio, al centro del canvas
    - Appena sopra al cerchio, scrivere il valore della sua area
    - Appena sotto al cerchio, scrivere il valore della sua circonferenza
- Se invece `r` è fuori range
    - Mostrare un messaggio d'errore

---

![](http://fondinfo.github.io/images/games/dragon.svg)
# L'anno del drago

- Il programma chiede all'utente il suo anno di nascita
- Poi comunica se quell'anno era sotto il segno del drago, oppure no
- Sappiamo che, secondo la tradizione cinese, il 2024 è l'anno del drago
- Sappiamo inoltre che il segno si ripete ogni 12 anni

---

![large](http://fondinfo.github.io/images/algo/holy-grail.jpg)
# The Bridge of Death

- Porre tre domande all'utente:
    - `"What is your name?"`
    - `"What is your quest?"`
    - `"What is your favorite color?"`
- Se le risposte sono `"Lancelot"`, `"Holy Grail"` e `"Blue"`, stampare:
    - `"Right. Off you go."`
- Altrimenti, stampare:
    - `"Down into the Gorge of Ethernal Peril!"`

>

Prima versione: chiedere e controllare solo il nome

---

![](http://fondinfo.github.io/images/misc/calendar-cols.png)
# Calcolo dell'età

- Chiedere all'utente la sua data di nascita
    - Anno, mese e giorno
- Chiedere all'utente la data di oggi
    - Anno, mese e giorno
- Comunicare l'età esatta attuale
    - Numero di compleanni già compiuti

>

Nell'anno corrente, l'utente ha già avuto il compleanno?
<br>
Espressione booleana composta con `and`, `or`, `not`…

---

![](http://fondinfo.github.io/images/misc/three-brothers.png)
# Minore e maggiore

- Generare e stampare tre numeri interi casuali: `a`, `b`, `c`
- Ciascuno compreso tra 1 e 6
- Determinare e mostrare qual è il minore dei tre

>

Controllare prima di tutto se `a` è minore degli altri due
<br>
Altrimenti controllare se `b` è minore di `c`
<br>
Altrimenti…

---

![](http://fondinfo.github.io/images/draw/random-squares.svg)
# Quadrati casuali

- Chiedere all'utente un numero `n`
- Disegnare `n` quadrati
    - Tutti con lato di 100 pixel
    - Ciascuno in posizione casuale
    - Ciascuno con un colore casuale

>

Cominciare a disegnare un solo quadrato grigio, in posizione casuale

---

![](http://fondinfo.github.io/images/draw/diagonal-squares.svg)
# Quadrati in diagonale

- Chiedere all'utente un numero `n`
- Su un canvas 500×500, disegnare `n` quadrati
    - Tutti con lato di 50 pixel
    - Disposti lungo la diagonale, in modo da condividere sempre un vertice
    - Ciascuno con un colore casuale
- Opzionalmente, determinare il lato in modo da occupare tutta la diagonale

---


![large](http://fondinfo.github.io/images/draw/segments-1.svg)
# Segmenti casuali

- Chiedere all'utente il numero di segmenti da disegnare
- Disegnare i segmenti
    - Tutti con lo stesso colore, nero
    - Ciascuno con entrambi gli estremi in posizione casuale
    - Ma interamente contenuto nel canvas

---

![large](http://fondinfo.github.io/images/draw/segments-2.svg)
# Linea spezzata

- Chiedere all'utente il numero di segmenti da disegnare
- Disegnare i segmenti come una linea spezzata, in nero
    - Iniziare da un punto casuale e congiungerlo con un successivo punto casuale
    - Proseguire a congiungere l'ultimo punto con un nuovo punto casuale
- La linea deve essere interamente contenuta nel canvas
