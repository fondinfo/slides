![](http://fondinfo.github.io/images/fun/juicer.svg)
# Funzioni
## Introduzione alla programmazione

---

![](http://fondinfo.github.io/images/fun/function.png)
# ⭐ Definizione di funzione

- *Operatore*, applicato a *operandi*, per ottenere un *risultato*
    - **`def`** per definire una funzione
    - **`return`** per terminare e restituire un risultato

``` py
from math import sqrt

def hypotenuse(a, b):
    c = sqrt(a ** 2 + b ** 2)
    return c
```

- Suddivisione di un problema in sotto-problemi
    - Astrazione rispetto all'implementazione
    - Generalizzazione e separazione della soluzione
    - Calcolo basato su parametri, modello

---

# ⭐ Chiamata di funzione

- **`def`** definisce una funzione, ma non la esegue!
- Bisogna *chiamarla*
- Funzione, quando eseguita, crea nuovo *spazio di nomi*
    - Parametri e variabili hanno **ambito locale**
    - Non visibili nel resto del programma
    - Nomi uguali, definiti in ambiti diversi, restano distinti
- ⚠️ Ricordarsi di assegnare il risultato a una variabile
    - ~ bicchiere per raccogliere la spremuta 🥤

``` py
side1 = float(input("1st side? "))
side2 = float(input("2nd side? "))
side3 = hypotenuse(side1, side2)  # call the function, get the result
print("3rd side:", side3)
```

---

![](http://fondinfo.github.io/images/fun/fun-hypotenuse.svg)
# 💡 Funzione principale

- Preferibile, per limitare le **variabili globali**
- *Procedura*, senza `return` (risultato `None`)

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
# ⭐ Parametri di una funzione

- **Parametri formali**: nomi usati nella *definizione*
- **Parametri effettivi**: valori passati alla *chiamata*
- Parametri passati “*per oggetto*”
    - Variabili esterne: non riassegnate
    - Azioni su oggetti mutabili: permanenti

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
# ⭐ Animazione

``` py
x, y, dx = 80, 80, 4  # sequence unpacking
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

# 💡 Tick, tastiera e mouse

- **`g2d.main_loop`**: *ciclo di gestione degli eventi*
    - Parametro opzionale: funzione che sarà chiamata periodicamente
- **`g2d.mouse_clicked`**: *controllo se il tasto sx del mouse è stato cliccato*
    - Risultato: `bool`
- **`g2d.mouse_pos`**: *posizione del mouse*
    - Risultato: `Point`
- **`g2d.current_keys`**: *tutti i tasti attualmente premuti*
    - Risultato: sequenza di `str` – [Possibili valori](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values)
    - Es.: `"q", "1", "ArrowLeft", "Enter", "Spacebar", "LeftButton"`
- **`g2d.close_canvas`**: *chiude il  canvas, termina l'esecuzione*

>

[**Documentazione g2d**](https://github.com/fondinfo/fondinfo#g2d)

---

![](http://fondinfo.github.io/images/hist/mcnulty.png) Kay McNulty <br> Subroutine per ENIAC
# 💡 Documentazione di funzione

- **Annotazioni**: utili per documentare il tipo di param. e risultato
    - Ma non c'è verifica!
- **Docstring**: descrizione testuale di una funzione
- **`help`**: funzione per visualizzare la documentazione

``` py
def hypotenuse(leg1: float, leg2: float) -> float:
    '''
    Return the hypotenuse of a right triangle,
    given both its legs (catheti).
    '''
    return sqrt(leg1 ** 2 + leg2 ** 2)

---

# 💡 Funzioni in moduli

- Ogni file Python è un *modulo*: nome del file, senza `.py`
- Se importato altrove, esecuzione `main` sotto condizione

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

![](http://fondinfo.github.io/images/fun/triangle-inequality.svg)
# 💡 Condizioni d'errore

- Precondizioni per attivazione non soddisfatte
- ⇒ Errore, instruzione **`raise`**
- Es. Triangolo errato

``` py
def triangle_perimeter(a: float, b: float, c: float) -> float:
    if a > b + c or b > a + c or c > a + b:
        raise ValueError("Not a triangle")
    return a + b + c

print(triangle_perimeter(4, 2, 1))
```

---

# 🧪 Risultato in tupla

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

# 🧪 Return multipli

- Una funzione può presentare più istruzioni `return`
- Alla prima incontrata, l'esecuzione termina e il controllo torna al codice chiamante
- Violazione accettabile della programmazione strutturata

``` py
def exceeds(data: list[int], limit: int) -> bool:
    for v in data:
        if v > limit:
            return True
    return False
```

- Viceversa, se non s'incontra `return` con risultato esplicito…
- Risultato implicito `None`: “*nessun valore*”

---

![](http://fondinfo.github.io/images/oop/anim-bounce.png)
# 🧪 Funzione per rimbalzi

- Le funzioni forniscono limitata astrazione
    - Incapsulano il comportamento
    - ❗ Ma espongono i dati

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

# 💡 Effetti collaterali

- Modifica di oggetti passati come parametri o variabili globali, operazioni di lettura/scrittura...
- Annullano la **trasparenza referenziale**
    - Impossibile semplificare, sostituendo una chiamata a funzione col suo valore di ritorno (es. presenti operazioni di I/O)
- Rendono la funzione **non idempotente**
    - Chiamata più volte, con gli stessi parametri, restituisce risultati diversi
- → Difficile fare verifiche matematiche
    - `z = f(sqrt(2), sqrt(2))`
    - `s = sqrt(2)` <br> `z = f(s, s)`

---

# 💡 Funzioni non idempotenti

- Esempio di semplificazione
    - `p = g(x) + g(y) * (g(x) - g(x))`
    - `p = g(x) + g(y) * (0)`
    - `p = g(x) + 0`
    - `p = g(x)`
- Ma se `g` ha effetti collaterali, non si può!

``` py
base_value = 0  # global variable

def g(x: int) -> int:
    global base_value
    base_value += 1
    return x + base_value
```

>

Ad esempio, con `x = 3` e `y = 4` i due risultati sono `-2` e `4`

---

# Funzioni trigonometriche

---

![](http://fondinfo.github.io/images/fun/sin-cos-tan-1.svg) ![](http://fondinfo.github.io/images/fun/sin-cos-tan-2.svg)
# 🧪 Coordinate polari

- Noti ipotenusa e angolo di un triangolo rettangolo
    - Con `cos` e `sin` si ricavano i cateti
- Sul piano cartesiano (o *raster*)
    - $x$ cateto adiacente, $y$ opposto, $r$ ipotenusa
- **Coordinate polari** di un punto: `$(r, \theta)$`
    - Distanza dall'origine e angolo
- Coord. *polari* `$(r, \theta)$` ⇒ *cartesiane* `$(x, y)$`
    - `$\begin{cases}x = r\cdot cos\theta \\ y = r\cdot sin\theta\end{cases}$`
- Coord. *cartesiane* `$(x, y)$` ⇒ *polari* `$(r, \theta)$`
    - `$\begin{cases}r = \sqrt{x^2 + y^2} = hypot(x, y) \\ \theta = atan2(y, x)\end{cases}$`

>

<https://github.com/tomamic/fondinfo/wiki/P03-Funzioni#coordinate-polari>

---

![](http://fondinfo.github.io/images/fun/move-around.svg)
# 🧪 Raggi sul canvas

- Spostamento `$(r, \theta)$` rispetto a `$(x_0, y_0)$`
    - *Traslazione*
- In modulo `math`, funzioni e costanti utili
    - `sin, cos, radians, pi`
    - `hypot, atan2, dist`
- Es. 4 raggi: stesso centro, stesso raggio, angoli diversi

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
# Funzioni su coord polari

- Funzioni più generali, astrazione migliore

```
Point = tuple[float, float]  # Pt in cartesian coords (x, y)
Polar = tuple[float, float]  # Pt in polar coords (r, angle)

def from_polar(plr: Polar) -> Point:
    r, angle = plr
    angle = radians(angle)
    return (r * cos(angle), r * sin(angle))

def move_around(start: Point, length: float, angle: float) -> Point:
    x0, y0 = start
    dx, dy = from_polar((length, angle))
    return x0 + dx, y0 + dy
```

- ❓ Riscrivere `draw_rays`, usando `move_around`

>

<https://fondinfo.github.io/play/?polar.py>

---

# 🏊 Esercizi su funzioni

---

![](/images/misc/thermometer.png)
# Funzione, Fahrenheit

- Definire una funzione `cels_to_fahr`
    - Parametro: temperatura Celsius, in `float`
    - Risultato: temperatura Fahrenheit, in `float`
- Invocare la funzione dalla shell interattiva
- Definire poi una funzione `main`
    - *Procedura, senza parametri e senza risultato*
    - Chiedere all'utente la temperatura Celsius
    - Poi chiamare `cels_to_fahr`
    - Infine mostrare all'utente il risultato

>

Partire dalla formula `fahr = cels * 1.8 + 32`

---

![](http://fondinfo.github.io/images/misc/ellipse.svg)
# Area di un'ellisse

- Definire una *funzione* `ellipse_area` che:
    - Riceve come *parametri* i semiassi di una ellisse:<br>`a`, `b`
    - Restituisce come risultato l'area dell'ellisse:<br>`π⋅a⋅b`
- Definire una *funzione* `main` che:
    - Chiede all'utente due valori
    - Invoca la funzione `ellipse_area` con questi parametri
    - Stampa il risultato ottenuto

---

![](http://fondinfo.github.io/images/misc/triangle-notations.svg)
# Perimetro di un triangolo

- Definire una *funzione* `triangle_perimeter` che:
    - Riceve come *parametri* i tre lati di un triangolo:<br>`a`, `b`, `c`
    - Restituisce come risultato il perimetro del triangolo
    - Se i tre lati non formano un triangolo, genera un `ValueError` <br> (se uno dei lati è maggiore della somma degli altri due)
- Definire una *funzione* `main` che, ciclicamente:
    - Chiede all'utente tre valori
    - Mostra il risultato di `triangle_perimeter` con questi parametri
    - Chiede all'utente se vuole elaborare altri dati, o terminare

---

# Gruppi di lettere

- Definire una funzione `count_groups`
    - Parametro testuale (`str`)
- Risultato: due valori
    - Quante lettere del testo sono comprese nel gruppo *A-M*
    - Quante lettere del testo sono comprese nel gruppo *N-Z*
- La funzione `count_groups` non distingue fra lettere maiuscole e minuscole
- Chiamare la funzione `count_groups` con un testo fornito dall'utente e mostrare i risultati

---

![](http://fondinfo.github.io/images/fun/comb-lock.svg)
# Parole di tre lettere

- Scrivere una funzione con un parametro di tipo `str`
    - La stringa rappresente un alfabeto di caratteri validi
- Genera la lista di tutte le parole
    - Di lunghezza esattamente uguale a 3
    - Composte con quei soli caratteri
- Se l'alfabeto contiene lettere ripetute, sollevare un `ValueError`

---

![](http://fondinfo.github.io/images/misc/perfect-squares.svg)
# Quadrato perfetto

- Scrivere una funzione `perfect_square`
    - Parametro: un numero
    - Verifica se si tratta di un *quadrato perfetto*
    - La sua radice quadrata è un numero naturale?
- Risultato: booleano, seguito da un numero
    - Radice perfetta del numero, se esiste
- Funzione `main` per eseguire `perfect_square`
    - Su un numero fornito dall'utente
    - Mostrare il risultato

>

Non usare `math.sqrt` e simili — Risolvere con una iterazione

---

# Divisori comuni

- Definire una funzione `common_divisors`
    - Prende due numeri naturali come parametri
    - Restituisce una lista con tutti i divisori comuni ai due numeri
- Funzione `main` per eseguire `common_divisors`
    - Su numeri fornito dall'utente
    - Mostrare il risultato

---

![](http://fondinfo.github.io/images/fun/polygon.svg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# Disegno di un poligono

- Definire una funzione `draw_polygon`
    - Parametri: numero dei lati, centro e raggio del cerchio circoscritto
    - Trovare i vertici attorno al centro con `move_around`
    - Unire i vertici per disegnare il poligono

---

![](http://fondinfo.github.io/images/misc/classical-watch.jpg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# Orologio classico

- Definire una funzione `draw_clock`
    - Disegnare 12 tacche a raggiera, come in un orologio classico
    - Miglioramento: disegnare anche le tacche dei minuti, più piccole

---

# 🏊 Esercizi su animazioni

---

![](http://fondinfo.github.io/images/draw/random-circles.svg)
# Cerchi al click

- Definire una funzione `tick`
- Quando il mouse viene cliccato…
- Se il mouse è vicino al centro del canvas…
    - Chiedere conferma all'utente
    - Se confermato, chiudere l'applicazione
- Altrimenti…
    - Disegnare un cerchio nella posizione del click
    - Con raggio fisso e colore casuale

---

![](http://fondinfo.github.io/images/misc/frogger.png)
# Veicolo in orizzontale

- Mostrare una tartaruga che si muove in orizzontale
    - Var. `dx`: spostamento a ogni frame
- Quando esce da un bordo, riappare dal bordo opposto, dopo un po'
    - Permettere di superare i bordi laterali
    - Se supera di 100px il bordo destro, ricompare a 100px prima del bordo sinistro e viceversa
- Al click del mouse, la tartaruga inverte la direzione
- Ritagliare l'immagine da `sprites.png`

``` py
g2d.draw_image("sprites.png", (x, y), (0, 20), (20, 20))
```

>

<https://github.com/fondinfo/fondinfo#images-and-sounds>

---

![](http://fondinfo.github.io/images/misc/space-invaders-school.png)
# Alieno

- Mostrare un alieno che si muove a serpentina
- Normalmente si sposta solo in orizzontale
- Quando arriva a un bordo laterale…
    - L'alieno scende di qualche pixel
    - Inverte la sua direzione orizzontale
- Evitare gli spostamenti in diagonale
    - Quando l'alieno scende, non si sposta in orizzontale
    - Quando si sposta in orizzontale, non scende
- Ritagliare l'immagine del fantasma da `sprites.png`

``` py
g2d.draw_image("sprites.png", (x, y), (20, 0), (20, 20))
```

---

![](http://fondinfo.github.io/images/misc/bouncing-ball.jpg)
# Rimbalzi con gravità

- Usando la funzione `tick` e variabili globali, mostrare una pallina che si muove e rimbalza sui bordi
    - La pallina subisce una accelerazione costante verso il basso
    - A ogni frame, aggiungere una piccola costante a `dy`
    - Simile all'effetto della gravità

---

![](http://fondinfo.github.io/images/misc/frogger.png)
# Movimento per 5 fotogrammi

- Mostrare una pallina che si muove in verticale
    - Variabile `dy` indica lo spostamento da effettuare a ogni frame
- La pallina si muove solo dopo il click del mouse
    - Si sposta solo per 5 fotogrammi
    - Dopo si ferma, fino a nuova pressione
- Invertire la direzione a ogni avvio del movimento

>

Incrementare (o decrementare) un contatore a ogni chiamata a `tick`

---

![](http://fondinfo.github.io/images/fun/polygon.svg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# Poligono in rotazione

- Chiede all'utente un numero $n$
- Mostrare un poligono regolare di $n$ lati in rotazione al centro del canvas
- Suggerimento
    - Riusare la funzione `draw_polygon`, già richiesta in un esercizio sulle funzioni
    - Rotazione, variando ultimo parametro della funzione (angolo del primo vertice)

---

![](http://fondinfo.github.io/images/games/climbing.svg)
# Free climbing

- Gara tra due arrampicatori, in forma grafica
- Due concorrenti, partono dal fondo del canvas
- Vince chi arriva prima in cima al canvas
- Nella funzione periodica `tick` generare due numeri casuali
    - Ciascun numero $∈ [-1, 3]$
    - Balzo in alto (o piccola discesa) di ciascun concorrente
    - Posizioni dei concorrenti sempre dentro i limiti del canvas
- Disegnare un cerchio o una immagine nella posizione di ogni concorrente
